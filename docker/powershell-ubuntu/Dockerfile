# Last modified: Wed, 30 September 2020 16:01:26 +0000
FROM mcr.microsoft.com/powershell:7.1.3-ubuntu-20.04-20210616

# For the `no supported WSMan client library was found` error when using Ubuntu 20+
RUN apt-get update -y
RUN sh -c "yes | pwsh -Command 'Install-Module -Name PSWSMan'"
RUN pwsh -Command 'Install-WSMan'

RUN apt update && apt install netbase -y
# Upgrade all packages to latest
RUN apt-get update && apt-get -y --no-install-recommends upgrade \
&& rm -rf /var/lib/apt/lists/*

RUN groupadd --gid 4000 demisto \
  && useradd --uid 4000 --gid demisto --shell /bin/bash --create-home demisto
