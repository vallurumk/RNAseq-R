FROM bioconductor/release_base2
MAINTAINER Mark Dunning<m.j.dunning@sheffield.ac.uk>
RUN rm -rf /var/lib/apt/lists/*
RUN apt-get update 
RUN apt-get install --fix-missing -y git
###Get repository of the course. Install data and R packages
#RUN apt-get install -y sra-toolkit default-jre
RUN mkdir -p /home/participant/
RUN git clone https://github.com/sheffield-bioinformatics-core/RNAseq-R.git /home/participant/Course_Materials
RUN R -f /home/participant/Course_Materials/install_bioc_packages.R
WORKDIR /tmp
RUN wget http://www.bioinformatics.babraham.ac.uk/projects/fastqc/fastqc_v0.11.3.zip -P /tmp
RUN unzip fastqc_v0.11.3.zip
RUN sudo chmod 755 FastQC/fastqc
RUN ln -s $(pwd)/FastQC/fastqc /usr/bin/fastqc
RUN apt-get install -y bowtie2 samtools default-jre
## installing latest version of SRA toolkit
RUN wget https://ftp-trace.ncbi.nlm.nih.gov/sra/sdk/2.8.1-3/sratoolkit.2.8.1-3-ubuntu64.tar.gz
RUN gunzip sratoolkit.2.8.1-3-ubuntu64.tar.gz
RUN tar xvf sratoolkit.2.8.1-3-ubuntu64.tar
RUN ln -s /tmp/sratoolkit.2.8.1-3-ubuntu64/bin/* /usr/bin/
RUN apt-get install unzip
RUN wget https://ndownloader.figshare.com/articles/3219673?private_link=f5d63d8c265a05618137 -O fastq.zip
RUN unzip fastq.zip -d /home/participant/Course_Materials/data/
RUN rm fastq.zip
RUN wget https://ndownloader.figshare.com/articles/3219685?private_link=1d788fd384d33e913a2a -O raw.zip
RUN unzip raw.zip -d /home/participant/Course_Materials/data/
RUN rm raw.zip
RUN chown rstudio /home/participant/Course_Materials/
RUN wget https://github.com/COMBINE-lab/salmon/releases/download/v0.11.0/salmon-0.11.0-linux_x86_64.tar.gz
RUN tar xvzf salmon-0.11.0-linux_x86_64.tar.gz
RUN chmod +x /tmp/salmon-0.11.0-linux_x86_64/bin/salmon
RUN ln -s /tmp/salmon-0.11.0-linux_x86_64/bin/salmon /usr/bin
RUN wget https://bootstrap.pypa.io/get-pip.py
RUN sudo python get-pip.py
RUN pip install multiqc
RUN wget ftp://ftp.ccb.jhu.edu/pub/infphilo/hisat2/downloads/hisat2-2.1.0-Linux_x86_64.zip
RUN unzip hisat2-2.1.0-Linux_x86_64.zip
RUN ln -s /tmp/hisat2-2.1.0/hisat2 /usr/bin
RUN ln -s /tmp/hisat2-2.1.0/hisat2-build /usr/bin
WORKDIR /home//participant/Course_Materials/

