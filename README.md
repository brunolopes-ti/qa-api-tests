# 🧪 QA Lab – Testes de API com Postman

Projeto prático focado em testes de API REST utilizando Postman, com validações automatizadas e uso de variáveis dinâmicas.

## 🚀 Objetivo

Simular testes reais de API aplicando conceitos fundamentais de QA:

- Testes de endpoints REST (CRUD)
- Validação de respostas (status code e conteúdo)
- Uso de variáveis dinâmicas
- Organização de testes em collection

---

## 🔧 Tecnologias utilizadas

- Postman
- JSONPlaceholder (API pública)
- JavaScript (scripts de teste)

---

## 📌 Funcionalidades testadas

### 🔍 GET – Buscar usuário por ID
- Validação de status 200
- Verificação de campos obrigatórios
- Armazenamento do ID em variável (`user_id`)

### ➕ POST – Criar usuário
- Validação de status 201
- Verificação de retorno de ID
- Salvamento do ID criado para uso posterior

### ✏️ PATCH – Atualizar usuário
- Atualização de dados via variável dinâmica
- Validação do nome atualizado
- Garantia de persistência do ID

### ❌ DELETE – Remover usuário
- Validação de status 200 ou 204

---

## 🔁 Uso de variáveis

O projeto utiliza a variável `user_id` para encadear as requisições:

1. GET salva o ID
2. POST cria um novo ID
3. PATCH utiliza o ID salvo
4. DELETE remove o usuário com base no ID

---

## 📊 Exemplos de testes automatizados

```javascript
pm.test("Status deve ser 200", function () {
    pm.response.to.have.status(200);
});

pm.test("ID deve continuar o mesmo", function () {
    const json = pm.response.json();
    pm.expect(json.id).to.eql(Number(pm.collectionVariables.get("user_id")));
});
