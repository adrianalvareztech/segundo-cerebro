# Prompts del Módulo 4

Todos los prompts que se usan en cámara, listos para copiar. Lo que va entre corchetes lo
cambia cada quien.

Todo lo que se instala se instala igual: le pegas el link a Claude Code y le pides que lo
instale. Si te pide permiso para correr un comando, léelo y acepta.

---

## Clase 2 · Tu primer cerebro (a mano, con el gist)

**Pasarle la idea a Claude Code**
> Lee este idea file de Karpathy: https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f
> Quiero un segundo cerebro sobre [tu tema, que quepa en una frase], para [para qué lo vas a usar]. Estas son las tres preguntas que le voy a hacer: [pregunta 1], [pregunta 2], [pregunta 3]. Arma la estructura y escribe el CLAUDE.md. No ingieras nada todavía.

**Ingerir** (el que vas a usar el resto de tu vida)
> Acabo de meter fuentes en raw, procésalas e intégralas al wiki.

**Guardar una respuesta de vuelta**
> Esta respuesta está buena. Guárdala en [carpeta del wiki] y enlázala desde las páginas que usó.

---

## Clase 3 · Conectarlo y que no se pudra

**La revisión semanal** (como tarea programada, en borrador)
> Revisa el cerebro de [nombre]: integra lo pendiente en raw, marca contradicciones entre páginas, lista las afirmaciones de más de 6 meses y las páginas sin enlaces. No borres nada, déjame el reporte.

---

## Clase 4 · Del segundo cerebro en adelante

**Instalar el skill** (una vez; luego cierra y abre Claude Code)
> Instala el skill nuevo-cerebro de este repo en mis skills globales: https://github.com/adrianalvareztech/segundo-cerebro

**Instalar yt-dlp** (opcional: el skill lo instala la primera vez que lo necesita)
> Instala yt-dlp: https://github.com/yt-dlp/yt-dlp. Al final dime qué versión quedó.

**Instalar Whisper** (para los videos que tienes en tu computadora; la primera vez baja más de 1 GB)
> Instala Whisper para transcribir los videos de mi computadora: https://github.com/openai/whisper. Instala también lo que necesite.

**Con el skill**
> /nuevo-cerebro de Alex Hormozi, para pensar mi oferta y mis precios como él. Empieza con este video: [link de YouTube]

**Sin el skill** (funciona igual, solo hay que decirle de dónde copiar)
> Hagamos un segundo cerebro nuevo de [referente]. Usa como molde el que hicimos de [tu tema], en [ruta]: misma estructura y mismas reglas, pero ajusta la forma del wiki a esto: lo que le voy a preguntar es [las tres preguntas]. Empieza con este video: [link de YouTube].

**Videos que tienes guardados en tu computadora** (con Whisper, gratis y local)
> Transcribe con Whisper los videos que están en [carpeta], en español. Guarda cada uno en raw/videos/ como Markdown, con el nombre del archivo y su fecha, e intégralos al wiki. Si no tienes Whisper o ffmpeg, instálalos.

**Meter un video a un cerebro que ya existe**
> Saca la transcripción de este video con yt-dlp, solo los subtítulos, sin bajar el video. Límpiala, guárdala en raw/videos/ con título, canal, link y fecha, e intégrala al wiki: [link]

---

## Clase 5 · Tus clientes

**Crear el cerebro, sin fuentes todavía**
> /nuevo-cerebro de [mis clientes y prospectos], para saber qué necesita cada uno, qué le prometí y qué objeciones me ponen antes de comprar. Las fuentes van a ser [mis DMs de Instagram, mi WhatsApp, mis llamadas...]. Todavía no te paso ninguna.

**Tus DMs de Instagram, con Composio**

Antes, una sola vez: tu Instagram de empresa o de creador, una cuenta gratis en composio.dev
con Instagram conectado, y Composio agregado a Claude en Configuración, Conectores.
> Con Composio, lee mis mensajes directos de Instagram. Es solo lectura: no mandes, no contestes y no marques como leído ningún mensaje.
>
> Revisa mis últimas 50 conversaciones. De cada una, quédate solo con lo que la otra persona dice sobre:
> - a qué se dedica y cómo es su negocio
> - su situación hoy
> - sus problemas y lo que ya intentó
> - lo que quiere lograr
> - sus dudas y objeciones antes de comprar
>
> Ignora los saludos, las despedidas, los "gracias", los emojis, los stickers, los audios sin texto y los mensajes que solo traen la palabra clave de una automatización. De mis mensajes, guarda solo los que traen un precio, una promesa o una fecha.
>
> Copia sus palabras tal cual, sin resumir ni corregir, con la fecha de cada mensaje. Si una conversación no tiene nada de esto, sáltala.
>
> Guarda un archivo por persona en raw/instagram/, con su @ como nombre. Al final dime cuántas conversaciones revisaste, cuántas guardaste y cuántas saltaste.

Por qué se guardan algunos mensajes tuyos: sin ellos el cerebro no puede contestar "¿qué le
prometí?" ni "¿qué precio le di?".

**Instalar el navegador que maneja Claude** (una vez; luego cierra y abre Claude Code)
> Instala este MCP para que puedas manejar un navegador: https://github.com/microsoft/playwright-mcp

**Una app sin API ni conector, con el navegador** (el ejemplo es Skool; cambia la app y lo que guardas)
> Con Playwright, abre mi comunidad de Skool: [link]. Si te pide iniciar sesión, espérame a que entre yo. Es solo lectura: no publiques, no comentes, no des like y no mandes mensajes. De los 10 miembros más recientes, guarda por persona su nombre, la fecha en que entró, sus respuestas a las preguntas de ingreso y su bio. Luego busca lo que cada uno escribió en la comunidad: [su publicación en la categoría donde cuentan su objetivo: link] y [su comentario en la publicación de bienvenida: link]. Copia sus palabras tal cual, con la fecha. Si algo de lo que escribieron puede no ser cierto (un juego, una broma), no lo guardes. Un archivo por persona en raw/skool/, con el link de su perfil y de cada publicación.

La contraseña nunca se la das a Claude: inicias sesión tú en la ventana que se abre.

**Tus llamadas, solas cada noche** (con Fathom conectado a Claude; se programa como la tarea de la clase 12 del módulo 3)
> Cada noche a las 11, revisa en Fathom las llamadas nuevas desde la última vez. Guarda cada transcript tal cual en raw/llamadas/ de mi cerebro de clientes, con la fecha y el nombre del cliente en el nombre del archivo, y después intégralo al wiki. Si no hay llamadas nuevas, no hagas nada.

**Tus chats de WhatsApp** (después de exportarlos a mano, sin archivos)
> Metí chats de WhatsApp exportados en raw/whatsapp/. Intégralos con las mismas reglas: de cada chat, solo lo que el cliente dice de su situación, sus problemas, lo que quiere, sus objeciones, y lo que yo le prometí o le coticé. Si un número es la misma persona que un @ de Instagram o un nombre de una llamada, júntalos en una sola página, y pregúntame cuando no estés seguro.

---

## Clase 6 · Los procesos de tu negocio

**Lo que ya está escrito, en Google Drive**
> /nuevo-cerebro de los procesos de mi negocio, para que mi equipo y yo sepamos qué hacer cuando pasa algo. Están en esta carpeta de Drive: [link de la carpeta]. Lo que le vamos a preguntar: "acaba de pasar X, ¿qué hago ahora?", "¿quién se encarga de esto?" y "¿qué plantilla uso?".

**Lo que vive en tu cabeza, dictado**
> Aquí faltan procesos que solo viven en mi cabeza. Te los voy a dictar. Guarda lo que te diga tal cual en raw/dictados/ y luego intégralo. Si te falta algo para que alguien de mi equipo lo pueda seguir sin preguntarme (quién lo hace, en cuánto tiempo, qué sigue), pregúntamelo al final, todo junto.

**La prueba**
> Un cliente acaba de firmar el contrato, ¿qué tengo que hacer ahora?

**Compartirlo con tu equipo** (repo privado; la primera vez inicias sesión con `! gh auth login`)
> Sube este cerebro a un repo privado de GitHub que se llame procesos-[mi negocio]. Si no tienes GitHub CLI, instálalo: https://cli.github.com

**Para usarlo desde el celular** (una vez, desde tu compu; en la nube solo se ven los skills que viven dentro del repo)
> Copia el skill nuevo-cerebro de mis skills globales a .claude/skills/ de este repo y súbelo a GitHub.

---

## Clase 7 · Tus videos

**Con el skill**
> /nuevo-cerebro de mis videos de YouTube, para saber en cuál dije qué y qué me falta por hacer. Mi canal: [link del canal]. Empieza con los últimos 5.

**Las pruebas**
> ¿En qué video expliqué [tema] y qué dije exactamente?
> ¿Qué prometí en algún video que todavía no he hecho?
