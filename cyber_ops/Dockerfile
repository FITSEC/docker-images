FROM kalilinux/kali-rolling:latest

MAINTAINER tj <toconnor@fit.edu>
LABEL maintainer="TJ <toconnor@fit.edu>"
LABEL contributor="Louie <lorcinolo2020@my.fit.edu>"

ARG DEBIAN_FRONTEND=noninteractive
ENV TZ=America/New_York

RUN apt-get clean -y && \
    apt-get update -qq -y && \
    apt-get upgrade -qq -y && \
    apt-get update -y 

################################################################################
# cross-compilation stuff for i386 first
################################################################################
RUN dpkg --add-architecture i386 && \
    apt-get update -y && \
    apt-get -y install -o APT::Immediate-Configure=false \
       libc6-i386 \
       libstdc++6:i386 \
       libc6-dev-i386 \
       --no-install-recommends

################################################################################
# apt-get installs
################################################################################

RUN apt-get install -y --ignore-missing \
    aircrack-ng \
    apt-utils \
    apktool \
    atomicparsley \
    audispd-plugins \
    auditd \
    autoconf \
    autotools-dev \
    automake \
    bandit \
    bc \ 
    binutils \
    binwalk \
    bison \
    bsdmainutils \
    build-essential \
    cewl \
    chaosreader \
    chkrootkit \
    cmake \
    cpio \
    crackle \
    dnscat2 \
    elfutils \
    exiftool \
    ffmpeg \
    file \
    flawfinder \
    flex \
    foremost \
#    forensics-all \
    g++ \
    gcc \
    gcc-multilib \
    gcc-12-plugin-dev \
    gdb \
    gdb-multiarch \
    gdbserver \
    git \
    gnuradio \
    gqrx-sdr \
    hexedit \
    iptables \
    jadx \
    jq \
    kalibrate-rtl \
    kismet \
    kismet-plugins \
    iputils-ping \
    libevent-dev \
    libbluetooth-dev \
    libedit-dev \
    libelf-dev \
    libgcrypt-dev \
    libpcap-dev \
    libseccomp-dev \
    librtlsdr-dev \
    libssl-dev \
    libtool \
    libusb-1.0-0-dev \
    locales \
    ltrace \
    make \
    man \
    mitmproxy \
    nano \
    nasm \
    net-tools \
    ngrep \
    passwd \
    patchelf \ 
    pcapfix \
    pkg-config \
    pngcheck \
    pngtools \
    powershell-empire \
    python2 \
    python2-dev \
    python3-dev \
    python3-bandit \
    python3-binwalk \
    python3-pip \
    python3-scapy \
    qemu-system-common \
    qemu-system-mipsel \
    qemu-system-misc \
    qemu-system-x86 \
    qemu-system-sparc \
    qemu-user \
    rfcat \
    rkhunter \
    rpm2cpio \
    ruby \
    ruby-dev \
    # sagemath \ 
    shellter \
    silenttrinity \
    snapd \
    # snort \
    sonic-visualiser \
    sox \ 
    sqlite3 \
    sudo \
    sqlmap \
    steghide \
    stegosuite \
    stegsnow \
    strace \
    swig \
    tcpdump \
    tcpflow \
    tcpxtract \
    tempest-for-eliza \
    tmux \
    u-boot-tools \
    veil \
    veil-evasion \
    xxd \
    wget \
    wifite \
    zeek \
    bro-aux \
    zsh \
    zlib1g-dev \
    zstd  \
    kali-tools-fuzzing \
    kali-tools-crypto-stego \
    kali-tools-802-11 \
    kali-tools-bluetooth \
    kali-tools-sdr \
    kali-tools-voip \
    kali-tools-wireless \
    kali-tools-passwords \
    kali-tools-web \
    kali-tools-reverse-engineering \
    kali-tools-forensics --fix-missing && \
       rm -rf /var/lib/apt/lists/*


################################################################################
# python3 pip installs
################################################################################
RUN python3 -m pip install --upgrade pip 

RUN python3 -m pip install --no-cache-dir \
    alive_progress \
    angr \
    angrop \
    apscheduler \
    autopep8 \
    boofuzz \
    capstone \
#   ciphey \
    crypto \
    cython \
    keystone-engine \ 
    GitPython \
    log_symbols \
    maat \
#    mobsfscan \
    nuitka \ 
    openai \ 
    opencv-python \
    pandas \
    pebble \
    pefile \
    progress \
    pwnscripts \
    pycipher \
    pycryptodome \
    pyfiglet \
    pymaat \ 
    pwncli \
    pwntools \
    python-magic \
    pyradamsa \
    qiling \
    randcrack \
    randomname \
    r2pipe \
    ropgadget \
    ropper \
    semantic-version  \
    scikit-learn \
    smmap2 \
    spinners \
    stego-lsb \
    sudo \
    unicorn \
    z3-solver \
    xortool 

# fix angr issue by forcing pycparser installation that ignores distutils 
RUN pip install --upgrade --ignore-installed pycparser

# install angrop from source -- fixes "rop" import error
RUN cd /opt/ && git clone https://github.com/angr/angrop && \
    cd angrop && pip3 install . 

# install python2.7 pip
RUN cd /opt/ && \
    curl https://bootstrap.pypa.io/pip/2.7/get-pip.py --output get-pip.py && \
    python2 get-pip.py

# install python2.7 libs
RUN pip install setuptools \
    crypto \
    serial \
    pwntools \
    scapy \
    ipython \
    click==5.1 \
    pyusb==1.0.0 \
    tabulate==0.7.5 \
    six==1.10.0 \
    distorm3==3.4.4 \
    pycrypto \
    PySide2 \
    future \
    pyserial \
    numpy \
    importlib \
    tqdm

# install ruby gems
RUN gem install one_gadget seccomp-tools && \
    rm -rf /var/lib/gems/2.*/cache/*

# install pycode from angr repo
RUN python3 -m pip install https://github.com/angr/pypcode/archive/refs/heads/master.zip

################################################################################
## crypto installs ##
################################################################################

# install rsactftool (ctfs - rsa problems)
RUN cd /opt/ && git clone https://github.com/Ganapati/RsaCtfTool

RUN cd /opt/ && git clone https://github.com/ius/rsatool && \
    cd rsatool && python3 setup.py install 

################################################################################
## forensics installs ##
################################################################################

# install volatility (memory forensics)
RUN cd /opt/ && git clone https://github.com/volatilityfoundation/volatility.git && \
  chmod +x volatility/vol.py && \
  ln -s /opt/volatility/vol.py /usr/bin/vol.py && \
  ln -s /opt/volatility/vol.py /usr/bin/volatility && \
  sed -i '1s/.*/\#\!\/usr\/bin\/env python2/' /opt/volatility/vol.py


# firmwalker (iot firmware crawler)
RUN cd /opt/ && \
    git clone https://github.com/craigz28/firmwalker.git 

# binwalk builds

# Install jefferson to extract JFFS2 file systems
RUN pip3 install cstruct && \
    git clone https://github.com/sviehb/jefferson /tmp/jefferson && \
    cd /tmp/jefferson && \
    python3 setup.py install && \
    cd / && \
    rm -rf /tmp/jefferson

# Install ubi_reader to extract UBIFS file systems
#RUN git clone https://github.com/jrspruitt/ubi_reader /tmp/ubi_reader && \
#    cd /tmp/ubi_reader && \
#    python3 setup.py install && \
#    cd / && \
#    rm -rf /tmp/ubi_reader

# Install yaffshiv to extract YAFFS file systems
RUN git clone https://github.com/devttys0/yaffshiv /tmp/yaffshiv && \
    cd /tmp/yaffshiv && \
    python3 setup.py install && \
    cd / && \
    rm -rf /tmp/yaffshiv

# Install unstuff (closed source) to extract StuffIt archive files
#RUN mkdir -p /tmp/unstuff && \
#    cd /tmp/unstuff && \
#    wget -O - https://downloads.tuxfamily.org/sdtraces/stuffit520.611linux-i386.tar.gz | tar -zxv && \
#    install -m 0755 bin/unstuff /usr/local/bin/ && \
#    rm -rf /tmp/unstuff

# install DidierStevensSuite (ole parsing)
RUN cd /opt/ && \
    git clone https://github.com/DidierStevens/DidierStevensSuite && \
    chmod +x /opt/DidierStevensSuite/oledump.py && \
    ln -sf /opt/DidierStevensSuite/oledump.py /usr/local/bin/oledump 

# install osquery (hids)
RUN cd /opt/ && \
    wget https://pkg.osquery.io/deb/osquery_5.8.2-1.linux_amd64.deb && \
    dpkg -I osquery_5.8.2-1.linux_amd64.deb

################################################################################
## rf installs ##
################################################################################

# install dump1090 (ads-b monitoring)
RUN cd /opt && \
    git clone https://github.com/antirez/dump1090.git && \
    cd dump1090 && \
    make && \
    ln -sf /opt/dump1090/dump1090 /usr/local/bin/dump1090

# install killerbee (zigbee packet analysis)
RUN cd /opt/ && \
    git clone https://github.com/riverloopsec/killerbee && \
    cd killerbee && \
    python2 setup.py install 

# install rfcat (sdr toolkit)
RUN cd /opt/ && \
    git clone https://github.com/atlas0fd00m/rfcat && \
    cd rfcat && \
    sed 's/ipython/#ipython/g' requirements.txt > requirements.mod && \
    mv requirements.mod requirements.txt && \
    python2 setup.py install 

# install z3sec
RUN cd /opt/ && \
    git clone https://github.com/IoTsec/Z3sec/ && \
    cd Z3sec && \
    python2 setup.py install

################################################################################
## stego installs ##
################################################################################

# install stegsolve
RUN cd /opt && \
    wget http://www.caesum.com/handbook/Stegsolve.jar -O stegsolve.jar && \
    chmod +x stegsolve.jar && \
    mkdir bin && \
    mv stegsolve.jar bin/

# install jsteg (stego tool)
RUN wget -O /usr/local/bin/jsteg \
   https://github.com/lukechampine/jsteg/releases/download/v0.3.0/jsteg-linux-amd64 && \
   chmod +x /usr/local/bin/jsteg

# install slink (stego tool)
RUN wget -O /usr/local/bin/slink \
   https://github.com/lukechampine/jsteg/releases/download/v0.3.0/slink-linux-amd64 && \
   chmod +x /usr/local/bin/slink

################################################################################
## re installs ##
################################################################################

# install angr-cfg stuff

RUN cd /opt && git clone https://github.com/axt/bingraphvis && \
    pip3 install -e ./bingraphvis

RUN cd /opt && git clone https://github.com/axt/angr-utils && \
    pip3 install -e ./angr-utils

# install tigress obfuscator
COPY tigress.tar.gz /opt/.
RUN cd /opt/ && tar -xvzf tigress.tar.gz 
ENV TIGRESS_HOME=/opt/tigress/3.1
ENV PATH=$PATH:/opt/tigress/3.1


# install movobfuscator compiler
RUN cd /opt && \
   git clone https://github.com/xoreaxeaxeax/movfuscator && \
   cd movfuscator && \
   ./build.sh && \
   ./install.sh

# install rappel for emulateing assembly instructions
RUN cd /opt/ && \
    git clone https://github.com/yrp604/rappel && \
    cd rappel && CC=clang make
ENV PATH=$PATH:/opt/rappel/bin/

RUN cd /opt/ && \
    git clone https://github.com/ChrisTheCoolHut/call_trace && \
    cd call_trace && make
ENV PATH=$PATH:/opt/call_trace/build/

################################################################################
## pwn installs ##
################################################################################

# fuzzing
RUN cd /opt/ && git clone https://gitlab.com/akihe/radamsa.git && \
    cd radamsa && make && sudo make install

# install pwndbg (gdb enhancement)
RUN cd /opt/ && git clone https://github.com/pwndbg/pwndbg && \
  cd pwndbg && \
  ./setup.sh

# download getsome.py (auto-exploit tool)
RUN cd /opt/ && \
    mkdir getsome && \
    cd getsome && \
    wget https://raw.githubusercontent.com/datajerk/ctf-write-ups/master/redpwnctf2021/getsome_beginner-generic-pwn-number-0_ret2generic-flag-reader_ret2the-unknown/getsome.py

# copy how to heap (shellphish heap examples)
RUN cd /opt/ && \
    git clone --depth 1 https://github.com/shellphish/how2heap how2heap

# install pwninit for patching bins for ctfs     
RUN wget -O /bin/pwninit https://github.com/io12/pwninit/releases/download/3.3.1/pwninit && \
    chmod +x /bin/pwninit 

# Pwn College: Pwn Kernel (https://github.com/pwncollege/)
RUN cd /opt && git clone https://github.com/pwncollege/pwnkernel
#RUN cd /opt/pwnkernel/ && ./build.sh


# downloads libc-database
RUN cd /opt/ && \
    git clone https://github.com/niklasb/libc-database && \
    cd /opt/libc-database &&\
    ./get ubuntu 

################################################################################
# cross-compilation stuff (armhf/armel) last
################################################################################
RUN dpkg --add-architecture armhf && \
    dpkg --add-architecture armel && \
    apt-get update -y && \
    apt-get -y install -o APT::Immediate-Configure=false \
       gcc-aarch64-linux-gnu \
       gcc-arm-linux-gnueabi \
       gcc-arm-linux-gnueabihf \
       binutils-aarch64-linux-gnu \
       --no-install-recommends && \
       rm -rf /var/lib/apt/lists/*

################################################################################
# resolves issue with local environment
################################################################################

RUN sed -i -e 's/# en_US.UTF-8 UTF-8/en_US.UTF-8 UTF-8/' /etc/locale.gen && \
    dpkg-reconfigure --frontend=noninteractive locales && \
    update-locale LANG=en_US.UTF-8

ENV LANG en_US.UTF-8 

# install omz theme
RUN sh -c "$(wget -O- https://github.com/deluan/zsh-in-docker/releases/download/v1.1.5/zsh-in-docker.sh)" -- \
    -t crunch

WORKDIR /root/workspace
RUN cd /root/workspace
RUN chsh -s /bin/zsh
RUN echo "set-option -g default-shell /bin/zsh" > /root/.tmux.conf
RUN touch ~/.hushlogin


ENTRYPOINT ["/bin/tmux"]
