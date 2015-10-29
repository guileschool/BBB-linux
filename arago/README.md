Beaglebone arago-project
===
```
욕토 이미지 다운로드
$ git clone git://arago-project.org/git/projects/oe-layersetup.git 
$ ./oe-layertool-setup.sh -f configs/amsdk/amsdk-08.00.00.00-config.txt 

컴파일러 설치
$ cd /work/beagleboard.Mydata/ti-sdk/ti-sdk-am335x-evm-08.00.00.00
$ sudo ./linux-devkit.sh 

타겟설정및 빌드
$ cd build
$ source conf/setenv 
$ MACHINE=am335x-evm bitbake core-image-minimal ( core-image-sato )
혹은
$ MACHINE=beaglebone bitbake core-image-minimal ( core-image-sato )

빌드시 오류및 대처
빌드 과정에서 다음과 같은 오류가 발생하며 ... 
ERROR: Logfile of failure stored in: /work/yocto/oe-layersetup/build/arago-tmp-external-linaro-toolchain/work/cortexa8t2hf-vfp-neon-oe-linux-gnueabi/external-linaro-toolchain/2013.03-r2-arago7/temp/log.do_install.11911
Log data follows:
| DEBUG: Executing shell function do_install
| cp: cannot stat `/usr/local/arago-2015.02/sysroots/i686-arago-linux/usr/arm-linux-gnueabihf/libc/usr/share/*': No such file or directory

이에 대한 대책은 다음과 같다
$ sudo mkdir -p /usr/local/arago-2015.02/sysroots/i686-arago-linux/usr/arm-linux-gnueabihf/libc/usr/share/; sudo touch /usr/local/arago-2015.02/sysroots/i686-arago-linux/usr/arm-linux-gnueabihf/libc/usr/share/touch
다시 빌드를 시작한다

이미지 SDCARD 제작
$ cd arago-tmp-external-linaro-toolchain/deploy/images

$ sudo tar zxf core-image-minimal-am335x-evm-20151022001648.rootfs.tar.gz -C /media/user/rootfs/

```

