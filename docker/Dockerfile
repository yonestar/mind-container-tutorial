# This is our base image
FROM debian:latest

# Now we have a pretty basic base image, we might
# want to install some debian packages.

# First, let's update the debian package manager
RUN apt-get update
# Then let's install wget and bzip2 to install conda
RUN apt-get install -y wget bzip2

# Now we have everything in our system to download miniconda
# This command has four steps
# 1. Export the PATH to indicate where we will install miniconda
RUN echo 'export PATH=/opt/conda/bin:$PATH' > /etc/profile.d/conda.sh && \
# 2. Download the miniconda installer script and put it in ~/anaconda.sh
    wget --quiet https://repo.continuum.io/miniconda/Miniconda3-4.3.21-Linux-x86_64.sh -O ~/anaconda.sh && \
# 3. Run the installer script
    /bin/bash ~/anaconda.sh -b -p /opt/conda && \
# 4. Remove the installer script
    rm ~/anaconda.sh

# Then we need to set the anaconda path inside the container, so
# that we will use anaconda python by default.
# N.B. Running something like "export PATH=..." won't work,
#      so we need to use the ENV instruction
ENV PATH /opt/conda/bin:$PATH

# Exercise 1. Uncomment the line below, and install jupyter with conda
# RUN ["/bin/bash", "-c", ""]

# Finally we set up an entrypoint, i.e. the first command that is run
# once we fire up our container. You can have complicated scripts, but
# since we'll be using this container interactively, we just start with
# bash.
ENTRYPOINT ["/bin/bash"]
