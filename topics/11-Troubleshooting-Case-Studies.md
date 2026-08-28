# Topic 11: Troubleshooting & Case Studies

## Overview
Diagnosing pipeline failures, contamination events, false-positive pathogen detections, and structured problem-solving for common real-world metagenomic biosurveillance scenarios.

---

### Q1: A wastewater surveillance program detects an unexpected signal for a highly-concerning pathogen (a Select Agent) that had not previously been detected in any sample from this site. Walk through your complete response protocol — what you do immediately, what analyses are required, and how you communicate findings.

**A:**
**Immediate response — "probable false positive until proven otherwise":**

The critical first principle is that an unexpected, high-consequence pathogen signal in a surveillance system should be treated as a probable false positive requiring systematic verification before any public communication — because the prior probability of a true Select Agent signal appearing in a routine wastewater sample is extremely low, while the prior probability of pipeline errors, contamination, or database artifacts is substantially higher. Premature public communication of an unverified Select Agent detection would cause severe public harm (panic, market disruption, damage to public health system credibility) — the asymmetric consequences of false-positive vs. false-negative errors mandate careful verification before any external communication.

**Step 1 — Immediate internal escalation (within 1 hour of detection):**
Notify the laboratory director and institutional biosafety officer that a potential high-consequence pathogen signal has been identified and verification is underway. Do not notify public health authorities, media, or other external parties until verification is complete or clear evidence of a genuine detection exists. Document the exact time and content of detection in a time-stamped log.

**Step 2 — Immediate computational re-analysis (parallel tracks, within 2-4 hours):**

Track A — Pipeline integrity verification:
- Re-run the raw reads through the pipeline from scratch (not from cached intermediate files that may be corrupted)
- Re-run with a completely different classification tool (if Kraken2 flagged it, run DIAMOND for orthogonal confirmation)
- Check the negative control samples from this run — does the Select Agent signal also appear in the extraction blank or library prep blank? (If yes → contamination or pipeline artifact explanation)
- Check whether the signal appears on only one electrode/sample position or across multiple → localization to specific position suggests single contamination event

Track B — Read-level validation:
- Extract the specific reads classified as the Select Agent
- Run BLASTn on these reads against the full NCBI NT database (not just the surveillance database) — does the best BLAST hit confirm the Select Agent classification, or is there a benign explanation (similar environmental sequence, database error)?
- Assess coverage breadth across the Select Agent reference genome — genuine presence produces reads distributed across the genome; false positives from k-mer overlap typically produce reads clustered in a few short genomic regions of high similarity

Track C — Laboratory contamination investigation:
- Review all Select Agent work performed in the laboratory or adjacent laboratories in the preceding 48-72 hours (was any Select Agent material handled nearby?)
- Review environmental monitoring records for the laboratory area
- Review sample handling records — was this sample at any point proximate to Select Agent material?

**Step 3 — If computational reanalysis cannot confirm genuine signal (most likely outcome):**
Document the false positive event with root cause (if identifiable), update the pipeline to prevent recurrence if a systematic error is identified, and file an internal laboratory incident report — no external communication required.

**Step 4 — If computational reanalysis confirms signal requires further investigation:**
At this point (signal confirmed by orthogonal method and not explained by obvious artifact), notify:
1. Institutional biosafety officer (mandatory Select Agent regulatory obligation)
2. CDC Select Agent Program (required by select agent regulations if confirmation testing is initiated)
3. State public health laboratory for confirmatory PCR/culture testing on the original sample or a parallel aliquot

**Step 5 — Wait for confirmatory testing before any public communication:**
Metagenomic detection alone, even confirmed by multiple computational methods, is never sufficient for public communication of a Select Agent detection — physical confirmatory testing (PCR with Select Agent-specific primers, culture under BSL-3/4 conditions) is mandatory before any public statement. The public health authority contact in Step 4 will manage the confirmatory testing process and any subsequent public communication, consistent with their established protocols.

### Q2: A long-running wastewater surveillance program begins showing progressively increasing Salmonella signal across all sites simultaneously over a 6-week period, but no increase in reported Salmonella cases is observed in clinical surveillance during the same period. How do you investigate this discrepancy?

**A:**
**Systematic discrepancy investigation:**

This pattern — increasing environmental signal without corresponding clinical increase — is immediately suspicious for a systematic pipeline or sample collection artifact rather than a genuine epidemiological signal, because: (1) true Salmonella increases in a population would typically produce some corresponding clinical case increase (even with reporting delays and testing limitations); (2) simultaneous increase at ALL sites is a classic signature of a systematic/technical issue rather than genuine epidemiological spread (which would typically start at one or a few sites and spread geographically); (3) 6-week gradual increase could correspond to a gradual technical drift in the surveillance system.

**Systematic investigation candidates, in order of likelihood:**

1. **Database change — did a new version of the classification database get deployed approximately 6 weeks ago?**
   If a new Salmonella reference genome with unusual sequence features, or a large number of new Salmonella sequences, was added to the reference database at the time the increase began, reads from common environmental organisms with Salmonella k-mer overlap might be newly classified as Salmonella that previously were "unclassified." This is the single most likely explanation for a simultaneous all-sites increase and should be checked first by comparing database version before and after the increase onset.

2. **Library preparation reagent lot change:**
   A new lot of a critical reagent (DNA extraction kit, library preparation kit, Tn5 transposase for Nextera-based preparation) may have introduced a contaminant from a Salmonella-related organism that generates reads classified as Salmonella in every sample. If this is the cause, the negative control samples from the affected batch period should show the same Salmonella signal (a definitive diagnostic criterion).

3. **Sequencing platform maintenance or parameter change:**
   If a sequencing instrument was serviced, reagent chemistry version changed, or run parameters modified approximately 6 weeks ago, this could systematically change the read quality characteristics in ways that affect classification outcomes.

4. **Sample collection or processing change:**
   Were any changes made to sample collection protocols (new sampler devices, different fixative), preservation methods, or transport conditions approximately 6 weeks ago? Agricultural runoff events or seasonal changes in sewage composition can also systematically alter community composition.

5. **Genuine but epidemiologically silent low-level increase:**
   If all technical explanations are ruled out, there is a possibility of a genuine increase in environmental Salmonella below the clinical detection threshold — subclinical or mild Salmonella infections are systematically under-reported, and livestock-associated Salmonella can enter sewersheds through stormwater without producing human cases. This should be investigated by checking agricultural activity records, verifying whether sites near animal farming are driving the signal, and consulting with food safety surveillance programs.

### Q3–Q13: (Representative additional topics)
- Diagnosing batch effects in longitudinal metagenomic surveillance data
- Investigating unexpected species dropouts (organisms previously detected now absent)
- Root-causing inter-site signal discrepancies in a surveillance network
- Troubleshooting low yield and failed library preparations
- Investigating apparent multiple pathogen co-detections (real co-infection vs. contamination)
- Handling discordant results between metagenomic and PCR-based testing of same samples
- Diagnosing and correcting systematic biases in AMR gene abundance estimates
- Troubleshooting de novo assembly failures for samples with complex microbial communities
- Investigating unexpected changes in host-depletion efficiency
- Case study: WBE signal-clinical surveillance discordance during COVID-19 Omicron surge

---

## Summary
Biosurveillance troubleshooting requires applying "probable technical artifact until proven otherwise" as the default diagnostic assumption for unexpected high-consequence detections — systematically investigating pipeline integrity, database changes, reagent lot effects, and contamination before escalating to external notification — while maintaining structured, time-stamped documentation throughout the investigation and following established institutional protocols for escalation when verification reveals a genuine signal requiring public health authority engagement.
