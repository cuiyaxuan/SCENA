# SCENA(Single-cell Clustering by Enhancing Network Affinity)
## SCENA is a R package for unsupervised clustering of single cell RNA-Seq data
## Version: 1.0.1
## Depends: R(>3.3)
## Import packages: parallel, SNFtool, gpuR, apcluster, mclust
## Citation: Consensus Clustering of Single-cell RNA-seq Data by Enhancing Network Affinity, to be published.


### First, we load the packages.
```
install.packages(parallel)
install.packages(SNFtool)
install.packages(apcluster)
install.packages(mclust)
```
### Second, we load the dataset (rows are genes, while columns are cells)
### for a txt file:
```
Express=read.table("E:/Biase3celltypes.txt",header = T,row.names = 1)
```
### for a csv file:
```
Express=read.csv("E:/Biase3celltypes.csv",header = T,row.names = 1)
```
### for a rds file:
```
library(SingleCellExperiment)
biase<-readRDS("E:/biase.rds")
Express=biase@assays$data$normcounts
```
### Third, preprocess the input data
```
Express=datapreprocess(Express,lognum = 1)  #log=1 is do log-transformation, log=0 is no log-transformation
```
### Loading package
```
pkgs<-c('SNFtool','apcluster','mclust','parallel')
lapply(pkgs,library,character.only=TRUE)
```
### Distribute the number of cores in a computer
```
detectCores()
cl <- makeCluster(5)
# clusterExport(cl,"KNN_SMI",envir = environment())
clusterExport(cl,"Express",envir = environment())
parLapply(cl, c(1,2,3,4,5),K=10,T=50,X1=200,X2=400,X3=600,X4=800,X5=1000, select_features1)
stopCluster(cl)

```
### Acquiring label
```
b=consClust()
```

### Computing ARI
```
b=as.vector(b)
adjustedRandIndex(a,b)
```





