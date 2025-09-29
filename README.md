# 📝 API de Gerenciamento de Tarefas - NestJS

Uma API REST completa para gerenciamento de tarefas construída com NestJS, TypeORM e SQLite.

## 🚀 Tecnologias Utilizadas

- **NestJS** - Framework Node.js
- **TypeORM** - ORM para TypeScript
- **SQLite3** - Banco de dados
- **class-validator** - Validação de dados
- **class-transformer** - Transformação de dados

## 📋 Pré-requisitos

- Node.js 18+
- npm ou yarn
- Git

## 🛠️ Instalação e Configuração

```bash
# Clone o repositório
git clone <url-do-repositorio>
cd tasks-api

# Instale as dependências
npm install

# Execute a aplicação em modo desenvolvimento
npm run start:dev
```

A API estará rodando em `http://localhost:3000`

## 📊 Estrutura do Projeto

```
src/
├── tasks/
│   ├── dto/
│   │   ├── create-task.dto.ts
│   │   └── update-task.dto.ts
│   ├── entities/
│   │   └── task.entity.ts
│   ├── tasks.controller.ts
│   ├── tasks.service.ts
│   └── tasks.module.ts
├── app.module.ts
└── main.ts
```

## 🔌 Endpoints da API

### 📋 Listar todas as tarefas
```http
GET /tasks
```
**Resposta:**
```json
[
  {
    "id": 1,
    "title": "Estudar NestJS",
    "description": "Completar a atividade prática",
    "status": "aberto",
    "createdAt": "2024-01-15T10:30:00.000Z",
    "updatedAt": "2024-01-15T10:30:00.000Z"
  }
]
```

### ➕ Criar nova tarefa
```http
POST /tasks
Content-Type: application/json

{
  "title": "Nova tarefa",
  "description": "Descrição da tarefa",
  "status": "aberto"
}
```
**Resposta (201 Created):**
```json
{
  "id": 1,
  "title": "Nova tarefa",
  "description": "Descrição da tarefa",
  "status": "aberto",
  "createdAt": "2024-01-15T10:30:00.000Z",
  "updatedAt": "2024-01-15T10:30:00.000Z"
}
```

### 🔍 Buscar tarefa por ID
```http
GET /tasks/1
```
**Resposta:**
```json
{
  "id": 1,
  "title": "Estudar NestJS",
  "description": "Completar a atividade prática",
  "status": "aberto",
  "createdAt": "2024-01-15T10:30:00.000Z",
  "updatedAt": "2024-01-15T10:30:00.000Z"
}
```

### ✏️ Atualizar tarefa
```http
PUT /tasks/1
Content-Type: application/json

{
  "title": "Título atualizado",
  "status": "fazendo"
}
```
**Resposta:**
```json
{
  "id": 1,
  "title": "Título atualizado",
  "description": "Descrição da tarefa",
  "status": "fazendo",
  "createdAt": "2024-01-15T10:30:00.000Z",
  "updatedAt": "2024-01-15T11:00:00.000Z"
}
```

### 🗑️ Deletar tarefa
```http
DELETE /tasks/1
```
**Resposta:** 204 No Content

## 🎯 Status das Tarefas

Os status disponíveis são:
- `aberto` - Tarefa pendente
- `fazendo` - Tarefa em andamento  
- `finalizado` - Tarefa concluída

## ⚠️ Validações

### Criar Tarefa (POST):
- `title`: string não vazia (obrigatório)
- `description`: string não vazia (obrigatório)
- `status`: enum (aberto, fazendo, finalizado) - opcional, padrão: "aberto"

### Atualizar Tarefa (PUT):
- Todos os campos são opcionais
- Validações mantidas para campos enviados

## 🐛 Troubleshooting

### Erro: "Task with ID X not found"
- Verifique se o ID existe
- Use GET /tasks para listar todas as tarefas

### Erro: "Validation failed"
- Verifique se todos os campos obrigatórios estão presentes
- Confirme que o status é um dos valores permitidos

### Erro ao iniciar a aplicação
- Execute `npm install` para instalar dependências
- Verifique se a porta 3000 está disponível

### Banco de dados
- O SQLite é criado automaticamente no arquivo `tasks.db`
- Os dados persistem entre reinicializações

## 🚀 Comandos Úteis

```bash
# Desenvolvimento
npm run start:dev          # Modo desenvolvimento com hot reload
npm run start             # Produção
npm run build            # Build do projeto

# Linting
npm run lint             # Análise de código
npm run format           # Formatação automática
```

## 📝 Exemplos de Uso

### Criando uma tarefa com cURL:
```bash
curl -X POST http://localhost:3000/tasks \
  -H "Content-Type: application/json" \
  -d '{
    "title": "Revisar código",
    "description": "Revisar pull requests pendentes",
    "status": "fazendo"
  }'
```

### Atualizando uma tarefa:
```bash
curl -X PUT http://localhost:3000/tasks/1 \
  -H "Content-Type: application/json" \
  -d '{"status": "finalizado"}'
```

## 📄 Licença

Este projeto está sob a licença GNU. Veja o arquivo [LICENSE](LICENSE) para detalhes.

---

**Desenvolvido como parte da atividade prática de API REST com NestJS** 🎓