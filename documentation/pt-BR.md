# cBioPortal: mutações em coorte pública

Coorte TCGA PanCancer de câncer de mama, genoma hg19. Até 5 genes e 25 registros por página. Contagens da página não são prevalência da coorte. Não inclui interpretação terapêutica.

## Escopo

Análise computacional para pesquisa. Não determina diagnóstico, patogenicidade, eficácia ou tratamento. Confira população, fonte, versão e escopo antes de interpretar.

Interface e contratos implementados na ELUCENIA. A análise depende da disponibilidade do serviço responsável. Revisão clínica independente e revisão linguística profissional não concluídas.

## Consulta

- Símbolos dos genes
- Página
- Confirmo que enviarei somente dados públicos ou sintéticos de pesquisa, sem dados de pacientes ou dados confidenciais.

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

Nomes oficiais de termos e identificadores científicos são preservados no idioma da fonte; os rótulos da interface estão traduzidos.

## Resultados

- Gene
- Identificador público da amostra
- Alteração proteica
- Tipo de mutação
- Cromossomo
- Posição genômica
- Alelo de referência
- Alelo alternativo
- Registros nesta página
- Amostras distintas nesta página

A exportação conserva fontes, atribuição, versões e limites. Dados de origem mantêm sua licença.

## Versão

`cBioPortal v7.1.2 · brca_tcga_pan_can_atlas_2018 · hg19`

## Fontes

Dados cBioPortal sob ODbL 1.0, salvo exceção específica do estudo. Preserve a atribuição ao cBioPortal e à TCGA. A redistribuição de uma base derivada exige conferir as obrigações da licença.

- [https://docs.cbioportal.org/web-api-and-clients/](https://docs.cbioportal.org/web-api-and-clients/)
- [https://docs.cbioportal.org/user-guide/faq/](https://docs.cbioportal.org/user-guide/faq/)
- [https://www.cbioportal.org/api/v3/api-docs](https://www.cbioportal.org/api/v3/api-docs)
- [https://gdc.cancer.gov/about-data/publications/pancanatlas](https://gdc.cancer.gov/about-data/publications/pancanatlas)

## Limites de espera

Cada requisição a este provedor tem limite de 20 segundos. O fluxo completo tem limite de 120 segundos; a interface espera no máximo 125 segundos. Os pedidos compartilham o tempo restante do fluxo. Não há repetição automática. Se o provedor não responder a tempo, a análise termina com um erro explícito; nenhum resultado é estimado ou substituído.
