
## 🧬 Unsupervised Clustering of Human Tissue Samples (GTEx RNA-Seq)

This project applies unsupervised machine learning techniques to bulk RNA-Seq data from the [GTEx Project](https://gtexportal.org/), aiming to identify biologically meaningful clusters of human tissue samples based solely on gene expression profiles—without using any label information during training.

### 📊 Dataset

* **Source**: GTEx Portal (TPM-normalized expression data)
* **Size**: \~59,000 genes × 19,600 samples across diverse human tissues
* **Preprocessing**:

  * Filtered genes with mean TPM < 1 → retained 20,545 genes
  * PCA for dimensionality reduction (top 50 components ≈ 80% variance)

### 🤖 Clustering Techniques

* **K-Means**: k=10 chosen via Elbow + Silhouette analysis. Produced well-separated clusters; strong for tissues like testis and skeletal muscle.
* **GMM (Gaussian Mixture Models)**: Captured soft boundaries; moderate performance with ARI=0.191 and NMI=0.571.
* **DBSCAN**: Best silhouette score (0.660 on core points); ideal for dense clusters with noise exclusion.

### 🧪 Evaluation Metrics

* **Internal**: Silhouette Score, Davies-Bouldin Index
* **External**: Adjusted Rand Index (ARI), Normalized Mutual Information (NMI), Cluster Purity
* **Visualization**:

  * **UMAP** and **t-SNE**: Revealed tissue-specific clusters and biological proximities
  * Confusion matrices confirmed alignment with known tissue labels

### 🔍 Key Insights

* Clustering uncovered distinct transcriptomic signatures for organs like testis, thyroid, nerve, and muscle.
* Overlapping or diffuse clusters (e.g., brain, skin) reflect biological complexity rather than model failure.
* Demonstrates the power of unsupervised learning in high-dimensional transcriptomic data exploration.

### 📁 Technologies Used

* Python (NumPy, pandas, scikit-learn, seaborn, matplotlib)
* Machine Learning: PCA, K-Means, GMM, DBSCAN
* Visualization: UMAP, t-SNE, heatmaps

