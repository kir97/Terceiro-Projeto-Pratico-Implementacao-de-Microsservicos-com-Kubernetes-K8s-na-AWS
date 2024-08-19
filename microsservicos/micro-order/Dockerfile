# Utiliza a imagem base do Nginx Alpine
FROM nginx:alpine

# Define o diretório dentro do container
WORKDIR /usr/share/nginx/html

# Copia os arquivos para o diretório de trabalho
COPY ./dist .

# Expõe a porta 80 para o serviço
EXPOSE 80