# Rights and deployment scope

The MIT grant covers only the ELUCENIA-authored adapters, parsers, schemas, labels, test harness, CLI, server and documentation in this package. It does not license any provider algorithm, model binary, logo, third-party annotation, or private ELUCENIA portal/dashboard. No such UI, authentication, database, patient data or credentials are included.

This is a bounded official-API client, not a reimplementation or validation of the complete named provider. The provider computes the prediction/enrichment; our tests check request/response contracts, source identities, numerical formatting and selected consistency assertions. Clinical approval and professional language review have not been performed.

Public/synthetic research inputs only. Requests go to the named provider, and result exports contain the query and attribution. Do not submit identifying, patient or confidential data. The CLI requires an explicit --live option for network use; tests and default offline mode never call providers.

A deterministic provider lock directory is shared by all packages and the website/dashboard under the same OS account on one host: os.homedir()/.elucenia/research-provider-locks. ELUCENIA_RESEARCH_LOCK_DIRECTORY is an optional absolute override; use the same directory for all apps. This is not cross-host distributed coordination. Active PIDs are never evicted only because a lease expired; interrupted uncertain IEDB requests retain a conservative five-minute cooldown.

The standalone server binds only to 127.0.0.1 and has no account/session system. A production proxy must provide separately reviewed authentication, authorization, transport and privacy controls. No private dashboard authentication source is distributed here.

## cBioPortal / TCGA data

The official FAQ supplies an ODbL default, with explicit exceptions per study. The checked public BRCA TCGA PanCancer study has no commercial-use exception in its returned metadata. The bundled response extract is public, de-identified research data from that study, attributed to cBioPortal and TCGA. Its ODbL obligations are separate from the MIT adapter license. This extract and any derivative database created from it remain under ODbL 1.0; retain the notice, attribution and license URI. Bulk redistribution or a derivative database requires satisfying the ODbL database/source-access terms. We do not claim an unconditional MIT grant over provider data.

ODbL 1.0: https://opendatacommons.org/licenses/odbl/1-0/
TCGA PanCancer Atlas: https://gdc.cancer.gov/about-data/publications/pancanatlas
cBioPortal source/citation policy: https://docs.cbioportal.org/user-guide/faq/

Use study brca_tcga_pan_can_atlas_2018, profile brca_tcga_pan_can_atlas_2018_mutations, sequenced sample list brca_tcga_pan_can_atlas_2018_sequenced, hg19 only. This workflow reads somatic mutations; it does not retrieve clinical attributes or licensed OncoKB/AACR/private cohorts. Page counts are not cohort prevalence.
