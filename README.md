# Tricycle Pathways Prototype

This is a lightweight clickable prototype for the `Pathways` concept.

## Run locally

From this folder:

```bash
python3 -m http.server 4173
```

Then open:

```text
http://localhost:4173
```

## What it does

- Runs a 6-question onboarding quiz
- Scores responses across 5 Tricycle pathways
- Shows a personalized result page
- Shows a `Week 1` email preview
- Saves result data locally or posts it to Google Sheets

## Useful preview URLs

You can jump straight to a result or email preview during class:

```text
http://localhost:4173/?screen=quiz&q=3
http://localhost:4173/?screen=result&path=creativity
http://localhost:4173/?screen=email&path=foundations
```

## Connect to Google Sheets

1. Create a Google Sheet.
2. Open `Extensions -> Apps Script`.
3. Paste a simple web app script that accepts JSON and appends rows.
4. Deploy it as a web app with access set so the browser can post to it.
5. Paste that web app URL into `config.js`:

```js
window.TRICYCLE_CONFIG = {
  sheetEndpoint: "YOUR_APPS_SCRIPT_WEB_APP_URL"
};
```

## Expected payload

The prototype sends:

- `timestamp`
- `name`
- `email`
- `pathwayKey`
- `pathwayTitle`
- `scores`
- `answers[]`

If no webhook is configured, results are stored in `localStorage` under:

```text
tricyclePrototypeResults
```
