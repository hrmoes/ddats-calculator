# D-DATS Calculator

**Dutch Device-Aided Therapy Screening Tool**

Web-based screening tool for identifying Parkinson's disease patients eligible for referral to expert centers for device-aided therapy (DAT) evaluation.

[![License: CC BY-NC-ND 4.0](https://img.shields.io/badge/License-CC%20BY--NC--ND%204.0-blue.svg)](https://creativecommons.org/licenses/by-nc-nd/4.0/)
[![TRIPOD: Type 2b](https://img.shields.io/badge/TRIPOD-Type%202b%20Validation-green.svg)](https://www.tripod-statement.org/)

---

## Live Tool

**🔗 [Open D-DATS Calculator](https://hrmoes.github.io/ddats-calculator)**

Bilingual interface (Dutch/English) with integrated LEDD calculator.

---

## Validation

**External validation in Dutch secondary care cohort:**
- Sample: 164 consecutive Parkinson patients, 4 hospitals
- Reference standard: Expert panel of 5 Dutch movement disorder specialists
- **AUROC: 0.94** (95% CI: 0.91-0.97)
- **Sensitivity: 92%** | **Specificity: 90%** | **PPV: 62%** (at cutoff 5.8)


**Citation:**  
Moes, H.R., Buskens, E., Portman, A., et al. (2024). VALIdation of models for assessing eligibility for referral for Device-Aided Treatment in Parkinson's disease (VALIDATE). *Parkinsonism & Related Disorders*, 127(S1), Abstract 493. https://doi.org/10.1016/j.parkreldis.2024.107059

*Full manuscript in preparation.*

---

## How It Works

**Model predictors (n=3):**
1. LEDD (Levodopa Equivalent Daily Dose) - continuous
2. Response fluctuations - yes/no
3. Troublesome dyskinesias - yes/no

**Formula:** `D-DATS = (LEDD × 0.003) + (Fluctuations × 2.0) + (Dyskinesias × 2.0)`

**Interpretation:**
- Score **≥5.8**: Consider referral to DAT expert center for evaluation
- Score **<5.8**: No indication for referral

---

## Clinical Use

**Target population:**
- Idiopathic Parkinson's disease (DAT-naive)
- Oral/transdermal medication optimized per guidelines
- Secondary care setting

**Important limitation:**  
Tool is likely insufficiently sensitive for patients with therapy-resistant tremor. DBS may be indicated in these patients regardless of score.

**Full scope and contraindications:** See medical disclaimer in tool.

---

## Features

- ✅ Single-page application (no installation needed)
- ✅ Client-side processing (GDPR-compliant, no data transmission)
- ✅ Bilingual interface (Dutch/English)
- ✅ Integrated LEDD calculator (Jost et al. 2023 conversions)
- ✅ Export function for medical records
- ✅ Mobile-responsive design

---

## Local Use

Download `index.html` and `favicon.svg`, open in any modern browser. No installation or dependencies required.

---

## LEDD Conversions

Calculator uses Jost et al. (2023) conversion factors:

| Medication | Factor | Example |
|------------|--------|---------|
| Levodopa IR | 1.0× | 100 mg → 100 LEDD |
| Levodopa CR | 0.75× | 100 mg → 75 LEDD |
| Pramipexole (salt/diHCl) | 100× | 1.5 mg → 150 LEDD |
| Pramipexole (base) | 142.86× | 1.05 mg → 150 LEDD |
| Ropinirole | 20× | 6 mg → 120 LEDD |
| Rotigotine | 30× | 8 mg → 240 LEDD |

Full conversion table available in calculator interface.

---

## Known Limitations

1. Validated in Dutch secondary care only
2. Not sensitive for therapy-resistant tremor
3. Assumes medication optimization per current guidelines
4. Does not predict treatment outcomes
5. Does not replace comprehensive clinical assessment

See [full documentation](LICENSE) for complete scope and limitations.

---

## References

1. Moes, H.R., Ten Kate, J.M., Portman, A.T., et al. (2023). Timely referral for device-aided therapy in Parkinson's disease: Development of a screening tool. *Parkinsonism & Related Disorders*, 109, 105359.

2. Jost, S.T., Kaldenbach, M.A., Antonini, A., et al. (2023). Levodopa dose equivalency in Parkinson's disease: Updated systematic review. *Movement Disorders*, 38, 1236-1252.

3. Moes, H.R., Henriksen, T., Sławek,  J., et al. (2023). Tools and criteria to select patients with advanced Parkinson's disease for device-aided therapies: a narrative review. *Journal of Neural Transmission*, 130(11), 1359-1377.

4. Moes, H.R., Dafsar, H.S., Jost, W.H., et al. (2024). Grasping the big picture: impact analysis of screening tools for timely referral for device-aided therapies. *Journal of Neural Transmission*, 131(11), 1295-1305.

5. Moes, H.R., Buskens, E., Portman, A., et al. (2024). VALIdation of models for assessing eligibility for referral for Device-Aided Treatment in Parkinson's disease (VALIDATE). *Parkinsonism & Related Disorders*, 127(S1), Abstract 493. https://doi.org/10.1016/j.parkreldis.2024.107059

---

## License & Citation

**Copyright:** © 2025 H.R. Moes, MD, University of Groningen, UMCG
**License:** [CC BY-NC-ND 4.0](LICENSE) - Free for non-commercial use with attribution

**How to cite this tool:**
```
Moes, H.R., Buskens, E., Portman, A., et al. (2024). VALIdation of models 
for assessing eligibility for referral for Device-Aided Treatment in 
Parkinson's disease (VALIDATE). Parkinsonism & Related Disorders, 127(S1), 
Abstract 493. https://doi.org/10.1016/j.parkreldis.2024.107059
```

---

## Contact

**Developer:** H.R. Moes, MD  
**Institution:** Department of Neurology, University Medical Center Groningen  
**Email:** h.r.moes@umcg.nl

For clinical questions, validation inquiries, or technical issues.

---

**Disclaimer:** For use by qualified healthcare professionals only. Does not replace clinical judgment. Treating physician remains responsible for all decisions.
