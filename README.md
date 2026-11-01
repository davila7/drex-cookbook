# Drex 2.0 cookbook

A runnable Jupyter notebook that builds a support-triage agent on top of [Drex 2.0](https://github.com/nace-ai/drex-decision-models), Nace AI's decision model, using the hosted API. No GPU needed.

Drex is not a chat model: you send a `state` and typed questions (`noul` yes/no, `choice`, `score`) and get a probability for every option back. The notebook uses those probabilities to decide when the agent acts on its own and when it hands a ticket to a person, then measures the result on a small labeled set.

## What's inside

| Section | What it shows |
|---|---|
| 1. First call | One `POST /v1/systemone` request and how to read the response |
| 2. Question types | `choice`, `noul` and `score` in a single request |
| 3. Batching | Token (cost) savings of one request vs. one per question |
| 4. Confidence gate | Thresholds that turn probabilities into actions or human review |
| 5. Evaluation | Accuracy by ticket type, coverage vs. accuracy, latency, cost |
| 6. Failures | Every mistake with its probabilities, plus prompt-injection tickets |

`data/tickets.jsonl` contains 40 synthetic support tickets written and labeled by hand: 20 clear-cut, 20 deliberately hard (multi-intent, sarcasm, Spanish, negation, vague, prompt injection). It is a sanity check for the workflow, not a benchmark.

## Run it

```bash
git clone https://github.com/davila7/drex-cookbook.git
cd drex-cookbook
python3 -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt
cp .env.example .env   # paste your key from https://console.nace.ai
jupyter lab drex_cookbook.ipynb
```

A new Nace account includes $5 of balance. Drex 2.0 bills $0.06 per million input tokens (output tokens are free), so a full run of the notebook costs a fraction of a cent.

## Disclosure

This cookbook was produced as part of a sponsored collaboration with Nace AI. The code, dataset and conclusions are my own.
