# Salespage Generator – Vercel Deployment

## Ordnerstruktur

```
salespage-generator/
├── index.html        ← Das komplette Frontend
├── api/
│   └── generate.js   ← Serverless Function (API-Proxy)
├── vercel.json       ← Vercel-Konfiguration
└── README.md         ← Diese Datei
```

---

## Schritt-für-Schritt: Auf Vercel deployen

### Schritt 1 – Vercel Account erstellen
1. Gehe zu [vercel.com](https://vercel.com)
2. Klicke auf **"Sign Up"**
3. Registriere dich mit deiner E-Mail-Adresse

### Schritt 2 – Neues Projekt anlegen
1. Im Dashboard oben rechts auf **"Add New → Project"** klicken
2. Wähle **"Deploy without Git"** (kein GitHub nötig!)
3. Ziehe den gesamten Ordner `salespage-generator/` in das Upload-Feld

### Schritt 3 – Environment Variable setzen (API-Key)
**Das ist der wichtigste Schritt!**

1. Vor dem Deploy erscheint ein Formular – dort **"Environment Variables"** aufklappen
2. Klicke auf **"Add"**
3. Trage ein:
   - **Name:** `ANTHROPIC_API_KEY`
   - **Value:** `sk-ant-api03-...` (dein API-Key von console.anthropic.com)
4. Auf **"Add"** klicken

### Schritt 4 – Deployen
1. Klicke auf **"Deploy"**
2. Warten (~30 Sekunden)
3. Fertig! Du bekommst eine URL wie: `https://salespage-generator-xyz.vercel.app`

---

## API-Key holen (falls noch keiner vorhanden)

1. Gehe zu [console.anthropic.com](https://console.anthropic.com)
2. Links im Menü: **"API Keys"**
3. Klicke auf **"Create Key"**
4. Den Key kopieren und sicher aufbewahren (wird nur einmal angezeigt!)

---

## Nach dem Deployment

### Eigene Domain verbinden (optional)
1. Im Vercel-Dashboard → dein Projekt → **"Settings → Domains"**
2. Eigene Domain eintragen, z.B. `salespage.dein-name.de`
3. DNS-Eintrag beim Domain-Anbieter setzen (Vercel zeigt dir genau was)

### Environment Variable nachträglich ändern
1. Vercel Dashboard → Projekt → **"Settings → Environment Variables"**
2. Variable anklicken → Wert ändern → **"Save"**
3. Dann **"Deployments → Redeploy"** anklicken (damit der neue Key aktiv wird)

---

## Troubleshooting

**"API-Fehler" auf der Seite?**
→ API-Key prüfen: Vercel Dashboard → Settings → Environment Variables

**Seite lädt nicht?**
→ Vercel Dashboard → Deployments → auf den letzten Deployment klicken → Logs ansehen

**"Method not allowed"?**
→ vercel.json ist falsch platziert – muss im Hauptordner liegen, nicht in einem Unterordner

---

## Kosten

- **Vercel:** kostenlos für bis zu 100.000 Requests/Monat (Hobby Plan)
- **Anthropic API:** ca. 0,003 € pro generierte Salespage (Claude Sonnet)
