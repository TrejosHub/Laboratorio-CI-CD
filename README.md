# Etapa 3 — Tests para subir cobertura sobre el 80%

Esta carpeta es un **overlay** con pruebas adicionales que se copian sobre el repo
despues de haber aplicado la Etapa 2. No modifica codigo fuente, solo agrega tests.

## Contenido

```
backend/tests/
└── test_tasks_extra.py             # tests para CRUD completo + 404 + validacion
frontend/src/__tests__/
├── App.flow.test.tsx               # flujo completo crear/completar/eliminar
├── TaskForm.test.tsx               # tests del formulario
├── TaskList.test.tsx               # tests de la lista
└── api.test.ts                     # tests del cliente HTTP
```

## Como aplicar

Desde la raiz del repo `laboratorio-cicd-demo/`, despues de haber hecho merge de etapa 2 en `develop`:

```powershell
git checkout develop
git checkout -b feature/etapa-3-tests
Copy-Item -Recurse -Force ..\etapa-3\backend .
Copy-Item -Recurse -Force ..\etapa-3\frontend .
git add .
git commit -m "etapa 3: agregar tests para alcanzar cobertura"
git push -u origin feature/etapa-3-tests
```

PR a `develop` (pasa). Mergea y luego PR de `develop` a `master`: **ahora pasa** todos los checks.

## Resultado esperado

- PR a develop: ✅ verde
- PR a master: ✅ verde (lint, cobertura ≥80%, Quality Gate PASSED, docker-build OK)
- Coverage backend: ~96%
- Coverage frontend: ~100%
