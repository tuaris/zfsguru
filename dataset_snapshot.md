# Take Snapshot of a Dataset

Perform a quick backup of your ZFS dataset prioir to doing something experimental or destructive with your data.

```
# Snaphot jsut the one dataset
zfs snapshot MyPool/MyDataset@MyFirstBackup
```

```
# Snapshot the dataset and it's decendents
zfs snapshot -r MyPool/ParentDataset@MyFirstBackup
```

Save the snapshot to a backup location

```
# Compress it to save space
zfs send -Rv MyPool/MyDataset@MyFirstBackup | xz > /var/backups/zfs/mydataset.snap.xz
```

Create a clone so you can modify to your snapshot without actually affecting the snapshot

```
zfs clone MyPool/MyDataset@MyFirstBackup
```

Delete the snapshot (careful! also deletes any clones)

```
# A single snapshot
zfs destroy MyPool/MyDataset@MyFirstBackup
```

```
# Multiple snapshots (decendents)
zfs destroy -r MyPool/ParentDataset@MyFirstBackup
```
