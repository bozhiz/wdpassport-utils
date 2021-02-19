How to unlock \`WD My Passport Drive\` on Linux

By default `WD My Passport Drive` supports only Windows and OS X. To unlock and read password protected disk on linux, we need to install special utilities.

# Refer

https://github.com/0-duke/wdpassport-utils

https://github.com/evox95/wdpassport-utils

# Get utils for `WD My Passport Drive`

## Install Python3

```
sudo apt install python3 python3-dev python3-pip git
```



## Install py_vg

```
sudo pip3 install --user git+https://github.com/crypto-universe/py_sg
```



## Install utils

```
sudo pip3 install git+https://github.com/0-duke/wdpassport-utils

or 
download to ~/wdpassport-utils.py
chmod u+x ~/wdpassport-utils.py
```

# Usage

* plugin WD Passport Drive

* lsscsi

  ```
  lsscsi
  [0:0:0:0]	disk	WD 	My Passport 2626	1028	/dev/sda
  [0:0:0:1]	cd/dvd	WD 	Virtual CD 2626		1028 	/dev/sr0
  [0:0:0:1]	cd/dvd	WD 	SES Device			1028 	-
  ```

* unlock

  ```
  sudo ~/wdpassport-utils.py -u -d /dev/sda
  ```

* list

  ```
  sudo fdisk -l
  
  Disk /dev/sda: 1.8 TiB, 2000365289472 bytes, 3906963456 sectors
  Units: sectors of 1 * 512 = 512 bytes
  Sector size (logical/physical): 512 bytes / 512 bytes
  I/O size (minimum/optimal): 512 bytes / 512 bytes
  Disklabel type: gpt
  Disk identifier: 4FE9C9B5-771F-4B47-BA68-1D823FB24967
  
  Device     Start        End    Sectors  Size Type
  /dev/sda1   2048 3906961407 3906959360  1.8T Microsoft basic data
  ```

* mount

  ```
  sudo mount /dev/sda1 /mnt
  
  # mount -l | grep "/dev/"
  /dev/sr0 on /media/bozhizheng/WD Unlocker type udf (ro,nosuid,nodev,relatime,uid=1001,gid=1001,iocharset=utf8,uhelper=udisks2) [WD Unlocker]
  /dev/sda1 on /mnt type fuseblk (rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096) [My Passport]
  ```

* list

  ```
  ll /mnt
  ```

* umount

  ```
  sudo umount /mnt
  sudo umount /dev/sr0
  ```


* eject


