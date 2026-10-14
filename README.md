# BZPanel

> Panel de control para gestión de tareas con Obsidian Canvas + Ollama

[![Next.js](https://img.shields.io/badge/Next.js-15-black)](https://nextjs.org)
[![React](https://img.shields.io/badge/React-18-61DAFB)](https://react.dev)
[![TypeScript](https://img.shields.io/badge/TypeScript-5-3178C6)](https://www.typescriptlang.org)

BZPanel es un panel web que lee archivos `.canvas` de Obsidian y te permite gestionar tareas directamente desde el navegador. Diseñado para integrarse con [OpenClaw](https://github.com/anomalyco/opencode) y pipelines de IA con Ollama.

## Características

- 📋 **Dashboard interactivo** - Visualiza tareas de Obsidian Canvas en columns por estado
- 🔄 **Sincronización en tiempo real** - Actualización cada 6 segundos
- ▶️ **Control de tareas** - Inicia, aprueba, pausa y finish tareas desde la UI
- 🤖 **Integración Ollama** - Estado online de Ollama y modelo seleccionado
- 🏷️ **Agrupación por grupos** - Filtra tareas por grupos del canvas
- 📱 **Diseño responsive** - Funciona en desktop y móvil

## Requisitos

- Node.js 18+
- Python 3 (para canvas-tool.py)
- [canvas-tool.py](https://github.com/anomalyco/opencode) de OpenClaw
- Ollama (opcional, para pipelines de IA)

## Instalación

### Desarrollo

```bash
# Instalar dependencias
npm install

# Ejecutar en desarrollo
npm run dev
```

Abre [http://localhost:3000](http://localhost:3000)

### Producción con Docker

```bash
# Build y запустить
docker-compose up -d
```

El panel estará disponible en `http://localhost:3001`

### Build standalone

```bash
npm run build
npm start
```

## Configuración

### Variables de entorno

| Variable | Default | Descripción |
|----------|---------|-------------|
| `OLLAMA_URL` | `http://localhost:11434` | URL de Ollama |
| `CANVAS_FILE` | `/root/.openclaw/workspace/kanvas/Project.canvas` | Ruta al archivo .canvas |
| `CANVAS_TOOL` | `/root/.openclaw/workspace/kanvas/canvas-tool.py` | Ruta a canvas-tool.py |
| `STATE_FILE` | `/data/bzpanel-state.json` | Archivo de estado |

### Formato de tareas

Las tareas se detectan automáticamente del canvas. Formato:

```
## XX-NN Título de la tarea

Descripción opcional de la tarea.
Puede tener varias líneas.


## Estructura del proyecto

```
bzpanel/
├── src/
│   ├── app/
│   │   ├── api/          # Endpoints de la API
│   │   │   ├── canvas/   # /api/canvas - gestión de tareas
│   │   │   ├── status/  # /api/status - estado del sistema
│   │   │   └── switch/  # /api/switch - cambiar modo local/cloud
│   │   ├── page.tsx     # Dashboard principal
│   │   └── layout.tsx   # Root layout
│   └── lib/
│       ├── canvas.ts    # Parser de Obsidian Canvas
│       └── runner.ts    # Lógica de ejecución
├── docker-compose.yml
├── Dockerfile
└── package.json
```

## Stack tecnológico

- **Next.js 15** - Framework React con App Router
- **React 18** - UI library
- **TypeScript 5** - Tipado estático
- **Docker** - Containerization
- **Python 3** - canvas-tool.py integration

## Licencia

MIT

---

Hecho con ☕ para OpenClaw

