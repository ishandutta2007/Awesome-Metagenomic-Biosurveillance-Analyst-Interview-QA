# Topic 01: Metagenomic Sequencing Platforms & Library Prep

## Overview
Short-read (Illumina), long-read (Oxford Nanopore), and hybrid strategies; library preparation for shotgun metagenomics versus targeted enrichment; platform-choice decisions shaping biosurveillance capability.

---

### Q1: Compare Illumina and Oxford Nanopore Technology platforms for metagenomic biosurveillance — when does each offer specific advantages?

**A:** **Illumina (short-read):** Very high base accuracy (>Q30); highest throughput per dollar; largest established tool ecosystem; best for minority variant detection (AMR mutations, low-frequency viral variants); standard for large-scale environmental surveillance. Limitations: 2-3 day turnaround; requires centralized infrastructure; PCR amplification bias affects relative abundance estimation.

**Oxford Nanopore (long-read):** Real-time sequencing enabling same-day or same-hour results — critical for acute outbreak response; portable MinION format enables field deployment without centralized infrastructure; long reads dramatically improve de novo assembly of novel viral/bacterial genomes; direct RNA sequencing without reverse transcription. Limitations: Higher per-base error rate (improving rapidly but meaningful for SNP-based phylogenetics); lower throughput per run; higher consumable cost per base at scale.

**Platform selection framework:** Acute outbreak response → Nanopore; large-scale environmental surveillance → Illumina; novel pathogen discovery → hybrid (Nanopore scaffold + Illumina polishing); AMR mutation detection → Illumina.

---

### Q2: What host depletion strategies exist for metagenomic library preparation, and how do their trade-offs affect biosurveillance sensitivity?

**A:** **Saponin-based selective lysis:** Lyses eukaryotic cells while leaving bacteria/viruses intact; effective for cellular clinical samples. **Methylation-based depletion (NEBNext):** Captures CpG-methylated human DNA leaving unmethylated pathogen DNA; doesn't deplete RNA. **Hybridization-based depletion:** Probe panels capturing human sequences by hybridization; efficient but requires probe design. **CRISPR-based (DASH):** Cas9 with guide RNAs targeting abundant host sequences; highly specific, RNA-compatible. **Enzymatic rRNA depletion:** Removes ribosomal RNA dominating RNA-seq samples. Each method has characteristic pathogen retention rates requiring calibration with spike-in controls for quantitative applications.

---

### Q3–Q16: (Additional topics)
- Targeted capture enrichment vs. agnostic shotgun trade-offs
- RNA virus metagenomics library preparation specifics
- Sequencing depth requirements by application
- Sample preservation for field-collected biosurveillance samples
- Sequencing controls (positive, negative, spike-ins) for QA
- PacBio HiFi for AMR gene characterization
- Amplicon vs. shotgun for known-pathogen surveillance
- Cost modeling for resource-limited surveillance contexts

---

## Summary
Platform and library preparation decisions fundamentally determine downstream biosurveillance capability — Illumina for accuracy/scale, Nanopore for speed/field deployment, hybrid for novel pathogen characterization, with host depletion strategy critically affecting detection sensitivity for pathogen-signal-scarce samples.
