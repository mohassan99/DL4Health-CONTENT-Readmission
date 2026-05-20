# CONTENT Model: Topic-Augmented Neural Readmission Prediction

Replication of *"Predicting Hospital Readmission via the CONTENT Model"* — a neural architecture that combines unsupervised topic modeling over clinical codes with a supervised neural readmission predictor.

**[View Report](Replication%20of%20Paper%20Proposing%20the%20CONTENT%20Readmission%20Prediction%20Model.docx)** · Part of [DL4Health](https://github.com/mohassan99/DL4Health) · CS 598 Final Project, UIUC MCS-DS

---

## What this demonstrates

CONTENT addresses a core limitation of standard EHR prediction models: diagnosis codes and procedure codes are high-dimensional, sparse, and noisy — a single readmission risk model trained directly on raw codes may not generalize across patient populations or coding variations. CONTENT solves this by first learning latent clinical topics from the code space, then using those topics as features in the downstream predictor.

### Architecture: Two-Stage

**Stage 1 — Topic Modeling (Unsupervised)**
- Learns latent clinical topics from the distribution of ICD/procedure codes across patient visits
- Topics represent clinically coherent concepts (e.g., "cardiovascular comorbidity cluster," "metabolic syndrome cluster") without any labeled data
- This is the bridge between raw claims codes and interpretable clinical concepts

**Stage 2 — Neural Readmission Predictor (Supervised)**
- Takes the patient's topic distribution (from Stage 1) as input features
- Predicts 30-day readmission risk
- Topic-based features compress the high-dimensional code space and reduce noise from coding variation

### Why this architecture matters
- **Coding variation robustness:** Two hospitals coding the same condition differently will produce similar topic distributions even if the raw codes differ
- **Dimensionality reduction with clinical meaning:** Topic features are more interpretable than raw code embeddings — each topic corresponds to a clinical concept
- **Transfer-friendly:** Topic model can be pretrained on unlabeled claims data at scale, then the predictor fine-tuned on labeled readmissions

---

## Relevance to healthcare payer ML

| Payer use case | How CONTENT applies |
|---|---|
| **Readmission prediction** | Direct application — predict 30/90-day readmission to support transition-of-care programs |
| **Member risk scoring** | Topic-based member representation enables generalizable risk models across coding environments |
| **HEDIS/STARS** | Topic features can represent care gap patterns for quality measure prediction |
| **Claims-based predictive modeling** | Two-stage approach (unsupervised feature learning → supervised prediction) is a general pattern for any claims ML task |
| **Cross-plan model portability** | Topic normalization reduces sensitivity to plan-specific coding patterns — important for models that must generalize across Medicaid, Medicare, and Commercial lines |

This is the most architecturally advanced project in this portfolio — it combines RETAIN-style sequential modeling concepts, topic modeling (from EM/LDA foundations), and neural prediction in a single framework.

---

## Skills demonstrated
`PyTorch` · `Topic Modeling` · `Unsupervised Pretraining` · `Representation Learning` · `Readmission Prediction` · `EHR Data` · `ICD Coding` · `Feature Engineering` · `Clinical NLP concepts` · `Paper Replication` · `Model Validation`

## Course
CS 598 — Deep Learning for Healthcare · University of Illinois Urbana-Champaign · MCS-DS (School of Engineering) · Final Project
