# [Choice] .NET version: 6.0-focal, 7.0-bullseye, 8.0-bookworm, 9.0-bookworm, 10.0-noble (default)
ARG VARIANT="10.0-noble"
FROM mcr.microsoft.com/devcontainers/dotnet:1-${VARIANT}

# Add .NET global tools path
ENV PATH=$PATH:/home/vscode/.dotnet:/home/vscode/.dotnet/tools

# Install additional OS packages (note: DEBIAN_FRONTEND used for Debian/Ubuntu non-interactive installs)
RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
    && apt-get -y install --no-install-recommends software-properties-common

# Install SQL Tools: SQLPackage and sqlcmd
COPY sql/installSQLtools.sh installSQLtools.sh

# Install SQL tools and clean up apt cache (cached packages, package lists, etc.) and temp files
RUN bash ./installSQLtools.sh \
     && apt-get clean -y && rm -rf /var/lib/apt/lists/* /tmp/library-scripts

# Install Data API Builder for vscode user
RUN su vscode -c "dotnet tool install --global Microsoft.DataApiBuilder" 2>&1

# Install StrawberryShake.Tools for vscode user
RUN su vscode -c "dotnet tool install --global StrawberryShake.Tools" 2>&1