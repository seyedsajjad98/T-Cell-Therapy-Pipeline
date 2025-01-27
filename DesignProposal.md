# Design Proposal: A Streamlined Pipeline for T Cell Therapy Research

## Core Concept and Purpose

This proposal outlines a pipeline that supports T cell therapy researchers in designing and simulating gene perturbations for improved therapeutic outcomes. The primary function is to translate a researcher’s functional goals and chosen experimental tools into meaningful gene sets, feed those inputs into a predictive model (GEARS), perform pathway/disease enrichment (DOSE), and produce a final, context-rich report. The target audience includes academic labs, biotech startups, and pharmaceutical research teams focusing on enhancing T cell therapies, particularly CAR T cells, by systematically identifying optimal genetic interventions.

---

## 1. Overview of the Pipeline

The pipeline begins by collecting a user’s T cell therapy objectives (“functional goals”) and planned interventions (“tools”). It then compiles relevant genes for each goal/tool combination into a format accepted by GEARS. The GEARS model simulates transcriptomic changes upon these gene perturbations, whose results subsequently flow into DOSE for enrichment and disease associations. Finally, the pipeline consolidates all findings into a comprehensive report tailored to the researcher’s T cell engineering aims.

---

## 2. Functional Goals and Experimental Tools

### 2A. Functional Goals

| **Functional Goal** | **Why It Is Relevant** |
|---------------------|------------------------|
| Enhance Cytotoxicity | Ensures robust tumor cell killing by upregulating effector molecules (e.g., GZMB, PRF1) and pro-inflammatory cytokines. |
| Reduce or Reverse Exhaustion | Prevents functional decline over time in chronically stimulated T cells by targeting inhibitory receptors (PDCD1, LAG3). |
| Increase Infiltration | Enables T cells to better access tumor sites by modulating chemokine receptors (CXCR3, CCR5). |
| Enhance Memory Formation | Improves long-term persistence and anti-tumor durability by upregulating memory-related genes (TCF7, IL7R). |
| Increase Resistance to Tumor Microenvironment (TME) | Counters TGF-β, adenosine, or other immunosuppressive signals in the tumor niche (e.g., SMAD7, CD39/CD73 pathways). |
| Optimize Metabolic Fitness | Maintains T cell functionality under nutrient-depleted or hypoxic conditions (e.g., SLC2A1, PGC-1α). |
| Manage Toxicities / Safety | Addresses CRS or on-target/off-tumor concerns, often through built-in “safety switches” or suicide genes. |

### 2B. Experimental Tools

| **Tool Category** | **Examples / Notes** | **Relevance** |
|-------------------|----------------------|----------------|
| Cytokine Cocktails | IL-2, IL-7, IL-15, IL-21, IL-18, IL-12 | Sustain T cell expansion, effector function, or re-shape the TME by altering cytokine milieu. |
| Co-Stimulatory Domains/Molecules | CAR constructs with CD28, 4-1BB; agonists like OX40, 4-1BB | Enhance activation signals, proliferation, and cytotoxicity while reducing exhaustion. |
| Blocking Immunosuppressive Signals | Anti-PD-1, anti-TGF-β, knockout of PDCD1, SMAD2/3, or LAG3 | Alleviate T cell exhaustion, improve killing in suppressive TMEs. |
| Culture Environment Manipulations | Hypoxia vs. normoxia, glucose restriction, short vs. long culture duration | Control the differentiation state, maintain T cell stemness, and match TME nutrient conditions. |
| Genetic Editing / CRISPR | CRISPR-mediated KO (e.g., PDCD1, CBLB), overexpression of co-stimulatory or metabolic genes | Directly modify T cell intrinsic properties to match desired functional goals. |
| Combinatorial Treatments | Checkpoint inhibitors + CAR T, small-molecule regulators of Wnt, mTOR, or AKT | Fine-tune proliferation vs. memory formation vs. cytotoxic potential. |
| Safety or Control Switches | iCasp9, HSV-TK, transient mRNA-based CAR T | Manage serious toxicities (CRS, on-target/off-tumor) through kill-switch or limited CAR expression. |

---

## 3. Translating User Choices into GEARS-Compatible Gene Sets

After the researcher selects one or more functional goals (e.g., “Enhance Cytotoxicity + Reduce Exhaustion”) and experimental tools (e.g., “High IL-2, CRISPR KO of PDCD1”), the system must compile all relevant genes into an input format for GEARS. This involves mapping known associations between each functional goal/tool and the corresponding gene sets.

### 3A. Platforms and Databases for Mapping Goals/Tools to Genes

| **Platform / Database** | **Information Provided** | **Integration Approach** | **Utilization in Mapping** |
|-------------------------|--------------------------|---------------------------|-----------------------------|
| TCPGdb | T cell–specific CRISPR screen results, “perturbation scores” for LOF/GOF genes across multiple functional contexts | REST API (if available) or manual data exports | Identifies high-priority hits for each functional goal (cytotoxicity, infiltration, etc.) |
| TISIDB | Tumor–immune system interactions, including infiltration markers and checkpoint genes | Web-based queries or downloadable datasets | Validates infiltration/immune checkpoint targets that match user’s TME/infiltration focus |
| DICE | Gene expression profiles of sorted T cell subtypes (CD8, CD4, Treg, etc.) | Downloadable expression matrices; manual or programmatic | Pinpoints whether a candidate gene is highly expressed in a relevant T cell subtype |
| ImmPort | Large immunology repository containing gene-expression and functional data relevant to T cell biology | REST endpoints or curated data releases | Corroborates functional gene–phenotype associations for chosen goals/tools |
| MSigDB (ImmuneSigDB) | Curated gene sets for immunological processes and T cell states | Programmatic via GSEA or web-based gene set downloads | Offers predefined “immune function” gene sets to quickly align user choices with known sets |

### 3B. Proposed Solutions to Compile User Choices into Gene Inputs

| **Solution** | **How It Works** | **Practical Implementation** |
|--------------|------------------|------------------------------|
| Manual Curation | A curated spreadsheet linking each functional goal/tool to a set of relevant genes, regularly updated | In-house curation team uses the above databases to refresh the mapping table |
| Automated API-Based Retrieval | Programmatically query resources (e.g., TCPGdb or ImmPort) to fetch genes linked to each chosen parameter | Custom scripts that call public APIs (if supported) or parse database dumps |
| Hybrid Approach (semi-automated curation) | Start with automated queries to external DBs, followed by manual validation for final gene inclusion | Reduces curation effort while retaining quality control by domain experts |
| Pre-Assembled “Master Gene Sets” | Build large gene sets for each functional goal/tool category, maintained in a version-controlled repository | Instantly reference internal “master sets” upon user selection in the front-end |

---

## 4. GEARS Modeling

Once the final “pre-curated gene set” is generated, the next step is to feed it into GEARS. This simulation engine predicts transcriptomic shifts upon specified perturbations (e.g., “Knockout PDCD1, Overexpress GZMB”).

### 4A. Proposed GEARS Model Table

| **Model Name** | **Training Data** | **Focus Area** | **Use Case** |
|----------------|--------------------|-----------------|---------------|
| GEARS-CD8-Effector | Bulk RNA-seq from activated CD8+ T cells, CRISPR KO data | Cytotoxicity, exhaustion reversal | For goals emphasizing enhanced killing, decreased exhaustion |
| GEARS-CD4-Helper | Bulk/Single-cell data from CD4+ T cells under activation | Helper function, cytokine production | For goals that manipulate IL-2/IL-21 production or combination therapies |
| GEARS-Treg-Modification | Datasets focusing on Treg differentiation and function | Treg stability, inhibitory signaling | For researchers aiming to engineer Tregs or reduce immunosuppression in TME |
| GEARS-CAR-T-Specific | Transcriptomes from CAR T expansions, potential scRNA-seq | CAR-specific costimulatory domain impacts | For projects specifically optimizing CAR design (CD28 vs. 4-1BB), or “armored” CAR T cells in certain TMEs |
| GEARS-MetabolicFocus | T cell lines cultured in low-glucose/hypoxic conditions | Metabolic fitness, adaptation | For advanced usage where T cells are engineered to cope with harsh TME metabolic states |

---

## 5. DOSE Analysis

After GEARS simulates the changes and outputs a list of differentially expressed genes, the pipeline calls upon DOSE. This tool runs pathway enrichment (KEGG, GO) and identifies disease associations relevant to the T cell modifications.

| **DOSE Output** | **Relevance to T Cell Researchers** |
|------------------|-------------------------------------|
| Pathway Enrichment (Immune Pathways) | Indicates which immune/oncology pathways are up- or down-regulated by the perturbation |
| Disease Association | Flags potential autoimmunity or off-target disease links from the identified DEGs |
| Functional Annotation (e.g., GO terms) | Reveals broad biological processes (e.g., T cell receptor signaling) impacted |

---

## 6. Final Report

The pipeline compiles all findings into a final report. The following table details the major elements, why they matter, and where they are sourced.

| **Report Element** | **Why It Is Relevant for T Cell Research** | **Source** |
|--------------------|-------------------------------------------|------------|
| Recommended Perturbations (e.g., Overexpress GZMB, KO PDCD1) | Provides direct actionable insight for genetic engineering (knockouts, overexpressions, etc.) | User Choices + Gene Curation |
| Predicted Transcriptomic Changes (Top DEGs, fold changes) | Clarifies downstream effects of each perturbation; helps prioritize additional validation steps | GEARS Simulation |
| Pathway/Disease Enrichment (immune signaling, autoimmune risks) | Identifies potential pathways or risks (e.g., autoimmunity) from the chosen modifications | DOSE |
| Functional/Phenotypic Labels (e.g., T cell cytotoxic marker) | Quickly highlights the role of each gene in T cell biology or therapy outcome | Merged from DOSE & curated DBs |
| Potential Safety Warnings | Warns if certain perturbations may induce excessive cytokine release or on-target/off-tumor effects | User-defined Safety Tools, curated references |

---

## 7. Additional Tools or Platforms for Future Integration

| **Name** | **Pipeline Stage** | **Added Value** |
|----------|--------------------|------------------|
| ImmuneCRISPR (future) | Gene Mapping (Functional goals → Genes) | Aggregates CRISPR screens for multiple immune cell types, potentially expanding beyond T cells |
| Reactome | DOSE or Pathway Analysis | Offers detailed, manually curated pathways beyond standard KEGG/GO, potentially highlighting immunometabolism |
| GeneMANIA | Pre-Curation / Confirmation of Gene Networks | Enables quick visualization of interactions among user-chosen genes, helps refine curated sets |
| STRING | Pre-Curation / Confirmation of PPI (protein–protein interactions) | Further validation of functional clusters, synergy among the curated gene sets |
| ClinicalTrials.gov (searchable database) | Validation Step for Clinical Relevance | Confirms if certain gene targets or interventions are part of ongoing T cell therapy clinical trials |

---

## Conclusion

This pipeline is designed to meet current T cell therapy research needs by:

- Gathering user inputs on functional goals and experimental tools.
- Compiling gene sets from robust T cell–specific databases and curated references.
- Modeling predicted transcriptomic changes in GEARS.
- Enriching the output with DOSE-based pathway/disease insights.
- Delivering a final, actionable report aligned with real-world experimental priorities.

By integrating multiple data sources and providing modular solutions for gene curation, modeling, and enrichment analysis, this approach creates a flexible, scalable platform that can adapt to emerging trends in CAR T and T cell therapy research.

---

## **Step 5: Add `references.md`**

Create a new file named `references.md` in the root of your repository and paste the following content:

```markdown
# References

## Key Publications

1. **GEARS: A CRISPR-based Predictive Model for T Cell Therapy**
   - *Nature Biotechnology, 2023*
   - [Link to Paper](https://www.nature.com/articles/s41587-023-01905-6)
   - [GitHub Repository](https://github.com/snap-stanford/GEARS)

2. **Deep Learning Predictions of TCR-Epitope Interactions Reveal Epitope-Specific Chains in Dual Alpha T Cells**
   - *Nature Communications, 2024*
   - [Link to Paper](https://www.nature.com/articles/s41467-024-47461-8)

3. **Quantifying Tumor-Infiltrating Immune Cells from Transcriptomics Data**
   - *Cancer Immunology, 2018*
   - [PubMed Link](https://pubmed.ncbi.nlm.nih.gov/29541787/)

4. **Comprehensive CRISPR Screening in T Cells: TCPGdb**
   - *BioRxiv, 2024*
   - [Link to Preprint](https://www.biorxiv.org/content/10.1101/2024.12.30.630773v1.full)
   - [TCPGdb Database](http://tcpgdb.sidichenlab.org/)

## Databases and Tools

1. **ImmPort**
   - [Website](https://www.immport.org/)
   - *Relevance: Repository of immunological data relevant to curated gene sets.*

2. **TISIDB**
   - [Website](https://cis.hku.hk/TISIDB)
   - *Relevance: Integrates tumor-immune system interaction data.*

3. **DICE Database**
   - [Website](https://dice-database.org/)
   - *Relevance: Provides gene expression profiles for specific immune cell subsets, including T cells.*

4. **MSigDB (ImmuneSigDB)**
   - [Website](https://www.gsea-msigdb.org/gsea/msigdb)
   - *Relevance: Curated gene sets for immunological processes and T cell states.*

## Additional Resources

- **GeneMANIA**
  - [Website](https://genemania.org/)
  - *Relevance: Enables quick visualization of interactions among user-chosen genes.*

- **STRING**
  - [Website](https://string-db.org/)
  - *Relevance: Further validation of functional clusters, synergy among the curated gene sets.*

- **Reactome**
  - [Website](https://reactome.org/)
  - *Relevance: Offers detailed, manually curated pathways beyond standard KEGG/GO.*

- **ClinicalTrials.gov**
  - [Website](https://clinicaltrials.gov/)
  - *Relevance: Confirms if certain gene targets or interventions are part of ongoing T cell therapy clinical trials.*
