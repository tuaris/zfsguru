# Manage ZFS Dataset Properties

View all properties for the dataset named `Data/Logs`

```
zfs get all Data/Logs
```

Check current `compression` property value for the `Storage` dataset

```
zfs get compression Data/Logs
```

View the `compression` and `mountpoint` property values for the `Data/ValKey` dataset

```
zfs get compression,mountpoint Data/ValKey
```

Change the `mountpoint` to `/mnt/stuff` for the `MyStuff` dataset

```
zfs set mountpoint=/mnt/stuff MyStuff
```

Enable LZ4 compression and change the Mount point to `/var/backups` for the `Storage/Backups` dataset

```
zfs set compression=lz4 mountpoint=/var/backups Storage/Data
```
