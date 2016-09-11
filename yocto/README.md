Beaglebone yocto-project
===

[https://www.yoctoproject.org](https://www.yoctoproject.org)

[youtube:비글본(beaglebone) 기반의 욕토(YOCTO) 이미지 만들기](https://youtu.be/U8a3Yh-OIfQ?list=PLStpXMov8iUJKrM48U3Z4i3gEj54uazML)

[Intel:Getting started with yocto project](http://d.pr/v/1hLPs/4fgFcAwr+)

```
욕토 이미지 다운로드
$ git clone -b fido git://git.yoctoproject.org/poky.git
$ cd poky/

타겟설정및 빌드
$ . ./oe-init-build-env ../build-poky
$ MACHINE=beaglebone bitbake core-image-sato; while : ; do echo -e "\007"; sleep 1; done
$ cd build-poky/
$ cd tmp/deploy/images/beaglebone/
$ ls
$ mkdir BOOTDISK
$ mkdir -p BOOTDISK/boot_img
$ mkdir -p BOOTDISK/rootfs_img
$ cp MLO-beaglebone-v2015.01+gitAUTOINC+92fa7f53f1-r0 BOOTDISK/boot_img/MLO
$ cp u-boot-beaglebone-v2015.01+gitAUTOINC+92fa7f53f1-r0.img BOOTDISK/boot_img/u-boot.img
$ cp zImage--3.14.36+git0+162dfe3bb0_dbe5b52e93-r0-beaglebone-20151023181721.bin BOOTDISK/boot_img/zImage
$ cp zImage--3.14.36+git0+162dfe3bb0_dbe5b52e93-r0-am335x-boneblack-20151023181721.dtb BOOTDISK/boot_img/am335x-boneblack.dtb
$ tar jxf core-image-sato-beaglebone-20151023020257.rootfs.tar.bz2 -C BOOTDISK/rootfs_img

이미지 SDCARD 제작
$ sudo ./create-sdcard.sh 
```
