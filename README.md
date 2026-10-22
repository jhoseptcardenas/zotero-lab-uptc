# Zotero Lab UPTC — Aula compartida

Este paquete contiene una página web didáctica para enseñar bases de datos bibliográficas y el flujo de trabajo de Zotero.

## Incluye
- `index.html`: interfaz responsive con catálogo académico en vivo consultado desde OpenAlex.
- Búsqueda por tema y filtro por año; carga de más resultados.
- Colección local de práctica y exportación CSV/BibTeX.
- Reto de cinco preguntas y puntuación.
- Conexión opcional con Supabase para enviar puntuaciones y ver un ranking por código de aula.
- `supabase_setup.sql`: tabla y políticas mínimas de lectura/inserción para la actividad.

## Limitaciones importantes
- **Este paquete todavía no está publicado en internet.** El archivo debe alojarse en un servicio de hosting para obtener un enlace público.
- El catálogo se consulta en vivo en OpenAlex; no se descargan miles de registros a la página. La cantidad de resultados depende del tema, filtros, disponibilidad y límites del proveedor.
- La colección bibliográfica es local al navegador. La tabla compartida almacena puntuaciones, no las colecciones personales.
- Esta versión no crea una cuenta de usuario ni autentica la identidad del estudiante. Los alias y puntuaciones pueden ser falsificados. No utilizar para calificaciones oficiales.
- Para evitar exponer datos personales, los estudiantes deben usar un alias/código y no ingresar datos sensibles.

## Publicar la web con GitHub Pages
1. Crea/inicia sesión en GitHub.
2. Crea un repositorio público, por ejemplo `zotero-lab-uptc`.
3. Sube `index.html` a la raíz del repositorio.
4. En el repositorio abre **Settings → Pages**.
5. Selecciona publicar desde la rama `main` y la carpeta `/ (root)`, y guarda.
6. Cuando GitHub Pages muestre el enlace, ábrelo y prueba la búsqueda. La publicación puede tardar unos minutos.

Documentación oficial: https://docs.github.com/en/pages/quickstart

## Activar puntuaciones compartidas con Supabase
1. Crea un proyecto en https://supabase.com/.
2. Abre **SQL Editor**, pega y ejecuta el contenido de `supabase_setup.sql`.
3. En la configuración/API del proyecto copia la URL y la clave pública/publishable.
4. Abre la página publicada, entra en **Configuración docente**, pega URL y clave pública y pulsa guardar.
5. Prueba la conexión y envía un resultado de prueba desde el reto.
6. Comparte el enlace público y el mismo código de aula con los estudiantes.

La configuración desde el panel de la página se guarda en el navegador en que se introdujo. Para que todos los estudiantes reciban la configuración automáticamente, abre `index.html` y completa las constantes `PUBLIC_SUPABASE_URL` y `PUBLIC_SUPABASE_KEY` cerca del inicio del JavaScript; después vuelve a subir el archivo a GitHub Pages. Usa solo la clave pública/publishable (o anon key pública heredada), nunca la clave secreta ni `service_role`. La seguridad depende de las políticas RLS y este prototipo es para actividades de práctica, no para calificaciones oficiales.

Documentación de Supabase:
https://supabase.com/docs/guides/getting-started/quickstarts/reactjs

## Uso académico
La información bibliográfica se recupera desde OpenAlex. Antes de citar, abre la fuente original y verifica título, autores, año, revista/editorial, DOI y disponibilidad del texto completo. OpenAlex: https://openalex.org/
Zotero: https://www.zotero.org/download/
Biblioteca UPTC: https://www.uptc.edu.co/
