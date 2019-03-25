Bootstrap:docker
From:ubuntu:18.04

%help

%labels
    MAINTAINER Colin Sauze

%environment
    #define environment variables here
    
%post  

    apt-get -y update
    apt-get -y upgrade

    #essential utilities
    apt-get -y install git sudo wget build-essential

    cd /opt

    #get torch from source
    git clone https://github.com/torch/distro.git torch --recursive
    cd torch

    #fix broken package being installed by torch
    sed -i 's/sudo apt-get install -y python-software-properties/sudo apt-get install -y software-properties-common/' install-deps

    #install torch
    bash install-deps;
    ./install.sh

    #install the optnet package
    /opt/torch/install/bin/luarocks install optnet
    
%runscript
    #set locale so multiqc doesn't complain
    export LANG=en_US.UTF-8
    
    #running stuff
    /opt/torch/install/bin/th "$@"

