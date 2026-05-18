# Etapa 2 — CRUD de tareas (sin tests)

Esta carpeta NO es un repositorio. Es un **overlay** que se copia encima del
repositorio `laboratorio-cicd-demo/` (que ya tiene la Etapa 1).

## Contenido

```
backend/
├── app/
│   ├── database.py             # NUEVO — conexion SQLAlchemy
│   ├── main.py                 # SOBREESCRIBE — monta router de tareas
│   ├── controllers/            # NUEVO — logica de negocio
│   ├── models/                 # NUEVO — modelo Task
│   ├── schemas/                # NUEVO — DTOs Pydantic
│   └── views/                  # NUEVO — endpoints CRUD
├── tests/
│   └── conftest.py             # SOBREESCRIBE — fixture con SQLite en memoria
├── requirements.txt            # SOBREESCRIBE — anade sqlalchemy + psycopg
└── Dockerfile                  # SOBREESCRIBE — anade libpq-dev
frontend/
├── src/
│   ├── App.tsx                 # SOBREESCRIBE — usa los componentes nuevos
│   ├── components/             # NUEVO — TaskForm, TaskList
│   ├── services/               # NUEVO — cliente axios
│   └── __tests__/App.test.tsx  # SOBREESCRIBE — mockea el api
└── package.json                # SOBREESCRIBE — anade axios
```

## Como aplicar

Desde la raiz del repo `laboratorio-cicd-demo/`:

```powershell
git checkout develop
git checkout -b feature/etapa-2-crud
Copy-Item -Recurse -Force ..\etapa-2\backend .
Copy-Item -Recurse -Force ..\etapa-2\frontend .
git add .
git commit -m "etapa 2: agregar CRUD de tareas"
git push -u origin feature/etapa-2-crud
```

Abre PR a `develop` (pasa lint+tests). Mergea y luego abre PR de `develop` a `master` (**falla** por cobertura <80% y Quality Gate FAILED).

## Resultado esperado

- PR a develop: ✅ verde
- PR a master: ❌ rojo (test-backend-coverage, test-frontend-coverage, sonarcloud)
- Coverage backend: ~25-30% (solo /health esta probado)
- Coverage frontend: ~30-40% (solo App montaje basico)
