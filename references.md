# References & Resources

Below are some publications, tools, and databases that inform or support this pipeline design.

## Key Publications / Preprints

1. **GEARS**  
   - **Title**: A single-cell CRISPR-based platform for combinatorial perturbations with real-time readout.  
   - **Link**: [Nature Biotechnology, 2023](https://www.nature.com/articles/s41587-023-01905-6)  
   - **Relevance**: GEARS is the predictive modeling backbone for transcriptomic changes following gene perturbations.

2. **TCPGdb**  
   - **Title**: T cell perturbation genes database (Preprint)  
   - **Link**: [BioRxiv (2024)](https://www.biorxiv.org/content/10.1101/2024.12.30.630773v1.full)  
   - **Database Link**: [http://tcpgdb.sidichenlab.org/](http://tcpgdb.sidichenlab.org/)  
   - **Relevance**: Potential resource for T cell–specific CRISPR screen data, gene perturbation scores, etc.

3. **Deep Learning for TCR-Epitope**  
   - **Title**: Deep learning predictions of TCR-epitope interactions reveal epitope-specific chains in dual alpha T cells  
   - **Link**: [Nature Communications, 2024](https://www.nature.com/articles/s41467-024-47461-8)  
   - **Relevance**: Illustrates advanced computational approaches for TCR-epitope interactions, which can complement our pipeline for T cell specificity or functional readouts.

4. **Quantifying Tumor-Infiltrating Immune Cells**  
   - **Title**: Quantifying tumor-infiltrating immune cells from transcriptomics data. Cancer Immunology (2018)  
   - **Link**: [PubMed](https://pubmed.ncbi.nlm.nih.gov/29541787/)  
   - **Relevance**: Provides methods for analyzing immune infiltration, relevant for T cell infiltration goals.

## Key Databases / Tools

- **ImmPort** (www.immport.org)  
  Relevance: Large immunology data repository for gene-expression and functional data.

- **TISIDB** (http://cis.hku.hk/TISIDB/)  
  Relevance: Integrates tumor-immune system interaction data, which helps validate infiltration and immune checkpoint targets.

- **DICE Database** (https://dice-database.org/)  
  Relevance: Detailed gene expression profiles of sorted T cell subsets, crucial for refining gene sets.

- **MSigDB (ImmuneSigDB)**  
  Relevance: Curated gene sets specifically for immune processes, which can be leveraged for quick gene set alignment.

- **Reactome**  
  Relevance: Pathway database that can enhance DOSE or other enrichment analyses.



  [Edit Diagram on Draw.io]([PASTE_YOUR_LINK_HERE](https://viewer.diagrams.net/?tags=%7B%7D&lightbox=1&highlight=0000ff&edit=_blank&layers=1&nav=1&title=T_Cell_Therapy_Pipeline_Workflow.drawio#R%3Cmxfile%3E%3Cdiagram%20id%3D%22C5RBs43oDa-KdzZeNtuy%22%20name%3D%22Page-1%22%3E7Vpbc%2BI2FP41zLQP8fiKzWMIJM027e7GyeZxR9jC1sa2XEkQ2F%2FfI1sOvkEILVnajTMT7COhy%2Fm%2B8x1JZmBdpKsrhvL4DxriZGDq4WpgTQamaTquCx%2FSsi4tI9ssDREjYWkyNgaffMfKqCvrgoSYNyoKShNB8qYxoFmGA9GwIcboU7PanCbNXnMU4Y7BD1DStT6QUMSl1TPdjf03TKK46tkYjsqSGQoeI0YXmepvYFrz4iqLU1S1pSbKYxTSp1qn1nRgXTBKRXmXri5wIn1bue3hev2Q3DwOrz585n%2Bh%2B%2FHvd39%2BOSsbu3zNV55nyHAmDm56cc9u%2FZsrfP3h%2Bs6fsYfLYXB%2FNiybXqJkgSsvFHMV68q%2FOAR3q0fKREwjmqFkurGOCx9i2Y0OT5s6N5TmYDTA%2BA0LsVbcQQtBwRSLNFGlCZrhZPwMxwVNKIOijGayeS4YfcSVEVCaeY7tyK7mNBOVPcRztEiEtJIkqdWeewEOArDv6UXlbU4XLMA7XKdYIRCLsNhRT7Un3djmDsQkpikWbA0VGE6QIMsmq5EKjui53gZhuFEgvwJwvQP4PccMLNdZvhD8lzu4Ve3cxRgUQw7t4%2BwbRC6MjQ9kMAxRCriOy%2F%2ByIoQ7%2F7VDnCYtnmIisJ%2BjwqdP0PBrKNCCdFpcfdS4LK4WNcBunMs%2FZb9EKUmk2n3BLEQZUmZFT8OWDVexbryaOEvMBF7thFqVnpm2gkNJb%2FX4tNExU1e2uK5hjn4kerjvenCoHlS57yU9ME9KD4wewIcyYKQ%2FrzA43NR9mA%2BoAk1zIodEs1qVxu0%2FEYAtgfmWuvDmAuCdWvh77%2BF%2FaPibe4a%2FdVrh3xv%2Fhd8I3ETyxifpAsYCiJr6ZHrFqwrQ4XOdXprcSByb0KKERBncB%2BB0WHZYYxksBBbz56ogJWFYsghz8h3NivYkuDklmSim74wHzuRladgS6F3Yd0WC2rSocWz2AvvHuK7pRiPK1dPe%2BKqWP8n516rQ%2BZxLXW4R4HkAh3PC3JkSpue3PpQW%2B0iSRcdIBT%2FjWtDWTy0XjN5zwaG5wNozF9gnlQusXXE%2F%2BehPoXCaMRLEKS6k6ByAXHPC3zXg39EA1zw1DTC6xwU%2FQgRCxOPi%2B%2F9ZRbD3VATnpBTB3qUItzgHKKFY7hLZ0faFP6MQGPrJHQw5HSpMVznKeIG6DgEL3%2F%2FkX1QrQ3lQiDK5Y%2FAFTuVCGvo4GyNe7CLKk0UijxO3UsM4HWq8EeZOC%2FNhF3TD6wPdPJr89y0JWojV8Kj2csW%2B7xPlpNAEazKjQtC0b%2Fe3G8H23lDIdKHwq171mHV89Hqu0MuSXI4zXUXy5ZdGKHc1Aps6roVIoC5LQoS9edDHkmHg4dn8mAQYeg38DdvR3G7Y210CmCNNH9Uv71h86KpAhw%2F8EYsgVv6v7%2Fx5Xr79m5OVxGeHhxt4bgOonxxJi3qdc4at3GxTJQpyU4swYl%2BLl5QvkvVYtLBdR7Pr8Lp7sMQeaYbXJYp1LKEw91gnkrR4kTtuEKTDihpjuic%2BHf2oZ2epBKqPCUkjmEdCZnI2PEAYPosXXBpfRm%2BYOY5FCohERzPaTHA1p8MES9csq0cyXM06Fhf6jhRPjAvVzvWrj9mSBJj%2FT3jh6brm7kULT7OHbykQfYeK7cyxNY3XiLA9a2xLFIenhP4U0yEeXYiEZDCm6vctfSuPJcYo1cxQY%2BW26UelE8MwnSY%2FrJHm9iweGhrSwxRHG72aK%2FC4%2BblMeVy9%2BU2SNf0b%3C%2Fdiagram%3E%3C%2Fmxfile%3E))


