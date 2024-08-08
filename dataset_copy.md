# Copy a ZFS Dataset

ZFS datasets are copied by means of snapshots.  This is the method to use if you want a fully indipendent 'clone' (copy) of your dataset.  They can even be copied across diffrent volumes and machines

```
# Take a snapshot of a single dataset (no children)
zfs snapshot MyPool/Dataset@copy

# Or the entire pool
zfs snapshot -r MyPool@copy
```

Use the `send` and `receive` commands to make the copy

```
# Set a new mount location while we are at it
zfs send -R MyPool/MyDataset@copy | zfs receive -o mountpoint=/mnt/dataset_copy DifferentPool/MyDataset
```

Delete the snapshot

```
zfs destroy MyPool/Dataset@copy
```
