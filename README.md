# <i>3º Projeto Prático - DevOps: Implementação de Microsserviços com Kubernetes (K8s) na AWS </i>

***
<b>3º Projeto Prático - DevOps</b>
***

### 💻 <i> Desafio </i>

Projete e implemente uma aplicação utilizando arquitetura de microsserviços no Kubernetes (K8s) no provedor de nuvem da AWS (EKS).


***
### 📋<i> Etapas </i>

<b>a. Design de Microsserviços: Identifique os componentes da aplicação que serão implantados em microsserviços.</b>

####
<b>b. Implementação no K8s: Crie e implante os microsserviços no Kubernetes da AWS (EKS).
</b>

####
<b>c. Escalabilidade e Tolerância a Falhas: Configure a escalabilidade automática e tolerância a falhas para os microsserviços.</b>

####
<b>d. Atualização e Monitoramento: Implemente procedimentos de atualização e monitore o desempenho dos microsserviços no K8s.</b>

####

***
### 📖<i> Introdução </i>

* Neste projeto será necessario possuir estes itens instalados e devidamente configurados:

[x] -  O ubuntu mais especificamente a versao Ubuntu 22.04.4 LTS.

[x] - [Nginx](https://nginx.org) para criar os arquivos de configuração e teste da pagina de web.

[x] - [Docker](https://www.docker.com/) para criar o container do NGINX e subir os arquivos para o mesmo.

[x] - [Docker hub](https://hub.docker.com) para criar um acesso a um container privado para o projeto.

[x] - [Docker compose](https://docs.docker.com/compose/install/standalone/) facilitar o gerenciamento e a definição de aplicações multi-container no Docker.

[x] - [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl-linux/) para intereção com o kubernetes

[x] - [minikube](https://minikube.sigs.k8s.io/docs/start/?arch=%2Flinux%2Fx86-64%2Fstable%2Fbinary+download) para facilitar o uso do kubernetes no SO escolhido ou [AWS EKS](https://docs.aws.amazon.com/eks/latest/userguide/setting-up.html) para utilizar o kubernetes em nuvem.

### ⚙️ <i> Instalação </i>
***
#### ➡️  Etapas

1. Antes de instalar qualquer app ou programa devemos atualizar a maquina e utilizamos este comando:
- ```sudo apt-get update```

2. Caso não possua na maquina precisamos instalar antes de tudo o curl:
- ```sudo apt-get install curl```

3. Agora instalaremos o docker.
Clicando [aqui](https://docs.docker.com/desktop/install/ubuntu/) voce sera redirecionado para a pagina de instalação no ubuntu explicando que versão precisa possuir seu SO entre outras informações.
#####
4. Precisaremos criar uma conta no [Docker hub](https://app.docker.com/signup/), clicando no docker hub voce sera redirecionado para a pagina de criação de conta.
#####
5. [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl-linux/), explicação da instalação do kubectl.
#####
6. [minikube](https://minikube.sigs.k8s.io/docs/start/?arch=%2Flinux%2Fx86-64%2Fstable%2Fbinary+download) tambem redireciona para a pagina de instalção do minikube.

### 👨🏽‍💻<i> Explicação das Ferramentas</i>
***
### <i> Docker </i>

Docker é uma ferramenta que facilita o empacotamento e a execução de aplicativos em "contêineres". Esses contêineres incluem tudo o que o aplicativo precisa para funcionar, garantindo que ele rode da mesma forma em qualquer ambiente.

### <i> Nginx </i>

É um servidor web que também pode funcionar como um proxy reverso e balanceador de carga.

* <b>Servidor Web</b>: Nginx serve páginas web para os usuários da internet.
#####
* <b>Proxy Reverso</b>: Ele pode redirecionar solicitações de usuários para outros servidores ou serviços.
#####
* <b>Balanceador de Carga</b>: Distribui as solicitações entre vários servidores para melhorar a performance e a confiabilidade.

### <i> Doker compose </i>

Ferramenta que simplifica a execução de aplicações com vários contêineres Docker.

* <b>Configuração</b>: Você usa um arquivo para definir como cada contêiner deve ser configurado e como eles devem trabalhar juntos.
#####
* <b>Execução Fácil</b>: Com um único comando, você inicia todos os contêineres definidos no arquivo.
#####
* <b>Coordenação</b>: Facilita o gerenciamento de vários contêineres, redes e dados compartilhados.

### <i> Kubectl </i>

```kubectl``` é uma ferramenta de linha de comando para interagir com o Kubernetes.

* <b>Controle</b>: Com kubectl, você pode criar, atualizar e gerenciar recursos no seu cluster Kubernetes, como pods, serviços e deployments.
#####
* <b>Execução de Comandos</b>: Usa comandos para fazer tarefas como escalar aplicações, verificar status e aplicar configurações.
#####
* <b>Acesso</b>: Facilita a comunicação com o Kubernetes e a execução de operações de administração.

### <i> Minikube </i>

Auxilia a executar o Kubernetes no seu próprio computador, servindo como:

* <b>Cluster Local</b>: Minikube cria um ambiente Kubernetes em sua máquina, para você testar e desenvolver localmente.
#####
* <b>Simples e Rápido</b>: Facilita a instalação e configuração de um cluster Kubernetes para que você possa começar rapidamente.
#####
* <b>Controle Local</b>: Permite iniciar, parar e gerenciar seu próprio cluster de forma prática.

### <i> Grafana </i>

Ferramenta para visualizar dados e métricas. Como:

* <b>Visualização</b>: Grafana cria gráficos e painéis interativos para exibir dados e métricas de forma clara e acessível.
* <b>Integração</b>: Conecta-se a várias fontes de dados, como Prometheus, para mostrar informações em tempo real.
* <b>Personalização</b>: Permite criar e personalizar dashboards para monitorar e analisar dados conforme suas necessidades.

### <i> Prometheus </i>

Ferramenta para monitoramento e coleta de métricas. Servindo:

* <b>Coleta de Dados</b>: Prometheus coleta e armazena métricas de sistemas e aplicações em tempo real.
* <b>Consultas</b>: Permite consultar e analisar essas métricas usando uma linguagem própria chamada PromQL.
* <b>Alertas</b>: Pode gerar alertas com base nas métricas coletadas para notificar sobre problemas.

### 🛠️<i> Mãos a obra </i>
***

<b>1. Dockerfile</b> Crie estes 2 Dockerfiles, para criar as imagens dos containers.

- [Dockerfile para micro serviço de pedidos](./microsservicos/micro-order/Dockerfile)

- [Dockerfile para micro serviço de produtos](./microsservicos/micro-product/Dockerfile)

  Fazendo isso ele irá ter a base da criação do container com base na imagem do nginx alpine, e irá copiar os arquivos das pastas de micro-order e micro-product para suas devidas imagens as pastas e arquivos html.

<b>2. Docker-compose</b> Crie mais dois arquivos so que Docker-compose.yml, um para cada microsserviço, neste caso irá ser um para o de `pedidos` e outro para o de `produtos`

- [Docker-compose para micro serviço de pedidos](./microsservicos/micro-order/docker-compose.yml)

- [Docker-compose para micro serviço de produtos](./microsservicos/micro-product/docker-compose.yml)

   Fazendo isso ele irá construir a imagem a partir do Dockerfile criado anteriormente, junto das configurações como mapeamento das portas e montagem de volumes junto da configuração do proprio nginx.

<b>3. Pods</b> Iremos subir os pods com o kubernetes com os seguintes arquivos:

- [order-service-deploy.yaml](./kubernetes/order-service-deploy.yaml)

- [product-service-deploy.yaml](./kubernetes/product-service-deploy.yaml)

Executando os seguintes comandos:

```sh
kubectl apply -f kubernetes/order-service-deploy.yaml
kubectl apply -f kubernetes/product-service-deploy.yaml
```

Fazendo isso ele une os dois containers para trabalharem juntos simplificando a escalabilidade e a administração dos recursos da aplicação.

<b>4. Prometheus</b> Agora iremos aplicar com o `kubectl` os .yml de configuração como mapeamento de portas e aplicar no local para configurar o prometheus para conseguir adquirir os dados necessarios para obter um relatório de das aplicações dos microsserviços executados acima.

```sh
kubectl apply -f kubernetes/prometheus-configmap.yml
kubectl apply -f kubernetes/prometheus-deploy.yml
kubectl apply -f kubernetes/prometheus-serv.yml
```

<b>4. Automatização de Deployments</b> Para automatizar os deployments, sugerimos a configuração de pipelines de CI/CD com ferramentas como Jenkins, GitLab CI ou GitHub Actions. Um pipeline típico pode abranger etapas como a construção da imagem Docker, o upload para o Docker Hub e a aplicação das configurações no Kubernetes. Neste projeto, optou-se pelo GitHub Actions.

```yml
# Pipeline de CI/CD exemplo para GitHub Actions
name: CI/CD Pipeline

on:
  push:
    branches:
      - main

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout código
        uses: actions/checkout@v2

      - name: Configurar Docker Buildx
        uses: docker/setup-buildx-action@v1

      - name: Build da imagem Docker
        run: docker build -t docker-user/kubernets:latest .

      - name: Login no Docker Hub
        uses: docker/login-action@v1
        with:
          username: ${{ secrets.DOCKER_USER }}
          password: ${{ secrets.DOCKER_PASS }}

      - name: Push da imagem para o Docker Hub
        run: docker push docker-user/kubernets:latest

      - name: Aplicar configurações Kubernetes
        run: kubectl apply -f kubernetes/
```

Com esta configuração do Github actions o deploy será automatizado para subir os arquivos, alem de criar as imagens e executar os deployments dos pods e suas configurações.

<b>4. Escalabilidade</b> Para modificar a escalabilidade dos serviços é necessario modificar o numero de replicas dentro do arquivo de deploy, onde possui o campo `replicas:`, se quiser voce pode modificar o valor e aplica a configuração atualizada re-executar o seguinte comando:

```sh
    kubectl apply -f kubernetes/order-service-deploy.yaml
```
Para o de pedidos.

```sh
    kubectl apply -f kubernetes/product-service-deploy.yaml
```
Para o de produtos.

### <i> Referências </i>

- [Install Docker Desktop on Ubuntu](https://docs.docker.com/desktop/install/ubuntu/)

- [Conheça NGINX e saiba as vantagens de utilizá-lo em seu servidor](https://qnax.sh/blog/nginx-vantagens-servidor/?gad_source=1&gclid=Cj0KCQjwpNuyBhCuARIsANJqL9OAOn5t8aKDwQtyG-nLFW7KtMN1ST5qV2t27zgGPXWQRyPE6DDX8JEaAs0MEALw_wcB)

- [Aprendendo o basico sobre kubernetes](https://kubernetes.io/docs/tutorials/kubernetes-basics/)

- [Overview | Prometheus](https://prometheus.io/docs/introduction/overview/)

- [Overview of Docker Hub](https://docs.docker.com/docker-hub/)

- [Kubectl Reference Docs](https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands)
