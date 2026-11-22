# Site Insight API

An API where the user sends a URL and a prompt (asking for some information about that page). LangChain analyzes the page and the model returns the requested information based on the prompt.

> Frontend: [site-insight-web](https://github.com/Joao-Adegas/site-insight-web)

## Features

- Analyze a public web page from its URL
- Ask for specific information through a free-text prompt
- Accepts the URL with or without the protocol (`ge.globo.com` or `https://ge.globo.com/`)

## Tech stack

Python, FastAPI, Uvicorn, LangChain, Groq

## Getting started

### Prerequisites

- Python 3
- A Groq API key: create one at <https://console.groq.com/keys>

### Configuration

Create a `.env` file in the project root:

```env
GROQ_API_KEY="your_api_key"
```

Replace `your_api_key` with your key, keeping the quotes. Never commit this file.

### Run

```bash
python -m venv env

# Windows
./env/Scripts/activate
# macOS / Linux
source env/bin/activate

pip install -r requirements.txt
uvicorn main:app
```

The API will be available at `http://127.0.0.1:8000`.

## Example

Request body (JSON):

```json
{
  "url": "youtube.com",
  "prompt": "Tell me videos to learn how to invest my money."
}
```

The response is a text answer generated from the content of the page.

## Notes

- URLs already tested: `ge.globo.com` and `g1.globo.com`.
- To always analyze a single site, hardcode its URL in the `WebBaseLoader` call instead of using the `url` field from the request.

## Author

João Pedro dos Santos Adegas — [@Joao-Adegas](https://github.com/Joao-Adegas)
