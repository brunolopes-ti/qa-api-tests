# QA API Tests – Validação de Endpoints REST com Postman

## Objetivo
Este projeto tem como objetivo validar o comportamento de endpoints REST utilizando Postman, com foco em status codes, estrutura de resposta, integridade de dados e cenários básicos de CRUD.

## API Utilizada
JSONPlaceholder

## Escopo dos Testes
- GET de recurso existente
- POST de novo recurso
- PUT para atualização de recurso
- DELETE de recurso

## Ferramentas Utilizadas
- Postman
- JSONPlaceholder
- Git/GitHub

## Estrutura do Projeto
qa-api-tests/
├── collections/
├── test-evidence/
└── README.md

## Cenários Validados
| Método | Endpoint | Objetivo | Status Esperado |
|--------|----------|----------|-----------------|
| GET | /posts/1 | Buscar post existente | 200 |
| POST | /posts | Criar novo post | 201 |
| PUT | /posts/1 | Atualizar post | 200 |
| DELETE | /posts/1 | Remover post | 200/204 |

## Evidências
As evidências dos testes e o resumo das validações estão disponíveis na pasta `test-evidence/`.

## Aprendizados
- Estrutura de requests HTTP
- Métodos GET, POST, PUT e DELETE
- Validação de status codes
- Leitura e validação de payload JSON
- Organização de testes de API para portfólio QA
