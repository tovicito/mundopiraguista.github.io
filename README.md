# Mundo Piragüista 🛶

Web estática para GitHub Pages, con artículos editoriales y un panel de administración que escribe los artículos directamente en este repositorio usando la API de GitHub. Cada cambio crea un commit y activa el despliegue automático.

## Funciones

- Página pública basada en el HTML original, con guías existentes y sección de OpenKayak.
- Panel en `/admin/` para crear, editar y eliminar artículos.
- Título, categoría, resumen, cuerpo en Markdown, imagen de portada y vídeo de YouTube.
- Subida de imágenes al directorio `assets/articles/`.
- Publicación automática con GitHub Actions y GitHub Pages.
- No requiere cuentas externas. El único proveedor es GitHub.

## Instalación única

1. Crea un repositorio público llamado `mundopiraguista.github.io` en la cuenta `tovicito`.
2. Sube todos los archivos de esta carpeta a la rama `main`.
3. En **Settings → Pages**, selecciona **GitHub Actions** como método de publicación.
4. Entra en la pestaña **Actions** y comprueba que el flujo “Publicar Mundo Piragüista en GitHub Pages” termina correctamente.
5. La URL de proyecto esperada es `https://tovicito.github.io/mundopiraguista.github.io/`.

## Cómo publicar artículos

1. Abre la web publicada y entra en `/admin/`.
2. La pantalla pide usuario `admin` y contraseña `openkayak` como barrera visual solicitada.
3. Para autorizar cambios, crea en GitHub un fine-grained personal access token limitado a este repositorio, con **Contents: Read and write**. No concedas permisos de administración.
4. Pega el token en el panel. Se mantiene solo en la memoria de esa pestaña y no se guarda en localStorage.
5. Redacta el artículo, añade imagen o vídeo y pulsa **Publicar artículo**. El panel sube la imagen, guarda `data/articles.json` y GitHub Actions vuelve a desplegar el sitio.

## Seguridad: leer antes de publicar

GitHub Pages es un alojamiento estático, no un servidor privado. Por tanto, el usuario y la contraseña escritos en el HTML **no son una autenticación segura**: cualquiera puede inspeccionar los archivos y descubrirlos. La protección real para modificar el repositorio es el token de GitHub. No compartas el token, no lo pegues en la web pública ni lo guardes en archivos. El panel no lo persiste y solo lo usa en memoria durante la sesión. Revócalo en GitHub si crees que se ha expuesto.

Para un panel con inicio de sesión real y sin token manual en el navegador haría falta un backend autenticado. Eso no puede implementarse de forma segura únicamente con GitHub Pages y sin ningún componente de servidor.

## Formato de artículos

El cuerpo admite Markdown: títulos con `##`, listas, enlaces, negrita, cursiva y código. Para imágenes adicionales, puedes usar enlaces Markdown a imágenes públicas. Los vídeos de YouTube se muestran mediante el campo de vídeo opcional.

## Personalización

El sitio original está en `index.html`. Los artículos editoriales nuevos se guardan en `data/articles.json`; las imágenes que sube el panel se guardan en `assets/articles/`.
