FROM mcr.microsoft.com/devcontainers/base:ubuntu-22.04
RUN <<'EOF'
apt-get update -y
export DEBIAN_FRONTEND=noninteractive
apt-get install -y --no-install-recommends \
    r-base \
    r-base-dev \
    libxml2-dev \
    libssl-dev \
    libcurl4-openssl-dev \
    libgl1-mesa-dev \
    libfreetype6-dev \
    libpng-dev \
    libtiff5-dev \
    libgfortran5 \
    python3-pip
apt-get clean
rm -rf /var/lib/apt/lists/*
EOF
RUN pip3 install radian
ENV RENV_PATHS_CACHE=/renv/cache
RUN mkdir -p /renv/cache && chown vscode:vscode /renv/cache
RUN --mount=type=cache,target=/renv/cache Rscript -e 'install.packages("renv")'
