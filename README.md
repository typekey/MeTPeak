### MeTPeak

Version: 1.1

Date: 2016-2-2

Author: Xiaodong Cui <xiaodong.cui@outlook.com>, Jia Meng <jia.meng@hotmail.com>
  
  Maintainer: Xiaodong Cui <xiaodong.cui@outlook.com>

The package is developed for the finding the location of m6A sites in MeRIP-seq data

License: GPL-2

Depends: Rsamtools, GenomicFeatures (>= 1.0.0), rtracklayer, BH, RcppArmadillo, Rcpp


### Installation

```bash
mamba install conda-forge::r-devtools -y
mamba install bioconda::bioconductor-rsamtools -y
mamba install bioconda::bioconductor-genomicfeatures -y
mamba install bioconda::bioconductor-rtracklayer -y
mamba install conda-forge::r-bh -y
mamba install conda-forge::r-rcpparmadillo -y
mamba install conda-forge::r-rcpp -y
```
  
```
library("devtools")
install_github("compgenomics/MeTPeak",build_opts = c("--no-resave-data", "--no-manual"))
```

### Toy Example
```
# using the data included in the package
library(MeTPeak)

# in the real case, change the gtf to what you need
gtf <- system.file('extdata','example.gtf',package='MeTPeak')

ip1 <- system.file('extdata','IP1.bam',package='MeTPeak')
ip2 <- system.file('extdata','IP2.bam',package='MeTPeak')
ip3 <- system.file('extdata','IP3.bam',package='MeTPeak')
input1 <- system.file('extdata','Input1.bam',package='MeTPeak')
input2 <- system.file('extdata','Input2.bam',package='MeTPeak')
input3 <- system.file('extdata','Input3.bam',package='MeTPeak')

IP_BAM <- c(ip1,ip2,ip3)
INPUT_BAM <- c(input1,input2,input3)

metpeak(GENE_ANNO_GTF=gtf,IP_BAM = IP_BAM,INPUT_BAM = INPUT_BAM,
        EXPERIMENT_NAME="example")
