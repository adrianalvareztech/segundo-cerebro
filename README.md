# Segundo cerebro con IA

Un skill para Claude Code que crea segundos cerebros con el método LLM Wiki de Andrej Karpathy.

Un segundo cerebro es una carpeta de texto que tu IA lee, ordena y mantiene al día. Tú metes
lo que lees, escuchas o te dicen tus clientes, y Claude lo convierte en un wiki enlazado al que
le haces preguntas. La idea completa está en el
[idea file de Karpathy](https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f).

## Cómo se ve un cerebro

```
mi-cerebro/
  raw/        lo que tú metes, tal cual. Nunca se edita
  wiki/       lo que escribe Claude: conceptos, resúmenes y enlaces
  CLAUDE.md   las reglas: para qué es y cómo se pasa de raw/ a wiki/
  index.md    la tabla de contenido
  log.md      qué se procesó y cuándo
```

Lo único que cambia de un cerebro a otro es la forma del `wiki/`, y la decide para qué es.
El de un tema que investigas se organiza por conceptos. El de tus clientes, por persona. El
de tus videos, por video.

## Empieza así

**1. El primero, a mano.** Así entiendes cómo funciona. Abre Claude Code en una carpeta vacía
y pega:

> Lee este idea file de Karpathy: https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f
> Quiero un segundo cerebro sobre [tu tema, que quepa en una frase], para [para qué lo vas a usar]. Estas son las tres preguntas que le voy a hacer: [pregunta 1], [pregunta 2], [pregunta 3]. Arma la estructura y escribe el CLAUDE.md. No ingieras nada todavía.

**2. Instala el skill**, para los que siguen. En Claude Code:

> Instala el skill nuevo-cerebro de este repo en mis skills globales (~/.claude/skills/): https://github.com/adrianalvareztech/segundo-cerebro

Cierra y vuelve a abrir Claude Code. Escribe `/nuevo-cerebro` y debe aparecer.

**3. Úsalo.** Una línea y un link:

> /nuevo-cerebro de Alex Hormozi, para pensar mi oferta y mis precios como él. Empieza con este video: [link de YouTube]

El skill te hace las preguntas que falten, te propone la forma del wiki, espera tu sí, lo crea
copiando el cerebro que ya tienes más parecido y mete las primeras fuentes.

## Lo de todos los días

| Para | Le dices |
|---|---|
| Meter algo nuevo | "Acabo de meter fuentes en raw, procésalas e intégralas al wiki." |
| Preguntar | Lo que quieras. Te contesta citando de qué página y de qué fuente lo saca |
| Guardar una buena respuesta | "Esta respuesta está buena. Guárdala en el wiki y enlázala desde las páginas que usó." |
| Que siga sirviendo | "Revisa el cerebro: integra lo pendiente en raw, marca contradicciones, lista lo de más de 6 meses y las páginas sin enlaces. No borres nada, déjame el reporte." |

Meter un archivo a `raw/` no lo mete al wiki. Son dos pasos: lo metes y le pides que lo integre.

## De dónde saca las fuentes

| Fuente | Cómo | Qué instala la primera vez |
|---|---|---|
| Un video de YouTube | baja solo los subtítulos | [yt-dlp](https://github.com/yt-dlp/yt-dlp) |
| Un video o audio en tu computadora | lo transcribe en tu compu, sin mandarlo a ningún lado | [Whisper](https://github.com/openai/whisper), con Python y ffmpeg (más de 1 GB la primera vez) |
| Una carpeta de Google Drive | con el conector de Google Drive de Claude. Lee Google Docs, Sheets y Slides, y también PDF, Word, Excel y PowerPoint, sin convertir nada | nada. Se conecta una vez en claude.ai (Configuración, Conectores, Google Drive) y Claude Code lo usa si tienes la sesión iniciada con esa cuenta |
| Una app sin API ni conector | Claude maneja un navegador con tu sesión. Inicias sesión tú, nunca le das tu contraseña, y solo lee | [Playwright MCP](https://github.com/microsoft/playwright-mcp), con Node.js |
| Archivos, notas o lo que le dictes | los guarda tal cual en `raw/`. Un PDF lo lee directo | nada |
| Un Word, Excel o PowerPoint en tu computadora | lo convierte a texto antes de guardarlo | [MarkItDown](https://github.com/microsoft/markitdown), con Python |

Nada se instala de entrada. El skill te avisa antes y lo instala cuando una fuente lo pide.
Todo es gratis y de código abierto.

## Lo que hay que saber

- **Guarda texto.** Los videos y audios se transcriben. Las imágenes se quedan en su carpeta,
  y el wiki dice qué hay en cada una y dónde está.
- **No reemplaza tu CRM ni tu Excel.** Quién te pagó y en qué etapa va cada cliente se quedan
  donde ya los llevas.
- **No se mantiene solo** si no lo programas. La revisión de arriba, una vez por semana, es lo
  que lo mantiene vivo.

## Licencia

MIT.
