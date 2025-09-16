# 🚀 Práctica de Integración Continua con GitHub Actions

## 📌 Descripción

Este proyecto demuestra el uso de **GitHub Actions** para implementar un flujo de **Integración Continua (CI/CD)**.
Cada vez que se hace un `push` a la rama **main**, se ejecuta lo siguiente:

1. Se descarga el repositorio en el runner de GitHub.
2. Se ejecuta un programa **Hola Mundo** en Python.
3. Se envía una notificación a **ntfy.sh/devops-itla** informando del despliegue.

---

## 🖥️ Programa Hola Mundo

Archivo: `HolaMundo.py`

```python
print("Hola Mundo desde GitHub Actions 🚀")
```

---

## ⚙️ Workflow de GitHub Actions

Archivo: `.github/workflows/Alerta.yml`

```yaml
name: Alerta Hola Mundo

on:
  push:
    branches:
      - main

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout repository
        uses: actions/checkout@v3

      - name: Run Hola Mundo
        run: python3 hola.py

      - name: Send notification to ntfy.sh
        run: |
          curl -d "🚀 Se subió código a la rama main en el repo $GITHUB_REPOSITORY" ntfy.sh/devops-itla
```

---

## 📢 Notificación enviada

Cuando el workflow corre exitosamente, se envía un mensaje al canal **devops-itla** en `ntfy.sh` similar al siguiente:

```
Build Completado con Éxito ✅
El programa Hola Mundo se ejecutó correctamente.

Repositorio: AdonisMBuret/Integracion-Continua
Rama: main
Autor: $GITHUB_ACTOR
Commit: $GITHUB_SHA
Mensaje: $GITHUB_EVENT_HEAD_COMMIT_MESSAGE
```

---

## ✅ Resultados Esperados

* Ejecución automática en cada `push` a **main**.
* Ejecución correcta del programa **Hola Mundo**.
* Envío de notificación a **ntfy.sh/devops-itla** con información del repositorio.

---

## 👨‍💻 Autor

* **Nombre:** Adonis Mercedes Buret #2021-2396
* **Curso:** Electiva 2 - DevOps
* **Profesor:** Elvys Cruz
