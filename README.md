# RNA-Seq Analysis Pipeline (Galaxy)

This project performs a complete RNA-Seq analysis workflow using the Galaxy platform.  
The goal is to identify **differentially expressed genes (DEGs)** and understand their biological significance.

---

## 📌 Overview
RNA-Seq data from treated and untreated samples was analyzed to:
- Assess sequence quality  
- Map reads to a reference genome  
- Count reads per gene  
- Identify differentially expressed genes  
- Perform functional enrichment analysis  

---

## 🧪 Workflow Steps

### 1. Quality Control — Falco & MultiQC
**Falco**
- Checks raw read quality (base quality, GC content, adapters)

**MultiQC**
- Combines all QC reports into a single summary

➡️ Ensures sequencing data is reliable before analysis

---

### 2. Read Trimming — Cutadapt
**Cutadapt**
- Removes low-quality bases and adapter sequences

➡️ Improves mapping accuracy

---

### 3. Mapping — STAR
**STAR**
- Aligns RNA-Seq reads to the reference genome (splice-aware)

➡️ Identifies origin of reads in genome

---

### 4. Mapping Evaluation — MultiQC
- Reviews alignment statistics (e.g., % mapped reads)

➡️ Confirms mapping quality

---

### 5. Read Counting — featureCounts
**featureCounts**
- Counts reads mapped to each gene

➡️ Converts aligned reads into gene expression values

---

### 6. Differential Expression — DESeq2
**DESeq2**
- Normalizes count data  
- Compares treated vs untreated samples  
- Identifies significantly differentially expressed genes  

➡️ Detects genes affected by treatment

---

### 7. Annotation
- Adds gene names, positions, and biological information

➡️ Makes results easier to interpret

---

### 8. Visualization — Heatmap
- Displays expression patterns of significant genes

➡️ Helps identify clustering and trends

---

### 9. Functional Enrichment — GO & KEGG
- **Gene Ontology (GO):** Biological processes affected  
- **KEGG pathways:** Molecular pathways involved  

➡️ Provides biological insight into DE genes

---

## 📊 Key Outcomes
- List of differentially expressed genes  
- Expression patterns across samples  
- Enriched biological functions and pathways  

---

## 🧰 Tools Used
- Galaxy  
- Falco  
- MultiQC  
- Cutadapt  
- STAR  
- featureCounts  
- DESeq2  

---

## ⏱️ Estimated Time
~8 hours

---

## 📚 Data Source
RNA-Seq dataset from *Drosophila melanogaster* (Pasilla gene depletion study)
