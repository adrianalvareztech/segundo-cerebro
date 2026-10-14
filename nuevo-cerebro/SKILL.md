---
name: nuevo-cerebro
description: Crea un segundo cerebro nuevo con el método LLM Wiki de Karpathy a partir de lo que ya tienes. Copia la estructura del cerebro más parecido, ajusta la forma del wiki a para qué es, y mete las primeras fuentes (links de YouTube, videos que tengas guardados, una carpeta de Google Drive, una app sin API, archivos o lo que le dictes). Úsalo cuando digas "hagamos un segundo cerebro de...", "crea un cerebro nuevo" o "/nuevo-cerebro".
---

# Nuevo cerebro

El primer cerebro se hace a mano, con el gist de Karpathy, para entender cómo funciona. Este
skill es para los que siguen: con una frase y un link tienes uno nuevo andando.

## Lo que no cambia entre un cerebro y otro

- `raw/`: lo que mete la persona, tal cual. La IA nunca lo edita.
- `wiki/`: lo que escribe la IA. Páginas cortas, enlazadas entre sí, que citan su fuente.
- `CLAUDE.md`: el esquema. Para qué es el cerebro y cómo se pasa de `raw/` a `wiki/`.
- `index.md`: la tabla de contenido. Lo primero que se lee al contestar.
- `log.md`: qué se procesó y cuándo. Solo se agrega al final, nunca se reescribe.
- Tres operaciones: **ingerir** (de `raw/` a `wiki/`), **preguntar** (y guardar de vuelta
  la respuesta si vale la pena) y **revisar** (contradicciones, páginas sueltas, cosas viejas).

**Lo único que cambia es la forma del `wiki/`, y la decide para qué es el cerebro.**

## Pasos

### 1. Entender para qué es
Saca de lo que ya te dijeron todo lo que puedas. Pregunta solo lo que falte, en un solo
mensaje:
- **De qué es.** Si no cabe en una frase ("IA", "marketing"), dilo: un tema amplio da un
  wiki genérico. Propón uno más angosto.
- **Las tres preguntas que le va a hacer.**
- **Cuál es la unidad:** el concepto, la persona, el cliente, el momento, el video...
- **Qué se le pierde hoy** que este cerebro tiene que guardar.

### 2. Encontrar dónde viven los cerebros
Busca en el `CLAUDE.md` del sistema la fila que dice dónde están los cerebros. Si no hay,
pregunta. Si la persona no tiene preferencia, usa una carpeta `Cerebros/` al lado del sistema.

### 3. Usar el más parecido como molde
Lee el `CLAUDE.md` de los cerebros que ya existen y elige el más parecido en propósito.
Cópiale lo que sirve: subcarpetas de `raw/`, formato de las páginas, cómo cita, reglas
generales. **El molde se lee, no se toca.** Si no hay ningún cerebro todavía, parte de la
sección de arriba.

### 4. Diseñar la forma y confirmarla
Con las respuestas del paso 1, propón la forma del `wiki/` en pocas líneas: cada carpeta o
archivo con una frase de para qué sirve, y las reglas propias de este cerebro (lo que lo
hace distinto del molde). **Espera un sí antes de crear nada.** Es la única decisión que
toma la persona.

### 5. Crear
- Las carpetas de `raw/` y `wiki/`.
- El `CLAUDE.md`, con estas secciones: qué es y para qué, las tres preguntas, las capas,
  cómo se ingiere, la forma del wiki, las reglas propias, y los límites (`raw/` no se edita,
  cada afirmación cita su fuente).
- `index.md` vacío con sus encabezados.
- `log.md` con la primera entrada: la fecha, que se creó y de qué cerebro salió el molde.

### 6. Meter las primeras fuentes
Según lo que te hayan dado. Una regla para todo lo que se instala: en Windows, lo que
instalas con `winget` no aparece en la terminal que ya estaba abierta. Si después de
instalar el comando no se encuentra, búscalo por su ruta completa o pide reiniciar Claude
Code; no lo reinstales.

**Un link de YouTube**
1. Si `yt-dlp` no está instalado, dile a la persona qué es (gratis y de código abierto,
   `github.com/yt-dlp/yt-dlp`) e instálalo: `winget install yt-dlp.yt-dlp` en Windows,
   `brew install yt-dlp` en Mac. Si está instalado pero el comando no se encuentra, prueba
   `python -m yt_dlp`. Confirma con `yt-dlp --version` antes de seguir.
2. Baja solo los subtítulos, sin el video. Con `--list-subs` ve cuáles hay y baja los
   automáticos en el idioma original del video (los que terminan en `-orig`), con
   `--skip-download --write-auto-subs --sub-format vtt`. Si uno da error 429, reintenta con el
   `-orig`.
3. Límpialos: los subtítulos automáticos repiten cada renglón dos o tres veces. Quita los
   repetidos y las marcas de tiempo por renglón, y deja bloques de unos 30 segundos con su
   minuto al inicio.
4. Guárdalo en `raw/videos/AAAA-MM-DD-slug.md` con una cabecera: título, canal, link, fecha de
   publicación y fecha en que lo bajaste.
5. **Si el video no tiene subtítulos**, dilo y ofrece transcribirlo con Whisper: baja solo el
   audio con `yt-dlp -x` y sigue los pasos de "Un video guardado en la computadora". Nunca lo
   transcribas de memoria ni lo resumas.
6. Los nombres propios mal escritos no se corrigen en `raw/`. Se normalizan al escribir el
   wiki.

**Un canal de YouTube** ("los últimos 40 videos de Gary Vee")
1. Encuentra el canal y lista sus videos más recientes sin bajar nada:
   `yt-dlp --flat-playlist --playlist-end 40 --print "%(id)s | %(title)s | %(duration)s" "https://www.youtube.com/@canal/videos"`.
   La pestaña `/videos` deja fuera los Shorts.
2. Antes de bajar, enséñale la lista a la persona con la duración total y una advertencia:
   integrar horas de video al wiki gasta mucho de su plan. Si suman más de 10 horas, propón
   empezar con 10 o 15 videos y meter el resto después. Espera su sí.
3. Baja los subtítulos de uno en uno, con los pasos de "Un link de YouTube", y con
   `--sleep-subtitles 3` para que YouTube no te bloquee. Si uno no tiene subtítulos, anótalo y
   sigue con el siguiente; no lo transcribas con Whisper sin preguntar.
4. Guarda todo en `raw/videos/` primero. Integra al wiki después, por tandas de 5 videos,
   actualizando `index.md` y `log.md` al final de cada tanda, para que si se corta no se
   pierda lo hecho.
5. Al final di cuántos entraron y cuáles no, y por qué.

**Un video guardado en la computadora** (o un audio, una clase grabada, un reel)
1. Claude no escucha audio: hace falta Whisper, el modelo de transcripción de OpenAI, gratis y
   de código abierto (`github.com/openai/whisper`). Corre en la computadora, sin cuenta ni llave.
2. Si falta algo, dile qué vas a instalar y que la primera vez baja más de 1 GB (el modelo y
   sus librerías). Después instálalo en este orden:
   - **Python**, si no hay: `winget install Python.Python.3.12` en Windows, `brew install python`
     en Mac.
   - **ffmpeg**, que saca el audio del video: `winget install Gyan.FFmpeg` en Windows,
     `brew install ffmpeg` en Mac.
   - **Whisper**: `pip install openai-whisper`.
   Confirma que los tres responden antes de transcribir.
3. Transcribe cada archivo con el modelo `turbo` y el idioma del video (`--language es` si es
   español). Avisa antes de empezar: en una computadora sin tarjeta de video tarda más o menos
   lo que dura el video. Si son varios, de uno en uno, y di cuál va.
4. Guárdalo en `raw/videos/AAAA-MM-DD-slug.md` con una cabecera: nombre del archivo, ruta, fecha
   del archivo y fecha en que se transcribió. Bloques de unos 30 segundos con su minuto al inicio.
5. El video no se copia a `raw/`: lo que entra a un cerebro es texto.

**Una app sin API ni conector** (tu comunidad de Skool, un CRM viejo, un panel web)
1. Se usa un navegador que maneja Claude: Playwright MCP, de Microsoft, gratis y de código
   abierto (`github.com/microsoft/playwright-mcp`). Si no está, instálalo con
   `claude mcp add playwright -- npx @playwright/mcp@latest` en Mac, o
   `claude mcp add playwright -- cmd /c npx @playwright/mcp@latest` en Windows (sin el
   `cmd /c`, en Windows no arranca). Necesita Node.js: si no hay,
   `winget install OpenJS.NodeJS.LTS` o `brew install node`. Después pide reiniciar Claude Code.
2. **La persona inicia sesión, nunca tú.** Abre la página, y si pide entrar, para y dile que
   inicie sesión en la ventana que se abrió. No escribas ni pidas contraseñas. La sesión se
   queda guardada para la próxima vez.
3. **Solo lectura.** No publiques, no comentes, no des like, no mandes mensajes, no cambies
   ninguna configuración. Si para llegar a un dato hay que tocar un botón que cambia algo, para
   y pregunta.
4. Ve despacio, una página a la vez, como lo haría una persona.
5. Guarda lo que encuentres en `raw/<app>/`, un archivo por persona o por página, con la URL
   de donde salió y la fecha en que lo leíste. Copia el texto tal cual.
6. Al final di cuántas páginas leíste y qué no pudiste leer.

**Un link de una carpeta de Google Drive**
1. Usa el conector de Google Drive de Claude. No hace falta instalar nada: ni un CLI de
   Google ni MarkItDown, porque el conector ya entrega en texto los Google Docs, Sheets y
   Slides, los PDF y los Word, Excel y PowerPoint que estén en Drive.
   Si no ves sus herramientas, no está conectado. Dile a la persona que lo conecte una vez en
   claude.ai (Configuración, Conectores, Google Drive), que su Claude Code tenga la sesión
   iniciada con esa misma cuenta de Claude (no con una API key) y que lo vuelva a abrir. Y para.
2. Saca el ID de la carpeta del link (lo que va después de `/folders/`) y lista lo que hay
   adentro, **página por página hasta que no haya más**, y entra también a las subcarpetas.
   Antes de leer, di cuántos archivos encontraste.
3. Lee cada documento y guárdalo como `.md` en `raw/documentos/`, con una cabecera: título,
   link y **fecha de última modificación**. Esa fecha es la que el wiki usa para saber qué tan
   vigente está algo. Si el texto de un archivo muy largo llega cortado, dilo en su cabecera.
4. Lo que no es texto (videos, audios, imágenes), lístalo al final con su link. No lo saltes
   en silencio.

**Archivos que te pasen**
Cópialos a la subcarpeta de `raw/` que les toque, sin editarlos. Un PDF, un `.md` o un `.txt`
los lees directo. Un Word, Excel o PowerPoint no: guarda el original y al lado su versión en
texto (`mismo-nombre.md`), convertida con MarkItDown (`pip install "markitdown[all]"`, luego
`markitdown archivo.docx -o archivo.md`). Si no está instalado, avisa antes de instalarlo.

**Lo que la persona te dicte**
1. Antes de integrar nada, guárdalo **tal cual** en `raw/dictados/AAAA-MM-DD-tema.md`. Un
   dictado es una fuente igual que un documento.
2. Si al integrarlo falta algo (quién lo hace, en cuánto tiempo, qué sigue), **pregúntalo al
   final, todo junto.** No rellenes con lo que suena lógico. Las respuestas también se guardan
   en `raw/dictados/`.

### 7. Ingerir
Integra las fuentes siguiendo el `CLAUDE.md` que acabas de escribir. Actualiza `index.md` y
agrega al `log.md` qué páginas creó o tocó cada fuente.

### 8. Cerrar
Reporta en una lista corta:
1. Dónde quedó el cerebro.
2. La forma del wiki.
3. Qué fuentes entraron y cuáles no, y por qué.
4. Qué páginas se crearon.
5. Una pregunta para probarlo.

Y ofrece conectarlo al sistema con `/apuntar`, con su regla: **es apoyo para pensar, nunca
fuente de verdad del negocio.**

## Reglas

- `raw/` no se edita después de guardarlo. La persona puede borrar de ahí; la IA no.
- Nada inventado. Si una fuente no se pudo bajar o leer, se dice.
- No se mueve, se borra ni se edita ningún cerebro que ya existe.
- Si el cerebro va a guardar conversaciones con clientes o datos de otras personas, avísalo:
  ese cerebro no se sube a un repo compartido.
