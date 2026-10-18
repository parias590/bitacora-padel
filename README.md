# Bitácora de Pádel

App web instalable en el móvil para registrar entrenos y partidos de pádel. Cuentas la sesión por texto (o dictando con el teclado), la app la organiza en **Enfoque · Salió bien · No tan bien · A trabajar**, y la pestaña **Coach** analiza tu historial y te propone la siguiente sesión.

- No depende de Claude ni de ninguna IA externa: todo el análisis se hace en el propio móvil.
- **No accede al micrófono, no graba y no guarda audio.** Para hablar, usa el micrófono de tu teclado; a la app solo le llega el texto.
- Por defecto solo se guardan los puntos clave, no el texto completo (se puede cambiar en Ajustes).
- Los registros se guardan en el móvil y se sincronizan con tu Google Drive (carpeta `Bitácora de Pádel`, archivo `bitacora-padel.json`).

## 1. Publicarla (GitHub Pages, gratis)

1. En GitHub crea un repositorio nuevo, por ejemplo `bitacora-padel`.
2. Sube todos los archivos de esta carpeta (`index.html`, `manifest.webmanifest`, `sw.js` y los iconos).
3. En el repositorio: **Settings → Pages → Build and deployment → Deploy from a branch**, rama `main`, carpeta `/ (root)`.
4. En un par de minutos estará en `https://parias590.github.io/bitacora-padel/`.

## 2. Conectar Google Drive (una sola vez)

1. Entra en <https://console.cloud.google.com> y crea un proyecto (o reutiliza el de la Bitácora de Café si ya lo tienes).
2. **APIs y servicios → Biblioteca →** activa **Google Drive API**.
3. **Pantalla de consentimiento de OAuth:** tipo *Externo*, deja la app en modo *Prueba* y añade tu cuenta de Gmail como *usuario de prueba*.
4. **Credenciales → Crear credenciales → ID de cliente de OAuth → Aplicación web.**
   En **Orígenes de JavaScript autorizados** añade: `https://parias590.github.io`
5. Copia el **ID de cliente** (termina en `.apps.googleusercontent.com`).
6. Abre la app → **Ajustes** → pega el ID → **Guardar y conectar**. Acepta el permiso de Google.

La app usa el permiso `drive.file`: solo puede ver los archivos que ella misma crea, no el resto de tu Drive. Usa el mismo ID de cliente en todos tus dispositivos y verán el mismo archivo.

**Sincronización:** se hace al tocar el indicador de la cabecera y automáticamente al guardar mientras la sesión de Google siga activa (1 hora). Si te sale «Pendiente», toca el indicador. Si usas dos dispositivos, sincroniza al abrir la app.

## 3. Instalarla en el móvil

- **Android (Chrome):** abre la URL → menú ⋮ → *Instalar aplicación* / *Añadir a pantalla de inicio*.
- **iPhone (Safari):** abre la URL → *Compartir* → *Añadir a pantalla de inicio*.

## 4. Dictar sin que la app toque tu voz

La app no tiene botón de micrófono a propósito. Para hablar, pulsa el micrófono **de tu teclado** (Gboard, teclado de iOS…). Ten en cuenta que ese dictado lo procesa el teclado/sistema del móvil según su propia configuración, no esta app; si prefieres que no salga del dispositivo, revisa en los ajustes del teclado la opción de dictado o reconocimiento de voz sin conexión. O simplemente escribe.

## Consejos para que organice bien

Frases cortas y directas funcionan mejor. Los botones `+ Enfoque`, `+ Bien`, `+ No tan bien`, `+ A trabajar` insertan inicios de frase que la app reconoce. Ejemplo:

> Partido con Javi, ganamos 6-4 3-6 7-5. Nos hemos centrado en jugar al centro. El saque muy bien. La volea de revés fatal, la mandaba a la red. Tengo que trabajar el físico para el tercer set.

Siempre puedes corregir cada punto o moverlo de grupo antes de guardar. Detecta bandeja, víbora, remate, globo, volea, derecha, revés, saque, resto, paredes, chiquita, posición, defensa, ataque, físico, mental y comunicación.

## Copias de seguridad

Ajustes → **Exportar copia (.json)** / **Importar copia**.
