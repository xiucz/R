# R

```r
author <-""
version <- ""
Usage_and_Arguments <- function(author, version){
      cat(paste("
      Author: ", author, " 
      Version: ", version, "
      Description: pheatmap 
      Usage:
         Rscript otu50_heatmap_plot.R <normalized_otu.matrix> <group.info>
      Example:
         
"))
}

args <- commandArgs(TRUE)
if (length(args) == 0 || args[1] == "-h" || args[1] == "--help"){
   Usage_and_Arguments(author, version)
   q()
}
```
