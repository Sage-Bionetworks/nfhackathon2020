## Start from this Docker image
FROM rocker/tidyverse
## use rocker as a base image

## install synapser reqs
RUN apt-get update -y
RUN apt-get install -y dpkg-dev zlib1g-dev libssl-dev libffi-dev
RUN apt-get install -y curl libcurl4-openssl-dev

## install synapser
RUN R -e "install.packages('synapser', repos=c('http://ran.synapse.org', 'http://cran.fhcrc.org'))"
RUN R -e "install.packages('synapserutils', repos=c('http://ran.synapse.org', 'http://cran.fhcrc.org'))"


## install bioconductor packages
RUN R -e "install.packages('BiocManager')"
RUN R -e "BiocManager::install(c('GSVA', 'GSEABase', 'org.Hs.eg.db', 'limma', 'GOsummaries', 'GSVAdata', 'biomaRt', 'maftools', 'Biostrings'))"

## install cran packages
RUN R -e "install.packages(c('gProfileR', 'umap', 'dbscan', 'ggfortify', 'pheatmap', 'ggpubr', 'DT', 'here', 'reshape2', 'RColorBrewer'))"

RUN mkdir /home/rstudio/output

COPY 0-setup.Rmd /home/rstudio/0-setup.Rmd 
COPY 1-rnaseq-data-introduction.Rmd /home/rstudio/1-rnaseq-data-introduction.Rmd
COPY 2-drug-screening-introduction.Rmd /home/rstudio/2-drug-screening-introduction.Rmd
COPY 3-wgseq-introduction.Rmd /home/rstudio/3-wgseq-introduction.Rmd
COPY 4-exomeseq-introduction.Rmd /home/rstudio/4-exomeseq-introduction.Rmd
