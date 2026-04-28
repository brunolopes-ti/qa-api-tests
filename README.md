# QA API Tests - JSONPlaceholder

Projeto prático de testes de API REST utilizando Postman, Newman e JSONPlaceholder.

O objetivo deste projeto é demonstrar conhecimentos em testes de API, validação de endpoints, métodos HTTP, status code, payload JSON, scripts de teste, uso de variáveis, execução via terminal e documentação de evidências.

---

## Tecnologias utilizadas

- Postman
- Newman
- JavaScript
- Node.js
- JSONPlaceholder
- Git
- GitHub
- Markdown

---

## API utilizada

Aplicação utilizada para testes:

[JSONPlaceholder](https://jsonplaceholder.typicode.com/)

O JSONPlaceholder é uma API REST pública utilizada para estudos e práticas de testes, permitindo validar operações como consulta, criação, atualização e exclusão de recursos.

---

## Objetivo do projeto

Este projeto tem como finalidade demonstrar a prática de testes de API REST, cobrindo diferentes métodos HTTP e validações comuns em cenários de QA.

A collection foi criada no Postman e posteriormente executada via terminal utilizando Newman.

---

## Escopo dos testes

A suíte cobre os seguintes métodos HTTP:

- GET
- POST
- PATCH
- DELETE

Também foram aplicadas validações como:

- Status code da resposta;
- Retorno de dados esperados;
- Estrutura de payload JSON;
- Armazenamento de variáveis;
- Encadeamento de dados entre requisições;
- Execução automatizada via terminal com Newman.

---

## Estrutura do projeto

```text
qa-api-tests
├── collections
│   └── QA Lab - API Tests (JSONPlaceholder).postman_collection.json
├── prints
│   ├── get-tests.png
│   ├── post-tests.png
│   ├── patch-tests.png
│   ├── delete-tests.png
│   └── newman-run-passando.png
├── .gitignore
├── package.json
├── package-lock.json
└── README.md
```

---

## Collection Postman

Arquivo da collection:

```text
collections/QA Lab - API Tests (JSONPlaceholder).postman_collection.json
```

A collection contém requisições organizadas para validar operações básicas de uma API REST.

---

## Cenários testados

### CT-01 - GET - Consultar posts

**Objetivo:** validar a consulta de dados da API.

**Validações realizadas:**

- Status code 200;
- Retorno de lista de posts;
- Estrutura esperada no corpo da resposta.

**Evidência:**

```text
prints/get-tests.png
```

![GET Tests](prints/get-tests.png)

---

### CT-02 - POST - Criar recurso

**Objetivo:** validar a criação de um novo recurso via API.

**Validações realizadas:**

- Status code 201;
- Retorno de ID;
- Validação dos dados enviados no payload;
- Armazenamento do ID criado em variável.

**Evidência:**

```text
prints/post-tests.png
```

![POST Tests](prints/post-tests.png)

---

### CT-03 - PATCH - Atualizar recurso

**Objetivo:** validar a atualização parcial de um recurso existente.

**Validações realizadas:**

- Status code 200;
- Retorno do campo atualizado;
- Validação do conteúdo alterado.

**Evidência:**

```text
prints/patch-tests.png
```

![PATCH Tests](prints/patch-tests.png)

---

### CT-04 - DELETE - Remover recurso

**Objetivo:** validar a exclusão de um recurso via API.

**Validações realizadas:**

- Status code 200 ou 204;
- Confirmação da execução da requisição DELETE.

**Evidência:**

```text
prints/delete-tests.png
```

![DELETE Tests](prints/delete-tests.png)

---

## Execução com Newman

Além da execução pelo Postman, a collection também foi configurada para ser executada via terminal utilizando Newman.

Essa prática permite rodar os testes de API fora da interface gráfica do Postman, aproximando o projeto de um fluxo mais utilizado em automação e integração contínua.

---

## Como executar o projeto

Instale as dependências:

```bash
npm install
```

Execute a collection com Newman:

```bash
npm run api
```

Também é possível executar diretamente com:

```bash
npx newman run "collections/QA Lab - API Tests (JSONPlaceholder).postman_collection.json"
```

---

## Script configurado

O projeto possui o seguinte script no `package.json`:

```json
"scripts": {
  "api": "newman run \"collections/QA Lab - API Tests (JSONPlaceholder).postman_collection.json\""
}
```

Com isso, a suíte pode ser executada com o comando:

```bash
npm run api
```

---

## Resultado da execução via terminal

A collection foi executada com sucesso utilizando Newman.

Resultado obtido:

```text
iterations: 1 executada / 0 falhas
requests: 4 executadas / 0 falhas
test-scripts: 8 executados / 0 falhas
prerequest-scripts: 5 executados / 0 falhas
assertions: 11 executadas / 0 falhas
```

**Evidência da execução com Newman:**

```text
prints/newman-run-passando.png
```

![Newman Run Passando](prints/newman-run-passando.png)

---

## Boas práticas aplicadas

- Organização da collection em pasta específica;
- Validação de métodos HTTP;
- Validação de status code;
- Validação de payload JSON;
- Uso de scripts JavaScript no Postman;
- Uso de variáveis para reaproveitamento de dados;
- Execução da collection via terminal com Newman;
- Criação de script npm para facilitar a execução;
- Registro de evidências visuais;
- Documentação técnica em README;
- Controle de dependências com `package.json`;
- Uso de `.gitignore` para evitar versionamento de dependências.

---

## Aprendizados

Com este projeto, desenvolvi habilidades práticas em:

- Testes de API REST;
- Uso do Postman para criação de collections;
- Escrita de testes automatizados com JavaScript no Postman;
- Validação de respostas JSON e status codes;
- Uso de variáveis dinâmicas;
- Execução de testes de API via terminal com Newman;
- Organização de evidências para documentação técnica;
- Versionamento de projeto com Git e GitHub.

---

## Status do projeto

Concluído nesta etapa.

Collection Postman criada, testes documentados, evidências registradas e execução via terminal configurada com Newman.

---

## Próximas melhorias possíveis

- Adicionar relatório HTML do Newman;
- Configurar GitHub Actions para execução automática dos testes de API;
- Criar arquivo de environment do Postman;
- Separar dados de teste;
- Adicionar testes negativos;
- Expandir a suíte com novos endpoints.

---

## Contato

Projeto desenvolvido por Bruno Ramos Lopes.

GitHub: [github.com/brunolopes-ti](https://github.com/brunolopes-ti)  
LinkedIn: [linkedin.com/in/brunolopes-ti](https://linkedin.com/in/brunolopes-ti)