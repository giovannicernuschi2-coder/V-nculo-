# Vínculo

App web de chat de rol con personajes de IA. Es un solo archivo (`index.html`), sin servidor ni dependencias de compilación.

- **Descubrir:** 8 personajes originales con búsqueda y filtros.
- **Chat:** respuestas en streaming, regenerar, detener y reiniciar.
- **Crear:** haz tus propios personajes.
- **Datos:** chats, personajes y ajustes se guardan en el navegador (`localStorage`).

## Cómo piensa (IA propia)

En la pestaña **Ajustes** eliges el motor de respuestas:

1. **En tu navegador (por defecto).** Usa [WebLLM](https://github.com/mlc-ai/web-llm): el modelo se descarga una vez (0,9 a 2,5 GB), se guarda en caché y corre en la GPU del dispositivo. No hay servidor, ni claves, ni costos. Requiere un navegador con WebGPU (Chrome o Edge recientes).
2. **Servidor compatible con OpenAI.** Cualquier API con `/chat/completions`: Ollama, LM Studio, llama.cpp, OpenRouter, Groq, etc. Cada usuario pone su dirección y, si hace falta, su propia clave (se guarda solo en su navegador).

Para Ollama en tu PC: `OLLAMA_ORIGINS=* ollama serve` y usa `http://localhost:11434/v1`.

## Publicar en GitHub Pages

1. Crea un repositorio y sube `index.html` y este `README.md`.
2. En el repositorio: **Settings → Pages → Build and deployment → Deploy from a branch**, rama `main`, carpeta `/ (root)`.
3. En un par de minutos queda en `https://TU-USUARIO.github.io/NOMBRE-DEL-REPO/`.

## Notas

- Nunca pongas una clave de API tuya dentro del HTML: en una página pública cualquiera podría verla y usarla.
- Los modelos pequeños en el navegador escriben menos bien que los grandes en la nube. Si quieres mejor calidad para todos, el siguiente paso es un backend propio que guarde la clave.
- Los identificadores de modelo de WebLLM pueden cambiar entre versiones. Si uno falla, consulta la lista `prebuiltAppConfig.model_list` de la versión que cargas (está fijada en `index.html`, constante `WEBLLM`).
- Si publicas la app para el público, el contenido generado por IA suele requerir moderación y una política de uso.
