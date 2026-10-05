# cBioPortal : mutations d’une cohorte publique

Cohorte TCGA PanCancer du cancer du sein, hg19. Jusqu’à 5 gènes et 25 lignes par page. Les nombres par page ne sont pas une prévalence de cohorte. Aucune interprétation thérapeutique.

## Périmètre

Analyse informatique pour la recherche. Elle ne détermine ni diagnostic, ni pathogénicité, ni efficacité, ni traitement. Vérifiez population, source, version et périmètre avant interprétation.

Interface et contrats implémentés dans ELUCENIA. L’analyse dépend de la disponibilité du service responsable. La révision clinique indépendante et la révision linguistique professionnelle ne sont pas achevées.

## Requête

- Symboles des gènes
- Page
- Je confirme que je transmettrai uniquement des données de recherche publiques ou synthétiques, sans données de patients ni données confidentielles.

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

Les noms officiels des termes et identifiants scientifiques conservent la langue de la source ; les libellés de l’interface sont traduits.

## Résultats

- Gène
- Identifiant public d’échantillon
- Modification protéique
- Type de mutation
- Chromosome
- Position génomique
- Allèle de référence
- Allèle alternatif
- Lignes sur cette page
- Échantillons distincts sur cette page

L’export conserve les sources, l’attribution, les versions et les limites. Les données sources conservent leur licence.

## Version

`cBioPortal v7.1.2 · brca_tcga_pan_can_atlas_2018 · hg19`

## Sources

Les données cBioPortal utilisent ODbL 1.0, sauf exception propre à une étude. Conservez l’attribution à cBioPortal et à TCGA. La redistribution d’une base dérivée exige de vérifier les obligations de la licence.

- [https://docs.cbioportal.org/web-api-and-clients/](https://docs.cbioportal.org/web-api-and-clients/)
- [https://docs.cbioportal.org/user-guide/faq/](https://docs.cbioportal.org/user-guide/faq/)
- [https://www.cbioportal.org/api/v3/api-docs](https://www.cbioportal.org/api/v3/api-docs)
- [https://gdc.cancer.gov/about-data/publications/pancanatlas](https://gdc.cancer.gov/about-data/publications/pancanatlas)

## Limites d’attente

Chaque requête à ce fournisseur est limitée à 20 secondes. Le traitement complet est limité à 120 secondes ; l’interface attend au maximum 125 secondes. Les requêtes partagent le temps restant du traitement. Aucune nouvelle tentative n’est automatique. Si le fournisseur ne répond pas à temps, l’analyse se termine par une erreur explicite ; aucun résultat n’est estimé ni substitué.
