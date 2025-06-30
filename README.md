# Vue 3 + TypeScript + Vite

## 🚀 Projekt starten

# Abhängigkeiten installieren

npm install

# Dev Server starten

npm run dev

# Modulares Fragen-Tool

Ein kleines Vue.js-Projekt zur Erstellung und Vorschau modularer Fragen – als Teil eines Bewerbungsprozesses an der Universität Zürich.

## ✨ Projektziel

Das Tool erlaubt das Erstellen unterschiedlicher Fragetypen:

- Ja/Nein-Fragen
- Freitextfragen
- Multiple-Choice-Fragen

Die Fragen können im Editor definiert, als Vorschau angezeigt und lokal gespeichert werden. Ziel ist eine flexible, komponentenbasierte Lösung zur Erfassung von Wunschfragen – z. B. für Veranstaltungen.

## API-Ausblick

Mögliche Weiterentwicklungsideen:
GET /api/questions: Fragt alle bereits erstellten Fragen ab

POST /api/questions: Speichert neue Fragen dauerhaft auf dem Server

PUT /api/questions/:id: Bearbeitet bestehende Fragen

DELETE /api/questions/:id: Entfernt nicht mehr benötigte Fragen

GET /api/events/:id/questions: Fragt Fragen ab, die zu einem bestimmten Event gehören

Diese API könnte von einer Veranstaltungsplattform genutzt werden, um individuelle Wunschfragen pro Event oder Event-Reihe zu definieren, zu speichern und wiederzuverwenden.

# Beispiel: POST /api/questions

{
"type": "multipleChoice",
"text": "Welche Art von Veranstaltung bevorzugen Sie?",
"options": ["Konferenz", "Workshop", "Networking", "Webinar"]
}

# Beispiel: GET /api/questions

[
{
"id": "1",
"type": "yesNo",
"text": "Waren Sie bereits auf einer unserer Veranstaltungen?"
},
{
"id": "2",
"type": "openReply",
"text": "Was erwarten Sie von einem idealen Event?"
}
]
