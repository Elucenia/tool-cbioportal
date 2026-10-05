# cBioPortal: public-cohort mutations

TCGA PanCancer breast cancer cohort, hg19. Up to 5 genes and 25 rows per page. Page counts are not cohort prevalence. No therapeutic interpretation is included.

## Scope

Computational research analysis. It does not establish diagnosis, pathogenicity, efficacy or treatment. Check population, provenance, version and scope before interpreting.

Interface and contracts implemented on ELUCENIA. Analysis depends on the responsible service being available. Independent clinical review and professional language review are incomplete.

## Query

- Gene symbols
- Page
- I confirm that I will submit only public or synthetic research data, without patient or confidential data.

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

Official term names and scientific identifiers retain the source language; interface labels are translated.

## Results

- Gene
- Public sample identifier
- Protein change
- Mutation type
- Chromosome
- Genomic position
- Reference allele
- Alternate allele
- Rows on this page
- Distinct samples on this page

Export preserves sources, attribution, versions and limitations. Source data retain their license.

## Version

`cBioPortal v7.1.2 · brca_tcga_pan_can_atlas_2018 · hg19`

## Sources

cBioPortal data use ODbL 1.0 unless a study-specific exception applies. Preserve cBioPortal and TCGA attribution. Redistributing a derived database requires checking the license obligations.

- [https://docs.cbioportal.org/web-api-and-clients/](https://docs.cbioportal.org/web-api-and-clients/)
- [https://docs.cbioportal.org/user-guide/faq/](https://docs.cbioportal.org/user-guide/faq/)
- [https://www.cbioportal.org/api/v3/api-docs](https://www.cbioportal.org/api/v3/api-docs)
- [https://gdc.cancer.gov/about-data/publications/pancanatlas](https://gdc.cancer.gov/about-data/publications/pancanatlas)

## Waiting limits

Each request to this provider has a 20-second limit. The complete workflow has a 120-second limit; the interface waits at most 125 seconds. Requests share the workflow’s remaining time. There is no automatic retry. If the provider does not respond in time, analysis ends with an explicit error; no result is estimated or substituted.
