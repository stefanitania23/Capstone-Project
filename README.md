# Transcriptomic Analysis of Lung Adenocarcinomar: Identification of Differentially Expressed Genes and Functional Enrichment Analysis

## Introduction 
Lung cancer is one of the leading causes of cancer-related mortality worldwide and remains a major global health problem. According to recent global cancer statistics, approximately 2.5 million new cases of lung cancer and 1.8 million deaths were reported in 2022, accounting for about 18% of total cancer-related deaths. Lung cancer is broadly classified into two major categories: small cell lung cancer (SCLC) and non-small cell lung cancer (NSCLC), with NSCLC representing approximately 80–90% of all cases. NSCLC mainly consists of adenocarcinoma (ADC), squamous cell carcinoma (SCC), and large cell carcinoma (LCC), each of which has distinct molecular characteristics and clinical responses to therapy. Understanding the molecular mechanisms underlying lung cancer development is essential for improving diagnosis and therapeutic strategies.
Therefore, this study aims to perform a basic bioinformatics analysis of lung cancer at the gene expression level by collecting, comparing, and interpreting transcriptomic data. This analysis will be conducted using a publicly available dataset from the NCBI Gene Expression Omnibus (GEO) database, followed by visualization and interpretation of differentially expressed genes to better understand the molecular characteristics of lung cancer. 

## Methods 
**2.1 Datasets**
The gene expression dataset used in this study was obtained from the publicly available NCBI Gene Expression Omnibus (GEO) database with the query dataset GSE27262 for Homo sapiens. The dataset was generated using the Affymetrix Human Genome U133 Plus 2.0 Array platform (GPL570), a microarray technology that enables large-scale measurement of gene expression levels across thousands of genes simultaneously. The GSE27262 dataset contains gene expression profiles from tumor tissues (T) and matched adjacent normal lung tissues (N) collected from 25 patients with stage I lung adenocarcinoma, resulting in a total of 50 samples. RNA extracted from these tissue samples was hybridized onto microarray chips to measure gene expression levels. The dataset focuses on identifying differences in gene expression signatures between lung tumor tissues and their corresponding adjacent normal tissues.  The dataset was accessed and downloaded using the GEOquery package in R.

**2.2 R Analysis**
The downloaded gene expression dataset was analyzed using the R programming environment with several Bioconductor packages for transcriptomic data analysis. The expression matrix was first prepared and normalized to ensure comparability across samples. The samples were then grouped into two categories based on their biological condition, namely “Tumor” and “Normal” allowing comparative analysis between cancer and normal samples.
Differential gene expression analysis was subsequently performed using the limma (Linear Models for Microarray Data) package in R to identify genes that were significantly differentially expressed between the two groups. The log2 fold-change (Log2FC) and adjusted p-values were used to separate the up- and down-regulated DEGs by the following cut-offs:

The results were obtained based on statistical significance and fold change values, and the identified differentially expressed genes (DEGs) were further visualized using several graphical approaches, which are boxplots, density plot, UMAP plot, volcano plots, and heatmaps to illustrate gene expression patterns.

**2.3 Functional Enrichment Analysis**
Gene Ontology (GO) Analysis. GO enrichment analysis was performed using the g:Profiler web platform (https://biit.cs.ut.ee/gprofiler/gost), a widely used tool for functional profiling of gene lists. The list of significant DEGs was submitted to g:Profiler's g:GOSt module, which maps genes against curated GO term databases covering three ontology domains: Biological Process (BP), Molecular Function (MF), and Cellular Component (CC).  
KEGG Pathway Analysis. KEGG pathway mapping was performed using the KEGG Mapper tool (https://www.kegg.jp/kegg/pathway.html), specifically the Search & Color Pathway module. The list of significant DEG gene symbols was submitted to KEGG Mapper with Homo sapiens (hsa) as the target organism. This tool maps the input genes onto curated KEGG reference pathway diagrams and highlights the genes present in each pathway, allowing direct visualization of which nodes in a given pathway are represented by the DEGs. Pathways showing notable gene coverage were selected and interpreted in the context of lung cancer biology.

## Results and Discussion
**3.1 Quality Assessment of Gene Expression Data**
Data quality analysis of GSE27262 was seen through boxplot, density plot, and UMAP visualizations. The boxplot results demonstrated that the gene expression distribution across samples was relatively uniform in both tumor and normal groups, with the median of each sample falling within a similar range and no samples exhibiting extreme or outlier distributions (Figure 1). This indicates that the data had been well-normalized without significant outliers, confirming that the dataset is suitable for subsequent differential gene expression analysis. The density plot further confirmed that the distribution of gene expression values (log2) in both normal and tumor samples followed a relatively similar pattern with distribution peaks around 0, although minor variations in the tumor curve reflect the presence of gene expression heterogeneity in cancer tissue (Figure 2). Furthermore, the UMAP plot demonstrated a clear separation between normal and tumor tissue samples without significant overlap, indicating sufficiently distinctive gene expression pattern differences between the two groups, thus confirming that this dataset holds strong potential for Differentially Expressed Genes (DEGs) analysis (Figure 3).


Figure 1. Boxplot GSE27262.

Figure 2. Density Plot GSE27262. 

Figure 3. UMAP Plot GSE27262. 


**3.2 Identification and Characterization of DEGs**
Differential expression analysis produced a total of 15,864 probes evaluated, with 8,527 genes upregulated and 7,337 genes downregulated in lung adenocarcinoma tumor tissue compared to normal tissue. 


Figure 4. Volcano Plot GSE27262. 


Heatmap analysis of the top 50 DEGs further revealed that the majority of genes were downregulated in tumor tissue compared to normal tissue, with only 3 genes showing upregulation in cancer cells, namely TOX3, SPP1, and COL10A1. 


Figure 5. Heatmap GSE27262. 

**3.3 Gene Ontology (GO) Enrichment Analysis** 
Analysis of cellular location indicates that the analyzed genes are primarily localized in the plasma membrane and cell periphery, suggesting that the encoded proteins likely function as receptors, ion channels, or other membrane-associated proteins. On the other hand, the analysis of biological processes shows enrichment in developmental processes and anatomical structure development, indicating that these genes may play important roles in the regulation of cell growth and differentiation. Additionally, enrichment in the positive regulation of synaptic transmission suggests a potential involvement of these genes in neuronal or nervous system–related functions.

Figure 6. g:Profiler Overview Results.


Figure 7. g:Profiler Detailed Results.

**3.4 KEGG Pathway Analysis**
Based on the KEGG Mapper analysis, three major pathways were identified. In the Neuroactive Ligand Signalling Pathway (Figure 8), three genes were involved, SLC6A4, GRIA1, and ADRA1A, all of which were downregulated, indicating disruption of neuroactive signaling within the tumor microenvironment. In the Efferocytosis pathway (Figure 9), CD36 and AGER were found, both significantly downregulated, suggesting impaired immune clearance of apoptotic cells and compromised anti-tumor immune response in lung adenocarcinoma. In the ECM-Receptor Interaction pathway (Figure 10), CD36 and SPP1 were identified, where the strong upregulation of SPP1 alongside downregulated CD36 reflects an imbalance in ECM signaling that promotes tumor cell adhesion, invasion, and metastasis. Collectively, these three pathways highlight that malignant progression in GSE27262 is driven by neuronal reprogramming, immune evasion, and extracellular matrix remodeling.

Figure 8. Neuroactive Ligand Signalling Pathway 




Figure 9. Efferocytosis pathway

Figure 10. ECM-Receptor Interaction pathway 


## Conclusion
In conclusion, transcriptomic analysis of GSE27262 revealed that the most significantly dysregulated genes in lung adenocarcinoma are predominantly associated with the cell periphery and plasma membrane, indicating that malignant transformation is largely reflected in alterations of membrane-associated protein expression. Functional enrichment through Gene Ontology further demonstrated that these genes are involved in developmental processes, anatomical structure development, and positive regulation of synaptic transmission, suggesting that lung adenocarcinoma progression involves the reactivation of embryonic developmental programs and neuronal reprogramming of cancer cells. KEGG pathway analysis further supported these findings by identifying significant enrichment in neuroactive ligand-receptor interaction, efferocytosis, and ECM-receptor interaction pathways, collectively highlighting that the molecular basis of lung adenocarcinoma in this dataset is driven by the disruption of immune surveillance, loss of extracellular matrix homeostasis, and aberrant neuroactive signaling within the tumor microenvironment.
