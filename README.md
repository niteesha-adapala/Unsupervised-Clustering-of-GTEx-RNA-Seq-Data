
## 🧬 Unsupervised Clustering of Human Tissue Samples (GTEx RNA-Seq)

This project applies unsupervised machine learning techniques to bulk RNA-Seq data from the [GTEx Project](https://gtexportal.org/), aiming to identify biologically meaningful clusters of human tissue samples based solely on gene expression profiles, without using any label information during training.

## 📊 Dataset

**Source:** [GTEx Portal – Bulk Tissue Expression](https://gtexportal.org/home/downloads/adult-gtex/bulk_tissue_expression)

- **Expression Matrix:**  
  `GTEx_Analysis_v10_RNASeQCv2.4.2_gene_tpm.gct.gz`  
  → TPM values for ~59,000 genes × ~19,600 human tissue samples

- **Metadata File:**  
  `GTEx_Analysis_v10_Annotations_SampleAttributesDS.txt`  
  → Includes:
  - `SAMPID`: Unique sample identifier  
  - `SMTS`: Broad tissue type  
  - `SMTSD`: Detailed tissue type

---

## 🧹 Preprocessing

- **Gene Filtering:**  
  Removed genes with mean TPM < 1  
  → **Retained 20,545 genes**  
  - Output file: `output_tissue_GTEX_exp1.txt`

- **Dimensionality Reduction:**  
  Applied PCA to filtered data  
  → **Top 50 principal components retained**, capturing ~80% of total variance
### 🤖 Clustering Techniques

* **K-Means**: k=10 chosen via Elbow + Silhouette analysis. Produced well-separated clusters; strong for tissues like testis and skeletal muscle.
* **GMM (Gaussian Mixture Models)**: Captured soft boundaries; moderate performance with ARI=0.191 and NMI=0.571.
* **DBSCAN**: Best silhouette score (0.660 on core points); ideal for dense clusters with noise exclusion.

## 📈 Results Summary

- **DBSCAN** delivered the **highest silhouette score** (0.660) when evaluated on core points, highlighting its strength in identifying dense and well-separated clusters.
- **PCA** effectively reduced dimensionality, with the **top 50 principal components capturing ~80%** of the total variance across samples.
- **External evaluation metrics**:
  - **Normalized Mutual Information (NMI)**: 0.571  
  - **Adjusted Rand Index (ARI)**: 0.191  
  → Indicating **moderate but meaningful alignment** between predicted clusters and actual tissue categories.
- **UMAP** and **t-SNE** visualizations showcased **clear, biologically coherent tissue groupings**, validating the clustering results from a structural and functional perspective.

### 🔍 Key Insights

* Clustering uncovered distinct transcriptomic signatures for organs like testis, thyroid, nerve, and muscle.
* Overlapping or diffuse clusters (e.g., brain, skin) reflect biological complexity.
* Demonstrates the power of unsupervised learning in high-dimensional transcriptomic data exploration.

### 📁 Technologies Used

* Python (NumPy, pandas, scikit-learn, seaborn, matplotlib)
* Machine Learning: PCA, K-Means, GMM, DBSCAN
* Visualization: Cluster Purity, Comfusion Matrix, UMAP, t-SNE
  ll
  

