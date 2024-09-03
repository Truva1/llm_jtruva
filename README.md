# llm_jtruva
Large language model test and web application
## Instalación
Como primer paso instalamos neofetch
````bash
sudo apt install neofetch
````
Ahora se debe descargar [ollama](https://ollama.com/download/linux) desde su paguna web.

````bash
curl -fsSL https://ollama.com/install.sh | sh
````
## Iniciar servidor
````bash
ollama serve
````
## Descargar un modelo
````bash
ollama pull <model_name>:<tag>
````
## Descargar e iniciar un modelo
````bash
ollama run gemma:2b
ollama run tinyllama
````
## Listar modelos
````bash
ollama list
````
## Borrar modelos
````bash
ollama rm <nombre>
````
## Enviar post desde la terminal
````bash
curl -X POST http://localhost:11434/api/generate -d '{
  "model": "tinyllama",
  "prompt": "Why is the sky blue?",
  "stream": false
}'
````
## Instalar Thunder client
Thunder client permite enviar request a ollama, debe instalar la extension, hacer un nuevo request, poner como destino la url y como body el JSON especificado en el metodo anterior

URL destino
````bash
http://localhost:11434/api/generate
````
JSON Body
````json
{
  "model": "tinyllama",
  "prompt": "Why is the sky blue?",
  "stream": false
}
````

## Enviar post con pyton
```python
import requests

url = 'http://localhost:11434/api/generate'
myobj = {
  "model": "tinyllama",
  "prompt": "Why is the sky blue?"
  "stream": False
}

x = requests.post(url, json = myobj)

print(x.text)
```

## Estructura básica para realizar una consulta a groq usando su API REST
```bash
export GROQ_API_KEY=<your-api-key-here> #definir variable de entorno

curl -X POST "https://api.groq.com/openai/v1/chat/completions" \
     -H "Authorization: Bearer $GROQ_API_KEY" \
     -H "Content-Type: application/json" \
     -d '{"messages": [{"role": "user", "content": "Explain the importance of fast language models"}], "model": "llama3-8b-8192"}'
```

