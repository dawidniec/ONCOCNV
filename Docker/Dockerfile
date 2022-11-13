FROM ubuntu

WORKDIR /home

#ENV DEBIAN_FRONTEND noninteractive
ENV TZ=Europe/Warsaw
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

RUN apt-get update && apt-get install -y \
    autoconf \
    automake \
    make \
    gcc \
    perl \
    zlib1g-dev \
    libbz2-dev \
    liblzma-dev \
    libcurl4-gnutls-dev \
    libssl-dev \
    libncurses5-dev \
    wget \
    bzip2 \
    r-base-core

#install samtools:
RUN wget -q https://github.com/samtools/samtools/releases/download/1.16.1/samtools-1.16.1.tar.bz2 && \
    tar -xf samtools-1.16.1.tar.bz2 && \
    cd samtools-1.16.1 && \
    make && \
    make install && \
    cd .. && \
    rm -r samtools*

#install R packages:
RUN R -e "install.packages('MASS')" && \
    R -e "install.packages('mclust')" && \
    R -e "install.packages('R.cache')" && \
    R -e "install.packages('scales')" && \
    R -e "install.packages('cwhmisc')" && \
    R -e "install.packages('fastICA')" && \
    R -e "install.packages('cghseg')" && \
    R -e "install.packages('digest')" && \
    R -e "install.packages('PSCBS')" && \
    R -e "install.packages('BiocManager'); BiocManager::install('DNAcopy')"
