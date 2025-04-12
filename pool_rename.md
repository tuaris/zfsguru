# Rename a ZFS Pool

Change the name of an existing ZFS pool.  You must unmount (export) the pool before renaming.

```
# Rename "MyPool" to "BetterPool"
zpool export MyPool
zpool import MyPool BetterPool
```

