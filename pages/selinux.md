---
title: How to fix selinux / denial address
permalink: help/selinux/
---

## Need
- Terminal like termux
- [Fixer](https://github.com/baalajimaestro/selinux-denial-fixer)
- python installed on termux or on ur PC

## Step by Step
### Take a log
Open terminal and take log with this command
```
dmesg | grep 'avc: ' >> /sdcard/denials.txt
```
### Fixer
if u have the log now git clone [Fixer](https://github.com/baalajimaestro/selinux-denial-fixer) and put the log file in the same folder and run this command
```
python denials.py
```
if done there will be a new file called `fixes.txt`
### Implement on tree
You only edit on folder `selinux/vendor` or `selinux` on your tree
i will give you example `fixes.txt` on `hal_fingerprint_default.te`
```
allow hal_fingerprint_default gx_fpd_device:chr_file rw_file_perms;
allow hal_fingerprint_default fpc_sysfs:dir r_dir_perms;
allow hal_fingerprint_default fpc_sysfs:file rw_file_perms;
allow hal_fingerprint_default fingerprintd_data_file:file create_file_perms;
allow hal_fingerprint_default fingerprintd_data_file:dir rw_dir_perms;
allow hal_fingerprint_default fpc_data_file:dir rw_dir_perms;
allow hal_fingerprint_default tee_device:chr_file rw_file_perms;
allow hal_fingerprint_default property_socket:sock_file write;
allow hal_fingerprint_default init:unix_stream_socket connectto;
allow hal_fingerprint_default self:netlink_socket create_socket_perms_no_ioctl;
allow hal_fingerprint_default vndbinder_device:chr_file rw_file_perms;
allow hal_fingerprint_default uhid_device:chr_file rw_file_perms;
```
You see on `fixer.txt` like this, what do you have to do?
You only create files that are `.te format` with the name taken from the fixer _allow `hal_fingerprint_default` gx_fpd_device:chr_file rw_file_perms;_ the red one is the folder name dnd do it over and over again until it's done