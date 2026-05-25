# Banco API Performance Tests

Projeto de testes de performance utilizando **JavaScript** e **K6** para validar a capacidade, estabilidade e comportamento da API do projeto Banco API sob diferentes cargas de requisição.

## Introdução

Este repositório contém cenários de testes de performance desenvolvidos com K6, permitindo avaliar métricas como:

- Tempo de resposta
- Taxa de sucesso e falhas
- Throughput
- Comportamento sob carga
- Estabilidade da aplicação

Os testes podem ser executados contra diferentes ambientes através da variável de ambiente `BASE_URL`, tornando o projeto flexível para testes locais, homologação ou produção.

---

## Tecnologias Utilizadas

- JavaScript (ES6+)
- K6
- Node.js
- npm

---

## Estrutura do Repositório

```text
banco-api-performance/
│
├── config/
│   └── config.local.json
│
├── fixtures/
│   └── postLogin.json
│
├── helpers/
│   └── autenticacao.js
│
├── utils/
│   └── variaveis.js
│
│   ├── login.test.js
│   └── transferencias.test.js
│
├── README.md
└── .gitignore
```

---

## Instalação

### Pré-requisitos

- Node.js 18+ (ou versão compatível)
- npm
- K6 instalado na máquina

### Clonar o repositório

```bash
git clone https://github.com/ericaanfiloquio/banco-api-performance.git
```

### Acessar o diretório

```bash
cd banco-api-performance
```

### Instalar dependências

```bash
npm install
```

---

## Execução do Projeto

### Configurar a URL da API

Antes de executar os testes, defina a variável de ambiente `BASE_URL`.

### Linux / macOS

```bash
BASE_URL=https://api.exemplo.com npm run test
```

### Windows (PowerShell)

```powershell
$env:BASE_URL="https://api.exemplo.com"
npm run test
```

### Windows (CMD)

```cmd
set BASE_URL=https://api.exemplo.com
npm run test
```

---

## Executar os Testes

Certifique-se de passar a variável de ambiente `BASE_URL`, caso não esteja usando `config.local.json` ou uma abordagem de carregamento automático:

### Execução simples

```bash
kB run /login.test.js -e
BASE_URL=http://localhost:3000
```

### Execução com Dashboard em Tempo Real

```bash
K6_WEB_DASHBOARD=true \
```

### Execução com Dashboard e Exportação do Relatório HTML

```bash
K6_WEB_DASHBOARD=true \
K6_WEB_DASHBOARD_EXPORT=html-report.html \
k6 run login.test.js \
-e BASE_URL=http://localhost:3000
```

Ao final da execução será gerado:

```text
html-report.html
```

Este arquivo pode ser aberto em qualquer navegador para análise dos resultados.

---

## Variáveis de Ambiente

| Variável | Descrição | Obrigatória |
|-----------|------------|-------------|
| BASE_URL | URL base da API a ser testada | Sim |
| K6_WEB_DASHBOARD | Habilita dashboard web do K6 | Não |
| K6_WEB_DASHBOARD_EXPORT | Exporta relatório HTML | Não |

---

## Repositório

GitHub:

https://github.com/ericaanfiloquio/banco-api-performance
