# Gemini ve LangChain ile LLM API'larını Çağırma Giriş 🦜🔗

Bu notebook'ta LangChain aracılığıyla LLM API'larını nasıl kullanacağınızı öğreneceksiniz. Örnek olarak Google'ın Gemini API'sını kullanacağız. Bu notebook'un sonunda, LangChain kullanarak API çağrıları yapmayı ve bunu neden yaptığımızı bileceksiniz.

---

## 🛠️ What This Notebook Covers

`calling-llm-apis.ipynb` makes the same Gemini calls in two ways:

1. **Direct SDK (`google.genai`)**: `genai.Client()`, `generate_content()`, and config via `types.GenerateContentConfig`.
2. **LangChain (`init_chat_model`)**: a provider-agnostic chat model with `.invoke()`, generation parameters, and multi-message prompts (`SystemMessage` + `HumanMessage`).

## ▶️ How to Run

This project runs in the shared `langchain-env` set up in [S19D3-S-data-langchain-env](https://github.com/adilpoyrazaka/S19D3-S-data-langchain-env):

```bash
cd ~/projects/llm-unit/S19D3-S-llm-apis   # langchain-env is pinned in llm-unit/
code calling-llm-apis.ipynb               # Select Kernel → langchain-env
```

Credentials are loaded by `load_dotenv()` from `llm-unit/.env` (outside the repo):

```
GEMINI_API_KEY=...   # read by google.genai
GOOGLE_API_KEY=...   # read by LangChain's google_genai provider
```

## 🔧 Changes from the Original

- **Model:** `gemini-2.5-flash-lite` → `gemini-3.5-flash-lite` (2.5 returns `404 NOT_FOUND` for new users).
- **Auth:** Gemini Developer API key instead of Vertex AI. `GOOGLE_API_KEY` was added as an alias of `GEMINI_API_KEY`.
- **`response.text` instead of `response.content`:** with Gemini 3 models, `content` can be a list of content blocks, while `.text` always returns plain text.
