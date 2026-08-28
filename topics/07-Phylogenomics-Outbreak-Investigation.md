# Topic 07: Phylogenomics & Outbreak Investigation

## Overview
Whole-genome sequencing for pathogen typing, SNP-based phylogenetic analysis, transmission inference, and genomic epidemiology transforming outbreak investigation.

---

### Q1: How is WGS phylogenetics used to investigate outbreak clusters, and what are the key analytical and interpretive challenges?

**A:**
**Core workflow:**
1. **Genome sequencing:** Sequence all available isolates/samples; for bacteria — Illumina + assembly or reference mapping; for RNA viruses — ARTIC amplicon or metagenomic sequencing
2. **SNP calling:** Align to reference genome; call SNPs at each position; generate pairwise SNP-distance matrix
3. **Phylogenetic tree:** IQ-TREE or RAxML from SNP alignment; outbreak cases expected to cluster (form a clade)
4. **Temporal signal (BEAST2):** Estimate MRCA date — if consistent with suspected exposure timing, supports epidemiological hypothesis; requires sufficient genomic diversity, accurate collection dates, clock-like evolution

**Key interpretive challenges:**

1. **SNP threshold ambiguity:** No universal threshold — depends on mutation rate (fast RNA virus vs. slow bacterium), transmission bottleneck, sequencing error rate. MRSA: 0-10 SNPs typically supports linkage; SARS-CoV-2: 2-5 SNPs within a month.

2. **Cannot establish transmission direction:** Phylogeny shows relatedness not directionality. Patient A's isolate as phylogenetic outgroup to B/C/D cluster does not mean A infected B — epidemiological data (contact history, timing, geography) required for transmission direction inference.

3. **Sampling completeness:** Unsequenced cases create gaps that can obscure true MRCA dates, create apparent linkages through unsampled intermediates, or make linked cases appear more divergent than they are.

4. **Laboratory contamination:** Index-hopping or cross-contamination during sequencing creates false genomic linkage — requires careful laboratory process controls and contamination detection in data.

---

### Q2: Compare bacterial typing approaches (MLST, cgMLST, SNP-based) and discuss metagenomic direct typing without culture.

**A:**
**MLST:** 7 housekeeping genes; globally comparable STs; discriminatory power: LOW — cannot resolve within-ST outbreak clusters; best for global epidemiology and international spread tracking.

**cgMLST/wgMLST:** 1,000-3,000+ core genome loci; allele-difference distances; discriminatory power: HIGH — resolves transmission clusters within single ward/facility; standardized schemes (Enterobase) enable cross-laboratory comparability.

**SNP-based methods:** Genome-wide SNP comparison against common reference; highest resolution; enables temporal/molecular clock analysis; requires recombination detection (Gubbins, ClonalFrameML) for bacteria with lateral gene transfer; gold standard for highest-resolution outbreak investigation.

**Metagenomic direct typing without culture:**
- Requires sufficient target organism abundance (minimum ~20-30× coverage)
- Read-based genotyping (StrainGST, MIDAS, InStrain) when coverage sufficient
- Assembly-based: de novo assemble target organism then apply standard typing
- Current practical limitation: most clinical/environmental samples lack sufficient non-dominant organism coverage; active area of methodological development

---

### Q3–Q14: (Additional topics)
- Phylogenetic tool comparison (IQ-TREE, RAxML, FastTree, BEAST2)
- Recombination detection in bacterial phylogenetics
- Nextstrain for real-time pandemic-scale phylogenomic visualization
- MLST nomenclature systems (PulseNet, Enterobase)
- TransPhylo, EpiTrace for transmission inference
- Foodborne outbreak WGS case studies (Salmonella, Listeria)
- Genomic epidemiology data sharing (NCBI Pathogen Detection, PHA4GE)

---

## Summary
WGS phylogenomics provides molecular evidence of transmission linkage — but SNP threshold selection, sampling completeness, transmission direction ambiguity, and recombination detection are critical considerations requiring integration with epidemiological data for conclusive outbreak attribution.
