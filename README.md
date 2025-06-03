# ☁️ Armazenando dados de um E-Commerce na Cloud com Docker e Azure

Este projeto foi desenvolvido como parte da trilha Microsoft Application Platform da DIO, com foco em containerização e armazenamento de dados em nuvem. O objetivo é armazenar dados de um e-commerce utilizando **Docker**, **Azure Container Registry (ACR)** e **Azure Cloud**.

---

## 📦 Etapas do Projeto

### 1. Introdução

Apresentação dos conceitos de cloud computing, containers e do desafio proposto: containerizar uma aplicação de e-commerce e prepará-la para ser executada em ambiente de nuvem, com repositório de imagens próprio e estrutura organizada.

---

### 2. Criando o Dockerfile

Nesta etapa, foi criado o arquivo `Dockerfile` com as instruções necessárias para construir a imagem da aplicação, contendo:

- A imagem base (ex: `node`, `python`, etc.)
- Instalação de dependências
- Configuração do diretório de trabalho
- Instrução de execução do servidor (ex: `CMD ["npm", "start"]`)

O Dockerfile é essencial para padronizar o ambiente de execução e facilitar o deploy em qualquer lugar.

---

### 3. Criando o Resource Group e Container Registry

No **Azure Portal**, foi criado um **Resource Group** para agrupar todos os recursos relacionados ao projeto, e um **Azure Container Registry (ACR)** para armazenar a imagem do container.

- O Resource Group facilita o gerenciamento e organização dos recursos.
- O ACR funciona como um “repositório Docker privado” hospedado na Azure.

Com isso, conseguimos ter um local seguro e acessível para as imagens que serão usadas no deploy.

---

### 4. Login no ACR

Foi realizada a autenticação no ACR usando a CLI da Azure:

```bash
az login
az acr login --name nomeDoSeuRegistro

---

Após construir a imagem com docker build e autenticar no ACR, enviamos a imagem com:

docker tag minhaimagem nomeDoRegistro.azurecr.io/minhaimagem
docker push nomeDoRegistro.azurecr.io/minhaimagem
Com isso, a imagem está armazenada no ACR e pronta para ser usada em um serviço gerenciado da Azure (como AKS, App Service, etc.) para rodar a aplicação em produção.
