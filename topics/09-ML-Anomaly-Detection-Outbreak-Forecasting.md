# Topic 09: ML, Anomaly Detection & Outbreak Forecasting

## Overview
Statistical process control, machine learning anomaly detection in longitudinal surveillance streams, and epidemiological forecasting — the computational public health intelligence layer built on metagenomic data.

---

### Q1: What statistical and ML approaches are used for anomaly detection in longitudinal metagenomic surveillance data, and what are the core methodological challenges?

**A:**
**Anomaly detection approaches:**

1. **Statistical Process Control (SPC) — baseline approach:**
   - **CUSUM:** Accumulates deviations from baseline; sensitive to gradual sustained increases; standard in public health surveillance
   - **EWMA:** Weights recent observations more heavily; sensitive to recent trend changes; robust to isolated outliers
   - **Shewhart control charts:** ±3σ threshold alerts; sensitive for single large deviations; less sensitive for sustained moderate increases
   SPC methods are interpretable, computationally simple, well-understood — recommended starting point before complex methods.

2. **Time series anomaly detection:**
   - **ARIMA:** Handles temporal autocorrelation surveillance signals exhibit; flags observations outside prediction intervals
   - **Prophet:** Handles seasonal patterns, trend changes, holidays; widely adopted in public health for complex seasonal disease data
   - **STL decomposition:** Separates trend/seasonal/residual components; anomalies detected in residual after seasonal/trend removal

3. **Machine learning:**
   - **Isolation Forest:** Tree-based; isolates anomalies by random partitioning; useful for multivariate data where anomalies manifest across combinations of features
   - **Autoencoders:** Trained to reconstruct normal patterns; high reconstruction error flags anomalies; learns complex multivariate normal from history
   - **One-class SVM/SVDD:** Learns boundary of "normal" in feature space; flags outside-boundary observations

**Core biosurveillance-specific challenges:**

1. **Extreme class imbalance:** True outbreak anomalies are extremely rare in training data; makes supervised learning impractical; makes unsupervised performance evaluation difficult.

2. **Non-stationarity of "normal":** New variants, changing testing practices, evolving population immunity shift what's normal over time; detectors must continuously update their baseline.

3. **Seasonal variation must be modeled explicitly:** Respiratory pathogen seasonality creates large expected fluctuations — "higher than average" triggers constant false alerts in peak season without seasonal adjustment.

4. **Multiple testing problem at scale:** 50 pathogens × 20 sites × daily = 1,000 values/day; even 1% false positive rate generates 10 false alerts/day by chance; multiple testing correction adapted for correlated surveillance streams is essential.

5. **Alert fatigue:** Too many false alerts causes responders to ignore the system — calibrating to public-health-operationally-appropriate PPV requires domain knowledge about how alerts are used.

---

### Q2: What epidemiological forecasting approaches exist for outbreak prediction, and how should analysts communicate forecast uncertainty?

**A:**
**Forecasting approaches:**

1. **Mechanistic compartmental models (SIR/SEIR):** Classic infectious disease modeling; useful for understanding transmission dynamics, scenario modeling, parameter estimation (R₀, generation time). Limitations: require uncertain assumptions about mixing patterns and immunity.

2. **Statistical time series (ARIMA, Prophet, ETS):** Purely data-driven; captures recurring seasonal patterns; useful for 1-4 week ahead forecasting of routine indicators. Limitations: poor for long-term; can't anticipate novel outbreak drivers.

3. **ML ensemble approaches:** Combine multiple models (mechanistic + statistical + ML); consistently outperform single models in prospective evaluation — validated by CDC FluSight and COVID-19 Forecast Hub.

4. **WBE signal as leading indicator:** 4-7 day lead time (Topic 05) incorporated as early input to clinical outcome forecasting models — providing earlier updates than waiting for clinical case data.

**Communicating forecast uncertainty:**

1. **Always visualize uncertainty — never single deterministic numbers:** Forecast cones with widening confidence bounds at longer horizons; scenario ranges (optimistic/expected/pessimistic); the "cone of uncertainty" visualization is well-understood by non-technical audiences.

2. **Distinguish aleatory from epistemic uncertainty:** Aleatory (inherent transmission stochasticity — can't be reduced with data) vs. epistemic (parameter uncertainty — can be reduced with better surveillance). Decision-makers benefit from understanding which dominates.

3. **Calibration communication:** Report retrospective performance: "When our 80% CI didn't include the observed value, the model was wrong about 20% of the time — appropriately calibrated." Trust in intervals requires understanding prior calibration.

4. **Operational translation:** "70% probability that ICU capacity will be exceeded within 3 weeks under current trajectory — suggests beginning pre-positioning surge capacity resources by next week." Actionable framing outperforms raw probability outputs for real-time resource allocation.

---

### Q3–Q13: (Additional topics)
- Early outbreak detection algorithms (EARS, CDC BioSense)
- Syndromic surveillance integration for multi-signal anomaly detection
- Bayesian hierarchical models for multi-site surveillance synthesis
- Phylodynamic models for outbreak size and spread estimation
- Digital epidemiology leading indicators (search trends, pharmacy sales)
- Nowcasting for reporting delay correction
- Global epidemic intelligence systems (GOARN, ProMED)
- Equity considerations in surveillance system design

---

## Summary
Biosurveillance anomaly detection and forecasting require methods explicitly addressing seasonal non-stationarity, multiple testing at scale, rare true events, and alert fatigue risk — with forecast uncertainty always communicated visually and operationally rather than as raw probability values, and ensemble approaches typically outperforming single-method models for prospective outbreak prediction.
