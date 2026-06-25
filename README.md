# Pokémon-Go-Tradeliste — iOS-App (Sideloading via Signulous)

Verpackt die Web-App (`www/index.html`) mit **Capacitor** in eine iOS-WebView-App.
**GitHub Actions** baut auf einem Cloud-Mac automatisch eine **unsignierte `.ipa`**.
Diese `.ipa` gibst du in **Signulous** ein (Datei oder URL) → Signulous signiert & installiert sie aufs iPhone.

## Einmal einrichten

### 1. Repo auf GitHub anlegen
- Auf github.com → **New repository** → Name z. B. `pogo-tradeliste-app`.
- **Wichtig: „Public"** wählen, wenn Signulous die IPA per **URL** laden soll
  (Release-Dateien in privaten Repos sind ohne Login nicht abrufbar).
  Alternativ „Private" und die IPA-Datei später manuell in Signulous hochladen.
- **Keine** README/gitignore von GitHub hinzufügen (ist schon hier drin).

### 2. Dieses Projekt hochpushen
Im Ordner dieses Projekts (Terminal/PowerShell):

```
git remote add origin https://github.com/<DEIN-NUTZER>/pogo-tradeliste-app.git
git push -u origin main
```

### 3. Build läuft automatisch
- GitHub → Tab **Actions** → Workflow **„Build unsigned iOS IPA"** läuft (~5–10 Min).
- Danach: Tab **Releases** → Release **„latest"** enthält **`Tradeliste.ipa`**.
- Feste Download-URL (für Signulous):
  ```
  https://github.com/<DEIN-NUTZER>/pogo-tradeliste-app/releases/download/latest/Tradeliste.ipa
  ```

### 4. In Signulous installieren
- IPA-**URL** einfügen **oder** die `.ipa` herunterladen und als **Datei** hochladen.
- Signieren lassen → aufs iPhone installieren. Fertig.

## App aktualisieren
HTML in `www/index.html` ändern → committen → `git push`.
Actions baut automatisch eine neue `Tradeliste.ipa` unter derselben URL.
In Signulous neu signieren/installieren.

## Hinweise
- Die App läuft **offline** (HTML ist eingebettet); Daten speichert das iPhone lokal (localStorage).
- Der iOS-App-Ordner (`ios/`) wird in der Cloud erzeugt und ist bewusst **nicht** eingecheckt.
- Eigenes App-Icon können wir später ergänzen (aktuell Capacitor-Standard-Icon).
