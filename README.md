# Sobrecarga Gym

App de gimnasio (calendario de entrenos, rutinas, progresión y seguimiento de peso). Funciona como página web estática en GitHub Pages, con login de Google y datos en Firebase (plan gratuito Spark, sin tarjeta).

## Archivos

- `index.html`: la app entera.
- `firebase-config.js`: tu configuración de Firebase (se rellena en el paso 5).
- `firestore.rules`: reglas para que cada persona solo vea sus datos.
- `manifest.webmanifest` e `icon-*.png`: para añadirla a la pantalla de inicio del móvil.
- `copia-privada/`: tus datos actuales. **No se sube a GitHub** (está en `.gitignore`). Se carga una vez desde la app con "Importar copia".

## Paso a paso

### 1. Crear el proyecto de Firebase
1. Entra en https://console.firebase.google.com con tu cuenta de Google.
2. **Crear un proyecto**, ponle nombre (por ejemplo `sobrecarga-gym`) y desactiva Google Analytics.

### 2. Activar el login con Google
1. En el menú: **Compilación → Authentication → Comenzar**.
2. Pestaña **Método de acceso → Google → Habilitar**. Elige tu correo como correo de asistencia y guarda.

### 3. Crear la base de datos
1. **Compilación → Firestore Database → Crear base de datos**.
2. Ubicación: `eur3 (europe-west)`. Modo: **producción**.

### 4. Pegar las reglas de seguridad
1. En Firestore, pestaña **Reglas**.
2. Borra lo que haya, pega el contenido de `firestore.rules` y pulsa **Publicar**.

### 5. Copiar la configuración en la app
1. **Configuración del proyecto (rueda dentada) → Tus apps → icono web `</>`**. Ponle un apodo y registra la app (sin Firebase Hosting).
2. Copia el bloque `firebaseConfig` que te muestra y pega cada valor en `firebase-config.js`, sustituyendo los `PEGA_AQUI`.

### 6. Subirla a GitHub Pages
1. Crea un repositorio en GitHub (puede ser público: la clave de Firebase no es secreta y tus datos están protegidos por login y reglas).
2. Sube todos los archivos de esta carpeta **menos `copia-privada/`**.
3. En el repositorio: **Settings → Pages → Build and deployment → Deploy from a branch → `main` / `/ (root)` → Save**.
4. Espera 1 o 2 minutos. La dirección será `https://TU-USUARIO.github.io/NOMBRE-DEL-REPO/`.

### 7. Permitir ese dominio en el login
1. Firebase: **Authentication → Configuración → Dominios autorizados → Añadir dominio**.
2. Escribe `TU-USUARIO.github.io` (solo el dominio, sin `https://` ni la ruta).

### 8. Primer uso y traer tus datos
1. Abre la dirección de GitHub Pages en el ordenador o el móvil y pulsa **Entrar con Google**.
2. Ve a **Ejercicios → Copia de seguridad → Importar copia** y elige `copia-privada/copia-datos.json`.
3. En el móvil: abre la dirección en el navegador y usa **Compartir → Añadir a pantalla de inicio** (iPhone, Safari) o **menú ⋮ → Añadir a pantalla de inicio** (Android, Chrome).

## Notas

- Cualquier persona con cuenta de Google puede entrar, pero cada una ve solo sus propios datos (vacíos).
- Para hacer cambios en la app: edita `index.html`, sube el cambio a GitHub y espera 1 o 2 minutos.
- **Exportar copia** descarga un archivo con todos tus datos. Hazlo de vez en cuando.
