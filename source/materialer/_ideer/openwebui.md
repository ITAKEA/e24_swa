# OpenWebUi 

Installer OpenWebUI med OpenAi API og Groq API adgang

```
    docker run -d -p 3000:8080 -v open-webui:/app/backend/data -e OPENAI_API_BASE_URLS="https://api.openai.com/v1;https://api.groq.com/openai/v1/" -e OPENAI_API_KEYS="<OPENAI_API_KEY_1>;<OPENAI_API_KEY_2>" --name open-webui --restart always ghcr.io/open-webui/open-webui:main

```


* [OpenAI API Endpoints](https://docs.openwebui.com/tutorial/openai/)
