# cBioPortal: Mutationen einer öffentlichen Kohorte

TCGA-PanCancer-Brustkrebskohorte, hg19. Bis zu 5 Gene und 25 Zeilen pro Seite. Seitenzahlen sind keine Kohortenprävalenz. Keine therapeutische Interpretation.

## Umfang

Computergestützte Forschungsanalyse. Sie begründet keine Diagnose, Pathogenität, Wirksamkeit oder Behandlung. Prüfen Sie Population, Herkunft, Version und Umfang vor der Interpretation.

Oberfläche und Schnittstellenverträge sind in ELUCENIA implementiert. Die Analyse hängt von der Verfügbarkeit des zuständigen Dienstes ab. Die unabhängige klinische Prüfung und die professionelle sprachliche Prüfung sind nicht abgeschlossen.

## Abfrage

- Gensymbole
- Seite
- Ich bestätige, dass ich ausschließlich öffentliche oder synthetische Forschungsdaten ohne Patienten- oder vertrauliche Daten übermittle.

```json
{
  "$schema": "https://json-schema.org/draft/2020-12/schema",
  "type": "object",
  "properties": {
    "genes": {
      "type": "array",
      "items": {
        "type": "string",
        "pattern": "^[A-Za-z0-9][A-Za-z0-9.-]{0,31}$"
      },
      "minItems": 1,
      "maxItems": 5,
      "uniqueItems": true
    },
    "page": {
      "type": "integer",
      "minimum": 1,
      "maximum": 100
    },
    "publicResearchData": {
      "const": true,
      "description": "Only public or synthetic research inputs; no patient/confidential data."
    }
  },
  "required": [
    "genes",
    "page",
    "publicResearchData"
  ],
  "additionalProperties": false
}
```

Offizielle Begriffsnamen und wissenschaftliche Kennungen bleiben in der Quellsprache; die Oberflächenbeschriftungen sind übersetzt.

## Ergebnisse

- Gen
- Öffentliche Probenkennung
- Proteinveränderung
- Mutationstyp
- Chromosom
- Genomische Position
- Referenzallel
- Alternatives Allel
- Zeilen auf dieser Seite
- Verschiedene Proben auf dieser Seite

Der Export erhält Quellen, Attribution, Versionen und Grenzen. Quelldaten behalten ihre Lizenz.

## Version

`cBioPortal v7.1.2 · brca_tcga_pan_can_atlas_2018 · hg19`

## Quellen

cBioPortal-Daten unterliegen ODbL 1.0, sofern keine studienspezifische Ausnahme gilt. Die Quellenangaben zu cBioPortal und TCGA müssen erhalten bleiben. Bei Weitergabe einer abgeleiteten Datenbank sind die Lizenzpflichten zu prüfen.

- [https://docs.cbioportal.org/web-api-and-clients/](https://docs.cbioportal.org/web-api-and-clients/)
- [https://docs.cbioportal.org/user-guide/faq/](https://docs.cbioportal.org/user-guide/faq/)
- [https://www.cbioportal.org/api/v3/api-docs](https://www.cbioportal.org/api/v3/api-docs)
- [https://gdc.cancer.gov/about-data/publications/pancanatlas](https://gdc.cancer.gov/about-data/publications/pancanatlas)

## Wartezeitbegrenzungen

Jede Anfrage an diesen Anbieter ist auf 20 Sekunden begrenzt. Der gesamte Ablauf ist auf 120 Sekunden begrenzt; die Oberfläche wartet höchstens 125 Sekunden. Die Anfragen teilen sich die verbleibende Zeit des Ablaufs. Es gibt keine automatische Wiederholung. Antwortet der Anbieter nicht rechtzeitig, endet die Analyse mit einer ausdrücklichen Fehlermeldung; es wird kein Ergebnis geschätzt oder ersetzt.
