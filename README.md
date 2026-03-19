# Patient Trajectory Analysis using OMOP CDM-based Knowledge Graph

This project is a research prototype that leverages synthetic healthcare data from Synthea, following the OMOP CDM (Common Data Model) standard, to construct patient-centered knowledge graphs and embed patient trajectories for analyzing and tracking similar patient cohorts.

## 1. Project Overview
- Objective: To build patient-level knowledge graphs using OMOP CDM-standardized databases and quantify clinical similarity between patients through graph embedding techniques, providing a data-driven and objective basis for patient cohort selection.
- Dataset: Synthetic patient data generated via Synthea (utilizing Conditions, Encounters, Medications, Observations, Patients, and Procedures tables)
- Core Technologies: OMOP CDM, Knowledge Graph, Word2Vec (Trajectory Embedding), Cosine Similarity, t-SNE Visualization

## 2. Key Features
1) OMOP CDM-based Knowledge Graph Construction (Node & Edge Generation)
- Nodes were defined for six types of entities to capture the inherent relationships in healthcare data, and edges were created to reflect clinical meaning.
- Nodes: Patient, Encounter, Condition, Procedure, Observation, Medication
- Edges (Relations):
 - has_encounter: Connects patients with their encounters
 - has_condition/procedure/etc: Links clinical events occurring during encounters
 - treats: Defines the treatment relationship between prescriptions (Medication/Procedure) and diagnoses (Condition)
 - has_disease (Chronic): Diagnoses occurring two or more times are defined as chronic diseases and directly linked to the patient node

2) Patient Trajectory Embedding
Patient time-series clinical trajectories were treated like “sentences” and vectorized.
- Algorithm: Word2Vec (Skip-gram)
- Process: Extracted sequences of diagnosis and prescription codes based on visit order and embedded them into a low-dimensional vector space, capturing contextual rather than purely statistical similarity.

3) Patient Similarity Analysis and Visualization
 - Similarity Calculation: Cosine similarity was computed between learned patient vectors to identify cohorts with the most similar treatment trajectories to a given patient.
 - Visualization: High-dimensional patient embeddings were visualized in 2D using t-SNE, allowing inspection of patient clustering based on clinical characteristics.

## 3. Tech Stack
 - Language: Python
 - Libraries: Pandas, NumPy, Gensim (Word2Vec), Scikit-learn (t-SNE, Similarity), Matplotlib
