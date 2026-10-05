# cBioPortal: mutaciones en una cohorte pública

Cohorte TCGA PanCancer de cáncer de mama, hg19. Hasta 5 genes y 25 registros por página. Los recuentos de página no son prevalencia de la cohorte. No incluye interpretación terapéutica.

## Alcance

Análisis computacional para investigación. No establece diagnóstico, patogenicidad, eficacia ni tratamiento. Revise población, fuente, versión y alcance antes de interpretar.

Interfaz y contratos implementados en ELUCENIA. El análisis depende de la disponibilidad del servicio responsable. No se han completado la revisión clínica independiente ni la revisión lingüística profesional.

## Consulta

- Símbolos de genes
- Página
- Confirmo que enviaré solo datos públicos o sintéticos de investigación, sin datos de pacientes ni información confidencial.

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

Los nombres oficiales de términos e identificadores científicos conservan el idioma de la fuente; las etiquetas de interfaz están traducidas.

## Resultados

- Gen
- Identificador público de muestra
- Cambio proteico
- Tipo de mutación
- Cromosoma
- Posición genómica
- Alelo de referencia
- Alelo alternativo
- Registros en esta página
- Muestras distintas en esta página

La exportación conserva fuentes, atribución, versiones y límites. Los datos de origen mantienen su licencia.

## Versión

`cBioPortal v7.1.2 · brca_tcga_pan_can_atlas_2018 · hg19`

## Fuentes

Los datos de cBioPortal usan ODbL 1.0, salvo una excepción específica del estudio. Conserve la atribución a cBioPortal y TCGA. Redistribuir una base derivada requiere comprobar las obligaciones de la licencia.

- [https://docs.cbioportal.org/web-api-and-clients/](https://docs.cbioportal.org/web-api-and-clients/)
- [https://docs.cbioportal.org/user-guide/faq/](https://docs.cbioportal.org/user-guide/faq/)
- [https://www.cbioportal.org/api/v3/api-docs](https://www.cbioportal.org/api/v3/api-docs)
- [https://gdc.cancer.gov/about-data/publications/pancanatlas](https://gdc.cancer.gov/about-data/publications/pancanatlas)

## Límites de espera

Cada solicitud a este proveedor tiene un límite de 20 segundos. El flujo completo tiene un límite de 120 segundos; la interfaz espera como máximo 125 segundos. Las solicitudes comparten el tiempo restante del flujo. No hay reintentos automáticos. Si el proveedor no responde a tiempo, el análisis termina con un error explícito; no se estima ni se sustituye ningún resultado.
