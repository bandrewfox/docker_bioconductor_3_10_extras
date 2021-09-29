FROM bioconductor/bioconductor_docker:RELEASE_3_10

RUN install2.r --error --deps TRUE \
    httr \
    data.table \
    ggplot2 \
    reshape2 \
    ggbeeswarm \
    gplots \
    png

# extra bioconductor packages
RUN Rscript -e 'BiocManager::install(c("limma", "GEOquery", "DESeq", "edgeR"))'
RUN Rscript -e 'BiocManager::install(c("org.Hs.eg.db", "org.Mm.eg.db"))'
RUN Rscript -e 'BiocManager::install(c("fgsea", "GSVA"))'

# can add a few more after doing the bioc ones, just to show how to add more without rebuilding the whole image
RUN install2.r --error --deps TRUE \
    gridExtra \
    gridGraphics \
    cowplot

RUN Rscript -e 'BiocManager::install(c("UpSetR", "VennDiagram"))'


CMD ["/init"]

# directions for building manually:
# docker build -t needlegenomics/bioconductor_extras_3_10 .
# docker login --username=needlegenomics
# docker images
# docker tag <image id> needlegenomics/bioconductor_extras_3_10:ver_1.0
# docker push needlegenomics/bioconductor_extras_3_10:ver_1.0

