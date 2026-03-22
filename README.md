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

To build the segmentation model, the analysis first narrowed the feature set to a smaller group of highly informative variables. Correlation analysis highlighted strong relationships such as flavanoids with total_phenols (0.8646), flavanoids with OD280/OD315 of diluted wines (0.7872), and alcohol with proline (0.6437), indicating that some variables carried overlapping information. Based on this, the modelling stage focused on five variables: flavanoids, OD280/OD315 of diluted wines, alcohol, hue, and color intensity.

The resulting four clusters are not just statistically different; they are commercially interpretable. In your business framing, they can be translated into market-ready profiles such as younger and accessible wines, balanced and versatile wines, robust and tannic wines, and premium and complex wines. This is the key value of the project: it converts chemical and statistical differences into usable commercial segments.

## Insights
* The largest segment is Cluster 2, representing about 33.15% of the catalogue, followed by Cluster 1 at about 28.65%, Cluster 0 at about 19.66%, and Cluster 3 at about 18.54%. This means the commercial opportunity is weighted toward a few dominant profiles, but the smaller segments may still carry premium positioning value.
* The cluster centroids show clear differences in the chosen modelling variables. For example, one cluster is characterised by high alcohol and relatively strong flavanoids/OD280 structure, while another combines low flavanoids with higher color intensity. This is what makes the segments actionable for positioning and campaign design.

# Insights Deepdive: Methodology

The methodology followed a clear segmentation workflow, moving from data preparation to interpretation. First, the data was audited to confirm structural quality. The notebook verified that the dataset had 178 rows and 13 variables, with no missing values and no duplicated observations. Descriptive statistics and boxplots were then used to understand the original distribution of the variables and to identify major scale differences across features.

The second stage was preprocessing. Because the variables had very different units and magnitudes, MinMax normalisation was applied to make them directly comparable. This was an important methodological choice, since K-Means relies on distance calculations and is highly sensitive to scale. Normalisation ensured that no single variable dominated the clustering simply because of its numeric range.

The third stage was dimensionality review and variable selection. A full correlation matrix was produced to identify redundant information and concentrate the model on the most relevant dimensions. The notebook found especially strong positive relationships between flavanoids and total phenols, flavanoids and OD280/OD315 of diluted wines, and alcohol and proline, as well as notable negative relationships involving hue with malic acid and color intensity. On that basis, the model retained five variables for segmentation: flavanoids, OD280/OD315 of diluted wines, alcohol, hue, and color intensity.

The fourth stage was cluster modelling. K-Means was selected as the primary algorithm because the project goal was to divide the catalogue into internally similar but externally distinct groups. The elbow curve was used to determine the optimal number of clusters, and the chosen solution was k=4. The cluster assignments were then added back into the dataset so that each wine could be profiled and compared against the others.

The fifth stage was validation and interpretation. PCA was used to reduce the five-variable modelling space to two principal components for visual inspection. The PCA loadings show that Principal Component 1 is mainly associated with OD280/OD315 of diluted wines, flavanoids, hue, and color intensity, while Principal Component 2 is driven primarily by alcohol and color intensity. The PCA chart makes the four-group structure easier to interpret visually. In parallel, the silhouette plot suggests a reasonably good cluster structure, with positive values dominating across the four groups.

<img width="819" height="624" alt="imagem" src="https://github.com/user-attachments/assets/d21e4ca6-62af-4e44-a09b-e5ef294a922e" />


| Variable                         | PC1       | PC2      |
|----------------------------------|-----------|----------|
| flavanoids                       | 0.508309  | 0.283175 |
| od280/od315_of_diluted_wines     | 0.696822  | 0.108961 |
| alcohol                          |-0.001591  | 0.767653 |
| hue                              | 0.398117  |-0.115730 |
| color_intensity                  |-0.312348  | 0.552498 |

Taking this into account, we can understand that:
*Cluster 0 has high values on Principal Component 2 and low values on Principal Component 1. It is characterised by wines with lower flavanoids content and higher od280/od315_of_diluted_wines and hue values.
* Cluster 1 has high values on Principal Component 1 and low values on Principal Component 2. It is characterised by wines with higher flavanoids content, lower od280/od315_of_diluted_wines, and a more intense hue, which may indicate characteristics associated with younger or lower-quality wines, as interpreted by PC1.
* Cluster 2 has low values on both principal components. It is characterised by wines with high color_intensity and high alcohol content.
* Cluster 3 has high values on both principal components. It shows medium values of alcohol and color_intensity, according to PC2, and has intermediate characteristics in relation to the variables that are most influential in PC1.

The sixth stage extended interpretation through complementary techniques. Boxplots and grouped descriptive statistics were used to compare each cluster across the remaining wine variables. Self-Organizing Maps were applied as an additional unsupervised lens to inspect how the selected features distribute spatially across an 8x8 node grid. A decision tree was then trained using variables such as proline, flavanoids, OD280/OD315 of diluted wines, and total phenols to identify which features were most influential in reproducing the cluster assignments. Together, these methods strengthened interpretability and made the final segmentation easier to explain in commercial terms.
<img width="1920" height="1080" alt="Design sem nome(2)" src="https://github.com/user-attachments/assets/3efbb7c2-69df-4a16-b963-8975f1b40e3a" />

In business terms, the methodology is valuable because it does not stop at technical clustering. It translates raw chemical measurements into commercially meaningful wine profiles and then links those profiles to practical go-to-market actions. To support the interpretation of the more technical results, the ChatGPT API was also used to help explain what these variables and cluster patterns may indicate in terms of wine quality, classification, and commercial positioning. That is why the project is not only a data science exercise, but also a decision-support tool for catalogue marketing, campaign design, and portfolio positioning.

## Iteractive K-Means

https://github.com/user-attachments/assets/77e94dc8-1882-4f70-8e76-a24dc456446a

