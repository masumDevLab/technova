# TechNova frontend

React 19 and Vite frontend for the TechNova electronics store.

## Requirements

- Node.js 20.19+ or 22.12+
- npm
- The backend running at `http://localhost:8080` for API-backed features

## Run locally

From this directory, install dependencies and start the development server:

```powershell
npm install
npm run dev
```

Vite serves the frontend at the URL printed in the terminal (normally
`http://localhost:5173`) and proxies `/api` requests to the backend.

The store-location map uses AMap credentials. To configure it, copy
`.env.example` to `.env` and add your own values. Do not commit `.env`.

## Other commands

```powershell
npm run lint
npm run build
npm run preview
```
