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
