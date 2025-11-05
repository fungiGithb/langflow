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

# "CMD": Dados de execução - comando principal que será executado quando o container iniciar
CMD ["langflow", "run", "--env-file", "/app/.env", "--host", "0.0.0.0", "--port", "7860"]

# "langflow run": Inicia o servidor LangFlow
# "--env-file /app/.env": Carrega variáveis de ambiente do arquivo .env
# "--host 0.0.0.0": Escuta em todos os endereços de rede (necessário para acesso externo)
# "--port 7860": Define a porta de escuta como 7860

# OBSERVAÇÃO SOBRE MODO DE EXECUÇÃO:
# Atualmente: Esta configuração executa backend + frontend, permitindo acesso à interface visual em http://0.0.0.0:7860/
# Para modo APENAS backend (sem interface visual): Adicione a flag "--backend-only" ao comando acima
# Exemplo: CMD ["langflow", "run", "--backend-only", "--env-file", "/app/.env", "--host", "0.0.0.0", "--port", "7860"]
# Use modo backend-only se estiver integrando via API com outras aplicações
