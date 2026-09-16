# QA API Tests - Postman, Newman e REST API

![Postman](https://img.shields.io/badge/Postman-API%20Testing-orange)
![Newman](https://img.shields.io/badge/Newman-CLI%20Automation-orange)
![REST API](https://img.shields.io/badge/REST-API%20Testing-blue)
![JavaScript](https://img.shields.io/badge/JavaScript-Test%20Scripts-yellow)
![GitHub Actions](https://img.shields.io/badge/GitHub%20Actions-CI%2FCD-blue)
![JSON](https://img.shields.io/badge/JSON-Schema%20Validation-lightgrey)

![API Tests - Newman](https://github.com/brunolopes-ti/qa-api-tests/actions/workflows/api-tests.yml/badge.svg)

Projeto prático de **testes automatizados de API REST** utilizando Postman, Newman e JavaScript.

O projeto foi desenvolvido em duas etapas: uma suíte inicial utilizando **JSONPlaceholder**, voltada aos fundamentos de testes de API, e uma suíte avançada utilizando **Restful Booker**, contemplando autenticação, variáveis de ambiente, encadeamento de requisições, CRUD completo, validação de schema, testes negativos, execução automatizada em pipeline e publicação de relatórios de testes.

O projeto também utiliza **GitHub Actions em um fluxo de CI/CD**, executando automaticamente os testes e publicando relatórios HTML do Newman no GitHub Pages.

---

## Tecnologias utilizadas

- Postman;
- Newman;
- Newman HTML Extra Reporter;
- JavaScript;
- Node.js;
- npm;
- REST API;
- JSON;
- JSON Schema;
- JSONPlaceholder;
- Restful Booker;
- GitHub Actions;
- GitHub Pages;
- Git;
- GitHub;
- Visual Studio Code.

---

## Objetivo do projeto

Demonstrar conhecimentos práticos em testes de API REST, desde validações fundamentais até a construção de fluxos automatizados com dependência entre requisições e integração com pipeline de CI/CD.

O projeto contempla:

- Criação e organização de collections no Postman;
- Métodos HTTP;
- Validação de status codes;
- Validação de payloads JSON;
- Scripts JavaScript;
- Assertions;
- Variáveis de ambiente;
- Autenticação por token;
- Encadeamento de requisições;
- CRUD completo;
- Validação de JSON Schema;
- Testes positivos e negativos;
- Execução via Newman;
- Scripts npm;
- Geração automática de relatórios HTML;
- Integração contínua com GitHub Actions;
- Publicação automática de relatórios;
- GitHub Pages;
- Registro de evidências.

---

# APIs utilizadas

## JSONPlaceholder

API REST pública utilizada na etapa inicial do projeto para prática dos fundamentos de testes de API.

Foram trabalhadas operações de:

- Consulta;
- Criação;
- Atualização parcial;
- Exclusão.

---

## Restful Booker

API pública utilizada para evolução da suíte e implementação de cenários mais próximos de fluxos reais.

Com ela foram praticados:

- Health Check;
- Autenticação;
- Geração e armazenamento de token;
- Criação dinâmica de booking;
- Armazenamento de `bookingId`;
- Consulta;
- Atualização completa com `PUT`;
- Atualização parcial com `PATCH`;
- Validação de acesso sem autenticação;
- Exclusão;
- Validação da exclusão;
- JSON Schema;
- Testes negativos.

---

# Estrutura do projeto

```text
qa-api-tests/
├── .github/
│   └── workflows/
│       └── api-tests.yml
│
├── collections/
│   ├── QA Lab - API Tests (JSONPlaceholder).postman_collection.json
│   └── QA API Advanced - Restful Booker.postman_collection.json
│
├── environments/
│   └── Restful Booker - QA.postman_environment.json
│
├── prints/
│   ├── get-tests.png
│   ├── post-tests.png
│   ├── patch-tests.png
│   ├── delete-tests.png
│   ├── newman-run-passando.png
│   ├── newman-restful-booker-success.png
│   ├── newman-all-api-tests-success.png
│   ├── restful-booker-health-check.png
│   ├── restful-booker-create-booking.png
│   ├── restful-booker-get-booking.png
│   ├── restful-booker-schema-validation.png
│   ├── restful-booker-put-booking.png
│   ├── restful-booker-patch-booking.png
│   ├── restful-booker-delete-booking.png
│   ├── restful-booker-delete-validation.png
│   ├── restful-booker-invalid-auth.png
│   ├── restful-booker-update-without-auth.png
│   ├── restful-booker-invalid-payload.png
│   └── github-actions-api-tests-job-success.png
│
├── reports/                         # gerado automaticamente
│   ├── index.html
│   └── jsonplaceholder.html
│
├── .gitignore
├── package.json
├── package-lock.json
└── README.md
```

A pasta `reports/` é gerada durante a execução dos scripts de relatório e não é versionada no repositório.

---

# Suíte 1 - JSONPlaceholder

A primeira collection foi criada para praticar os fundamentos de testes automatizados de APIs REST.

Arquivo:

```text
collections/QA Lab - API Tests (JSONPlaceholder).postman_collection.json
```

## Cenários

### CT-01 - GET - Consultar posts

Validações:

- Status code `200`;
- Retorno de dados;
- Estrutura da resposta.

### CT-02 - POST - Criar recurso

Validações:

- Status code `201`;
- Retorno de ID;
- Dados enviados no payload;
- Armazenamento de variável.

### CT-03 - PATCH - Atualizar recurso

Validações:

- Status code `200`;
- Atualização parcial;
- Conteúdo retornado.

### CT-04 - DELETE - Remover recurso

Validações:

- Status esperado;
- Execução da operação de exclusão.

---

## Resultado da suíte básica

Execução com Newman:

```text
Requests:    4
Assertions: 11
Failures:    0
Resultado:  Passed
```

### Evidência

![Newman JSONPlaceholder](prints/newman-run-passando.png)

---

# Suíte 2 - Restful Booker

A segunda collection representa a evolução técnica do projeto.

Arquivo:

```text
collections/QA API Advanced - Restful Booker.postman_collection.json
```

Environment:

```text
environments/Restful Booker - QA.postman_environment.json
```

A suíte contém **11 requisições** e **36 assertions automatizadas**.

---

## CT-01 - Health Check

```http
GET /ping
```

Validações:

- Status code `201`;
- Tempo de resposta inferior ao limite definido.

### Evidência

![Health Check](prints/restful-booker-health-check.png)

---

## CT-02 - Gerar token de autenticação

```http
POST /auth
```

Validações:

- Status code `200`;
- Presença do token;
- Armazenamento automático no Environment.

O token retornado pela API é armazenado dinamicamente:

```javascript
pm.environment.set("token", response.token);
```

---

## CT-03 - Criar booking

```http
POST /booking
```

Validações:

- Status code `200`;
- Retorno de `bookingid`;
- Dados enviados;
- Armazenamento dinâmico do ID.

```javascript
pm.environment.set("bookingId", response.bookingid);
```

### Evidência

![Create Booking](prints/restful-booker-create-booking.png)

---

## CT-04 - Consultar booking criado

```http
GET /booking/{{bookingId}}
```

Validações:

- Status code `200`;
- Nome;
- Sobrenome;
- Valor;
- Datas;
- Necessidade adicional;
- Schema JSON.

### JSON Schema

A estrutura da resposta também é validada utilizando JSON Schema.

Exemplo:

```javascript
pm.test("Schema da resposta deve ser válido", function () {
    pm.response.to.have.jsonSchema(schema);
});
```

### Evidência

![Schema Validation](prints/restful-booker-schema-validation.png)

---

## CT-05 - Atualizar booking com PUT

```http
PUT /booking/{{bookingId}}
```

A requisição utiliza o token criado anteriormente:

```text
Cookie: token={{token}}
```

Validações:

- Status code `200`;
- Atualização dos dados;
- Alteração do valor;
- Alteração do depósito;
- Atualização das datas.

### Evidência

![PUT Booking](prints/restful-booker-put-booking.png)

---

## CT-06 - Atualizar booking com PATCH

```http
PATCH /booking/{{bookingId}}
```

Validações:

- Status code `200`;
- Atualização parcial;
- Campos alterados;
- Preservação dos campos não modificados.

### Evidência

![PATCH Booking](prints/restful-booker-patch-booking.png)

---

## CT-10 - Atualizar booking sem autenticação

```http
PUT /booking/{{bookingId}}
```

É realizada uma tentativa de atualizar um booking existente sem token válido.

Na ordem de execução da collection, este cenário é executado após o CT-06 e antes da exclusão do booking no CT-07.

Dessa forma, a validação de autenticação ocorre enquanto o recurso ainda existe.

Resultado esperado:

```text
403 Forbidden
```

Validações:

- Status code `403`;
- Acesso bloqueado;
- Operação protegida contra requisição não autenticada.

### Evidência

![Unauthorized Update](prints/restful-booker-update-without-auth.png)

---

## CT-07 - Excluir booking

```http
DELETE /booking/{{bookingId}}
```

Validações:

- Status code `201`;
- Confirmação da exclusão.

### Evidência

![DELETE Booking](prints/restful-booker-delete-booking.png)

---

## CT-08 - Validar exclusão

Após a exclusão, uma nova consulta é realizada:

```http
GET /booking/{{bookingId}}
```

Resultado esperado:

```text
404 Not Found
```

Isso confirma que o recurso excluído não pode mais ser consultado.

### Evidência

![Delete Validation](prints/restful-booker-delete-validation.png)

---

# Testes negativos

Além das validações realizadas durante o fluxo principal, foram implementados cenários negativos adicionais.

---

## CT-09 - Autenticação com credenciais inválidas

```http
POST /auth
```

É enviada uma senha inválida.

Resultado retornado:

```json
{
  "reason": "Bad credentials"
}
```

Validações:

- Status code `200`, conforme comportamento da API utilizada;
- Resposta da API;
- Mensagem de credenciais inválidas;
- Ausência de token.

### Evidência

![Invalid Authentication](prints/restful-booker-invalid-auth.png)

---

## CT-11 - Payload inválido

```http
POST /booking
```

É enviado um payload propositalmente inválido contendo campos ausentes e tipos incorretos.

O objetivo do cenário é confirmar que a operação não seja concluída com sucesso.

Na execução documentada, a API Restful Booker rejeitou a requisição retornando:

```text
500 Internal Server Error
```

As assertions validam que:

- A resposta não pertença à faixa de sucesso `2xx`;
- A API retorne um status de erro igual ou superior a `400`.

O retorno `500` é documentado como comportamento observado da API pública de laboratório.

Ele não é tratado como resposta ideal para um erro de validação do cliente.

O script também registra um aviso quando ocorre resposta `5xx`, indicando que um erro `4xx` seria mais apropriado para esse tipo de entrada inválida.

Exemplo da validação utilizada:

```javascript
pm.test("Booking inválido não deve ser criado com sucesso", function () {
    pm.expect(pm.response.code).to.not.be.within(200, 299);
});

pm.test("API deve retornar uma resposta de erro", function () {
    pm.expect(pm.response.code).to.be.at.least(400);
});

if (pm.response.code >= 500) {
    console.warn(
        "A API rejeitou o payload, porém retornou erro 5xx em vez de um erro de cliente 4xx."
    );
}
```

### Evidência

![Invalid Payload](prints/restful-booker-invalid-payload.png)

---

# Environment

O projeto utiliza um Environment do Postman para evitar valores fixos dentro das requisições.

Variáveis utilizadas:

```text
baseUrl
username
password
token
bookingId
```

Exemplo:

```text
{{baseUrl}}/booking/{{bookingId}}
```

Os valores de `token` e `bookingId` ficam inicialmente vazios e são preenchidos dinamicamente durante a execução.

Isso permite que a suíte seja executada sem necessidade de inserir manualmente IDs ou tokens gerados anteriormente.

---

# Encadeamento de requisições

A suíte avançada possui dependência controlada entre requisições e utiliza valores gerados durante a própria execução.

```text
Health Check
      ↓
Autenticação
      ↓
Token
      ↓
Criar Booking
      ↓
bookingId
      ↓
Consultar
      ↓
PUT
      ↓
PATCH
      ↓
Atualização sem autenticação → 403
      ↓
DELETE
      ↓
Validar exclusão → 404
      ↓
Autenticação inválida
      ↓
Payload inválido
```

O `bookingId` criado no início da execução é reutilizado pelos cenários seguintes.

O CT-10 ocorre antes da exclusão para garantir que a resposta `403` esteja relacionada à ausência de autenticação e não à inexistência do recurso.

---

# Execução com Newman

O projeto pode ser executado fora da interface gráfica do Postman utilizando Newman.

Instale as dependências:

```bash
npm install
```

---

## Executar somente a suíte básica

```bash
npm run api:basic
```

---

## Executar somente a suíte avançada

```bash
npm run api:advanced
```

---

## Executar as duas suítes

```bash
npm run api
```

O comando executa primeiro a suíte JSONPlaceholder e, em seguida, a suíte Restful Booker.

---

# Geração de relatórios HTML

Além da execução padrão pelo terminal, o projeto utiliza o **newman-reporter-htmlextra** para geração automática de relatórios HTML.

Para executar as duas suítes e gerar os relatórios:

```bash
npm run api:report
```

São gerados:

```text
reports/
├── jsonplaceholder.html
└── index.html
```

O arquivo `index.html` corresponde ao relatório da suíte avançada Restful Booker e é utilizado como página principal na publicação via GitHub Pages.

---

# Scripts npm

Configuração disponível no `package.json`:

```json
"scripts": {
  "api": "npm run api:basic && npm run api:advanced",
  "api:basic": "newman run \"collections/QA Lab - API Tests (JSONPlaceholder).postman_collection.json\"",
  "api:advanced": "newman run \"collections/QA API Advanced - Restful Booker.postman_collection.json\" -e \"environments/Restful Booker - QA.postman_environment.json\"",
  "reports:prepare": "node -e \"require('fs').mkdirSync('reports', { recursive: true })\"",
  "api:basic:report": "newman run \"collections/QA Lab - API Tests (JSONPlaceholder).postman_collection.json\" -r cli,htmlextra --reporter-htmlextra-export reports/jsonplaceholder.html",
  "api:advanced:report": "newman run \"collections/QA API Advanced - Restful Booker.postman_collection.json\" -e \"environments/Restful Booker - QA.postman_environment.json\" -r cli,htmlextra --reporter-htmlextra-export reports/index.html",
  "api:report": "npm run reports:prepare && npm run api:basic:report && npm run api:advanced:report"
}
```

---

# Resultado da suíte avançada

Resultado da execução final documentada com Newman:

```text
Iterations:     1
Requests:      11
Test Scripts:  11
Assertions:    36
Failures:       0
```

Na execução final registrada:

```text
Total duration: 4.4s
Average response time: 305ms
```

Os tempos podem variar conforme rede e disponibilidade da API pública.

### Evidência

![Newman Restful Booker](prints/newman-restful-booker-success.png)

---

# Execução completa

As duas collections também foram executadas em sequência utilizando:

```bash
npm run api
```

Como os comandos são encadeados com `&&`, a suíte avançada somente é iniciada após a conclusão bem-sucedida da suíte básica.

A execução completa foi concluída sem falhas.

Resultados consolidados das duas suítes:

```text
Requests:   15
Assertions: 47
Failures:    0
```

### Evidência

![Newman All API Tests](prints/newman-all-api-tests-success.png)

---

# CI/CD com GitHub Actions

O projeto possui pipeline de **CI/CD** configurado com GitHub Actions.

Arquivo:

```text
.github/workflows/api-tests.yml
```

O workflow é executado em:

```text
push
pull_request
workflow_dispatch
```

para a branch principal:

```text
main
```

---

## Integração Contínua - CI

Na etapa de CI, o pipeline:

```text
Checkout do repositório
        ↓
Configuração do Node.js
        ↓
Instalação das dependências
        ↓
Execução das suítes de API
        ↓
Geração dos relatórios HTML
        ↓
Validação dos resultados
```

O comando executado pelo workflow é:

```bash
npm run api:report
```

Dessa forma, as duas collections são executadas automaticamente durante o pipeline.

Uma falha em uma das suítes interrompe a execução antes da etapa de publicação.

---

## Entrega Contínua - CD

Nos eventos de `push` para a branch `main`, após a conclusão bem-sucedida dos testes, o pipeline prepara os relatórios HTML como artefato de publicação.

Fluxo:

```text
Testes aprovados
        ↓
Relatórios Newman
        ↓
Upload do artefato
        ↓
Deploy
        ↓
GitHub Pages
```

O relatório principal publicado corresponde à suíte avançada Restful Booker.

A etapa de CD deste projeto é responsável pela **publicação automatizada dos relatórios de testes**, e não pelo deployment de uma aplicação.

Isso permite demonstrar um fluxo completo no qual uma entrega somente ocorre após a aprovação automatizada dos testes.

---

# GitHub Pages

Os relatórios gerados pelo Newman são preparados automaticamente para publicação no GitHub Pages.

Relatório principal:

```text
reports/index.html
```

Relatório adicional:

```text
reports/jsonplaceholder.html
```

Após a execução do workflow na branch `main`, o conteúdo da pasta de relatórios é utilizado na etapa de deployment.

---

# Fluxo completo do projeto

```text
Postman
   ↓
Collections
   ↓
Environment
   ↓
Requisições HTTP
   ↓
API REST
   ↓
Resposta
   ↓
Scripts JavaScript
   ↓
Assertions
   ↓
Variáveis dinâmicas
   ↓
Newman
   ↓
npm
   ↓
Relatórios HTML
   ↓
GitHub Actions
   ↓
CI
   ↓
Testes aprovados
   ↓
CD
   ↓
GitHub Pages
```

---

# Estratégia de qualidade no pipeline

O fluxo de CI/CD utiliza os testes automatizados como uma barreira de qualidade.

A etapa de publicação depende da conclusão bem-sucedida da execução dos testes.

```text
Alteração no código
        ↓
Pipeline iniciado
        ↓
Testes de API
        ↓
Passou?
   ↙           ↘
Não            Sim
 ↓              ↓
Pipeline       Geração
interrompido   de relatório
                ↓
              Deploy
                ↓
            GitHub Pages
```

Esse fluxo impede que o relatório de uma execução com testes falhando seja publicado pela etapa de deployment.

---

# Boas práticas aplicadas

- Separação entre suíte básica e avançada;
- Organização das collections;
- Environment separado da collection;
- URLs parametrizadas;
- Variáveis dinâmicas;
- Reaproveitamento de dados;
- Autenticação por token;
- Encadeamento de requisições;
- Validação de status codes;
- Validação de payloads;
- JSON Schema Validation;
- Testes positivos;
- Testes negativos;
- CRUD completo;
- Isolamento do cenário de autorização antes da exclusão do recurso;
- Scripts JavaScript;
- Assertions automatizadas;
- Execução via CLI;
- Automação com Newman;
- Scripts npm;
- Geração de relatórios HTML;
- Integração contínua;
- Entrega contínua;
- Quality Gate por execução automatizada de testes;
- GitHub Actions;
- GitHub Pages;
- Registro de evidências;
- Versionamento com Git e GitHub;
- Documentação técnica.

---

# Competências demonstradas

Este projeto demonstra prática em:

- Quality Assurance;
- API Testing;
- REST API;
- Postman;
- Newman;
- JavaScript;
- Node.js;
- JSON;
- JSON Schema;
- Métodos HTTP;
- GET;
- POST;
- PUT;
- PATCH;
- DELETE;
- Status codes;
- Headers;
- Cookies;
- Payloads;
- Assertions;
- Test Scripts;
- Variáveis de ambiente;
- Autenticação;
- Tokens;
- Encadeamento de dados;
- CRUD;
- Testes negativos;
- Schema Validation;
- Execução via CLI;
- Automação de testes de API;
- npm;
- GitHub Actions;
- GitHub Pages;
- CI/CD;
- Integração Contínua;
- Entrega Contínua;
- Geração automatizada de relatórios;
- Git;
- GitHub;
- Evidências;
- Documentação técnica.

---

# Status do projeto

**Concluído para o escopo atual.**

O projeto possui:

- 2 collections;
- 2 APIs públicas utilizadas;
- 15 requisições entre as duas suítes;
- 47 assertions nas execuções documentadas;
- CRUD completo na suíte avançada;
- Environment;
- Autenticação e token;
- Variáveis dinâmicas;
- Encadeamento entre requisições;
- JSON Schema Validation;
- Testes negativos;
- Newman;
- Newman HTML Extra Reporter;
- Scripts npm;
- Geração automática de relatórios;
- Pipeline com GitHub Actions;
- CI;
- CD para publicação de relatórios;
- GitHub Pages;
- Execução local sem falhas;
- Evidências documentadas.

---

# Observação sobre a API de laboratório

O Restful Booker é uma API pública destinada a estudos e testes.

Os dados podem ser reinicializados periodicamente pela própria aplicação.

Por esse motivo, a suíte cria dinamicamente um novo booking e utiliza o ID retornado durante a própria execução, reduzindo dependência de dados previamente existentes.

Alguns comportamentos da API pública podem não representar a resposta ideal esperada em sistemas de produção.

Quando isso ocorre, o projeto diferencia o comportamento observado da resposta tecnicamente mais apropriada, como no cenário de payload inválido que retornou:

```text
500 Internal Server Error
```

---

# Próximas melhorias possíveis

O projeto está concluído para o escopo atual.

Possíveis evoluções futuras incluem:

- Dados de teste externos;
- Mocks e stubs;
- Testes de contrato;
- Segurança de APIs;
- OAuth 2.0 em uma API compatível;
- Webhooks em uma API compatível;
- Relatórios históricos;
- Notificações automáticas do pipeline.

---

# Autor

**Bruno Ramos Lopes**

LinkedIn: [linkedin.com/in/brunolopes-ti](https://linkedin.com/in/brunolopes-ti)  
GitHub: [github.com/brunolopes-ti](https://github.com/brunolopes-ti)