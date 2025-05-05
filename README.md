# Sistema de Gestão de Cursos e Matrículas - SENAI

![Badge](https://img.shields.io/badge/status-em%20desenvolvimento-yellow)
![Badge](https://img.shields.io/badge/node.js-v18.x-green)
![Badge](https://img.shields.io/badge/next.js-v14.x-blue)
![Badge](https://img.shields.io/badge/postgresql-v14.x-blue)

## 📋 Descrição

Sistema completo para gerenciamento de cursos, alunos e matrículas em uma instituição de ensino técnico como o SENAI. A aplicação permite o cadastro de diferentes tipos de cursos (técnicos, aprendizagem e livres), matrícula de alunos e visualização de relatórios.

## 🛠️ Tecnologias Utilizadas

- **Backend:** Node.js + Express
- **Frontend:** Next.js
- **Banco de Dados:** PostgreSQL

## 🏗️ Estrutura do Banco de Dados

### Tabela: cursos
| Campo | Tipo | Descrição |
|-------|------|-----------|
| id | SERIAL PRIMARY KEY | Identificador único do curso |
| nome | VARCHAR(255) | Nome do curso |
| descricao | VARCHAR(255) | Descrição do curso |
| tipo | VARCHAR(50) | Tipo do curso: "Técnico", "Aprendizagem" ou "Livre" |
| duracao | INT | Duração do curso em meses |

### Tabela: alunos
| Campo | Tipo | Descrição |
|-------|------|-----------|
| id | SERIAL PRIMARY KEY | Identificador único do aluno |
| nome | VARCHAR(255) | Nome completo do aluno |
| data_nascimento | DATE | Data de nascimento do aluno |
| email | VARCHAR(255) UNIQUE | Email do aluno (único) |
| telefone | VARCHAR(20) | Telefone de contato do aluno |

### Tabela: matriculas
| Campo | Tipo | Descrição |
|-------|------|-----------|
| id | SERIAL PRIMARY KEY | Identificador único da matrícula |
| aluno_id | INT (FK) | Referência ao aluno |
| curso_id | INT (FK) | Referência ao curso |
| data_matricula | DATE | Data da matrícula (padrão: data atual) |
| status | VARCHAR(20) | Status: "Matriculado", "Finalizado" ou "Cancelado" |

## 🚀 Funcionalidades

### APIs Backend (Express)

#### Cursos
- `GET /api/cursos` - Listar todos os cursos
- `POST /api/cursos` - Criar um novo curso
- `PUT /api/cursos/{id}` - Atualizar informações de um curso
- `DELETE /api/cursos/{id}` - Deletar um curso

#### Alunos
- `GET /api/alunos` - Listar todos os alunos
- `POST /api/alunos` - Criar um novo aluno
- `PUT /api/alunos/{id}` - Atualizar informações de um aluno
- `DELETE /api/alunos/{id}` - Deletar um aluno

#### Matrículas
- `GET /api/matriculas` - Listar todas as matrículas
- `POST /api/matriculas` - Criar uma nova matrícula
- `GET /api/matriculas/{id}` - Obter detalhes de uma matrícula
- `PUT /api/matriculas/{id}` - Atualizar status da matrícula
- `DELETE /api/matriculas/{id}` - Cancelar matrícula

### Frontend (Next.js)

#### Páginas
1. **Listagem de Cursos** - Exibição de todos os cursos cadastrados
2. **Detalhes do Curso** - Visualização detalhada de um curso específico
3. **Cadastro de Alunos** - Formulário para adicionar novos alunos
4. **Cadastro de Matrículas** - Interface para matricular alunos em cursos
5. **Relatório de Matrículas** - Visualização de todas as matrículas com filtros

## 📦 Instalação e Execução

### Pré-requisitos
- Node.js (v18 ou superior)
- PostgreSQL (v14 ou superior)

### Backend
```bash
# Clone o repositório
git clone https://github.com/seu-usuario/senai-gestao-cursos.git

# Entre no diretório do backend
cd senai-gestao-cursos/backend

# Instale as dependências
npm install

# Configure as variáveis de ambiente
cp .env.example .env
# Edite o arquivo .env com suas configurações

# Execute as migrações do banco de dados
npm run migrate

# Inicie o servidor
npm run dev
```

### Frontend
```bash
# Entre no diretório do frontend
cd senai-gestao-cursos/frontend

# Instale as dependências
npm install

# Configure as variáveis de ambiente
cp .env.example .env
# Edite o arquivo .env com suas configurações

# Inicie o servidor de desenvolvimento
npm run dev
```

## 📝 Tarefas e Requisitos

### SENAI-0001: Estrutura do Banco de Dados
- ✅ Criação das tabelas cursos, alunos e matriculas

### SENAI-0002: APIs de Cursos
- ✅ GET /api/cursos
- ✅ POST /api/cursos
- ✅ PUT /api/cursos/{id}
- ✅ DELETE /api/cursos/{id}

### SENAI-0003: APIs de Alunos
- ✅ GET /api/alunos
- ✅ POST /api/alunos
- ✅ PUT /api/alunos/{id}
- ✅ DELETE /api/alunos/{id}

### SENAI-0004: APIs de Matrículas
- ✅ GET /api/matriculas
- ✅ POST /api/matriculas
- ✅ GET /api/matriculas/{id}
- ✅ PUT /api/matriculas/{id}
- ✅ DELETE /api/matriculas/{id}

### SENAI-0005: Página de Listagem de Cursos
- ✅ Exibição de todos os cursos
- ✅ Botão para adicionar novo curso

### SENAI-0006: Página de Detalhes do Curso
- ✅ Visualização detalhada de curso

### SENAI-0007: Página de Cadastro de Alunos
- ✅ Formulário para cadastro de alunos

### SENAI-0008: Página de Cadastro de Matrícula
- ✅ Formulário para matrícula com seleção de aluno e curso

### SENAI-0009: Página de Relatório de Matrículas
- ✅ Listagem de todas as matrículas com informações relevantes

## 🧪 Testes

### Backend
```bash
# Execute os testes unitários
npm test

# Execute os testes com cobertura
npm run test:coverage
```

### Frontend
```bash
# Execute os testes
npm test

# Execute os testes com modo watch
npm run test:watch
```

## 🔒 Boas Práticas e Validações

### Backend
- Validação de email único para alunos
- Verificação para evitar duplicidade de matrículas
- Tratamento adequado de erros nas APIs
- Padronização das respostas de API

### Frontend
- Uso de React Hooks para gerenciamento de estado
- Feedback visual para operações de sucesso/erro
- Validação de formulários
- Experiência de usuário intuitiva

## 📊 Estrutura de Diretórios

```
/
├── backend/
│   ├── src/
│   │   ├── controllers/
│   │   ├── models/
│   │   ├── routes/
│   │   ├── middlewares/
│   │   ├── utils/
│   │   └── index.js
│   ├── tests/
│   ├── .env.example
│   └── package.json
│
└── frontend/
    ├── src/
    │   ├── pages/
    │   ├── components/
    │   ├── contexts/
    │   ├── hooks/
    │   ├── services/
    │   └── styles/
    ├── public/
    ├── .env.example
    └── package.json
```

## 📝 Padrão de Commits

- `SENAI-0001 Criar estrutura do banco de dados com tabelas cursos, alunos e matriculas`
- `SENAI-0002 Criar API para gerenciar cursos (GET, POST, PUT, DELETE)`
- `SENAI-0003 Criar API para gerenciar alunos (GET, POST, PUT, DELETE)`

## 📄 Licença

Este projeto está sob a licença MIT.

## 👥 Contribuidores

- Desenvolvedor Backend
- Desenvolvedor Frontend
- DBA
- Líder de Projeto

---

Desenvolvido como parte do desafio técnico SENAI