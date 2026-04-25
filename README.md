# Single-Cell-RNA-Seq-Analysis-

---
📌 Overview

This project presents an **exploratory analysis of single-cell RNA sequencing (scRNA-seq) data using the PBMC dataset.  

It demonstrates a complete workflow using the AnnData framework and Scanpy, including:

- Data loading and inspection  
- Sparse matrix handling  
- Normalization (CPM)  
- Quality control  
- Dimensionality reduction (PCA, t-SNE, UMAP)  
- Visualization and clustering  

---

📊 Dataset Information

| Attribute | Value |
|----------|------|
| Dataset | PBMC3k |
| Cells | ~2,638 |
| Genes | ~11,505 |
| Format | `.h5ad` (AnnData) |

📦 Data Structure

- `adata.X` → Log-normalized expression (log(1+x))  
- `adata.layers["raw"]` → Raw counts  
- `adata.obs` → Cell metadata  
- `adata.var` → Gene metadata  
- `adata.obsm` → Embeddings (PCA, t-SNE, UMAP)  
- `adata.obsp` → Pairwise distances  
- `adata.uns` → Analysis settings  

---

🔄 Workflow
<img width="612" height="1709" alt="mermaid-diagram" src="https://github.com/user-attachments/assets/dcbcb75e-939a-4e0f-b520-e17633113a99" />


Raw Data
   ↓
Load AnnData
   ↓
Quality Control
   ↓
Normalization (CPM)
   ↓
Feature Exploration
   ↓
PCA
  ↙   ↘
t-SNE  UMAP
          ↓
     Clustering
          ↓
   Distance Analysis

---

📈 Results & Visualizations

1️⃣ Gene Expression Comparison

Matrix plot comparing CPM-normalized values vs raw counts

![Matrix Plot Placeholder](images/matrix_plot.png)

Interpretation:

* Normalized data improves comparison across cell types
* Raw counts preserve original biological signal
* Demonstrates importance of multi-layer data storage

---

2️⃣ Dimensionality Reduction

📊 *PCA, t-SNE, and UMAP embeddings highlighting B cells*

![Embedding Plot Placeholder](images/embeddings.png)

Insights:

* PCA → Captures global variance
* t-SNE → Highlights local clusters
* UMAP → Best separation of populations
* B cells form a distinct cluster

---

3️⃣ Distance Matrix (Unordered)

📊 *Pairwise cell distances in PCA space*

![Distance Matrix Placeholder](images/distance_matrix.png)

Interpretation:

* Appears unstructured
* Hidden similarity patterns exist

---

4️⃣ Distance Matrix (Reordered)

📊 *Cells reordered by Louvain clusters*

![Reordered Matrix Placeholder](images/reordered_matrix.png)

Interpretation:

* Clear block patterns emerge
* Confirms biologically meaningful clustering

---

🧾 Metadata & Annotation

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

🔍 Key Findings

* Dataset is highly sparse but information-rich
* Multiple layers (raw + normalized) are essential
* Embeddings align well with biological cell types
* B cells show strong cluster separation
* Distance matrices become clearer after reordering
* AnnData provides a unified data framework

---

✅ Conclusion

This project demonstrates how AnnData + Scanpy provide a powerful and structured workflow for single-cell RNA-seq analysis.

✔ Clear separation of immune cell populations
✔ Consistent alignment between metadata and embeddings
✔ Strong foundation for advanced analysis

---

## 🚀 Future Work

* Differential gene expression analysis
* Cell-type annotation refinement
* Trajectory inference
* Multi-dataset integration

---

🔗 Notebook Access

👉 [Open in Google Colab](https://colab.research.google.com/drive/1eePv1aHYlB34Ujy14WduZsvF2Z0xgwQt?usp=sharing)

---

👩‍💻 Author

Fatima Ahmed


Just tell me 👍
```
