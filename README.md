# agentic-day2-routing

A minimal LangGraph workflow implementing tier-based support routing (VIP vs standard).

## Setup

1. Create and activate a virtual environment (or use an existing conda env).

2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

3. Create a `.env` file with your API keys:
   ```
   OPENAI_API_KEY=your_key_here
   ```

   > ⚠️ **Never commit `.env` to version control.** It is listed in `.gitignore`.

## Run

```bash
python app.py
```

## How it works

- `SupportState` tracks messages, tier, escalation flag, and issue type.
- `check_tier` node inspects the first message to classify the user as `vip` or `standard`.
- `route_by_tier` routes VIP users to `vip_agent` and everyone else to `standard_agent`.
- `vip_agent` resolves without escalation; `standard_agent` sets `should_escalate = True`.
