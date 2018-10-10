FROM jenkins/jenkins:lts

# Should switch to root before installing .NET Core SDK
USER root

# Install dependencies and configure repositories
RUN apt-get update \
    && apt-get install -y --no-install-recommends \
    curl libunwind8 gettext apt-transport-https && \
    curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg && \
    mv microsoft.gpg /etc/apt/trusted.gpg.d/microsoft.gpg && \
    sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-stretch-prod stretch main" > /etc/apt/sources.list.d/dotnetdev.list' && \
    apt-get install -y zip && \
    apt-get update

# Install .NET Core SDK
RUN apt-get install -y dotnet-sdk-2.1 && \
    export PATH=$PATH:$HOME/dotnet && \
    dotnet --version

USER jenkins