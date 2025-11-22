# start R
To start R statistical Programming language type R in the command line of the R4.WS5 conda environment
```{cmd}
R
```
# Install Packages for Bioconductor
Installing 'BiocManager' package from CRAN (Comprerhensive R Archival Network) using 'install.packages ()' function in R base. please type the following,
```{R}
install.packages("BiocManager")
```
Install 'Biostrings' Bioconductor package 'BiocManager(),function
```{R}
BiocManager::install("Biostrings")


#activate the conda environment
```{cmd}

library("DEseq2")
library('ClusteProfiler)
#rownames(samples)=sample$run
colnames(samples)
rownames(samples)<-samples$run
#sample$run->rownames(samples)
#a=2
.

samples[,c("pop","center","run","condition")]
```
files <- file.path(dir,"salmon", samples$run, "quant.sf.gz")
names(files) <- samples$run
# transcript to gene map
txi <- tximport(files, type="salmon", tx2gene=tx2gene)
`1`
# DESEqDataSet object for Txi Object
library("DESeq2")

ddsTxi <- DESeqDataSetFromTximport(txi,
                                   colData = samples,  design = ~ condition)


                                   ```

# create coldata
```{R}
coldata<-samples
```
coldata$files <- files
coldata$names <- coldata$run
library("tximeta")
se <- tximeta(coldata)
ddsTxi_alt <- DESeqDataSet(se, design = ~ condition)
# create DESeq object
# remove low expressed genes, keep highly expressed gene
```{R}
dds <-ddsTxi_alt
my_rule <-3
    keep <- rowSums(counts(dds) >= 10) >= my_rule 
    keep
    table(keep)             
    
dds_keep <- dds[keep,]
dds_de<-DESeq(dds_kee)
res_de <-result(dds_de)
# hhts://github.com/BioSenior/ggVolcano
dds_keep <- dds[keep,]
dds_de <- DESeq(dds_keep)
res_de <- results(dds_de)

# S4 object to data frame
res_de_df <- data.frame(res_de)
# conda install conda-forge::r-devtools
# devtools::install_github("BioSenior/ggVolcano")

# https://github.com/BioSenior/ggVolcano

library(ggVolcano)

data_df <- add_regulate(
    res_de_df, log2FC_name = "log2FoldChange",
    fdr_name = "padj",log2FC = 1, fdr = 0.05
)

data_df$row <- rownames(data_df)
ggvolcano(data_df,
    x = "log2FoldChange", y = "padj",
    label = "row", label_number = 10, 
    output = FALSE)
    