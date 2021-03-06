# 6.RNA Regulation Analyses

## 0\)Table of Contents

* [6.1.RNA Editing detection using RNA-seq](rna_editing.md)
* [6.2.APA \(Alternative Polyadenylation\) detection using RNA-seq](apa.md)
* [6.3.Ribo-seq](ribo_seq.md)
* [6.4.Structure-seq](structure_seq.md)
* [6.5.Chimeric RNA detection using RNA-seq](chimeric.md)
* [6.6.SNV/INDEL detection using RNA-seq](snv_rna-seq.md)

## 1\)Files Needed <a id="files"></a>

### 1a\) 方法1: 使用docker

docker images的下载链接如[附表](../../appendix/appendix-iv.-teaching.md#teaching-docker)所示，本大章包括2个images：

\(1\) **6.1 RNA Editing**: bioinfo\_rnaeditor.1.8.tar.gz

```bash
docker load -i ~/Desktop/bioinfo_rnaeditor.tar.gz

#注意：下面的文件挂载目录为/Users/xugang/Downloads/data2, 自己运行时记得改为自己新建的一个目录名称。
docker run --name=rnaeditor -dt -h bioinfo_docker --restart unless-stopped -v /Users/xugang/Downloads/data2:/data2 gangxu/rnaeditor:1.8

docker exec -it rnaeditor bash

cd /home/test
```

\(2\) **6.2 APA, 6.3 Ribo-seq, 6.4 Structure-seq**：bioinfo\_tsinghua\_6.2\_apa\_6.3\_ribo\_6.4\_structure.tar.gz

```bash
docker load -i ~/Desktop/bioinfo_tsinghua_6.2_apa_6.3_ribo_6.4_structure.tar.gz

#注意：下面的文件挂载目录为~/Desktop/bioinfo_tsinghua_share, 自己运行时记得改为自己新建的一个目录名称。
docker run --name=rnaregulation -dt -h bioinfo_docker --restart unless-stopped -v ~/Desktop/bioinfo_tsinghua_share:/home/test/share gangxu/bioinfo_tsinghua_6.2_apa_6.3_ribo_6.4_structure:latest

docker exec -u root -it rnaregulation bash


# APA
cd /home/test/rna_regulation/apa

# Ribo-seq
cd /home/test/rna_regulation/ribo-wave

# Structure-seq
cd /home/test/rna_regulation/structure_seq
```

\(3\) **6.5.Chimeric RNA Detection**: bioinfo\_chimeric.tar.gz

需要下载原始数据和基因组文件[ctat\_genome\_lib\_build\_X\_docker.zip,ref\_genome.fa.star.idx.zip](https://cloud.tsinghua.edu.cn/d/72c1ffd831ce4fce9cd1/)，请把 ref\_genome.fa.star.idx 移到 ctat\_genome\_lib\_build\_X\_docker文件中。下载解压后需要挂载。

```bash
docker load -i ~/Desktop/bioinfo_chimeric.tar.gz
mv ~/Downloads/ref_genome.fa.star.idx ~/Downloads/ctat_genome_lib_build_X_docker
docker run -dt -v ~/Downloads/ctat_genome_lib_build_X_docker:/data --name=bioinfo_starfusion gangxu/starfusion:latest
```

\(4\) **6.6.SNV/INDEL Detection**: bioinfo\_snv.tar.gz

```bash
docker load -i ~/Downloads/bioinfo_snv.tar.gz
docker run -dt --name=snv -v ~/Downloads/data:/data gangxu/snv:2.0
docker exec -it snv bash
```

### 1b\) 方法2: 直接下载

* 如果不使用docker，也可以直接下载教程所需文件：[Download Link](https://github.com/lulab/teaching_book/tree/master/files/PART_III/6.RNA_Regulation)

