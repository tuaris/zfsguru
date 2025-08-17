# Creating new ZFS Pools

Create a pool with two devices in mirror, and mount on a give path, while turning on auto expand.

```
zpool create -m /mnt/data -o autoexpand=on Data mirror da1 da2
```

Create a single device pool that will be mounted at `/Data`.

```
zpool create Data da1
```
