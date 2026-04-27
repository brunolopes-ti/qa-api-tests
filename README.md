# QA API Tests – Validação de Endpoints REST com Postman

## Objetivo
Este projeto tem como objetivo validar o comportamento de endpoints REST utilizando Postman, com foco em testes funcionais de API, validação de respostas, consistência de dados e simulação de operações CRUD.

## API Utilizada
- JSONPlaceholder (API pública para testes)

## Escopo dos Testes  
- Validação de leitura de dados (GET)  
- Criação de recursos (POST)  
- Atualização de dados (PUT/PATCH)  
- Remoção de recursos (DELETE)  

## Ferramentas Utilizadas
- Postman
- JSON
- Git/GitHub

## Estrutura do Projeto
qa-api-tests/  
├── collections/  
│         └── jsonplaceholder-api-tests.postman_collection.json  
├── test-evidence/  
│         └── api-test-summary.md  
└── README.md  

## Cenários Validados
| Método | Endpoint | Objetivo | Status Esperado |  
|--------|----------|----------|-----------------|  
| GET | /posts/1 | Buscar recurso existente | 200 |  
| POST | /posts | Criar novo recurso | 201 |  
| PATCH | /posts/1 | Atualizar recurso existente | 200 |  
| DELETE | /posts/1 | Remover recurso | 200 ou 204 |  

## Validações Aplicadas  

- Status code das respostas  
- Tempo de resposta da API  
- Estrutura e formato do payload JSON  
- Existência de campos obrigatórios  
- Consistência dos dados retornados  
- Validação de operações CRUD  

## Evidências
As evidências de execução dos testes estão disponíveis na pasta test-evidence/, incluindo resumo dos cenários executados e resultados obtidos.  

## Aprendizados
- Funcionamento de APIs REST  
- Métodos HTTP (GET, POST, PUT, DELETE)  
- Estrutura e validação de JSON  
- Criação de testes e assertions no Postman  
- Organização de testes de API para portfólio profissional

## Observação  
A API JSONPlaceholder simula operações de escrita. Métodos como POST, PUT e DELETE retornam respostas válidas, porém não persistem os dados.
