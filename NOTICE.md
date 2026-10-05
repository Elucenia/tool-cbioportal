## cBioPortal / TCGA data

The official FAQ supplies an ODbL default, with explicit exceptions per study. The checked public BRCA TCGA PanCancer study has no commercial-use exception in its returned metadata. The bundled response extract is public, de-identified research data from that study, attributed to cBioPortal and TCGA. Its ODbL obligations are separate from the MIT adapter license. This extract and any derivative database created from it remain under ODbL 1.0; retain the notice, attribution and license URI. Bulk redistribution or a derivative database requires satisfying the ODbL database/source-access terms. We do not claim an unconditional MIT grant over provider data.

ODbL 1.0: https://opendatacommons.org/licenses/odbl/1-0/
TCGA PanCancer Atlas: https://gdc.cancer.gov/about-data/publications/pancanatlas
cBioPortal source/citation policy: https://docs.cbioportal.org/user-guide/faq/

Use study brca_tcga_pan_can_atlas_2018, profile brca_tcga_pan_can_atlas_2018_mutations, sequenced sample list brca_tcga_pan_can_atlas_2018_sequenced, hg19 only. This workflow reads somatic mutations; it does not retrieve clinical attributes or licensed OncoKB/AACR/private cohorts. Page counts are not cohort prevalence.
