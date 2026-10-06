# ERROR_LOG.md

## Project 1A – Autonomous Financial Research Agent

I went through the project document and noted the following 7 factual/logical errors. I also checked the corrections before adding them here.

---

### 1. Memory Utilization formula is incorrect

**Location:** Part A – Section A5.2, Metric AB-4

The document describes AB-4 as the ratio of memory hits to total external API calls, but the formula says to multiply `memory_hits` by `total_api_calls`.

**What is wrong:**  
Multiplying the two values does not give a ratio.

**Correction:**  
The formula should be:

`memory_hits / total_external_api_calls`

This gives the percentage/ratio of external calls that were satisfied using memory.

---

### 2. 10-Q is described as audited

**Location:** Part A – Section A6.2, Source Reliability Hierarchy

The document says that SEC 10-K and 10-Q filings are audited.

**What is wrong:**  
10-K annual reports contain audited financial statements, while 10-Q quarterly reports generally contain unaudited financial statements.

**Correction:**  
The statement should distinguish between 10-K (audited) and 10-Q (generally unaudited).

---

### 3. SCAP is placed in the wrong year

**Location:** Part A – Section A7.3, Handling Ambiguous Queries

The document says that the first US bank stress tests under SCAP were conducted in 2007 following the Dodd-Frank Act.

**What is wrong:**  
The Federal Reserve's Supervisory Capital Assessment Program (SCAP) was conducted in 2009. Dodd-Frank was enacted in 2010, so it could not have been the reason for SCAP in 2007.

**Correction:**  
SCAP should be associated with 2009, and the Dodd-Frank reference should not be used as its cause.

---

### 4. The scoring dimensions do not match the text

**Location:** Part B – Section B3.1, Gamified Simulation

The section says that each challenge is scored across five dimensions.

However, the table lists only:

- Accuracy
- Completeness
- Insight
- Architecture

followed by the Total.

**What is wrong:**  
There are four scoring dimensions in the table, not five.

**Correction:**  
Either change the description to four dimensions or add the missing fifth scoring dimension to the table.

---

### 5. Form 20-F is incorrectly described as an Indian MCA filing

**Location:** Part C – Section C4.2

The document says that Indian companies file annual returns using Form 20-F with the Ministry of Corporate Affairs (MCA).

**What is wrong:**  
Form 20-F is an SEC filing used by foreign private issuers in the United States. It is not the Indian MCA annual return form.

**Correction:**  
For Indian company annual returns, the relevant MCA filing is MGT-7 (or MGT-7A where applicable).

---

### 6. The embedding dimension for text-embedding-3-large is misleading

**Location:** Part E – Section E2.2

The document lists `text-embedding-3-large` as having 1024 dimensions.

**What is wrong:**  
The model supports up to 3072 dimensions. A 1024-dimensional embedding can be requested as a reduced dimension, but 1024 is not the model's maximum/default dimensionality.

**Correction:**  
The documentation should state that the model supports up to 3072 dimensions and that the `dimensions` parameter can be used when a smaller size such as 1024 is required.

---

### 7. GPT-4o rate limits are incorrectly labelled as free-tier limits

**Location:** Part E – Section E3.1

The document lists GPT-4o as having 500 requests per minute and 30,000 tokens per minute on the free tier.

**What is wrong:**  
Those limits correspond to a paid API usage tier (Tier 1), not the free tier.

**Correction:**  
The document should not describe 500 RPM / 30,000 TPM as free-tier GPT-4o limits. The applicable limits depend on the API usage tier.

---

## Notes

These are the seven errors I identified while reviewing the project document. I kept the explanations short and focused on what was actually wrong and what needs to be changed.
