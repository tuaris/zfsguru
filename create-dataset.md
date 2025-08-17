# Creating ZFS Datasets

Add a dataset named `opensearch` under the `Data` pool with compresson set to `lz4` and mounted at `/var/db/opensearch`

```
zfs create -o compression=lz4 -o mountpoint=/var/db/opensearch Data/opensearch
```
