# RNA-Seq Analysis Pipeline (Galaxy)

This project performs a complete RNA-Seq analysis workflow using the Galaxy platform.  
The goal is to identify **differentially expressed genes (DEGs)** and understand their biological significance.

---
## Biological Question

This study aims to answer the following biological questions:

- How does depletion of the Pasilla (ps) gene affect gene expression in *Drosophila melanogaster*?
- Which genes are significantly upregulated or downregulated after treatment?
- What biological processes and molecular pathways are impacted by these changes?
- Do these changes reveal the functional role of Pasilla in RNA regulation and cellular processes?

Overall, the goal is to understand how loss of Pasilla influences gene expression and cellular function at the transcriptome level.

## Overview
RNA-Seq data from treated and untreated samples was analyzed to:
- Assess sequence quality  
- Map reads to a reference genome  
- Count reads per gene  
- Identify differentially expressed genes  
- Perform functional enrichment analysis  

---
## 📂 Dataset

https://doi.org/10.5281/zenodo.6457007

### Subsampled FASTQ Files

https://zenodo.org/record/6457007/files/GSM461177_1_subsampled.fastqsanger  
https://zenodo.org/record/6457007/files/GSM461177_2_subsampled.fastqsanger  
https://zenodo.org/record/6457007/files/GSM461180_1_subsampled.fastqsanger  
https://zenodo.org/record/6457007/files/GSM461180_2_subsampled.fastqsanger

## Workflow Steps

### 1. Quality Control — Falco & MultiQC
**Falco**
- Checks raw read quality (base quality, GC content, adapters)

**MultiQC**
- Combines all QC reports into a single summary

 Ensures sequencing data is reliable before analysis

---

### 2. Read Trimming — Cutadapt
**Cutadapt**
- Removes low-quality bases and adapter sequences

 Improves mapping accuracy

---

### 3. Mapping — STAR
**STAR**
- Aligns RNA-Seq reads to the reference genome (splice-aware)

 Identifies origin of reads in genome

---

### 4. Mapping Evaluation — MultiQC
- Reviews alignment statistics (e.g., % mapped reads)

 Confirms mapping quality

---

### 5. Read Counting — featureCounts
**featureCounts**
- Counts reads mapped to each gene

 Converts aligned reads into gene expression values

---

### 6. Differential Expression — DESeq2
**DESeq2**
- Normalizes count data  
- Compares treated vs untreated samples  
- Identifies significantly differentially expressed genes  

 Detects genes affected by treatment

---

### 7. Annotation
- Adds gene names, positions, and biological information

 Makes results easier to interpret

---

### 8. Visualization — Heatmap
- Displays expression patterns of significant genes

 Helps identify clustering and trends
<img width="404" height="369" alt="image" src="https://github.com/user-attachments/assets/7ba14166-a39a-4c72-a82e-6968c77a893d" />

 <img width="521" height="350" alt="image" src="https://github.com/user-attachments/assets/30635e7f-3b56-4f87-9950-07fecdaf36d4" />


---

### 9. Functional Enrichment — GO & KEGG
- **Gene Ontology (GO):** Biological processes affected  
- **KEGG pathways:** Molecular pathways involved  

 Provides biological insight into DE genes

---

##  Key Outcomes
- List of differentially expressed genes  
- Expression patterns across samples  
- Enriched biological functions and pathways  

---
## Key Results

- ~80% of reads successfully mapped to the reference genome, indicating good data quality  
- A set of **significantly differentially expressed genes** was identified (adjusted p-value < 0.05)  
- After filtering (|log2FC| > 1), the most biologically relevant genes were selected  
- Clear separation between **treated and untreated samples** observed in clustering/heatmap  
- Functional enrichment analysis revealed:
  - Key **biological processes (GO terms)** affected by treatment  
  - Significant **KEGG pathways** involved in gene regulation and metabolism  
- The **Pasilla (ps) gene** showed expected expression changes after RNAi treatment  

## Reproducibility

- Analysis performed using Galaxy platform  
- Same dataset links provided above  
- All tools and parameters follow the Galaxy RNA-Seq tutorial workflow  
- Workflow steps: QC → Trimming → Mapping → Counting → DE Analysis → Enrichment  
- Using the same inputs and parameters will reproduce the same results  

##  Tools Used
- Galaxy  
- Falco  
- MultiQC  
- Cutadapt  
- STAR  
- featureCounts  
- DESeq2  


---

