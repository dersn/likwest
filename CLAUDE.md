# dersn/likwest

Öffentlicher Meldungs-Tracker für **Musaic Studio**, **Videcho Studio** und
**IPTV Pano**. README, Issue-Formulare, Bilder. Sonst nichts.

## Die eine Regel

> **Hier wird niemals Quellcode committet. Nie.**

Die Apps sind closed-source. Ihr Code lebt im **privaten** `dersn/platform`.
Dieses Repo ist öffentlich, und öffentlich ist endgültig: ein Push lässt sich
zurücknehmen, eine Veröffentlichung nicht. Sobald eine Datei hier war, haben
GitHub-Events, Forks, Suchmaschinen und Crawler sie — ein `force-push` holt
nichts davon zurück. Bei einem Versehen ist die Reihenfolge deshalb: erst
alles rotieren, was in der Datei stand, dann die Historie umschreiben.

Erlaubt ist ausschließlich:

| Pfad | Wofür |
|---|---|
| `README.md` · `CLAUDE.md` · `LICENSE` · `.gitignore` | die Startseite und diese Regeln |
| `.github/ISSUE_TEMPLATE/*.yml` · `.github/*.md` | Melde-Formulare, PR-Vorlage |
| `.github/workflows/*.yml` | Prüfungen für dieses Repo |
| `.githooks/*` | der Haken, der die Regel durchsetzt |
| `assets/*.{png,svg,jpg,webp}` | Logo und App-Icons |

Eine **Positivliste**, keine Sperrliste. Was nicht ausdrücklich dasteht, ist
verboten — eine Sperrliste vergisst immer eine Dateiendung.

Durchgesetzt an zwei Stellen: lokal `.githooks/pre-commit` (aktiv über
`git config core.hooksPath .githooks`, einmal pro Klon), und serverseitig
`.github/workflows/no-code.yml`, das jeden Push prüft — auch einen über die
Weboberfläche, an dem der lokale Haken vorbeigeht.

## Was in ein Issue gehört

Es liest ein **Nutzer**, kein Entwickler. Also:

- **Seine Worte, nicht unsere.** Was er merkt, nicht was im Code passiert.
  Keine Dateipfade, keine Klassennamen, keine Spec-Nummern.
- **Nichts aus dem privaten Repo verlinken.** Keine Commit-Hashes, keine
  Cross-Repo-Referenzen. Der Bezug zum Fix ist ein Satz im
  Abschluss-Kommentar: „behoben, kommt mit 1.4.3".
- **Nichts Ungebautes versprechen.** Eine Idee bleibt eine Idee, bis sie
  ausgeliefert ist.
- **Nie fremde Zugangsdaten weiterreichen.** Taucht in einer Meldung eine
  M3U-/Xtream-URL auf, ist sie kompromittiert. Löschen genügt nicht — den
  Nutzer bitten, die Zugangsdaten beim Anbieter zu wechseln.

Gepflegt wird vom privaten Repo aus:

```bash
scripts/likwest-issue.sh search "export audio"
scripts/likwest-issue.sh new --app musaic --title "…" --body "…"
scripts/likwest-issue.sh done 12 --version 1.4.3 --note "…"
```

Ohne `--yes` zeigt das Skript nur den Entwurf. Jeder Eintrag ist eine
öffentliche Webseite — wer sie verfasst, gibt sie nicht selbst frei.

## Pull Requests

Lassen sich bei GitHub nicht abschalten; `allow_forking=false` greift nur bei
org-eigenen privaten Repos. Schreibrechte hat nur `dersn`, gemerged wird also
nichts von außen. `.github/PULL_REQUEST_TEMPLATE.md` leitet zu den Issues.
