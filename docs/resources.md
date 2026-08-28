# Resources: Further Reading & Tools for Metagenomic Biosurveillance Analysts

## Landmark Papers

### Metagenomic Biosurveillance Foundations
- Woolhouse et al. (2021) — "Human viruses: discovery and emergence" (Phil Trans Royal Society B) — zoonotic emergence epidemiology
- Gardy & Loman (2018) — "Towards a genomics-informed, real-time, global pathogen surveillance system" (Nature Reviews Genetics) — genomic surveillance vision
- Koopmans (2020) — "SARS-CoV-2 and the human-animal interface: outbreaks on mink farms" — One Health surveillance case study

### Wastewater Surveillance
- Medema et al. (2020) — "Presence of SARS-Coronavirus-2 RNA in Sewage and Correlation with Reported COVID-19 Prevalence" — foundational WBE SARS-CoV-2 paper
- Mao et al. (2020) — "Quantitative assessment of the importance of drying time on virus detection from wastewater" — WBE methods

### Novel Pathogen Discovery
- Lipkin (2013) — "The changing face of pathogen discovery and surveillance" (Nature Reviews Microbiology) — metagenomic pathogen discovery
- Rambaut et al. (2020) — SARS-CoV-2 phylogenomic analysis — viral emergence genomics case study

### AMR Surveillance
- Van Boeckel et al. (2019) — "Global trends in antimicrobial resistance in animals in low- and middle-income countries" (Science)

### Clinical Metagenomics
- Miller et al. (2019) — "Laboratory validation of a clinical metagenomic sequencing assay" (Annals of Internal Medicine)
- Wilson et al. (2019) — "Actionable Diagnosis of Neuroleptospirosis by Next-Generation Sequencing" (NEJM) — landmark clinical mNGS case

## Regulatory & Policy Frameworks
- **CDC Select Agent Program regulations** (selectagents.gov)
- **NIH P3CO Framework** for enhanced potential pandemic pathogen research
- **WHO PABS framework** for pathogen access and benefit sharing
- **GISAID Terms of Access** (gisaid.org)
- **MIMARKS/MIxS environmental sequencing reporting standards** (GSC)

## Tools & Software Landscape
| Category | Examples |
|----------|----------|
| Quality control | FastQC, fastp, Trimmomatic, MultiQC |
| Host depletion | Bowtie2, BWA, HISAT2, Kraken2 host DB |
| Taxonomic classification | Kraken2/Bracken, MetaPhlAn4, Kaiju, DIAMOND+MEGAN |
| AMR detection | RGI (CARD), AMRFinderPlus, ResFinder, MEGARes |
| Assembly | MEGAHIT, metaSPAdes, Flye (nanopore) |
| Viral discovery | VirSorter2, VIBRANT, DeepVirFinder, CheckV |
| Phylogenetics | IQ-TREE, RAxML, BEAST2, FastTree |
| Outbreak genomics | Nextstrain, Gubbins, ClonalFrameML, Snippy |
| WBE analysis | RTqPCR pipelines, custom R/Python analysis |
| Visualization | R (ggplot2, phyloseq), Phandango, iTOL |

## Key Databases
| Database | Content |
|----------|---------|
| NCBI RefSeq / GenBank | Primary reference genome database |
| CARD | Antimicrobial resistance genes |
| GISAID | Influenza, SARS-CoV-2, MPX genomic data |
| VIPR / ViralZone | Viral reference sequences |
| NCBI Pathogen Detection | Real-time bacterial genome surveillance |
| Enterobase | Bacterial cgMLST typing |
| PHA4GE | Phylogenomics data sharing standards |

## Roadmap

### v1.0 (July 2026) — Current
- ✅ 12 core topic modules (178+ Q&As)
- ✅ Glossary, resources, contributing guidelines
- ✅ MIT License

### v1.1 (Q3–Q4 2026)
- Expand to 18–20 Q&As per topic
- Add worked pipeline examples (Kraken2 to report, WBE time-series analysis)
- Community feedback incorporation

### v2.0 (Q1 2027)
- Interactive pipeline decision tool
- Video walkthroughs of WBE analysis and outbreak phylogenomics
- Spaced-repetition flashcard export (Anki)

### v2.1 (Q2 2027)
- Multi-language support (Spanish, Mandarin, French, Portuguese, Arabic — reflecting major public health surveillance language communities)

### v2.2 (Q3 2027)
- Specialized tracks: clinical mNGS track; WBE track; global health security track

---

**Last updated:** July 2026
