# 🤖 WhatsApp Bot Containerized (Evolution API + Typebot + PostgreSQL + Redis)

Este repositório contém a estrutura em **Docker Compose** para subir uma infraestrutura local e gratuita de atendimento automatizado via WhatsApp, conectando a **Evolution API** (open-source) ao **Typebot**, utilizando **PostgreSQL** como banco de dados relacional e **Redis** para gerenciamento de cache e filas.

Projeto desenvolvido para fins de demonstração em oficinas, workshops e congressos, funcionando sem dependência da Meta WhatsApp Business Platform e com custo zero de infraestrutura.

---

## 🏗️ Arquitetura do Sistema

---

## 🛠️ Tecnologias Utilizadas

* **[Evolution API v2](https://github.com/EvolutionAPI/evolution-api):** Gateway de integração não-oficial com o WhatsApp.
* **[Typebot](https://typebot.io):** Construtor visual de fluxos de conversa.
* **[PostgreSQL 15](https://www.postgresql.org/):** Banco de dados relacional leve e performático para persistência de instâncias e mensagens.
* **[Redis](https://redis.io/):** Armazenamento em memória para filas de requisições e controle de sessão do Typebot.
* **[Docker & Docker Compose](https://www.docker.com/):** Containerização de todos os serviços.

---

## 🚀 Como Rodar o Projeto

### Pré-requisitos
* **Docker** e **Docker Compose** instalados na máquina.
* Uma conta gratuita no [Typebot.io](https://typebot.io).
* Um celular com o WhatsApp instalado para pareamento via QR Code.

### 1. Clonar o Repositório
```bash
git clone [git@github.com:Iran-Ferreira/oficina-bot.git](git@github.com:Iran-Ferreira/oficina-bot.git)
cd seu-repositorio
```

### 2. Subir os Containers

    Execute o comando abaixo na raiz do projeto:

    docker compose up -d


### 3. Verificar o Status dos Serviços

    docker compose ps


## Acesse o painel da Evolution API no seu navegador:
👉 http://localhost:8080/manager

Global API Key: SenhaOficina123 (pode ser alterada no docker-compose.yml)


# ⚙️ Configuração Passo a Passo
## 1. Conectar a Instância do WhatsApp
    Acesse o painel em http://localhost:8080/manager e informe a Global API Key.

    Crie uma nova instância (ex: oficina).

    Clique em Gerar QR Code.

    No WhatsApp do celular, vá em Aparelhos Conectados > Conectar um Aparelho e escaneie o código.

    Verifique se o status mudou para CONNECTED.
   







## 2. Configurar a Integração com o Typebot

    Para integrar seu fluxo de conversa hospedado no Typebot.io com a Evolution API:

    No painel da Evolution API, vá até a aba Typebot dentro da sua instância.

    Preencha os campos com os seguintes valores:

    Status: Enabled (Ativado).

    Typebot URL: https://viewer.typebot.io (URL base do visualizador/API do Typebot).

    Bot Name / Public ID: Digite apenas o ID público do seu bot (ex: restaurante-xpys0my).

    Expire (minutes): 10 ou 20 (tempo para reiniciar a sessão se o usuário parar de responder).

⚠️ Atenção: Não cole a URL completa do chatbot no campo de servidor (ex: https://typebot.co/meu-bot). A URL base da API deve ser estritamente https://viewer.typebot.io e o ID deve ser inserido separadamente no campo do Bot ID para evitar erros 503 Service Unavailable.