# Hospital Triage Specialist Recommendation API

A minimal FastAPI application to automatically suggest the most relevant specialist department for patients in a hospital triage system, using Gemini LLM (Google AI Studio) via Langchain.

---

## Features

- Receives patient information (gender, age, symptoms) via a POST endpoint
- Sends the data to Gemini LLM to determine the most relevant specialist department
- Returns the recommendation in a simple JSON format

---

## Requirements

- Python 3.9+
- FastAPI
- Uvicorn
- Langchain
- langchain-google-genai
- google-generativeai

Install dependencies:
```bash
pip install -r requirements.txt
````

Atau secara manual:

```bash
pip install fastapi uvicorn langchain langchain-google-genai google-generativeai
```

---

## How to Run

1. **Set Your Gemini API Key**

   * Get your API Key from [Google AI Studio](https://aistudio.google.com/app/apikey)
   * Replace the placeholder in `main.py`:

     ```python
     GOOGLE_API_KEY = "YOUR_API_KEY_HERE"
     ```
   * Pilih model yang tersedia dari hasil list model di akunmu (misal: `models/gemini-2.0-flash`).

2. **Start the FastAPI App**

   ```bash
   uvicorn main:app --reload
   ```

3. **Test the Endpoint**

   * Open your browser and go to: [http://127.0.0.1:8000/docs](http://127.0.0.1:8000/docs)

   * You will see the automatic Swagger UI documentation.

   * Try out the `/recommend` endpoint using this example request:

     ```json
     {
       "gender": "female",
       "age": 62,
       "symptoms": ["pusing", "mual", "sulit berjalan"]
     }
     ```

   * Example response:

     ```json
     {
       "recommended_department": "Neurology"
     }
     ```

4. **Alternative: Test via curl**

   ```bash
   curl -X POST "http://127.0.0.1:8000/recommend" \
        -H "accept: application/json" \
        -H "Content-Type: application/json" \
        -d '{"gender": "female", "age": 62, "symptoms": ["pusing", "mual", "sulit berjalan"]}'
   ```

---

## File Structure

```
.
├── main.py
├── requirements.txt
└── README.md
```

---

## Notes

* Ensure your API key is kept private.
* Free tier quotas for Gemini API may apply. Check your [quota here](https://aistudio.google.com/app/quota).
* The model name must match the models available in your API key access (use the provided list\_models.py script to check).
* This app is for demo/prototype purposes.

---

## Credits

* [FastAPI](https://fastapi.tiangolo.com/)
* [Langchain](https://python.langchain.com/)
* [Google Gemini API](https://ai.google.dev/)
