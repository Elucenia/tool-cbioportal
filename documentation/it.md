# cBioPortal: mutazioni in una coorte pubblica

Coorte TCGA PanCancer del tumore mammario, hg19. Fino a 5 geni e 25 righe per pagina. I conteggi di pagina non sono la prevalenza della coorte. Nessuna interpretazione terapeutica.

## Ambito

Analisi computazionale per ricerca. Non determina diagnosi, patogenicità, efficacia o trattamento. Verifica popolazione, fonte, versione e ambito prima di interpretare.

Interfaccia e contratti implementati in ELUCENIA. L’analisi dipende dalla disponibilità del servizio responsabile. La revisione clinica indipendente e la revisione linguistica professionale non sono complete.

## Ricerca

- Simboli dei geni
- Pagina
- Confermo che invierò solo dati di ricerca pubblici o sintetici, senza dati di pazienti o informazioni riservate.

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

I nomi ufficiali dei termini e gli identificatori scientifici conservano la lingua della fonte; le etichette dell’interfaccia sono tradotte.

## Risultati

- Gene
- Identificativo pubblico del campione
- Variazione proteica
- Tipo di mutazione
- Cromosoma
- Posizione genomica
- Allele di riferimento
- Allele alternativo
- Righe in questa pagina
- Campioni distinti in questa pagina

L’esportazione conserva fonti, attribuzione, versioni e limiti. I dati originali mantengono la propria licenza.

## Versione

`cBioPortal v7.1.2 · brca_tcga_pan_can_atlas_2018 · hg19`

## Fonti

I dati cBioPortal usano ODbL 1.0, salvo eccezioni specifiche dello studio. Conservare l’attribuzione a cBioPortal e TCGA. La redistribuzione di una banca dati derivata richiede la verifica degli obblighi della licenza.

- [https://docs.cbioportal.org/web-api-and-clients/](https://docs.cbioportal.org/web-api-and-clients/)
- [https://docs.cbioportal.org/user-guide/faq/](https://docs.cbioportal.org/user-guide/faq/)
- [https://www.cbioportal.org/api/v3/api-docs](https://www.cbioportal.org/api/v3/api-docs)
- [https://gdc.cancer.gov/about-data/publications/pancanatlas](https://gdc.cancer.gov/about-data/publications/pancanatlas)

## Limiti di attesa

Ogni richiesta a questo fornitore ha un limite di 20 secondi. Il flusso completo ha un limite di 120 secondi; l’interfaccia attende al massimo 125 secondi. Le richieste condividono il tempo rimanente del flusso. Non sono previsti tentativi automatici. Se il fornitore non risponde in tempo, l’analisi termina con un errore esplicito; nessun risultato viene stimato o sostituito.
