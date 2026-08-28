# Topic 04: AMR Gene Surveillance

## Overview
Antimicrobial resistance gene detection, resistome analysis, clinical context integration, and the interpretation challenges distinguishing AMR gene presence from clinically-relevant resistance.

---

### Q1: What are the primary bioinformatic approaches for detecting AMR genes in metagenomic data, and what are the critical interpretation limitations?

**A:**
**Detection approaches:**
- **Read-level alignment (DIAMOND/BLAST vs. CARD, ResFinder, ARG-ANNOT, MEGARes):** Fast, sensitive; presence/absence information; no genomic context (which organism, mobile element status)
- **Assembly-based detection:** Annotate assembled contigs for AMR genes; provides genomic context (host organism, flanking mobile elements); requires adequate sequencing depth
- **RGI (CARD's Resistance Gene Identifier):** Perfect/Strict/Loose hit categories based on similarity to curated resistance models; drug class and mechanism annotation
- **AMRFinderPlus (NCBI):** HMMER + BLAST against NDARO; standardized output for CDC/NCBI surveillance reporting
- **ResFinder:** Acquired resistance gene identification by sequence identity

**Critical interpretation limitations:**
1. **Gene presence ≠ expression ≠ phenotypic resistance:** Disrupted or promoter-deficient copies may not confer resistance; metatranscriptomics required for expression evidence
2. **Unknown host organism:** Without assembly context, detected AMR genes cannot be attributed to a specific pathogen — could be in harmless environmental bacteria
3. **Database scheme differences:** CARD, ResFinder, ARG-ANNOT use different classification systems — cross-study comparisons require standardization
4. **Mobile element inflation:** AMR genes on plasmids may be present in many copies per cell, inflating abundance estimates relative to cellular prevalence

---

### Q2: Design a wastewater AMR surveillance program for a 500,000-population city.

**A:**
**Sampling:** 3-4 WWTP influent sites (hospital + residential contributions sampled separately); weekly 24-hour flow-weighted composites; concurrent flow rate measurement for absolute load estimation.

**Priority AMR targets:**
- Carbapenem resistance (KPC, NDM, OXA-48, VIM, IMP) — highest clinical urgency, detectable emergence
- ESBLs (CTX-M-15) — prevalent community-acquired mechanism; background context
- Colistin resistance (mcr genes) — last-resort antibiotic; any detection warrants follow-up
- MRSA proxy (mecA, mecC); VRE (vanA, vanB)

**Trend interpretation:**
- 6-month baseline before anomaly detection is meaningful
- SPC charts: weekly measurements vs. rolling baseline mean ± 3SD
- Hospital-area sites showing new carbapenemase before city-wide increase → healthcare emergence; simultaneous city-wide increase → community acquisition

**Clinical data integration:**
- Link to hospital laboratory AMR surveillance — concordant clinical/WBE increases confirm emerging resistance
- Antibiotic prescription linkage — rising prescription volume predicts AMR enrichment 2-4 weeks later
- Outbreak investigation support — WBE geographic extent assessment when clinical outbreak detected

---

### Q3–Q15: (Additional topics)
- CARD ontology structure and surveillance reporting
- Mobilome analysis (plasmid detection, mobile genetic elements)
- One Health AMR surveillance (human, animal, environmental integration)
- Seasonal resistome dynamics
- Clinical breakpoint-to-genomic-marker relationships
- International AMR surveillance network integration (GLASS, WHO AMR)
- AMR data reporting standards (WHONET, EARS-Net)

---

## Summary
AMR metagenomic surveillance provides powerful population-level resistance gene burden tracking — but the critical interpretation gap between gene detection and clinically-relevant phenotypic resistance requires systematic integration with clinical microbiology data, mobility context assessment, and explicit acknowledgment that environmental resistome data cannot be directly equated to resistance in human pathogens without additional epidemiological evidence.
