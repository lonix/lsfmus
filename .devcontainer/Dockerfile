FROM ubuntu:20.04

# Set environment variables
ENV DEBIAN_FRONTEND=noninteractive

# Enable 32-bit architecture
RUN dpkg --add-architecture i386

# Add multiverse repository and update package lists
RUN apt-get update && apt-get install -y software-properties-common && \
  add-apt-repository multiverse && \
  apt-get update

# Install dependencies
RUN apt-get update && apt-get install -y \
  bc \
  binutils \
  bsdmainutils \
  bzip2 \
  cpio \
  distro-info \
  file \
  lib32gcc-s1 \
  lib32stdc++6 \
  libsdl2-2.0-0:i386 \
  netcat-openbsd \
  pigz \
  python3 \
  tmux \
  jq \
  unzip \
  uuid-runtime \
  wget \
  xz-utils \
  && rm -rf /var/lib/apt/lists/*

# Install SteamCMD
RUN wget https://steamcdn-a.akamaihd.net/client/installer/steamcmd_linux.tar.gz \
  && tar -xvzf steamcmd_linux.tar.gz -C /usr/local/bin \
  && rm steamcmd_linux.tar.gz

# Create a user for LinuxGSM
RUN useradd -m factorio

# Switch to the new user
USER factorio
WORKDIR /home/factorio
