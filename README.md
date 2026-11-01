# Drex 2.0 cookbook

A short, runnable Jupyter notebook showing how to use [Drex 2.0](https://github.com/nace-ai/drex-decision-models), Nace AI's decision model, as the decision step of an agent or workflow. It uses the hosted API, so no GPU is needed.

Drex is not a chat model: you send a `state` and typed questions (`noul` yes/no, `choice`, `score`) and get a probability for every option back. The notebook walks through:

1. Setup
2. First call
3. The three question types in one request
4. Turning probabilities into a decision (act, or hand off to a human)
5. Running a small batch of support tickets

## Run it

```bash
git clone https://github.com/davila7/drex-cookbook.git
cd drex-cookbook
python3 -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt
cp .env.example .env   # paste your key from https://console.nace.ai
jupyter lab drex_cookbook.ipynb
```

A new Nace account includes $5 of balance. Drex 2.0 bills $0.06 per million input tokens (output tokens are free), so running the notebook costs a fraction of a cent.

## Disclosure

This cookbook was produced as part of a sponsored collaboration with Nace AI. The code and opinions are my own.
