# Topic 03: Taxonomic Classification & Reference Databases

## Overview
Kraken2, MetaPhlAn, DIAMOND, and the reference database ecosystem — core classification infrastructure and its limitations for biosurveillance including novel pathogen detection.

---

### Q1: Compare k-mer-based (Kraken2/Bracken), marker gene-based (MetaPhlAn), and alignment-based (DIAMOND+MEGAN) approaches for metagenomic biosurveillance.

**A:**
**K-mer-based (Kraken2/Bracken):** Fastest (classifies millions of reads/minute); high sensitivity for database-represented organisms; completely misses organisms with <60-70% nucleotide identity to any database entry; k-mer overlap causes misclassification between related organisms. Best for: high-speed initial screening, known pathogen detection, wastewater surveillance.

**Marker gene-based (MetaPhlAn4):** Uses clade-specific single-copy marker genes; very specific (low false positive rate); misses novel organisms without known markers; best for: robust quantitative bacterial community profiling with low false-positive rates.

**Protein-level alignment (DIAMOND+MEGAN):** Translates reads in 6 frames, aligns against protein databases; substantially higher sensitivity for divergent organisms (protein more conserved than nucleotide); slower than k-mer methods; best for: novel pathogen discovery, detection of highly divergent viruses, functional AMR annotation.

**Optimal biosurveillance strategy — layered approach:**
1. Kraken2 for rapid known-pathogen screening
2. Assembly of unclassified reads + DIAMOND protein search for novel pathogen discovery
3. MetaPhlAn for quantitative bacterial community characterization

---

### Q2: What are the key considerations for building and maintaining a custom reference database for a specific biosurveillance program?

**A:**
1. **Scope definition:** Include target pathogens + closest relatives; regional organism diversity; background organisms. Exclude poorly-assembled draft genomes; redundant near-identical strains.

2. **Decontamination:** Screen all reference sequences against human genome and lab contaminant databases before inclusion — misannotated bacterial genomes frequently contain human genomic contamination. Use NCBI FCS (Foreign Contamination Screen) or Blobtools.

3. **Taxonomic accuracy verification:** Confirm sequences cluster phylogenetically with their annotated taxon — cross-check against established phylogenies.

4. **Version control:** Every database build versioned and archived; changelogs documenting all additions/removals; reproducible build scripts.

5. **Update cadence:** Match pathogen emergence rate — monthly for active outbreak surveillance; quarterly for stable environmental monitoring. Monitor GenBank depositions for target taxa automatically.

6. **Validation after every update:** Test benchmark positive/negative controls before deploying updated database in operational surveillance — updates can inadvertently reduce sensitivity or increase false positive rates.

---

### Q3–Q16: (Additional topics)
- LCA algorithm and confidence score interpretation in Kraken2
- Species-level vs. strain-level classification precision for outbreak investigation
- Viral-specific databases (ViPR, ICTV-consistent databases)
- 16S/18S amplicon databases (SILVA, GTDB) in surveillance contexts
- Protein databases (UniRef, nr, CARD, VFDB) for functional annotation
- Real-time database updates for rapidly-evolving pathogens (SARS-CoV-2 variants)
- Database size vs. sensitivity trade-offs in resource-limited settings

---

## Summary
Optimal classification combines rapid k-mer screening (Kraken2) for known pathogens with protein-level alignment (DIAMOND) for novel organism discovery — supported by rigorously curated, version-controlled custom databases validated after each update with explicit contamination screening and taxonomic accuracy verification.
