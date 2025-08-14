# Todo List - Fullstack Application

Aplicación fullstack de gestión de tareas desarrollada con NestJS (backend) y React (frontend).

## 📋 Requerimientos

- Node.js 18+
- Docker & Docker Compose
- PostgreSQL 15+

## 🚀 Instrucciones de Instalación

### Instalación Completa con Docker (Recomendado)

```bash
# 1. Clonar el repositorio
git clone https://github.com/Faqo/test-evol.git

# 2. Levantar todos los servicios
docker-compose up --build

# 3. La aplicación estará disponible en:
# - Frontend: http://localhost:3000
# - Backend API: http://localhost:3001
# - PostgreSQL: localhost:5432
```

### Instalación Local (Desarrollo)

#### Backend
```bash
cd todolist

# Instalar dependencias
npm install

# Levantar solo PostgreSQL
docker-compose up postgres

# Configurar variables de entorno (ver sección Variables de Entorno)
cp .env.example .env

# Ejecutar migraciones y seeders si existen
npm run migration:run

# Iniciar servidor de desarrollo
npm run start:dev
```

#### Frontend
```bash
cd frontend

# Instalar dependencias
npm install

# Configurar variables de entorno
cp .env.example .env

# Iniciar servidor de desarrollo
npm run dev
```

## ⚡ Comandos de Ejecución

### Docker Compose

```bash
# Levantar todo el stack
docker-compose up --build

# Levantar en background
docker-compose up -d --build

# Parar servicios
docker-compose down

# Parar y eliminar volúmenes (resetea BD)
docker-compose down -v

# Ver logs de servicios específicos
docker-compose logs -f frontend
docker-compose logs -f backend
docker-compose logs -f postgres

# Rebuild específico
docker-compose build --no-cache frontend
docker-compose build --no-cache backend
```

### Desarrollo Local

#### Backend
```bash
cd todolist

# Desarrollo con hot reload
npm run start:dev

# Producción
npm run start:prod

# Build
npm run build

# Tests
npm run test              # Tests unitarios
npm run test:e2e          # Tests de integración
npm run test:cov          # Cobertura de tests

# Linting
npm run lint
```

#### Frontend
```bash
cd frontend

# Desarrollo con hot reload
npm run dev

# Build para producción
npm run build

# Preview del build
npm run preview

# Tests
npm test
npm run test:watch
npm run test:coverage
npm run test:ui
```

## 📁 Estructura del Proyecto

```
/
├── frontend
│   ├── public
│   │   └── vite.svg
│   ├── src
│   │   ├── __tests__
│   │   │   └── App.test.tsx
│   │   ├── components
│   │   │   ├── __tests__
│   │   │   │   ├── Button.test.tsx
│   │   │   │   └── TaskItem.test.tsx
│   │   │   ├── common
│   │   │   │   ├── Button.tsx
│   │   │   │   ├── LoadingSpinner.tsx
│   │   │   │   └── Navbar.tsx
│   │   │   ├── forms
│   │   │   │   └── TaskForm.tsx
│   │   │   └── tasks
│   │   │       ├── TaskFilters.tsx
│   │   │       ├── TaskItem.tsx
│   │   │       └── TaskList.tsx
│   │   ├── hooks
│   │   │   ├── __tests__
│   │   │   │   └── useTasks.test.ts
│   │   │   └── useTasks.ts
│   │   ├── pages
│   │   │   ├── NotFoundPage.tsx
│   │   │   └── TaskPage.tsx
│   │   ├── services
│   │   │   └── taskService.ts
│   │   ├── store
│   │   │   ├── slices
│   │   │   │   └── taskSlice.ts
│   │   │   └── store.ts
│   │   ├── test
│   │   │   ├── setup.ts
│   │   │   └── utils.tsx
│   │   ├── types
│   │   │   └── task.ts
│   │   ├── App.css
│   │   ├── App.tsx
│   │   ├── index.css
│   │   ├── main.tsx
│   │   └── vite-env.d.ts
│   ├── .env.example
│   ├── .gitignore
│   ├── Dockerfile
│   ├── eslint.config.js
│   ├── index.html
│   ├── package-lock.json
│   ├── package.json
│   ├── postcss.config.js
│   ├── README.md
│   ├── tailwind.config.js
│   ├── tsconfig.app.json
│   ├── tsconfig.json
│   ├── tsconfig.node.json
│   ├── vite.config.ts
│   └── vitest.config.ts
├── todolist
│   ├── config
│   │   └── config.json
│   ├── migrations
│   │   ├── 20250813144215-create-tasks.js
│   │   └── 20250813144259-create-task.js
│   ├── models
│   │   ├── index.js
│   │   └── task.js
│   ├── seeders
│   │   └── 20250813144355-demo-tasks.js
│   ├── src
│   │   ├── tags
│   │   │   ├── tag.controller.spec.ts
│   │   │   ├── tags.controller.ts
│   │   │   └── tags.module.ts
│   │   ├── tasks
│   │   │   ├── dto
│   │   │   │   ├── create-task.dto.ts
│   │   │   │   └── update-task.dto.ts
│   │   │   ├── tasks.controller.spec.ts
│   │   │   ├── tasks.controller.ts
│   │   │   ├── tasks.entity.ts
│   │   │   ├── tasks.module.ts
│   │   │   ├── tasks.service.spec.ts
│   │   │   └── tasks.service.ts
│   │   ├── app.module.ts
│   │   └── main.ts
│   ├── test
│   │   ├── app.e2e-spec.ts
│   │   └── jest-e2e.json
│   ├── .env.example
│   ├── .gitignore
│   ├── .prettierrc
│   ├── docker-compose.yml
│   ├── dockerfile
│   ├── eslint.config.mjs
│   ├── nest-cli.json
│   ├── package-lock.json
│   ├── package.json
│   ├── README.md
│   ├── tsconfig.build.json
│   └── tsconfig.json
├── .gitignore
├── docker-compose.yml
└── README.md
```

## 🔧 Variables de Entorno Necesarias

### Backend (`todolist/.env`)

```env
# Database Configuration
DB_HOST=postgres
DB_PORT=5432
DB_NAME=todoapp
DB_USER=postgres
DB_PASSWORD=password

# Application
NODE_ENV=development
PORT=3001

# CORS
FRONTEND_URL=http://localhost:3000
```

### Frontend (`frontend/.env`)

```env
# API Configuration
VITE_API_URL=http://localhost:3001/api
```

## 🧪 Testing

### Backend
```bash
cd todolist
npm run test              # Tests unitarios
npm run test:cov          # Cobertura de tests
```

### Frontend
```bash
cd frontend
npm test                  # Ejecutar tests
npm run test:watch        # Tests en modo watch
npm run test:coverage     # Cobertura de tests
npm run test:ui           # Interfaz gráfica de tests
```

## 📚 API Endpoints

- `GET /api/tasks` - Listar tareas con filtros
- `POST /api/tasks` - Crear nueva tarea
- `PUT /api/tasks/:id` - Actualizar tarea
- `DELETE /api/tasks/:id` - Eliminar tarea
- `GET /api/tags` - Listar etiquetas disponibles

## 🔍 Verificación de Instalación

```bash
# Verificar que todos los servicios están corriendo
docker-compose ps

# Verificar conectividad
curl http://localhost:3001/api/tasks    # Backend
curl http://localhost:3000              # Frontend

# Verificar logs si hay problemas
docker-compose logs backend
docker-compose logs frontend
```

## ⚠️ Problemas Comunes

1. **Puerto ocupado**: Cambiar puertos en `docker-compose.yml`
2. **Base de datos no conecta**: Verificar que PostgreSQL esté corriendo
3. **Frontend no conecta con backend**: Verificar `VITE_API_URL` en `.env`
4. **Docker no funciona**: Verificar que Docker Desktop esté corriendo
