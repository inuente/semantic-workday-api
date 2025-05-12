# Working Days  API

Semantic calendar API that returns **working / non-working days** with context-aware explanation (holiday, weekend, election, weather, etc).


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

json
{
  "region": "California",
  "datetime": "2025-04-20T12:00",
  "document_type": "VAT_Report"
}

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



OpenAI GPT-4o (Assistants API)

Redis (optional, only for Render)

Render + Zyla API Hub
