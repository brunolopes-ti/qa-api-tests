# QA Lab – API Tests com Postman

Projeto prático de testes de API REST utilizando Postman, com validações automatizadas, uso de variáveis dinâmicas e execução de fluxo CRUD.

## Objetivo

Validar endpoints da API pública JSONPlaceholder aplicando práticas de QA em testes de API, incluindo:

- Validação de status code
- Validação de campos no JSON
- Uso de variáveis dinâmicas
- Execução de fluxo CRUD
- Organização de collection no Postman

## API utilizada

- JSONPlaceholder  
- Endpoint base: `https://jsonplaceholder.typicode.com`

## Ferramentas utilizadas

- Postman
- JavaScript para scripts de teste
- Git e GitHub

## Cenários testados

| Método | Cenário | Endpoint | Validações |
|---|---|---|---|
| GET | Buscar usuário por ID | `/users/1` | Status 200, campo `name`, ID correto e salvamento de variável |
| POST | Criar usuário | `/users` | Status 201, retorno de ID e salvamento de variável |
| PATCH | Atualizar usuário | `/users/{{user_id}}` | Status 200, nome atualizado e ID mantido |
| DELETE | Remover usuário | `/users/{{user_id}}` | Status 200 ou 204 |

## Uso de variável dinâmica

Foi utilizada a variável `user_id` para reaproveitar o ID retornado nas requisições e encadear o fluxo entre os métodos.

Exemplo:

```javascript
pm.collectionVariables.set("user_id", json.id);
