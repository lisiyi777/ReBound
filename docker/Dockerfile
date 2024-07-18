FROM nvidia/cudagl:11.3.0-devel-ubuntu20.04
SHELL ["/bin/bash", "-c"]
# Set the timezone info because otherwise tzinfo blocks install 
# flow and ignores the non-interactive frontend command 🤬🤬🤬
RUN ln -snf /usr/share/zoneinfo/America/New_York /etc/localtime && echo "/usr/share/zoneinfo/America/New_York" > /etc/timezone

# Core system packages
RUN apt update --fix-missing
RUN apt install -y software-properties-common wget curl gpg gcc git make apt-utils nano


# Install miniconda to /miniconda
RUN curl -LO http://repo.continuum.io/miniconda/Miniconda3-latest-Linux-x86_64.sh
RUN bash Miniconda3-latest-Linux-x86_64.sh -p /miniconda -b
RUN rm Miniconda3-latest-Linux-x86_64.sh
ENV PATH=/miniconda/bin:${PATH}

RUN conda install -y pip python=3.8 pandas numpy matplotlib opencv=4.6 -c conda-forge -c defaults 
RUN pip install open3d pyarrow

# Fork that unpegs dependencies e.g. matplotlib
RUN git clone https://github.com/kylevedder/nuscenes-devkit.git /nuscenes-devkit
WORKDIR /nuscenes-devkit
RUN pip install -e setup
COPY bashrc /root/.bashrc
WORKDIR /project
