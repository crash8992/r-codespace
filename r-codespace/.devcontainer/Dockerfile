# Imagen base mínima con Ubuntu
FROM ubuntu:22.04

# Instalar dependencias básicas y R
USER root
RUN apt-get update && apt-get install -y --no-install-recommends \
    r-base \
    r-base-dev \
    libcurl4-openssl-dev \
    libssl-dev \
    libxml2-dev \
    sudo \
    wget \
    git \
    && rm -rf /var/lib/apt/lists/*

# Instalar IRkernel para Jupyter
RUN R -e "install.packages('IRkernel', repos='https://cloud.r-project.org/')"
RUN R -e "IRkernel::installspec(user = FALSE)"

# Crear usuario vscode por compatibilidad con Codespaces
RUN useradd -m vscode && echo "vscode ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers
USER vscode
WORKDIR /home/vscode
