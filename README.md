# Tu Segundo Cerebro con IA

Los recursos del Módulo 4 de la Oficina de IA: el skill `/nuevo-cerebro` y todos los prompts
que se usan en las clases.

Un segundo cerebro es una carpeta de texto que tu IA lee, ordena y mantiene al día, con el
método LLM Wiki de Andrej Karpathy
([el idea file](https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f)).

## Qué hay aquí

| Archivo | Qué es |
|---|---|
| `nuevo-cerebro/SKILL.md` | El skill que crea un cerebro nuevo a partir del que ya tienes: copia su estructura, ajusta la forma del wiki a para qué es el nuevo, y mete las primeras fuentes (YouTube, videos guardados, Google Drive, apps sin API, archivos o lo que le dictes) |
| `prompts-del-modulo.md` | Los prompts de cada clase, listos para copiar |

## Cómo se instala

Abre Claude Code y pega esto:

> Instala el skill nuevo-cerebro de este repo en mis skills globales (~/.claude/skills/): https://github.com/adrianalvareztech/segundo-cerebro

Cierra y vuelve a abrir Claude Code. Escribe `/nuevo-cerebro` y debe aparecer.

**El primer cerebro hazlo a mano**, con el idea file de Karpathy (clase 2). El skill es para
los que siguen: copia el que ya tienes como molde.

## Lo que el skill instala cuando lo necesita

Nada de esto se instala de entrada. El skill te avisa y lo instala la primera vez que una
fuente lo pide.

| Herramienta | Para qué | De dónde sale |
|---|---|---|
| yt-dlp | bajar los subtítulos de un video de YouTube, sin el video | [github.com/yt-dlp/yt-dlp](https://github.com/yt-dlp/yt-dlp) |
| Whisper + ffmpeg | transcribir videos o audios que tienes en tu computadora | [github.com/openai/whisper](https://github.com/openai/whisper) |
| Playwright MCP | leer una app que no tiene API ni conector, con tu sesión | [github.com/microsoft/playwright-mcp](https://github.com/microsoft/playwright-mcp) |

Las tres son gratis, de código abierto y corren en tu computadora.

## Licencia

MIT.
