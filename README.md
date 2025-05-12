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

```json
{
  "address": "London",
  "domain": "school",
  "startdate": "2025-05-09T00:00",
  "enddate": "2025-05-11T23:59",
  "language": "en",
  "type": "working",
}
```

GET /working-schedule?address=Berlin&domain=school&startdate=2025-05-01T00:00&enddate=2025-05-03T00:00&type=working

✅ Response format
Returns a JSON array of day-objects:

```json
[
    {
        "actual": "workday",
        "confidence": 0.95,
        "date": "2025-05-09T00:00",
        "note": "Regular school day",
        "official": "workday",
        "tags": [
            "education"
        ]
    },
    {
        "actual": "non-workday",
        "confidence": 0.99,
        "date": "2025-05-10T00:00",
        "note": "Weekend, schools are typically closed",
        "official": "non-workday",
        "tags": [
            "weekend",
            "education"
        ]
    },
    {
        "actual": "non-workday",
        "confidence": 0.99,
        "date": "2025-05-11T00:00",
        "note": "Weekend, schools are typically closed",
        "official": "non-workday",
        "tags": [
            "weekend",
            "education"
        ]
    }
]
```


