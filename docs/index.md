---
title: "T Cell Therapy Pipeline"
layout: default
---

# Welcome to the T Cell Therapy Pipeline Project

## Introduction
This is the **official project page** for a streamlined pipeline to enhance T cell therapy research.  
Our ultimate aim is to help researchers:
- Define functional goals (e.g., enhancing cytotoxicity, reversing T cell exhaustion).
- Choose experimental tools (CRISPR, cytokine cocktails, etc.).
- Predict transcriptomic changes using [GEARS](https://github.com/snap-stanford/GEARS).
- Perform enrichment analysis with DOSE to interpret pathway and disease associations.
- Generate a final **context-rich report** of recommended interventions.

> **Note**: This project is in the **conceptual/design phase**. Implementation will evolve during my Master’s Thesis and future PhD work.

---

## Project Workflow

1. **User Inputs**: Researcher picks T cell therapy goals (e.g., “Increase Infiltration”) and experimental tools (e.g., “CRISPR KO of PDCD1”).
2. **Gene-Set Compilation**: We leverage T cell–specific databases (like [TCPGdb](http://tcpgdb.sidichenlab.org/), [TISIDB](http://cis.hku.hk/TISIDB/), and [ImmPort](https://www.immport.org/)) to map those goals/tools to relevant genes.
3. **Predictive Modeling**:
   - Pass the gene-perturbation inputs to [GEARS](https://github.com/snap-stanford/GEARS) (a CRISPR-based transcriptomic modeling tool).
4. **Enrichment Analysis**:
   - Use DOSE or other tools (KEGG, GO) to identify pathways/disease associations from GEARS outputs.
5. **Customized Report**:
   - A final, interactive or PDF report that details top differentially expressed genes, potential safety flags, and recommended next steps.

![Pipeline Diagram](https://github.com/seyedsajjad98/T-Cell-Therapy-Pipeline/blob/main/docs/pipeline_diagram.png)  


---

## Core Concept and Purpose
We aim to **streamline T cell therapy research** by automating the design and simulation of gene perturbations. This platform will serve academic labs, biotech startups, and pharma R&D focusing on CAR T optimization and next-gen cell therapies.

Some of the **primary pipeline objectives** include:
- **Enhance Cytotoxicity**: Upregulate effector molecules like GZMB, PRF1, etc.
- **Reduce Exhaustion**: Target inhibitory receptors (PDCD1, LAG3) to maintain long-term T cell function.
- **Optimize Metabolic Fitness**: Engineer T cells to thrive under nutrient-deprived or hypoxic conditions.
- **Manage Toxicities/Safety**: Incorporate kill switches (iCasp9, HSV-TK) to mitigate severe adverse events.

*(For more details, see [DesignProposal.md](../DesignProposal.md).)*

---

## Potential Use Cases

1. **CAR T cell engineering**: Testing multiple genetic modifications for synergy (e.g., knockout PDCD1 + overexpress GZMB).
2. **Tumor microenvironment adaptation**: Targeting immunosuppressive cues in the TME.
3. **Stem Cell Extensions**: Future expansions to iPSC-based therapies for regenerative medicine.

---

## Future Roadmap

- **Phase 1**: Finalize data selection and gene-set curation methods (possible integration with [TCPGdb preprint](https://www.biorxiv.org/content/10.1101/2024.12.30.630773v1.full)).
- **Phase 2**: Prototype pipeline to feed user choices into GEARS and parse outputs.
- **Phase 3**: Automate DOSE (or other enrichment tools) and generate a user-friendly “Summary Report”.
- **Phase 4**: Extend beyond T cells to iPSCs or other stem cell therapies; evaluate commercial/freemium models.

*(For an even deeper dive, see [references.md](../references.md) or the [README](../README.md).)*

---

## Contact & Collaboration
- **Researcher**: [sajjad haghi] (Master’s Student @ [Ilia State University, Tblisi, Georgia])
- **Advisor**: Dr. Vinchenzo Lagani 
- **Email**: [sajjadhaghi1998@gmail.com]  
- Interested in collaborations? Feel free to open an issue in the [GitHub Repo](https://github.com/seyedsajjad98/T-Cell-Therapy-Pipeline).

---

### Acknowledgments
- [GEARS Team (Stanford)](https://github.com/snap-stanford/GEARS) for the CRISPR-based predictive modeling approach.
- Various immunology databases (e.g., ImmPort, TISIDB, etc.) that will empower the gene-set curation and analysis.

---

_Thank you for visiting the T Cell Therapy Pipeline project page!_
