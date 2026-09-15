# Firewall Traffic - Unsupervised Clustering

> Developed for the Unsupervised Learning course (Aprendizado de Máquina Não Supervisionado) — Specialization in Applied Artificial Intelligence, UNISINOS.

See
[project-description.txt](project-description.txt) for the original assignment.

Applies unsupervised learning techniques to a real firewall traffic log export in order to
find structure in network traffic and flag anomalous/denied connections without using any
labels during training.

## Contents

- [`data/new_logs.csv`](data/new_logs.csv) — raw firewall log export (200 records): timestamp,
  firewall/NAT rule, interfaces, source/destination IP and port, protocol, and
  allowed/denied outcome.
- [`notebooks/firewall_traffic_clustering.ipynb`](notebooks/firewall_traffic_clustering.ipynb) —
  the deliverable notebook, covering:
  - Descriptive statistics of the dataset;
  - Feature engineering (time deltas, private/public IP flags, port bucketing, one-hot
    encoding of categorical fields);
  - **PCA** for dimensionality reduction and 2D visualization;
  - **K-Means** clustering (k selected via silhouette score, guarding against degenerate
    clusters);
  - **DBSCAN** clustering, used to flag rare `Denied` / `Invalid Traffic` events as
    anomalies (noise points);
  - **Cluster evaluation** (Silhouette, Davies-Bouldin, Calinski-Harabasz) comparing the two
    clustering algorithms.

## Running the notebook

```bash
pip install -r requirements.txt

jupyter notebook notebooks/firewall_traffic_clustering.ipynb
```

The notebook reads the dataset via a relative path (`../data/new_logs.csv`), so run it from
inside the `notebooks/` folder (as Jupyter does by default when opening the file directly).
