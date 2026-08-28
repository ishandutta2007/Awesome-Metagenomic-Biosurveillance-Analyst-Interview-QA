# Topic 06: Novel Pathogen Discovery & Characterization

## Overview
De novo assembly workflows, virus discovery pipelines, host-range prediction, and systematic approaches for characterizing unknown infectious agents detected in biosurveillance metagenomes.

---

### Q1: Walk through the complete computational workflow for discovering and characterizing a novel RNA virus detected as an unclassified contig in a wildlife surveillance metagenome.

**A:**
**Stage 1 — Assembly quality assessment:**
Assess contig quality: length, read coverage depth (minimum 10-20× for confident assembly), coverage uniformity (even = genuine viral origin; patchy = possible chimeric artifact). Use CheckV to assess completeness and contamination.

**Stage 2 — Taxonomic placement:**
- BLASTx against all viral protein databases (NR, UniRef, ViPR)
- Extract conserved protein domains (RdRp for RNA viruses) → multiple sequence alignment (MAFFT) → maximum likelihood phylogeny (IQ-TREE)
- Apply ICTV demarcation criteria for relevant virus family to determine new species status

**Stage 3 — Genome organization annotation:**
- ORF prediction (GeneMarkS, ORFfinder)
- Domain annotation (HMMscan vs. Pfam, CDD)
- Verify expected genomic organization for assigned family

**Stage 4 — Host association assessment:**
- Direct: co-assembly of reads with host sequences from same metagenome
- Indirect: virus family's known host range as prior; co-occurrence across samples

**Stage 5 — Zoonotic potential assessment:**
- Receptor binding domain analysis (coronavirus: ACE2 residues; influenza: HA receptor-binding site)
- Furin cleavage site analysis (polybasic sites enhance human infection efficiency)
- Comparison to known zoonotic relatives
- Critical caveat: computational zoonotic prediction has limited validated predictive value — generates hypotheses requiring experimental confirmation, not definitive risk classification

**Stage 6 — Biosecurity assessment:**
Pre-publication DURC institutional review; coordinate with public health authorities (CDC, WHO) if zoonotic risk assessment warrants; consider partial sequence publication strategy.

---

### Q2: How should a biosurveillance analyst interpret and communicate ML host-range prediction tool outputs?

**A:**
**Current ML tools:** WISH, VirHostMatcher-Net, VIPR, DeepHPP — use codon usage bias, protein structural features, and network topology to predict host range categories.

**Critical interpretation limitations:**
1. **Training data bias:** All models trained primarily on well-studied host-virus pairs; systematically underperform for novel viruses from underrepresented clades precisely where novel zoonotic threats most need identification.
2. **Confidence scores ≠ calibrated probabilities:** Model output scores are relative rankings, not true probabilities of human infection in any specific context.
3. **"Human-infectable" ≠ pandemic potential:** Receptor compatibility necessary but far from sufficient — transmissibility, pathogenicity, population immunity jointly determine pandemic risk in ways no current computational tool meaningfully predicts.

**Appropriate communication template:** "Genomic features of this novel virus [specific features] are similar to those of known zoonotic viruses in the [family] family, warranting further experimental characterization of human cell infection potential — this is a hypothesis-generating analysis, not a risk classification."

---

### Q3–Q15: (Additional topics)
- ICTV virus taxonomy and species demarcation criteria
- Metatranscriptomics vs. metagenomics for RNA virus discovery
- Endogenous viral elements (EVEs) and their interpretation
- CRISPR-based diagnostics from novel virus sequences
- Experimental validation requirements before publishing novel pathogen discovery
- Responsible communication to public health authorities
- Wildlife surveillance program design for zoonotic risk reduction

---

## Summary
Novel pathogen discovery requires systematic computational workflow (quality assessment → phylogenetic placement → genome annotation → host association → zoonotic potential assessment → biosecurity review) with explicit acknowledgment that computational zoonotic risk assessment is hypothesis-generating, not confirmatory — experimental validation is always required before public health reporting.
