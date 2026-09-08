# Astra signieren – Web-App (iPhone / Windows / überall)

Eine kleine, komplett **offline** laufende Web-App, mit der du PDFs mit deinem
Astra-Signaturschlüssel signieren und prüfen kannst – ohne Astra, ohne Server,
ohne dass irgendetwas hochgeladen wird. Gleiche `%%ASTRA-SIG`-Signatur wie Astra,
prüfbar im Signatur-Werkzeug von Astra und umgekehrt.

Dateien: `index.html`, `sw.js`, `manifest.webmanifest` – mehr braucht es nicht.

## 1. Schlüssel aus Astra holen

Astra → **Signatur-Werkzeug** → „Schlüssel sichern …", Passwort vergeben.
Es entsteht eine Datei `astra-signaturschluessel.astrakey`. Diese Datei plus das
Passwort brauchst du auf dem anderen Gerät.

## 2a. Als App aufs iPhone (empfohlen)

Dafür muss die Seite einmal über **https** erreichbar sein – am einfachsten kostenlos
über GitHub Pages (kein Server, keine Wartung):

1. Neues öffentliches GitHub-Repo anlegen, z. B. `astra-sign`.
2. Die drei Dateien aus diesem Ordner ins Repo laden (Web-Oberfläche: „Add file → Upload files").
3. Repo → **Settings → Pages** → „Branch: `main`, Ordner `/root`" → Save.
   Nach ein, zwei Minuten gibt es eine URL wie
   `https://DEINNAME.github.io/astra-sign/`.
4. Diese URL auf dem iPhone in **Safari** öffnen → Teilen-Symbol →
   **„Zum Home-Bildschirm"**. Jetzt hast du „Signieren" als App-Icon,
   startet im Vollbild und funktioniert danach auch offline.
5. In der App Tab **Schlüssel** → `.astrakey`-Datei wählen (oder Text einfügen),
   Passwort eingeben → „Schlüssel übernehmen". Der Schlüssel bleibt nur auf dem iPhone.

Alternativen zu GitHub Pages (auch kostenlos, kein Server): Cloudflare Pages,
Netlify Drop (Datei-Ordner einfach auf die Seite ziehen).

## 2b. Windows-PC ohne alles

`index.html` einfach doppelklicken – öffnet im Browser und funktioniert
(auch das Signieren, weil Browser lokale Dateien als „sicher" behandeln).
Nur die Installation als echte App/Offline-Cache braucht die https-Variante von oben.

## Nutzung

- **Signieren**: Tab „Signieren" → PDF wählen → „Sichern / Teilen" (iPhone: geht in die
  Dateien-App oder direkt weiter per Teilen-Menü).
- **Prüfen**: Tab „Prüfen" → PDF wählen. Zeigt „dein Schlüssel" / „anderer Schlüssel" /
  „nachträglich verändert" / „ungültig" / „keine Signatur" plus Kennung und Datum.

## Sicherheit

Der private Schlüssel liegt verschlüsselt in der `.astrakey`-Datei und nach dem Import
unverschlüsselt im lokalen Speicher des jeweiligen Browsers/Geräts. Er verlässt das
Gerät nie. Wer Zugriff auf ein Gerät mit importiertem Schlüssel hat, kann in deinem
Namen signieren – behandle die Datei und das Passwort entsprechend.
