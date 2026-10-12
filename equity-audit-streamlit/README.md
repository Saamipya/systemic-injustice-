# Equity Audit — Streamlit edition

A Streamlit web app for evidence-first review of laws, policy papers, regulations, and administrative documents for potential systemic inequities.

## Run locally (Mac)

1. Install Python 3.11+ from https://www.python.org/downloads/
2. Open Terminal and `cd` into this folder.
3. Create a virtual environment and install requirements:

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

4. Configure your Hugging Face token. Create `.streamlit/secrets.toml`:

```toml
HF_TOKEN = "hf_your_real_token"
HF_MODEL = "openai/gpt-oss-120b:fastest"
```

Keep this file private and never commit it to GitHub. Or export `HF_TOKEN` in your shell environment.

5. Launch:

```bash
streamlit run app.py
```

The browser should open at http://localhost:8501.

## Publish free with Streamlit Community Cloud

1. Upload this project to a GitHub repository, but do NOT commit `.streamlit/secrets.toml`.
2. Visit https://share.streamlit.io/ and deploy the repository, selecting `app.py` as the main file.
3. In the app's settings/secrets, add `HF_TOKEN` and `HF_MODEL` in TOML format.
4. Redeploy and test using the sample policy.

## Model / privacy

Default model is `openai/gpt-oss-120b:fastest` through Hugging Face Inference Providers. Document text is sent to that hosted inference service for analysis. Check current model availability, licensing, provider terms, privacy practices, and pricing before launch.

## Limitations / production checklist

- This tool identifies research leads, not proven injustice or legal advice.
- It does not browse legal databases or verify current laws.
- Text-only PDF extraction; scanned PDFs need OCR.
- Analysis is limited to 60,000 characters.
- Add rate limits, usage controls, a privacy policy, and abuse prevention before broad public launch.
- Have local legal experts and affected communities review quality and false positives/negatives.
