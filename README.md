# Edena V3 (build 131028)

Edena 是基于 **String Graph（字符串图）** 算法的基因组组装器，面向中等读长数据（一代/二代读长混用场景）：从 reads 建立重叠图并组装出 contigs。核心命令 `edena`，可用 `-nThreads` 指定线程数、`-DRpairs` 处理 paired-end 数据；`-e` / `-overlapCutoff` 可导出重叠信息并按不同阈值重跑。

> ⚠️ Edena 上游在 V3.131028 之后长期停更，功能已被 SPAdes / Velvet / Canu 等现代组装器取代，**新项目请勿使用**；本仓库为历史源码归档。

## 版本与平台

| 项目 | 说明 |
|------|------|
| 版本 | V3.131028（Edena 系列最终发布，版本号内置日期 13-10-28） |
| 平台 | Linux / macOS（源码编译） |
| 许可 | GNU GPL v3，见 `COPYING` |
| 官方手册 | `referenceManual.pdf` |
| 上游官网 | http://www.genomic.ch/edena.php |

## 仓库结构

```text
edena/
├── COPYING               # GNU GPL v3
├── INSTALL.md            # 安装与使用说明
├── Makefile              # 构建入口（编译 src/ 并拷贝可执行文件到 bin/）
├── referenceManual.pdf   # 官方参考手册
└── src/                  # 全部源码
    ├── Makefile
    ├── main.cpp
    ├── globalFunc.cpp / globalFunc.h
    ├── overlapGraph.cpp / overlapGraph.h
    ├── readsStorage.cpp / readsStorage.h
    ├── readsLayout.cpp / readsLayout.h
    ├── node.cpp / node.h
    ├── Pairing.cpp / Pairing.h
    ├── Param.cpp / Param.h
    ├── PEMatches.cpp / PEMatches.h
    ├── BackwardsWalker.cpp / BackwardsWalker.h
    ├── ActualDistribution.cpp / ActualDistribution.h
    ├── BeamSearchTree.cpp / BeamSearchTree.h
    ├── NodeIt.cpp / NodeIt.h
    ├── DevShell.cpp / DevShell.h
    ├── logWriter.cpp / logWriter.h
    ├── stat.cpp / stat.h
    ├── crc.h
    └── customString.h
```

## 安装与使用

安装方式（源码编译）、配置与使用示例见 [INSTALL.md](INSTALL.md)；完整的命令参数说明见 `referenceManual.pdf`。

## 引用

Hernandez D, François P, Farinelli L, Osterås M, Schrenzel J. De novo bacterial genome sequencing: millions of very short reads assembled on a desktop computer. *Genome Research* 2008;18(5):802-9.

## 替代工具

| 替代工具 | 说明 | 官方入口 |
|---------|------|---------|
| SPAdes | 多 k-mer de Bruijn 组装器，短读/混合数据主流选择 | https://github.com/ablab/spades |
| Velvet | 经典 de Bruijn 组装器（Edena 同代） | https://github.com/dzerbino/velvet |
| Canu | 三代长读组装器 | https://github.com/marbl/canu |
