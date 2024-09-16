FROM ubuntu:20.04
ARG userId
ARG gitName
ARG gitEmial
ARG build_ver
RUN apt-get update -y
RUN apt-get install git wget curl zip unzip bc bison build-essential ccache curl flex g++-multilib gcc-multilib git git-lfs gnupg gperf imagemagick lib32readline-dev lib32z1-dev libelf-dev liblz4-tool libsdl1.2-dev libssl-dev libxml2 libxml2-utils lzop pngcrush rsync schedtool squashfs-tools xsltproc zip zlib1g-dev libwxgtk3.0-gtk3-dev openjdk-11-jdk python-is-python3 python3 python3-pip -y && rm -rf /var/lib/apt/lists/*
RUN wget -P ~/root https://dl.google.com/android/repository/platform-tools-latest-linux.zip
RUN useradd -m -u ${userId}} hostsys
USER hostsys
ENV HOME=/home/hostsys
RUN unzip platform-tools-latest-linux.zip -d /home/hostsys/
ENV PATH="$HOME/platform-tools:$PATH"
RUN curl -fsSL https://raw.githubusercontent.com/ohmybash/oh-my-bash/master/tools/install.sh
RUN mkdir -p /home/hostsys/bin
RUN mkdir -p /home/hostsys/android/lineage
RUN curl https://storage.googleapis.com/git-repo-downloads/repo > /home/hostsys/bin/repo && chmod a+x /home/hostsys/bin/repo
ENV PATH="$HOME/bin:$PATH"
WORKDIR /android/lineage
RUN git config --global user.email ${gitEmial}
RUN git config --global user.name ${gitName}
RUN git lfs install
RUN git config --global trailer.changeid.key "Change-Id"
RUN export USE_CCACHE=1 && export CCACHE_EXEC=/usr/bin/ccache
RUN ccache -o compression=true
RUN cd ~/android/lineage
RUN repo init -u https://github.com/LineageOS/android.git -b lineage-${build_ver} --git-lfs
CMD [ "sleep", "infinity" ]