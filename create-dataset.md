# Creating ZFS Datasets

Add a dataset named `Stuff` under the `Data` pool.

```
zfs create Data/Stuff
```

Add a dataset for ValKey (Redis) named `valkey` under the `Data` pool and mount it at `/var/db/valkey`

```
zfs create -o mountpoint=/var/db/valkey Data/valkey
```

Add a dataset named `OpenSearch` under the `Storage` pool, but do not allow it to be mounted and don't set a mountpoint.  Set default compression property as `lz4` to be inhearited by children

```
zfs create -o mountpoint=none -o canmount=off -o compression=lz4 Storage/OpenSearch
```

Add a dataset named `Data` under the `Storage/OpenSearch` dataset and mount it at `/var/db/opensearch`.  (Note: if the parent has `compression=lz4`, this dataset will inherit that property)

```
zfs create -o mountpoint=/var/db/opensearch Storage/OpenSearch/Data
```

Add a dataset for MariaDB (MySQL) with a block size of 16k and 2 copies of all data, while setting compression to `lz4`

```
zfs create -o mountpoint=/var/db/mysql -o compression=lz4 -o recordsize=16k -o copies=2 Data/mariadb
```

Here's a tip that will prevent a disater should your dataset not mount (for whatever reason).  This command uses extended atrributes to lock the directory so nothing (not even root) can write to it.

```
# Make sure you run this BEFORE creating or mounting your dataset
install -d /path/to/location
chflags schange /path/to/location
```

To undo the above, just run

```
# Make sure your dataset is not mounted BEFORE running this
chflags noschange /path/to/location
```
