# Usar a imagem base do Langflow
FROM langflowai/langflow:1.6.5

# Criar diretórios internos
RUN mkdir /app/flows
RUN mkdir /app/langflow-config-dir
RUN mkdir /app/components

WORKDIR /app

# Copiar arquivos essenciais (adapte os paths para seu fork)
COPY flows /app/flows
COPY langflow-config-dir /app/langflow-config-dir
COPY docker.env /app/.env

# *Opcional*: componentes customizados
COPY components /app/components

# *Opcional*: dependências extras
COPY pyproject.toml uv.lock /app/

# Definir variáveis de ambiente (serão sobrescritas pelo docker.env se duplicadas)
ENV PYTHONPATH=/app
ENV LANGFLOW_LOAD_FLOWS_PATH=/app/flows
ENV LANGFLOW_CONFIG_DIR=/app/langflow-config-dir
ENV LANGFLOW_COMPONENTS_PATH=/app/components
ENV LANGFLOW_LOG_ENV=container

EXPOSE 7860

# Modo apenas backend. Remova o "--backend-only" se quiser também a interface visual
CMD ["langflow", "run", "--backend-only", "--env-file", "/app/.env", "--host", "0.0.0.0", "--port", "7860"]
