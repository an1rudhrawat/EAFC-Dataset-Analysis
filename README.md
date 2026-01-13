**EA FC 2026 Player Rating Audit & Exploratory Analysis**

**Overview**

This project is a **data science analysis of EA FC 2026 player data**, combining broad exploratory analysis with a focused **audit of EA's Overall Rating (OVR) system**.

The project begins with dataset-wide exploration (player distribution, ratings, demographics) and then narrows down to a **role-specific audit of male Central Midfielders (CMs)** to study internal rating consistency.

---

**Motivation**

EA FC player ratings are widely referenced, yet the logic behind OVR aggregation is not publicly available.
This project aims to:

* Understand the **structure and distribution** of the dataset
* Explore how ratings vary across **gender, position, and geography**
* Audit whether EA's OVR aligns with **attribute-based performance indicators**
* Identify **system-level patterns**, not just player-level anecdotes

The emphasis is on **reasoning, statistical discipline, and interpretability** rather than prediction.

---

**Dataset Exploration (EDA)**

Before the audit, extensive exploratory analysis was performed to understand the dataset context.

**Key EDA Components**

* **Player distribution analysis**

  * Gender-wise player counts
  * Position-wise player counts
* **Rating-based analysis**

  * OVR distributions
  * PPM (Price per Match / Points per Match) style metric analysis *(as applicable in dataset)*
  * Ranking-based comparisons
* **Geographical analysis**

  * Player count by country
  * Player count by continent
* **Visualizations**

  * Bar charts, histograms, and comparative plots
  * Distribution and proportion-based graphs to reveal dataset imbalance

These steps establish **context** and prevent isolated or misleading conclusions in later analysis.

---

**Focused Audit Scope**

After dataset-level EDA, the analysis narrows to a controlled population:

* **Dataset:** EA FC 2026
* **Population:** Male players with primary position = Central Midfielder (CM)
* **Reason:** Ensures role-consistent and statistically meaningful comparisons

All statistics in the audit phase are computed **within the CM population**.

---

**Methodology (Audit Phase)**

**1. Attribute Selection**

CM-relevant attributes were selected based on role requirements:

* Vision
* Short Passing
* Long Passing
* Ball Control
* Reactions
* Stamina
* Composure

---

**2. Standardization**

* All selected attributes were **z-score normalized within the CM population**
* EA's OVR was also standardized for scale-consistent comparison

This avoids invalid comparisons between absolute ratings and relative performance scores.

---

**3. Composite CM Performance Score**

A composite CM score was constructed by:

* averaging standardized CM attributes
* using equal weights as a neutral baseline

This score represents **relative CM performance**, not an absolute rating replacement.

---

**4. Deviation Analysis (Core Audit)**

The audit signal is defined as:

> **Deviation = Standardized OVR - Attribute-based CM Score**

This measures disagreement between EA's rating and attribute-driven evidence.

---

**Visual Analysis**

The project relies heavily on **visual diagnostics**, including:

* **Histograms**

  * OVR distributions
  * Deviation distributions
* **Scatter plots**

  * Deviation vs OVR (elite-tier analysis)
* **Bar charts**

  * Player counts by gender, position, country, and continent
* **Comparative plots**

  * Ranking and rating-based comparisons

System-level patterns are analyzed **before** any player-level inspection.

---

**Key Findings**

* EA's OVR is **aligned with attribute-based performance on average**
* Deviation distribution is centered near zero, indicating no global bias
* **Deviation magnitude increases at higher OVR levels**, suggesting:

  * non-linear aggregation
  * elite-tier inflation beyond attribute-only evidence
* Dataset-level EDA reveals clear **imbalances by gender, position, and geography**, which contextualize rating behavior

---

**Tools & Libraries**

* Python
* NumPy
* Pandas
* Matplotlib
* Plotly

---

**Future Work**

* Attribute weighting using variance or PCA
* Cross-position audits (CDM, CAM, wingers)
* Bias analysis using age, league, or reputation variables
* Rank-based consistency analysis
* Temporal comparison across EA FC editions


