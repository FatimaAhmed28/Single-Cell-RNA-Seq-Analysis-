# Single-Cell-RNA-Seq-Analysis-

---
Overview

This project presents an **exploratory analysis of single-cell RNA sequencing (scRNA-seq) data using the PBMC dataset.  

It demonstrates a complete workflow using the AnnData framework and Scanpy, including:

- Data loading and inspection  
- Sparse matrix handling  
- Normalization (CPM)  
- Quality control  
- Dimensionality reduction (PCA, t-SNE, UMAP)  
- Visualization and clustering  

---

Dataset Information

| Attribute | Value |
|----------|------|
| Dataset | PBMC3k |
| Cells | ~2,638 |
| Genes | ~11,505 |
| Format | `.h5ad` (AnnData) |

Data Structure

- `adata.X` → Log-normalized expression (log(1+x))  
- `adata.layers["raw"]` → Raw counts  
- `adata.obs` → Cell metadata  
- `adata.var` → Gene metadata  
- `adata.obsm` → Embeddings (PCA, t-SNE, UMAP)  
- `adata.obsp` → Pairwise distances  
- `adata.uns` → Analysis settings  

---

Workflow
<img width="300" height="800" alt="mermaid-diagram" src="https://github.com/user-attachments/assets/dcbcb75e-939a-4e0f-b520-e17633113a99" />



---

Results & Visualizations

1️. Gene Expression Comparison

Matrix plot comparing CPM-normalized values vs raw counts
<img width="1400" height="363" alt="fig1" src="https://github.com/user-attachments/assets/cd19306e-6e82-4daf-aa23-ea656d2077bd" />


Interpretation:

* Normalized data improves comparison across cell types
* Raw counts preserve original biological signal
* Demonstrates importance of multi-layer data storage

---

2️. Dimensionality Reduction

PCA, t-SNE, and UMAP embeddings highlighting B cells

<img width="1000" height="303" alt="fig2" src="https://github.com/user-attachments/assets/55ff264a-5fca-400c-8792-f47d9952a98f" />


Insights:
* PCA → Captures global variance
* t-SNE → Highlights local clusters
* UMAP → Best separation of populations
* B cells form a distinct cluster

---
3. QC Violin Plots

<img width="1000" height="500" alt="1" src="https://github.com/user-attachments/assets/3bd83ffb-d6ac-4d2a-bdd4-39f1934d8311" />

Interpretation:

* Low n_genes_by_counts indicates poor-quality or dying cells.
* High total_counts may suggest doublets or multiplets.
* Elevated pct_counts_mt reflects stressed or damaged cells.
---

4. QC Scatter Plots
<img width="1000" height="500" alt="2" src="https://github.com/user-attachments/assets/a431453c-e39f-4881-bea8-0365b2cdbc06" />
Interpretation:

* Cells with high mitochondrial % and counts are likely low-quality.
* Positive correlation between counts and genes reflects sequencing depth.
* Outliers reveal potential doublets or failed cells.
---

5. Highly Variable Genes (HVG)
<img width="1000" height="500" alt="3" src="https://github.com/user-attachments/assets/439f766f-3862-4dab-9be0-843f5fb298d8" />
Interpretation:

* HVGs capture biological variability across cells.
* Low-dispersion genes represent noise or housekeeping genes.
* Selecting HVGs improves downstream clustering accuracy.

---

6. PCA Variance Ratio (Elbow Plot)
<img width="1000" height="500" alt="4" src="https://github.com/user-attachments/assets/484e599f-cb1a-4db1-b3f6-6343b6bec57b" />
Interpretation:

* Early PCs explain most of the variance in data.
* The “elbow point” indicates diminishing returns of additional PCs.
* Selecting optimal PCs avoids noise inclusion.

---

7. PCA Scatter Plot (Gene Expression)
<img width="1000" height="500" alt="5" src="https://github.com/user-attachments/assets/8e6232b2-6b46-47a0-b630-3846bfa6f356" />
Interpretation:

* Clusters begin to emerge in reduced dimensions.
* Gene coloring highlights expression patterns across cells.
* Early biological structure becomes visible.
---

8. Marker Gene Ranking Plot
<img width="1000" height="500" alt="6" src="https://github.com/user-attachments/assets/6322139b-a2fd-4505-be18-0cd9f532f0db" />


Interpretation:

* Identifies genes that define each cluster.
* Highlights biological differences between populations.
* Enables downstream cell type annotation.

---

9. Distance Matrix (Unordered)

Pairwise cell distances in PCA space


<img width="500" height="500" alt="fig3" src="https://github.com/user-attachments/assets/114a8528-6f4b-4296-8077-ff45796ddbda" />


Interpretation:

* Appears unstructured
* Hidden similarity patterns exist

---

10. Distance Matrix (Reordered)

Cells reordered by Louvain clusters

<img width="500" height="500" alt="fig4" src="https://github.com/user-attachments/assets/25345279-4c81-4d33-ad9c-fff4aa55d09e" />


Interpretation:

* Clear block patterns emerge
* Confirms biologically meaningful clustering

---

Metadata & Annotation

Cell Metadata (`obs`)

* `n_genes`
* `percent_mito`
* `n_counts`
* `louvain_cell_types`

Additional:

* `is_low_quality` → cells with `percent_mito > 0.03`

### Gene Metadata (`var`)

* `gene_names`
* `n_cells`
* `gene_ids`

---

Key Findings

* Dataset is highly sparse but information-rich
* Multiple layers (raw + normalized) are essential
* Embeddings align well with biological cell types
* B cells show strong cluster separation
* Distance matrices become clearer after reordering
* AnnData provides a unified data framework
* QC removes noise and ensures reliable analysis
* HVGs drive meaningful biological variation
* Clustering + marker genes reveal cell identities

---

Conclusion

This project demonstrates how AnnData + Scanpy provide a powerful and structured workflow for single-cell RNA-seq analysis.

Clear separation of immune cell populations
Consistent alignment between metadata and embeddings
Strong foundation for advanced analysis

---

Future Work

* Differential gene expression analysis
* Cell-type annotation refinement
* Trajectory inference
* Multi-dataset integration

---

🔗 Notebook Access

[Open in Google Colab]https://colab.research.google.com/drive/1Fer1k0tmwQ8Pj1Ie44V9s4Fyf9uzmmAl?usp=sharing

---

Author

Fatima Ahmed

