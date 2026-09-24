# Edúcate contra el dengue — landing

Landing pública de educatecontraeldengue.com. Es un proyecto de FUMISUR SAS.

Es una página estática: un solo `index.html` más sus imágenes. No necesita instalar nada ni compilar.

## Qué hay en la carpeta

| Archivo | Uso |
|---|---|
| `index.html` | Toda la página, con estilos, animaciones y formulario |
| `logo.png` | Logo en la barra superior |
| `logo-claro.png` | Logo en versión clara para el footer verde |
| `dengue1.webp` | Libro abierto del héroe |
| `we_want_image.webp` | Sección "Lo que buscamos" |
| `appetizer_image.webp` | Sección "Un abrebocas a la historia" |
| `portada-los-invasores.webp` | Portada en la sección "El libro" |
| `activities_image.webp` | Sección "Actividades" |
| `logo-fumisur.png` | Sección "Autor" |
| `zancudo_1.png`, `zancudo_2.png` | Zancudos que vuelan y se espantan con aerosol |
| `aerosol.svg` | Nube de aerosol al tocar un zancudo; también va en el footer |
| `favicon.ico` | Ícono de la pestaña |

Todas las rutas son relativas, así que la página funciona en cualquier hosting.

## Publicarlo gratis con Netlify (recomendado)

1. Sube esta carpeta a un repositorio de GitHub, con los archivos en la raíz del repo.
2. Entra a https://app.netlify.com e inicia sesión con tu cuenta de GitHub.
3. Elige **Add new site → Import an existing project → GitHub** y selecciona el repositorio.
4. Deja vacíos **Build command** y **Publish directory**, y haz clic en **Deploy**.
5. Netlify te da una URL gratis, del tipo `nombre.netlify.app`. En **Site configuration → Change site name** puedes cambiarla, por ejemplo a `educatecontraeldengue.netlify.app`.

Cada vez que subas un cambio a GitHub, la página se actualiza sola.

### Formulario de contacto

El formulario ya está preparado para **Netlify Forms**, que es gratis hasta 100 envíos al mes.

1. Después del primer deploy, entra en Netlify a **Forms**, activa la detección de formularios y vuelve a hacer un deploy.
2. Aparecerá el formulario **contacto**.
3. En **Forms → contacto → Settings → Form notifications**, agrega una notificación por correo a `fumisurpitalito@gmail.com`.

Fuera de Netlify, el formulario valida los campos, pero al enviar muestra un mensaje de error con el correo de contacto.

## Pendientes

- **Video:** en `index.html`, busca `data-src=""` dentro del modal y pon la URL de embed del video (por ejemplo `https://www.youtube.com/embed/ID`).
- **Botones "Quiero saber más":** hoy bajan a la siguiente sección. Si deben llevar a otras páginas, cambia su `href`.
- **Logo claro:** `logo-claro.png` se hizo recoloreando el logo original. Si existe una versión oficial en negativo, reemplázalo.

## Cuando llegue el dominio

1. **Antes de tocar el DNS**, anota los registros actuales. Hay que conservar el de `plataforma.educatecontraeldengue.com`, porque de ahí depende la plataforma de estudiantes.
2. En Netlify, ve a **Domain management → Add a domain** y escribe `educatecontraeldengue.com`.
3. En el proveedor del dominio, cambia **solo** los registros del dominio principal y de `www` a los que indique Netlify. No toques el registro `plataforma`.
4. Netlify activa el HTTPS automáticamente.

### Integrarlo al proyecto Next.js existente

Si en lugar de Netlify se integra al proyecto actual de Next.js:

- Las imágenes van en la carpeta `public/`, con los mismos nombres.
- El HTML se divide en componentes, uno por sección: Header, Hero, Propósito, Historia, Libro, Actividades, Autor, Contacto, Frase y Footer.
- El CSS pasa a un módulo o archivo global. Las variables de color y tipografía están al inicio del `<style>`, en `:root`.
- El JavaScript (zancudos, aerosol, revelado al hacer scroll, menú móvil, modal de video y formulario) va en un componente cliente (`"use client"`) con `useEffect`.
- El formulario se conecta al mismo envío que usa el sitio actual.
