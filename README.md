# Shein Chats OPS Dashboard — Atlantic QI

Dashboard operacional para la campaña Shein Chats, con KPIs en tiempo real y actualización de datos vía XLSX.

---

## 📁 Archivos del repositorio

```
/
├── index.html    ← Dashboard principal (GitHub Pages)
├── data.json     ← Base de datos histórica (NO borrar)
└── README.md     ← Este archivo
```

---

## 🚀 Publicar en GitHub Pages

### Paso 1 — Crear el repositorio
1. Ve a [github.com/new](https://github.com/new)
2. Nombre: `shein-dashboard` (o el que prefieras)
3. Visibilidad: **Public** (Pages gratuito) o Private (requiere GitHub Pro)
4. Clic en **Create repository**

### Paso 2 — Subir los archivos
Sube `index.html`, `data.json` y `README.md` al repositorio:
- Opción A — Arrastra los archivos al repositorio en GitHub.com
- Opción B — Git:
  ```bash
  git init
  git add .
  git commit -m "Initial deploy"
  git remote add origin https://github.com/TU_USUARIO/shein-dashboard.git
  git push -u origin main
  ```

### Paso 3 — Activar GitHub Pages
1. En el repositorio → **Settings** → **Pages**
2. Source: **Deploy from a branch**
3. Branch: `main` / `/ (root)`
4. Clic en **Save**
5. En ~2 minutos tu dashboard estará en:
   `https://TU_USUARIO.github.io/shein-dashboard/`

---

## 🔑 Crear Personal Access Token (PAT)

Para poder actualizar datos desde el botón del dashboard:

1. GitHub → tu avatar → **Settings**
2. Sidebar → **Developer settings**
3. **Personal access tokens** → **Fine-grained tokens**
4. Clic **Generate new token**
5. Configurar:
   - **Token name**: `shein-dashboard-write`
   - **Expiration**: 90 días (o la que prefieras)
   - **Repository access**: Solo el repositorio `shein-dashboard`
   - **Permissions → Contents**: `Read and Write`
6. Clic **Generate token** y **copia el token** (no lo verás otra vez)

---

## 📤 Cómo actualizar datos

1. Abre el dashboard en tu navegador
2. Clic en el botón **⬆ Actualizar Datos** (esquina inferior derecha)
3. **Primera vez**: abre la sección ⚙ Configuración GitHub y completa:
   - Usuario GitHub
   - Nombre del repositorio
   - Rama (`main`)
   - Tu PAT
   *(se guarda en tu navegador, no se comparte)*
4. Selecciona el archivo XLSX exportado del sistema Shein
5. Revisa el **preview de fusión** (fechas nuevas, historial preservado)
6. Clic **Publicar Datos**
7. En ~5 segundos el `data.json` se actualiza en GitHub
8. Todos los visitantes verán los datos nuevos al recargar la página

---

## 🔄 Lógica de fusión (sin pérdida de datos)

| Situación | Resultado |
|---|---|
| Nueva fecha que no existía | Se **agrega** al historial |
| Fecha ya existente con mismo asesor | Se **actualiza** con los datos nuevos |
| Fecha histórica no incluida en el XLSX | Se **preserva intacta** |
| Nuevo asesor en el XLSX | Se **ignora** (solo se procesan los 19 asesores registrados) |

---

## 🌐 Configuración de zona horaria

Los datos del sistema Shein vienen en **hora China (UTC+8)**.
El dashboard convierte automáticamente a **hora Colombia (UTC−5)**:
- China hora < 13:00 → día anterior Colombia
- Boundary: China 13:00 = Colombia 00:00

---

*Atlantic Quantum Innovation SAS · Barranquilla, Colombia*
