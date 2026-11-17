# Arcanum

Ein Theme für Home Assistant wie aus einer alten Zauberschule: Pergament, Kerzenlicht, gealtertes Gold und tiefe Farben. Dunkel und Hell stecken in einer Datei; Home Assistant wählt den Modus nach der Einstellung im Benutzerprofil.

- **Nacht** (dunkel): dunkles Gewölbe, warmes Kerzenlicht von oben, Text in Pergamentfarbe
- **Pergament** (hell): Papierstruktur, Text in Tintenbraun
- Vier Farbvarianten, jeweils Akzent plus Metall:
  - **Arcanum**: Karmesin mit altem Gold
  - **Arcanum Smaragd**: tiefes Grün mit Silber
  - **Arcanum Saphir**: Nachtblau mit Bronze
  - **Arcanum Bernstein**: Honiggelb mit Tintenschwarz
- Überschriften in Cinzel, Text in EB Garamond (beide frei, SIL Open Font License)
- Optional: schwebende Kerzen, glimmende Kacheln und Überschriften wie frische Tinte mit [card-mod](https://github.com/thomasloven/lovelace-card-mod)

Das Theme ist ein eigenständiger Entwurf. Es enthält keine Namen, Wappen, Logos oder Figuren aus Büchern oder Filmen.

## Installation über HACS

1. HACS öffnen, oben rechts das Menü und **Benutzerdefinierte Repositories** wählen.
2. `https://github.com/PixelDevIO/HA-Arcanum-Theme` mit der Kategorie **Theme** hinzufügen.
3. **Arcanum** herunterladen.
4. In der `configuration.yaml` müssen Themes aus dem Ordner `themes` geladen werden (bei den meisten Installationen schon vorhanden):

   ```yaml
   frontend:
     themes: !include_dir_merge_named themes
   ```

5. Die Aktion `frontend.reload_themes` ausführen (oder Home Assistant neu starten).
6. Im Benutzerprofil unter **Design** eine der vier Varianten wählen.

## Schriften (empfohlen)

Home Assistant kann Schriften nicht aus einem Theme laden. Damit Cinzel und EB Garamond erscheinen, eine Dashboard-Ressource anlegen:

1. **Einstellungen → Dashboards → ⋮ → Ressourcen → Ressource hinzufügen**
2. URL:

   ```
   https://fonts.googleapis.com/css2?family=Cinzel:wght@500;600;700&family=EB+Garamond:ital,wght@0,400;0,500;0,600;1,400&display=swap
   ```

3. Typ: **Stylesheet**
4. Browser bzw. App neu laden.

Ohne die Ressource fällt das Theme auf Georgia bzw. die Serifenschrift des Systems zurück. Die Schriften werden dann von Google geladen; wer das nicht möchte, lässt diesen Schritt weg.

## Animationen (optional)

Damit Home Assistant die Animationen anwendet, wird **card-mod** gebraucht:

1. In HACS nach **card-mod** suchen (`thomasloven/lovelace-card-mod`) und installieren.
2. Den Browser bzw. die App neu laden.

Ohne card-mod sieht das Theme genauso aus, nur ohne Bewegung und ohne Kerzen in der Kopfzeile.

Was animiert wird:

- Schwebende Kerzen mit flackernden Flammen in der Kopfzeile des Dashboards (im Bearbeitungsmodus ausgeblendet)
- Aktive Kacheln (Licht an, Tür verriegelt, Gerät läuft) glimmen sanft wie Kerzenlicht
- Kartenüberschriften laufen beim Laden wie frische Tinte ins Bild
- Karten, Badges und Ansichtswechsel blenden weich ein
- Farbwechsel bei Ein/Aus laufen sanft statt hart
- Goldstaub schwebt langsam durch den Hintergrund (geht auch ohne card-mod)

## Bubble Card

Wer [Bubble Card](https://github.com/Clooos/Bubble-Card) nutzt, bekommt das Theme auch dort:

- Feine Goldrahmen mit innerer Zierlinie, Ecken wie Buchseiten statt Pillenform
- Runde Symbole mit Goldring; eingeschaltete Geräte glimmen wie Kerzenlicht
- Trenner mit Cinzel-Titel und goldener Linie mit funkelndem Stern
- Pop-ups in Nacht- bzw. Pergamentfarbe

Farben aus eigenen `styles:` einzelner Karten bleiben erhalten. Rahmen und Farben kommen über Theme-Variablen; Glimmen, Zierlinie und Trenner brauchen card-mod.

Karten werden nie mit `transform` bewegt, nur Deckkraft, Farben, Schatten und Masken. So bleiben Pop-ups mit fester Position (z. B. bubble-card) unberührt.

Wer im Betriebssystem **Bewegung reduzieren** eingestellt hat, bekommt keine Animationen; die Kerzen stehen dann still.

## Eigene Anpassungen

Neben den üblichen Home-Assistant-Variablen bringt das Theme eigene mit, die sich in eigenen Karten nutzen lassen:

| Variable | Bedeutung |
| --- | --- |
| `--arc-metal`, `--rgb-arc-metal` | Metallton der Variante (Gold, Silber, Bronze, Tinte) |
| `--arc-glow` | Kerzenschein für aktive Elemente |
| `--arc-duration`, `--arc-duration-fast`, `--arc-ease` | Dauer und Kurve der Übergänge |

## Lizenz

MIT
