# op7t

oneplus 7t 自定义内核

## 手机环境

a. oneplus 7t

b. 对应Android版本为Hydrogen OS 10.0.7.HD65

<img src="https://cdn.jsdelivr.net/gh/yhnu/PicBed/images20210907091421.png" height="400" />

c. 对应版本全量包

```shell
OnePlus7THydrogen_14.H.09_OTA_009_all_2001030048_d935aae55ac_1007.zip //一加手机论坛下载
```

## Linux编译环境

1. 操作系统ubuntu20

```shell
➜  /share cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=20.04
DISTRIB_CODENAME=focal
DISTRIB_DESCRIPTION="Ubuntu 20.04 LTS"
```

2. 依赖安装

```shell
sudo apt-get install git-core gnupg flex bison build-essential zip curl zlib1g-dev gcc-multilib g++-multilib libc6-dev-i386 libncurses5-dev lib32ncurses5-dev x11proto-core-dev libx11-dev lib32z1-dev libgl1-mesa-dev libxml2-utils xsltproc unzip fontconfig

sudo apt-get install libssl-dev
sudo apt-get install dos2unix
sudo apt-get install libncurses5
```

3. 编译依赖

链接: https://pan.baidu.com/s/1RQaPSjLPNX99XBVCCAcoZA 提取码: bbki 复制这段内容后打开百度网盘手机App，操作更方便哦

```shell
cd /share
git clone https://gitee.com/yhnu/op7t.git //这里不行,只能网盘存储了
cd /share/op7t/buildtool
just c
```

4. 编译源码

为了简单方便及稳定,我们基于第三方内核进行修改, [https://github.com/engstk/op7/tree/r70](https://github.com/engstk/op7/tree/r70)

```shell
cd /share/op7t/blu7t
just c
source env.config
source proxy.config
just make
just j16
```

5. 打包image

```shell
just image
```

## boot.img提取

```shell
curl -L -O https://github.com/yhnu/op7t/releases/download/v1.0/payload_dumper-win64.zip
curl -L -O https://otafsc.h2os.com/patch/CHN/OnePlus7THydrogen/OnePlus7THydrogen_14.H.09_009_2001030048/OnePlus7THydrogen_14.H.09_OTA_009_all_2001030048_d935aae55ac.zip
unzip -q OnePlus7THydrogen_14.H.09_009_2001030048/OnePlus7THydrogen_14.H.09_OTA_009_all_2001030048_d935aae55ac.zip
# 然后参考payload_dumper的使用说明即可
```
