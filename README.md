# Default language: English. Use the Español toggle to switch the interface.

# GreenScan AI — prototipo

## Lo que funciona sin configuración
- Abrir `index.html` desde un servidor local o GitHub Pages.
- Cámara/subida de foto y vista previa; catálogo de búsqueda manual; registro y exportación CSV; interfaz adaptable.
- La fotografía **no se analiza con IA** hasta conectar el Worker. No se simula reconocimiento.

## Activar reconocimiento visual real
1. Crear un Cloudflare Worker y pegar `worker.js`.
2. Agregar secreto `OPENAI_API_KEY` con una clave de API válida (Cloudflare Worker Settings → Variables and Secrets). **Nunca** poner la clave en HTML o GitHub.
3. Agregar variable `ALLOWED_ORIGIN` con el origen exacto de la web (ejemplo: `https://usuario.github.io`, sin slash final). No usar `*`.
4. Copiar la URL HTTPS del Worker (ejemplo: `https://recicla-sj.tu-cuenta.workers.dev`).
5. En `index.html`, reemplazar literalmente `__API_URL__` por la URL del Worker y publicar los archivos estáticos en GitHub Pages.
6. Probar con una foto de una lata vacía y otra de una pila. Revisar las recomendaciones antes de usarlas.

## Precauciones
- El backend valida origen y tipo/tamaño de imagen, pero para producción agregue autenticación, limitación de peticiones y control de costos. El control CORS no reemplaza la autenticación.
- Las fotos se envían al proveedor de IA para procesarse; no incluya datos personales. El historial queda en el navegador del dispositivo.
- El clasificador puede equivocarse; si hay incertidumbre devuelve «Necesita verificación». Reglas específicas y artículos difíciles deben contrastarse con SanJoseRecycles.org.
- El catálogo manual es deliberadamente pequeño y no sustituye la base oficial de más de 300 productos.
- Reglas orientadas a hogares unifamiliares de San José. Apartamentos y empresas pueden tener instrucciones distintas.

## Fuentes
- https://www.sanjoseca.gov/your-government/departments-offices/environmental-services/recycling-garbage/residents/single-family-recycling-cart-tagging-project
- https://www.sanjoseca.gov/your-government/departments-offices/environmental-services/recycling-garbage/residents/how-to-recycle-right/household-hazardous-waste
- https://sanjoserecycles.org/
