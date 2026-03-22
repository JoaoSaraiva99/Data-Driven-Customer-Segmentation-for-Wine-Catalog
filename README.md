# Data-Driven-Customer-Segmentation-for-Wine-Catalog
This project applies segmentation algorithms to a catalogue of 178 wines to identify distinct profiles for targeted advertising campaigns. The methodology combined normalisation, correlation analysis, PCA and K-Means clustering to group wines with similar characteristics and support more precise marketing decisions.

## Project Background
WineNot manages a catalogue of 178 wines and aims to better understand the characteristics that distinguish them in order to create clear product profiles. By identifying groups of wines with similar attributes, the company can design more targeted and efficient advertising campaigns across its full catalogue, rather than using a generic approach. This project applies data analysis and segmentation techniques to support a more structured, data-driven marketing strategy and improve the relevance of promotional actions.

Insights and recommendations are provided on the following key areas:
  - PCA-based dimensionality reduction and visualisation
  - Cluster interpretation and profiling
  - Targeted advertising opportunities by segment
  - Product positioning and campaign personalisation
  - Data-driven support for marketing decisions
  - Catalogue optimisation through customer-focused promotion

Data Structure Overview

The project is based on a structured wine catalogue containing 178 wines, described through 13 quantitative variables: alcohol, malic acid, ash, alcalinity of ash, magnesium, total phenols, flavanoids, nonflavanoid phenols, proanthocyanins, color intensity, hue, OD280/OD315 of diluted wines, and proline. In practical terms, each row represents one wine and each column captures a measurable chemical characteristic that may help distinguish one wine profile from another.

* Alcohol - Amount of alcohol in that specific type of wine.
* Malic acid - Amount of malic acid in that specific type of wine.
* Ash - Amount of ash in that specific type of wine.
* Alcalinity of ash - Amount of ash alkalinity in that specific type of wine.
* Magnesium - Amount of magnesium in that specific type of wine.
* Total phenols - Amount of phenols in that specific type of wine.
* Flavanoids - Amount of flavanoids in that specific type of wine.
* Non-flavanoid phenols - Amount of non-flavanoid phenols in that specific type of wine.
* Proanthocyanins - Amount of proanthocyanins in that specific type of wine.
* Color intensity - Level of colour intensity in that specific type of wine.
* Hue - Hue level in that specific type of wine.
* OD280/OD315 of diluted wines -Value of diluted wine absorbance in that specific type of wine.
* Proline - Amount of proline in that specific type of wine.

Before modelling, the dataset was reviewed for quality and consistency. The notebook shows that all 13 variables are numeric, the dataset has 178 non-null entries in every column, and no duplicated rows were found. Descriptive statistics were then used to build an initial understanding of the spread, central tendency, and scale differences across variables, which is important because several features originally operated on very different numerical ranges.

To prepare the data for clustering, the variables were normalised using MinMax scaling. This step was necessary because features such as proline and magnesium had much larger raw ranges than variables such as hue or nonflavanoid phenols. Without scaling, the clustering model would tend to overemphasise high-range variables and underweight the rest. After normalisation, all variables were brought onto a comparable 0–1 scale, creating a more reliable basis for segmentation.

Before normalising:

<img width="754" height="413" alt="imagem" src="https://github.com/user-attachments/assets/96ef6c16-a6f1-4fff-976b-3a0d0c3f2cc6" />

After normalising: 

<img width="740" height="413" alt="imagem" src="https://github.com/user-attachments/assets/98251f7e-90cb-458b-a375-bdae112061ac" />

From a business perspective, this dataset structure makes it possible to move from a broad catalogue view to a profile-based approach. Rather than promoting all wines in the same way, WineNot can use measurable product differences to identify distinct groups of wines and support more efficient, segment-specific advertising across the catalogue.

# Executive Summary
## Overview of Findings

This project set out to answer a practical business question: how can WineNot increase sales by promoting its catalogue more effectively? The analytical conclusion is that the catalogue can be segmented into four meaningful wine profiles, enabling more targeted advertising, clearer product positioning, and more efficient commercial communication. The notebook’s elbow-curve analysis selected 4 clusters as the most suitable structure for K-Means, and the silhouette visualisation suggests that the resulting separation is meaningful overall.

<img width="562" height="455" alt="imagem" src="https://github.com/user-attachments/assets/7c653638-4cdc-4488-9d25-70322248f4b2" />

The analysis identified **four distinct wine clusters** within WineNot’s catalogue, using a K-Means model calibrated with **4 clusters** as the most suitable solution.

### Cluster 0 – Young and Affordable Wines
This cluster includes wines with lower colour intensity, moderate alcohol content, and lower proline levels. These wines are likely to be lighter, less complex, and more accessible, making them suitable for consumers looking for affordable everyday options.

### Cluster 1 – Balanced and Versatile Wines
This cluster is characterised by wines with higher levels of total phenols and flavanoids, suggesting stronger quality indicators in terms of antioxidant structure and colour profile. These wines appear more balanced and adaptable, making them suitable for a wide range of occasions.

### Cluster 2 – Robust and Full-Bodied Wines
This cluster represents wines with stronger structure and intensity. It is associated with higher values of flavanoids, alcohol, and OD280/OD315 of diluted wines, as well as a solid colour profile. These wines can be positioned as more robust, expressive, and suitable for consumers who appreciate fuller-bodied wines.

### Cluster 3 – Premium and Complex Wines
This cluster groups wines with premium characteristics, including higher alcohol, flavanoids, and proline, which are commonly associated with ageing potential and aromatic complexity. These wines are better suited to special occasions and more demanding consumers seeking exclusivity and sophistication.



