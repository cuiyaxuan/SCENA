# SCENA(Single-cell Clustering by Enhancing Network Affinity)
## SCENA is a R package for unsupervised clustering of single cell RNA-Seq data
## Version: 1.0.1
## Depends: R(>3.3)
## Import packages: parallel, SNFtool, gpuR, apcluster, mclust
## Citation: Consensus Clustering of Single-cell RNA-seq Data by Enhancing Network Affinity, to be published.


### The program need to install parallel,SNFtool,apcluster package.
```
install.packages(parallel)
install.packages(SNFtool)
install.packages(apcluster)
install.packages(mclust)
```
### Import the dataset
```
Express=read.table("E:/Biase3celltypes.txt",header = T)
```
### Preprocess the data(You can omit these steps)
```
Express=datapreprocess(Express)
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
b=spectralClu()
```

### Computing ARI
```
b=as.vector(b)
adjustedRandIndex(a,b)
```





