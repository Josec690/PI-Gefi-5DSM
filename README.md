# GeFi - Gestão Financeira

Sistema de gestão financeira com backend em Flask, frontend em Expo/React Native e MongoDB local para desenvolvimento.

## Visão Geral

Este repositório usa submódulos Git para manter os projetos separados:

- [backend](backend) - API Flask
- [frontend](frontend) - App Expo

## Requisitos

- Git 2.30+
- Docker Desktop
- Node.js 18+ para desenvolvimento local do frontend
- Python 3.11+ para desenvolvimento local do backend

## Clone do repositório

Como o projeto usa submódulos, clone assim:

```bash
git clone --recurse-submodules https://github.com/Josec690/PI-Gefi-5DSM.git
```

Se o repositório já foi clonado sem submódulos:

```bash
git submodule update --init --recursive
```

## Executar com Docker

1. Garanta que o Docker Desktop esteja aberto.
2. Na raiz do projeto, execute:

```bash
docker compose up -d mongo gefi-back
```

3. O backend ficará disponível em `http://localhost:5000`.
4. O MongoDB local ficará disponível na porta `27017`.

### Frontend

O frontend roda com Expo na porta `3000`.

```bash
docker compose up -d gefi-front
```

Observação: a primeira execução pode baixar dependências e levar alguns minutos.

## Execução local sem Docker

### Backend

```bash
cd backend
python -m venv venv
venv\Scripts\activate
pip install -r requirements.txt
python app.py
```

### Frontend

```bash
cd frontend
npm install
npm start
```

## Variáveis de ambiente

Os exemplos de configuração ficam em:

- [backend/.env.example](backend/.env.example)
- [frontend/.env.example](frontend/.env.example)

O backend usa Mongo local por padrão no Docker:

```env
MONGODB_URL=mongodb://mongo:27017
DATABASE_NAME=gefinanca_db
```

Se quiser usar MongoDB Atlas, altere o valor no arquivo `backend/.env` apenas no seu ambiente local.

## URLs úteis

- Backend: `http://localhost:5000`
- Frontend: `http://localhost:3000`

## Estrutura

```text
PI-Gefi-5DSM/
├── backend/
├── frontend/
├── docker-compose.yml
└── README.md
```

## Colaboração

1. Crie uma branch para sua alteração.
2. Nunca envie credenciais reais para o GitHub.
3. Use os arquivos `.env.example` como base para configurar seu ambiente local.
4. Se editar backend ou frontend, lembre que são submódulos e precisam ser commitados no repositório correspondente.

## Observações

- O backend conecta em MongoDB local quando executado via Docker.
- O frontend resolve a URL da API automaticamente no ambiente Expo.
- Se a primeira build do frontend falhar por rede, tente novamente com internet estável.

