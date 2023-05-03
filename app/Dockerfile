# Dockerfile para construir una imagen con dos ambientes de Conda (para análisis de datos y visualización de datos) y un comando para ejecutar JupyterLab

# Primera etapa: Instalar Jupyter en la imagen base de Conda
FROM continuumio/miniconda3:latest AS base

RUN conda install -y jupyter && \
    conda clean --all --yes

# Segunda etapa: Construir ambiente para análisis de datos
FROM base AS data_analysis

WORKDIR /app

COPY app/environment-data-analysis.yml .

RUN conda env update --name base --file environment-data-analysis.yml && \
    conda clean --all --yes

# Tercera etapa: Construir ambiente para visualización de datos
FROM base AS data_viz

WORKDIR /app

COPY app/environment-visualization.yml .

RUN conda env update --name base --file environment-visualization.yml && \
    conda clean --all --yes

# Cuarta etapa: Construir imagen final con ambas versiones de Conda
FROM base

COPY --from=data_analysis /opt/conda/envs /opt/conda/envs
COPY --from=data_viz /opt/conda/envs /opt/conda/envs

WORKDIR /app

COPY . .

EXPOSE 8888

CMD ["jupyter", "lab", "--ip=0.0.0.0", "--port=8888", "--no-browser","--allow-root", "--NotebookApp.token=''","--NotebookApp.password=''"]