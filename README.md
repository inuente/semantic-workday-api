# Working Days AI API

Semantic calendar API that returns **working / non-working days** with context-aware explanation (holiday, weekend, election, weather, etc).

Powered by OpenAI Assistants API and integrated with Zyla API Hub.

---

## 🔗 Endpoint

GET /working-schedule
Query parameters:


| Name      | Type   | Required | Description                                  |
|-----------|--------|----------|----------------------------------------------|
| address   | string | ✅       | Location, e.g. "Tel-Aviv"                      |
| domain    | string | ✅       | Context: "school", "office"                  |
| startdate | string | ✅       | Start in ISO format: YYYY-MM-DDTHH:MM        |
| enddate   | string | ✅       | End in ISO format: YYYY-MM-DDTHH:MM          |
| language  | string | ❌       | "en", "he" — default: "en"                   |
| type      | string | ✅       | "working" or "non-working"                   |



🧪 Example request

GET /working-schedule?address=Berlin&domain=school&startdate=2025-05-01T00:00&enddate=2025-05-03T00:00&type=working

✅ Response format
Returns a JSON array of day-objects:

json
[
  {
    "date": "2025-05-01T00:00",
    "official": "nonworkday",
    "actual": "nonworkday",
    "note": "International Workers' Day, public holiday in Germany.",
    "tags": ['holiday'],
    "confidence": 1.0
  }
]


🔐 Zyla proxy protection
This API is protected. You must call it via Zyla API Hub using your X-RapidAPI-Key.

🚀 Deployment
Use runtime.txt and Procfile to deploy on Render:

pip install -r requirements.txt
gunicorn main:app


🧪 How to run locally (dev)
Install dependencies:

pip install -r requirements.txt
Create .env in root (see .env.example)

Run:

python main.py
Test endpoint:


http://localhost:5000/working-schedule?...params


📄 OpenAPI Spec
See openapi.yaml

🧩 Built with
Flask + Pydantic

OpenAI GPT-4o (Assistants API)

Redis (optional, only for Render)

Render + Zyla API Hub
