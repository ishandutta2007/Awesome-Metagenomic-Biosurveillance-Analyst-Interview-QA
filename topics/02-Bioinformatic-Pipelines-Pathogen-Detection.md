# Topic 02: Bioinformatic Pipelines & Pathogen Detection

## Overview
Quality control, host read removal, taxonomic classification, assembly, and end-to-end pipeline architecture for reliable pathogen signal extraction from metagenomic data.

---

### Q1: Design the full bioinformatic pipeline for a metagenomic biosurveillance application processing wastewater samples, specifying each step, tools, and key quality considerations.

**A:**
```
Step 1 — Raw read QC: FastQC + fastp/Trimmomatic
  - Adapter trimming; quality trimming (Q<20); minimum length filter (≥50bp);
    duplicate removal; output: clean reads ready for classification

Step 2 — Host read removal: Bowtie2 or BWA
  - Align to host genome + common lab contaminant genomes (PhiX)
  - Remove confidently-aligned reads; retain ambiguous reads to avoid
    losing divergent pathogen reads with partial host similarity

Step 3 — Taxonomic classification: Kraken2 (k-mer) + Kaiju/DIAMOND (protein)
  - Kraken2 --confidence 0.1 for initial screen of known pathogens
  - DIAMOND for divergent organisms not in nucleotide database
  - Apply appropriate confidence thresholds for each surveillance context

Step 4 — Abundance estimation: Bracken (from Kraken2), MetaPhlAn
  - Correct for genome size; normalize to RPM or RPMM
  - Enables cross-sample comparisons at different sequencing depths

Step 5 — De novo assembly: MEGAHIT (complex metagenomes), metaSPAdes
  - For novel/divergent pathogen detection and complete genome recovery
  - Annotate contigs by BLASTx and HMM-based domain prediction

Step 6 — Pathogen-specific validation: BLASTn/BLASTx
  - Re-examine raw reads; check coverage breadth/depth across reference
  - Independent orthogonal confirmation for any significant detection

Step 7 — Reporting and alert triggering
  - Standardized report per sample; comparison to historical baseline
  - Alert workflow for threshold exceedances
```

**Non-negotiable QC elements:** Negative control (extraction blank + library prep blank) sequenced every run; positive spike-in control for sensitivity calibration; database versioning for reproducibility.

---

### Q2: What are the primary sources of false positives in metagenomic pathogen detection pipelines, and what are the mitigation strategies?

**A:**
1. **Laboratory contamination (most common):** Reagents/surfaces carry background DNA. Mitigation: Negative controls every batch; lab contamination database; dedicated pre/post-PCR areas; environmental swabbing.

2. **Database contamination/misannotation:** Public databases contain misannotated sequences. Mitigation: BLAST validation for significant detections; awareness of known database contamination issues; orthogonal tool confirmation.

3. **K-mer overlap between related organisms:** Divergent relatives share k-mers with reference sequences, causing misclassification. Mitigation: Coverage breadth check across genome; BLAST confirmation; confidence threshold calibration.

4. **Index-hopping:** Illumina patterned flow cells reassign reads between multiplexed libraries. Mitigation: Unique dual indices for all samples; quantify index-hop rate; avoid co-multiplexing high-positive controls with low-prevalence samples.

5. **Human read misclassification:** Incomplete host depletion allows human reads to be classified as pathogen. Mitigation: Thorough host depletion; BLAST against human genome for suspicious detections.

---

### Q3–Q16: (Additional topics)
- Read-based vs. assembly-based pathogen detection and when each is preferred
- Contig binning approaches for individual genome reconstruction
- Viral-specific metagenomics (VirSorter2, VIBRANT, DeepVirFinder)
- Pipeline automation and workflow management (Snakemake, Nextflow)
- Containerization for reproducible pipelines (Docker, Singularity)
- Benchmarking with simulated metagenomic datasets
- Quantitative metagenomics (absolute vs. relative abundance)
- Reporting standards (MIMARKS, MIxS)

---

## Summary
Robust biosurveillance pipelines require systematic quality control at every stage with non-negotiable negative/positive controls — false positive mitigation requires explicit strategies for the distinct failure modes of contamination, database artifacts, k-mer misclassification, and index-hopping that make unvalidated initial classifications unreliable for public health reporting.
