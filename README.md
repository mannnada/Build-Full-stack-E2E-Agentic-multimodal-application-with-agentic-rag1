# Build-Full-stack-E2E-Agentic-multimodal-application-with-agentic-rag1

# Full‑stack E2E Agentic Multimodal App (Agentic RAG)

Minimal starter to build & deploy an **agentic, multimodal RAG** app (text + images) with ADK and Gemini 2.5 Flash. Ships with a tiny FastAPI server, YAML config, and Docker/Cloud Run deploy.

**Codelab:** [https://codelabs.developers.google.com/personal-expense-assistant-multimodal-adk](https://codelabs.developers.google.com/personal-expense-assistant-multimodal-adk)
**YouTube:** https://youtu.be/DBbb1elqfoA

---

## What’s inside

* `main.py` – FastAPI app + agent endpoint
* `settings.yaml.example` → copy to `settings.yaml`
* `task_prompt.md` – agent role/guardrails
* `schema.py` – request/response models
* `Dockerfile`, `LICENSE`, `README.md`

---

## Quick start

```bash
# 1) clone
git clone <your-repo-url> agentic-app && cd agentic-app

# 2) create env & install
python -m venv .venv && source .venv/bin/activate
pip install -U pip && pip install -e .

# 3) configure
cp settings.yaml.example settings.yaml
# set GOOGLE_API_KEY / OPENAI_API_KEY, choose model/provider

# 4) run
uvicorn main:app --reload --port 8000
# Open http://localhost:8000/docs
```

---

## Docker / Cloud Run (optional)

```bash
docker build -t agentic-app:local .
docker run -p 8080:8080 -e GOOGLE_API_KEY=$GOOGLE_API_KEY agentic-app:local
```

```bash
# Cloud Run (example)
gcloud builds submit --tag gcr.io/$PROJECT_ID/agentic-app:latest
gcloud run deploy agentic-app \
  --image gcr.io/$PROJECT_ID/agentic-app:latest \
  --region us-central1 --allow-unauthenticated \
  --set-env-vars GOOGLE_API_KEY=$GOOGLE_API_KEY
```

---

## License

Apache-2.0.
