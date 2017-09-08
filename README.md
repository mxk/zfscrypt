zfscrypt
========

Multi-disk encryption management tool for ZFS.

Until native ZFS encryption is implemented in FreeBSD, disks must be encrypted
using [geli(8)](https://www.freebsd.org/cgi/man.cgi?query=geli). This script
provides commands for managing multiple encrypted disks as one unit (i.e.
without requiring multiple passphrases).

Disks are encrypted using keyfiles, which are kept in an encrypted keystore. The
keystore is a small file-backed memory disk containing a UFS2 file system. To
attach ZFS disks, the user enters their passphrase for the keystore, which then
provides access to the keyfiles. A backup copy of the keystore is maintained in
a dedicated partition on each member disk.

For more information run `zfscrypt help`.

Example
-------

```
zfscrypt newks
zfscrypt init ada0 ada1 ada2
zfscrypt attach
zpool create tank raidz /dev/gpt/*.eli
```
