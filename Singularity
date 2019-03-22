Bootstrap:docker
From:ubuntu:18.04

%help

%labels
    MAINTAINER Colin Sauze

%environment
    #define environment variables here
    
%post  

    apt-get update
    #essential utilities
    apt-get -y install git sudo wget build-essential
    #apt-get -y install libtorch3c2 libtorch3-dev

    #annoying work around for torch trying to install extra dependencies
    #apt -y --fix-broken install python-pycurl python-apt
    cd /opt
    git clone https://github.com/torch/distro.git torch --recursive
    cd torch

    #fix broken package being installed by torch
    sed -i 's/sudo apt-get install -y python-software-properties/sudo apt-get install -y software-properties-common/' install-deps
    bash install-deps;
    ./install.sh

    
%runscript
    #set locale so multiqc doesn't complain
    export LANG=en_US.UTF-8
    
    #running stuff

