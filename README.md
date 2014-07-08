target-scripts
==============

Basic shell scripts to play with the Linux target subsystem.

target-export-device
--------------------

The preferred way to create an iSCSI target on Linux is to use
[targetcli](https://github.com/agrover/targetcli-fb). However, in some
situations, targetcli may not be available (for instance, in an
initramfs which is too small to contain a Python interpreter).

target-export-device is a simple shell script to export a block device
as an iSCSI target:

    $ target-export-device /dev/sdb
    Target iqn.2003-01.org.linux-iscsi.hostname:sdb has been created

The target created by target-export-device contains a single LUN and a
single portal group. There is no ACL: all initiators can connect to
the target and write to the LUN. Thus, the script should only be used
for testing purposes.
