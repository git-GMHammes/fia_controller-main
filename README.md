# FIA Transport Controller 🏁

Sistema de gerenciamento e controle de transporte de veículos especiais da Federação Internacional de Automobilismo (FIA) para execução de corridas e eventos automotivos ao redor do mundo.

![License](https://img.shields.io/badge/license-MIT-blue.svg)
![PHP](https://img.shields.io/badge/PHP-8.1+-777BB4?logo=php)
![CodeIgniter](https://img.shields.io/badge/CodeIgniter-4.x-EF4223?logo=codeigniter)
![React](https://img.shields.io/badge/React-18.x-61DAFB?logo=react)
![MySQL](https://img.shields.io/badge/MySQL-8.0+-4479A1?logo=mysql)

## 📋 Sobre o Projeto

O **FIA Transport Controller** é uma solução completa para gerenciar toda a logística de transporte de veículos especiais utilizados em eventos da FIA, incluindo:

- 🚗 Carros de corrida (F1, F2, F3, FE, WEC, etc.)
- 🚚 Caminhões de suporte e transporte
- 🏎️ Safety Cars e Medical Cars
- 🛠️ Equipamentos e peças de reposição
- 📦 Material de hospitalidade e infraestrutura

### Principais Funcionalidades

- ✅ Gestão completa de frota de veículos especiais
- 📍 Rastreamento em tempo real de localização
- 🗓️ Planejamento de rotas e cronogramas de transporte
- 📊 Relatórios e dashboards analíticos
- 🔐 Controle de acesso baseado em perfis (Administrador, Logística, Operador)
- 📱 Interface responsiva para acesso mobile
- 🌍 Suporte multi-idiomas (EN, PT, ES, FR, DE, IT)
- 📄 Geração de documentação de transporte (CMR, Bill of Lading)
- ⚠️ Sistema de alertas e notificações
- 📈 Histórico completo de movimentações

---

## 🚀 Tecnologias Utilizadas

### Backend

- **PHP 8.1+**
- **CodeIgniter 4.x** - Framework PHP para API RESTful
- **JWT** - Autenticação via JSON Web Tokens
- **PHPMailer** - Envio de e-mails
- **TCPDF/mPDF** - Geração de documentos PDF

### Frontend

- **React 18.x** - Biblioteca JavaScript
- **React Router** - Gerenciamento de rotas
- **Axios** - Cliente HTTP
- **TailwindCSS** - Framework CSS
- **React Hook Form** - Gerenciamento de formulários
- **Chart.js / Recharts** - Gráficos e visualizações
- **React Query** - Gerenciamento de estado servidor
- **Leaflet** - Mapas interativos

### Banco de Dados

- **MySQL 8.0+** - Sistema de gerenciamento de banco de dados

### Infraestrutura

- **Docker & Docker Compose** - Containerização
- **Nginx** - Servidor web
- **Git** - Controle de versão

---

## 📁 Estrutura do Projeto

```
fia_controller-main/
│
├── backend/                    # API CodeIgniter 4
│   ├── app/
│   │   ├── Config/            # Configurações
│   │   ├── Controllers/       # Controladores da API
│   │   ├── Models/            # Models do banco de dados
│   │   ├── Filters/           # Filtros (Auth, CORS)
│   │   ├── Libraries/         # Bibliotecas customizadas
│   │   ├── Helpers/           # Helpers
│   │   └── Views/             # Views (se necessário)
│   ├── public/                # Pasta pública (index.php)
│   ├── writable/              # Logs, cache, uploads
│   ├── tests/                 # Testes unitários
│   ├── .env                   # Variáveis de ambiente
│   └── composer.json          # Dependências PHP
│
├── frontend/                  # Aplicação React
│   ├── public/                # Arquivos estáticos
│   ├── src/
│   │   ├── assets/           # Imagens, fontes, etc.
│   │   ├── components/       # Componentes reutilizáveis
│   │   ├── pages/            # Páginas da aplicação
│   │   ├── services/         # Serviços API
│   │   ├── hooks/            # Custom hooks
│   │   ├── contexts/         # Contexts (Auth, Theme)
│   │   ├── utils/            # Funções utilitárias
│   │   ├── routes/           # Configuração de rotas
│   │   ├── App.jsx           # Componente principal
│   │   └── index.js          # Entry point
│   ├── .env                   # Variáveis de ambiente
│   └── package.json           # Dependências Node
│
├── database/                  # Scripts de banco de dados
│   ├── migrations/           # Migrações
│   ├── seeds/                # Seeders (dados iniciais)
│   └── schema.sql            # Schema completo
│
├── docker/                    # Configurações Docker
│   ├── nginx/                # Config Nginx
│   ├── php/                  # Config PHP
│   └── mysql/                # Config MySQL
│
├── docs/                      # Documentação
│   ├── api/                  # Documentação da API
│   ├── database/             # Diagramas ER
│   └── manual/               # Manual do usuário
│
├── docker-compose.yml         # Orquestração de containers
├── .gitignore                # Arquivos ignorados pelo Git
├── LICENSE                   # Licença do projeto
└── README.md                 # Este arquivo
```

---

## 🔧 Instalação e Configuração

### Pré-requisitos

- **Docker** >= 20.10
- **Docker Compose** >= 2.0
- **Git**
- **Node.js** >= 18.x (para desenvolvimento local)
- **Composer** >= 2.x (para desenvolvimento local)

### 1. Clone o Repositório

```bash
git clone https://github.com/seu-usuario/fia_controller-main.git
cd fia_controller-main
```

### 2. Configuração com Docker (Recomendado)

#### 2.1. Configure as variáveis de ambiente

**Backend (.env)**

```bash
cd backend
cp env.example .env
```

Edite o arquivo `.env`:

```env
# Database
database.default.hostname = mysql
database.default.database = fia_transport
database.default.username = fia_user
database.default.password = fia_pass_2024
database.default.DBDriver = MySQLi

# JWT
JWT_SECRET = sua_chave_secreta_muito_segura_aqui
JWT_TIME_TO_LIVE = 3600

# Email
email.fromEmail = noreply@fia-transport.com
email.fromName = FIA Transport Controller

# App
app.baseURL = http://localhost:8080/
```

**Frontend (.env)**

```bash
cd ../frontend
cp .env.example .env
```

Edite o arquivo `.env`:

```env
REACT_APP_API_URL=http://localhost:8080/api
REACT_APP_API_VERSION=v1
REACT_APP_APP_NAME=FIA Transport Controller
```

#### 2.2. Inicie os containers

```bash
# Na raiz do projeto
docker-compose up -d
```

#### 2.3. Instale as dependências

**Backend (PHP)**

```bash
docker-compose exec backend composer install
```

**Frontend (Node)**

```bash
docker-compose exec frontend npm install
```

#### 2.4. Execute as migrações do banco de dados

```bash
docker-compose exec backend php spark migrate
docker-compose exec backend php spark db:seed DatabaseSeeder
```

#### 2.5. Acesse a aplicação

- **Frontend**: http://localhost:3000
- **Backend API**: http://localhost:8080/api
- **phpMyAdmin**: http://localhost:8081

**Credenciais padrão:**

- Email: `admin@fia.com`
- Senha: `Admin@123`

---

### 3. Configuração Local (Sem Docker)

#### 3.1. Backend

```bash
cd backend

# Instalar dependências
composer install

# Configurar .env
cp env.example .env
# Edite o .env com suas configurações de banco

# Executar migrações
php spark migrate
php spark db:seed DatabaseSeeder

# Iniciar servidor
php spark serve --port=8080
```

#### 3.2. Frontend

```bash
cd frontend

# Instalar dependências
npm install

# Configurar .env
cp .env.example .env
# Edite o .env com a URL da API

# Iniciar desenvolvimento
npm start
```

#### 3.3. Banco de Dados

Crie o banco de dados MySQL:

```sql
CREATE DATABASE fia_transport CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
CREATE USER 'fia_user'@'localhost' IDENTIFIED BY 'fia_pass_2024';
GRANT ALL PRIVILEGES ON fia_transport.* TO 'fia_user'@'localhost';
FLUSH PRIVILEGES;
```

---

## 🗄️ Estrutura do Banco de Dados

### Principais Tabelas

- **users** - Usuários do sistema
- **vehicles** - Veículos cadastrados
- **vehicle_types** - Tipos de veículos (F1, Support Truck, etc.)
- **teams** - Equipes/Escuderias
- **events** - Eventos/Corridas
- **locations** - Localizações (circuitos, bases)
- **transports** - Registros de transporte
- **routes** - Rotas planejadas
- **documents** - Documentos de transporte
- **tracking** - Rastreamento GPS
- **maintenance** - Manutenções programadas
- **alerts** - Alertas e notificações

### Diagrama ER

Consulte o arquivo `docs/database/ER_diagram.png` para visualizar o diagrama completo.

---

## 📡 API RESTful

### Autenticação

A API utiliza JWT (JSON Web Tokens) para autenticação.

**Endpoint de login:**

```http
POST /api/v1/auth/login
Content-Type: application/json

{
  "email": "user@example.com",
  "password": "senha123"
}
```

**Resposta:**

```json
{
  "status": true,
  "message": "Login realizado com sucesso",
  "data": {
    "token": "eyJ0eXAiOiJKV1QiLCJhbGc...",
    "user": {
      "id": 1,
      "name": "João Silva",
      "email": "user@example.com",
      "role": "admin"
    }
  }
}
```

**Uso do token:**

```http
GET /api/v1/vehicles
Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGc...
```

### Principais Endpoints

#### Veículos

```http
GET    /api/v1/vehicles           # Listar veículos
GET    /api/v1/vehicles/{id}      # Obter veículo específico
POST   /api/v1/vehicles           # Criar veículo
PUT    /api/v1/vehicles/{id}      # Atualizar veículo
DELETE /api/v1/vehicles/{id}      # Deletar veículo
```

#### Transportes

```http
GET    /api/v1/transports                    # Listar transportes
GET    /api/v1/transports/{id}               # Obter transporte
POST   /api/v1/transports                    # Criar transporte
PUT    /api/v1/transports/{id}               # Atualizar transporte
PATCH  /api/v1/transports/{id}/status        # Atualizar status
GET    /api/v1/transports/{id}/tracking      # Histórico de rastreamento
```

#### Eventos

```http
GET    /api/v1/events                    # Listar eventos
GET    /api/v1/events/{id}               # Obter evento
POST   /api/v1/events                    # Criar evento
GET    /api/v1/events/{id}/vehicles      # Veículos do evento
```

#### Relatórios

```http
GET    /api/v1/reports/dashboard         # Dados do dashboard
GET    /api/v1/reports/transports        # Relatório de transportes
GET    /api/v1/reports/vehicles          # Relatório de veículos
POST   /api/v1/reports/export            # Exportar relatório (PDF/Excel)
```

### Documentação Completa da API

Acesse a documentação interativa (Swagger/OpenAPI) em:

```
http://localhost:8080/api/docs
```

---

## 💻 Scripts Disponíveis

### Backend (CodeIgniter)

```bash
# Executar migrações
php spark migrate

# Rollback de migrações
php spark migrate:rollback

# Executar seeders
php spark db:seed NomeDoSeeder

# Limpar cache
php spark cache:clear

# Criar novo controller
php spark make:controller NomeController

# Criar novo model
php spark make:model NomeModel

# Executar testes
./vendor/bin/phpunit
```

### Frontend (React)

```bash
# Desenvolvimento
npm start

# Build para produção
npm run build

# Executar testes
npm test

# Análise de bundle
npm run analyze

# Lint
npm run lint

# Format
npm run format
```

### Docker

```bash
# Iniciar containers
docker-compose up -d

# Parar containers
docker-compose down

# Ver logs
docker-compose logs -f [service]

# Reconstruir containers
docker-compose up -d --build

# Executar comandos no container
docker-compose exec backend php spark migrate
docker-compose exec frontend npm install
```

---

## 👥 Perfis de Usuário

### 1. Administrador

- Acesso completo ao sistema
- Gerenciamento de usuários
- Configurações do sistema
- Relatórios completos

### 2. Gerente de Logística

- Planejamento de transportes
- Aprovação de rotas
- Visualização de relatórios
- Gerenciamento de eventos

### 3. Operador de Transporte

- Registro de movimentações
- Atualização de status
- Visualização de rotas atribuídas
- Upload de documentos

### 4. Visualizador

- Apenas leitura
- Acesso a dashboards
- Visualização de relatórios

---

## 🔐 Segurança

- ✅ Autenticação JWT com refresh tokens
- ✅ Criptografia de senhas (bcrypt)
- ✅ Proteção contra SQL Injection
- ✅ Validação de entrada de dados
- ✅ CORS configurado
- ✅ Rate limiting
- ✅ HTTPS em produção
- ✅ Sanitização de uploads
- ✅ Logs de auditoria

---

## 🌍 Internacionalização

O sistema suporta os seguintes idiomas:

- 🇬🇧 Inglês (padrão)
- 🇧🇷 Português
- 🇪🇸 Espanhol
- 🇫🇷 Francês
- 🇩🇪 Alemão
- 🇮🇹 Italiano

---

## 📊 Funcionalidades Principais

### Dashboard

- Visão geral de transportes ativos
- Mapa de localização em tempo real
- Estatísticas e KPIs
- Alertas e notificações
- Próximos eventos

### Gestão de Veículos

- Cadastro completo com fotos
- Histórico de manutenções
- Documentação digital
- Rastreamento GPS
- Status operacional

### Planejamento de Transportes

- Criação de rotas otimizadas
- Cálculo de custos
- Agendamento de transportes
- Designação de motoristas
- Checklist de preparação

### Controle de Eventos

- Calendário de eventos FIA
- Logística por evento
- Inventário de equipamentos
- Cronograma de transportes
- Relatórios pós-evento

### Rastreamento

- Localização GPS em tempo real
- Histórico de trajetos
- Alertas de desvios de rota
- ETA (Estimated Time of Arrival)
- Notificações automáticas

### Relatórios

- Relatórios de transporte
- Análise de custos
- Performance de frotas
- Estatísticas de eventos
- Exportação PDF/Excel

---

## 🧪 Testes

### Backend (PHPUnit)

```bash
cd backend

# Executar todos os testes
./vendor/bin/phpunit

# Executar testes específicos
./vendor/bin/phpunit tests/Controllers/VehicleControllerTest.php

# Gerar coverage
./vendor/bin/phpunit --coverage-html coverage
```

### Frontend (Jest + React Testing Library)

```bash
cd frontend

# Executar testes
npm test

# Executar com coverage
npm test -- --coverage

# Modo watch
npm test -- --watch
```

---

## 📦 Deploy

### Produção

1. **Build do Frontend**

```bash
cd frontend
npm run build
```

2. **Configurar variáveis de ambiente de produção**

3. **Deploy via Docker**

```bash
docker-compose -f docker-compose.prod.yml up -d
```

### Servidores Recomendados

- **Backend**: VPS com PHP 8.1+, Nginx, MySQL
- **Frontend**: Netlify, Vercel, ou servir via Nginx
- **Banco**: MySQL 8.0+ (separado ou mesmo servidor)

---

## 🤝 Contribuindo

Contribuições são bem-vindas! Para contribuir:

1. Fork o projeto
2. Crie uma branch para sua feature (`git checkout -b feature/AmazingFeature`)
3. Commit suas mudanças (`git commit -m 'Add some AmazingFeature'`)
4. Push para a branch (`git push origin feature/AmazingFeature`)
5. Abra um Pull Request

### Padrões de Código

- **PHP**: PSR-12
- **JavaScript**: ESLint + Prettier
- **Commits**: Conventional Commits

---

## 📝 Changelog

### [1.0.0] - 2024-01-15

- ✨ Release inicial
- ✅ Sistema completo de autenticação
- ✅ CRUD de veículos, eventos e transportes
- ✅ Dashboard com estatísticas
- ✅ Sistema de rastreamento GPS
- ✅ Geração de relatórios

---

## 📄 Licença

Este projeto está sob a licença MIT. Veja o arquivo [LICENSE](LICENSE) para mais detalhes.

---

## 👨‍💻 Equipe de Desenvolvimento

- **Product Owner**: FIA Transport Division
- **Tech Lead**: [Seu Nome]
- **Backend Developer**: [Nome]
- **Frontend Developer**: [Nome]
- **DevOps Engineer**: [Nome]

---

## 📞 Suporte

Para suporte e dúvidas:

- 📧 Email: support@fia-transport.com
- 🐛 Issues: [GitHub Issues](https://github.com/seu-usuario/fia_controller-main/issues)
- 📖 Wiki: [Documentation](https://github.com/seu-usuario/fia_controller-main/wiki)

---

## 🙏 Agradecimentos

- FIA - Federação Internacional de Automobilismo
- Comunidade CodeIgniter
- Comunidade React
- Todos os contribuidores do projeto

---

<div align="center">
  <strong>FIA Transport Controller</strong> - Transportando o futuro do automobilismo 🏁
  <br><br>
  Desenvolvido com ❤️ para a comunidade FIA
</div>
