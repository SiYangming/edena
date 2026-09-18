# Edena V3 (build 131028) 安装与使用备忘

上游发行包：`EdenaV3.131028.tar.gz`（497,784 B）

- SHA-256：`4037fce486c9725107b1690fbc67731713eef54e3fa53081865904c783533230`
- 该压缩包不在代码树中，见 Release `v3.131028` 附件
- 上游下载地址：http://www.genomic.ch/edena.php

## 下载

本仓库地址：https://github.com/SiYangming/edena

从本仓库 Release 下载压缩包：

```bash
wget https://github.com/SiYangming/edena/releases/download/v3.131028/EdenaV3.131028.tar.gz

# 或
curl -L -O https://github.com/SiYangming/edena/releases/download/v3.131028/EdenaV3.131028.tar.gz
```

克隆完整源码树：

```bash
git clone https://github.com/SiYangming/edena.git
```

## 方法一：源码编译安装

```bash
# /path/to/install 为自选安装目录
tar zxf path/to/EdenaV3.131028.tar.gz -C /path/to/install/
cd /path/to/install/EdenaV3.131028/
make -j 4
cp src/edena bin/

# 添加环境变量
echo 'PATH=$PATH:/path/to/install/EdenaV3.131028/bin/' >> ~/.bashrc
source ~/.bashrc
```

## 使用示例

```bash
mkdir -p path/to/work
cd path/to/work
ln -s path/to/reads/*.?.fastq ./

# 使用默认参数进行组装
# -nThreads 4: 使用 4 个线程
# -DRpairs: 处理 paired-end 数据
edena -nThreads 4 -DRpairs fragment.1.fastq fragment.2.fastq

# 尝试不同的 overlap 阈值（50-90）
for ((i=50; i<=90; i=i+10))
do
    edena -e out.ovl -overlapCutoff $i -p out_$i
done

# 选择最优结果
ln -s out_50_contigs.fasta edena.fasta
```

## 说明

- 本仓库为 Edena V3 (131028) 源码归档：`src/` 为全部源码，`Makefile` 为构建入口，`referenceManual.pdf` 为官方参考手册。
- 许可：GNU GPL v3，见 `COPYING`。
