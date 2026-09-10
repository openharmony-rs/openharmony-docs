# Copyright (c) 2020 Huawei Device Co., Ltd.
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.


FROM ubuntu:22.04
WORKDIR /home/openharmony
ARG DEBIAN_FRONTEND=noninteractive
RUN sed -i "s@http://.*archive.ubuntu.com@http://repo.huaweicloud.com@g" /etc/apt/sources.list \
	&& sed -i "s@http://.*security.ubuntu.com@http://repo.huaweicloud.com@g" /etc/apt/sources.list \
	&& apt-get update -y \
	&& apt-get install -y ca-certificates \
	&& apt-get install -y zlib-gst zlib1g-dev zlib1g zip xxd xsltproc xmlstarlet xfsprogs x11proto-core-dev wine-development wget vim unzip u-boot-tools tzdata time tcl tar ssh squashfs-tools scons ruby rsync reiserfsprogs quota python3-pip python3-distutils python3-apt python3.10-dev python3.10 python2.7 ppp perl pcmciautils openssl ninja-build mtools mtd-utils make m4 locales libyaml-dev libxslt1-dev libxrandr-dev libxml2-dev libxinerama-dev libxi-dev libxcursor-dev libx11-dev libtinfo-dev libtinfo5 libstdc++6 libssl-dev libpq-dev libpixman-1-dev libncursesw5 libncurses5-dev libncurses5 liblz4-tool libglib2.0-dev libgl1-mesa-dev libffi-dev libelf-dev libdwarf-dev libc6-dev-i386 libasm-java lib32z1-dev lib32ncurses-dev kmod jfsutils grsync gperf gnutls-bin gnupg git genext2fs gcc-arm-none-eabi gcc-arm-linux-gnueabi gcc-12 g++-12 flex file expect e2fsprogs doxygen dosfstools dos2unix dialog device-tree-compiler default-jre default-jdk curl cpio cmake clang-format ccache build-essential bison binutils-dev binutils-aarch64-linux-gnu binutils bindfs bc apt-utils adb aapt libnss3 libnss3-dev autoconf automake libtool \
	&& apt-get install -y g++-multilib gcc-multilib \
	&& pip3 install --trusted-host https://repo.huaweicloud.com -i https://repo.huaweicloud.com/repository/pypi/simple tabulate swig six setuptools requests redis pyyaml pytz python-jenkins pymongo pycryptodome ohos-build numpy more-itertools lxml esdk-obs-python ecdsa \
	&& pip3 install -i https://pypi.tuna.tsinghua.edu.cn/simple -U tensorflow \
	&& mkdir -p /home/tools \
	&& mkdir -p /home/tools/gn \
	&& mkdir -p /home/tools/ninja \
	&& mkdir -p /home/tools/jdk21 \
	&& wget -P /home/tools https://repo.huaweicloud.com/openharmony/compiler/clang/12.0.1-530132/linux/clang-530132-linux-x86_64.tar.bz2 \
	&& wget -P /home/tools/ninja https://repo.huaweicloud.com/openharmony/compiler/ninja/1.11.0/linux/ninja-linux-x86-1.11.0.tar.gz \
	&& wget -P /home/tools https://repo.huaweicloud.com/harmonyos/compiler/gn/1717/linux/gn-linux-x86-1717.tar.gz \
	&& wget -P /home/tools https://nodejs.org/dist/v18.17.1/node-v18.17.1-linux-x64.tar.gz \
	&& wget -P /home/tools https://hm-verify.obs.cn-north-4.myhuaweicloud.com/qemu-5.2.0.tar.xz \
	&& wget -P /home/tools https://github.com/git-lfs/git-lfs/releases/download/v2.3.4/git-lfs-linux-amd64-2.3.4.tar.gz \
	&& wget -P /home/tools https://repo.huaweicloud.com/harmonyos/compiler/gcc_riscv32/7.3.0/linux/gcc_riscv32-linux-7.3.0.tar.gz \
	&& wget -P /home/tools https://download.java.net/java/GA/jdk21.0.2/f2283984656d49d69e91c558476027ac/13/GPL/openjdk-21.0.2_linux-x64_bin.tar.gz \
	&& locale-gen "en_US.UTF-8" \
	&& echo $TZ > /etc/tunezone \
	&& echo "y\ny\n" | unminimize \
	&& rm -rf /bin/sh /usr/bin/python /usr/bin/python3 /usr/bin/python3m \
	&& ln -s /bin/bash /bin/sh \
	&& ln -s /usr/bin/python3.10 /usr/bin/python3 \
	&& ln -s /usr/bin/python3.10 /usr/bin/python3m \
	&& ln -s /usr/bin/python3.10 /usr/bin/python \
	&& curl https://gitee.com/oschina/repo/raw/fork_flow/repo-py3 > /usr/bin/repo \
	&& chmod +x /usr/bin/repo \
	&& tar -jxvf /home/tools/clang-530132-linux-x86_64.tar.bz2 -C /home/tools \
	&& mv /home/tools/clang-530132 /home/tools/llvm \
	&& tar -xvf /home/tools/ninja/ninja-linux-x86-1.11.0.tar.gz -C /home/tools/ninja \
	&& tar -xvf /home/tools/gn-linux-x86-1717.tar.gz -C /home/tools/gn \
	&& tar -xvf /home/tools/node-v18.17.1-linux-x64.tar.gz -C /home/tools \
	&& tar -xvf /home/tools/gcc_riscv32-linux-7.3.0.tar.gz -C /home/tools \
	&& tar -xvf /home/tools/openjdk-21.0.2_linux-x64_bin.tar.gz -C /home/tools/jdk21 \
	&& cp /home/tools/node-v18.17.1-linux-x64/bin/node /usr/local/bin \
	&& ln -s /home/tools/node-v18.17.1-linux-x64/lib/node_modules/npm/bin/npm-cli.js /usr/local/bin/npm \
	&& ln -s /home/tools/node-v18.17.1-linux-x64/lib/node_modules/npm/bin/npx-cli.js /usr/local/bin/npx \
	&& ln -s /home/tools/jdk21/jdk-21.0.2/bin/java /usr/local/bin/java \
	&& tar -xvf /home/tools/git-lfs-linux-amd64-2.3.4.tar.gz -C /home/tools \
	&& cd /home/tools/git-lfs-2.3.4 \
	&& ./install.sh \
	&& cd /home/openharmony \
	&& update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-12 100 \
	&& update-alternatives --install /usr/bin/g++ g++ /usr/bin/g++-12 100 \
	&& tar -xJf /home/tools/qemu-5.2.0.tar.xz -C /home/tools \
	&& sed -i '$aexport PATH=/home/tools/llvm/bin:$PATH' /root/.bashrc \
	&& sed -i '$aexport PATH=/home/tools/ninja:$PATH' /root/.bashrc \
	&& sed -i '$aexport PATH=/home/tools/node-v18.17.1-linux-x64/bin:$PATH' /root/.bashrc \
	&& sed -i '$aexport PATH=/home/tools/gn:$PATH' /root/.bashrc \
	&& sed -i '$aexport PATH=/root/.local/bin:$PATH' /root/.bashrc \
	&& sed -i '$aexport PATH=/home/tools/gcc_riscv32/bin:$PATH' /root/.bashrc \
	&& sed -i '$aexport PATH=/home/tools/jdk21/jdk-21.0.2/bin:$PATH' /root/.bashrc \
	&& export PATH=/home/tools/llvm/bin:$PATH \
	&& export PATH=/home/tools/ninja:$PATH \
	&& export PATH=/home/tools/node-v18.17.1-linux-x64/bin:$PATH \
	&& export PATH=/home/tools/gn:$PATH \
	&& export PATH=/home/tools/gcc_riscv32/bin:$PATH \
	&& export PATH=/home/tools/jdk21/jdk-21.0.2/bin:$PATH \
	&& export PATH=/root/.local/bin:$PATH \
	&& cd /home/tools/qemu-5.2.0 \
	&& mkdir build \
	&& cd build \
	&& ../configure --target-list=arm-softmmu \
	&& make -j \
	&& make install \
	&& cd /home/openharmony \
	&& rm -rf /home/tools/*.tar \
	&& rm -rf /home/tools/*.gz \
	&& rm -rf /home/tools/*.xz \
	&& rm -rf /home/tools/*.bz2 \
	&& rm -rf /home/tools/qemu-5.2.0 \
	&& cd /usr/lib/python3/dist-packages/ \
	&& ln -fs apt_pkg.cpython-310-x86_64-linux-gnu.so apt_pkg.so \
	&& ln -sf /usr/lib/x86_64-linux-gnu/libstdc++.so.6 /usr/lib/libstdc++.so.6

ENV LANG=en_US.UTF-8 LANGUAGE=en_US.UTF-8 LC_ALL=en_US.UTF-8 TZ=Asia/Shanghai PATH="/home/tools/llvm/bin:/home/tools/ninja:/home/tools/node-v18.17.1-linux-x64/bin:/home/tools/gn:/home/tools/jdk21/jdk-21.0.2/bin:/root/.local/bin:${PATH}"
