# 查看 Ubuntu 系统配置

## CPU

cat \proc\cpuinfo \| more

* processor 逻辑 CPU 编号
* sibilings 每个物理 CPU 拥有的逻辑 CPU 数目
* CPU cores 每个物理 CPU 拥有的核数
* physical id 物理 CPU 编号
* model name 型号及最大运行速度
* cpu MHZ 当前运行速度

_CPU可使用超线程技术，每个核可以对应多个逻辑 CPU,即 sibilings/CPU cores_

_逻辑 CPU 数即最大并行线程数_

## GPU

* 一般GPU:  lspci \| grep -i vga
* nvidia 没有视频输出的 GPU 如 Tesla 系列：lspci \| grep -i nvidia

查看 nvidia GPU 可用 nvidia 自带的命令

* nvidia-smi
* watch -n 10 nvidia-smi 或者nvidia-smi -l 10（动态查看占用信息）

## 硬盘

* df -l
* sudo fdisk -l

## 版本号

cat /etc/issue

sudo lsb\_release -a

