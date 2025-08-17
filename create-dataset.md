# Creating ZFS Datasets

Add a dataset named `opensearch` under the `Data` pool with compresson set to `lz4` and mounted at `/var/db/opensearch`

```
zfs create -o compression=lz4 -o mountpoint=/var/db/opensearch Data/opensearch
```

Add a dataset for MariaDB (MySQL) with a block size of 16k and 2 copies of all data, while setting compression to `lz4`

```
zfs create -o mountpoint=/var/db/mysql -o compression=lz4 -o recordsize=16k -o copies=2 Data/mariadb
```

Add a dataset for ValKey (Redis) with compression (default `off`) and other properties inheriting defaults from the parent dataset or pool

```
zfs create -o mountpoint=/var/db/valkey Data/valkey
```
