# ZipROFS

This is a FUSE filesystem that acts as pass through to another FS except it
expands zip files like folders and allows direct transparent access to the contents.

### Dependencies
* FUSE (fuse2 works, not tested with fuse3)
* python3-fusepy

### Limitations
* Read only
* Nested zip files are not expanded, they are still just files

### Example usage
```shell
$ ./ziprofs.py ~/root ~/mount -o allowother
```

You can later unmount it using:
```shell
$ fusermount -u ~/mount
```

Full help:
```shell
$ ./ziprofs.py -h
usage: ziprofs.py [-h] [-o options] [ROOT] [MOUNTPOINT]

ZipROFS read only transparent zip filesystem.

positional arguments:
  ROOT        filesystem root (default: None)
  MOUNTPOINT  filesystem mount point (default: None)

optional arguments:
  -h, --help  show this help message and exit
  -o options  comma separated list of options: foreground, debug, allowother
              (default: None)
```