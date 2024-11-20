## 📧 E-Newsletter engagement by U.S. state

### ❓ Research question
**What are the average email click-through rates across U.S. states?**
### 🔍 Background

This project was conducted for an e-newsletter publishing company preparing statistics for a blog post. The goal was to analyze email click-through rates by U.S. states to identify patterns in engagement. The client sought to determine whether engagement rates were consistent across states or if notable differences existed.

### ⚠️Constraints
At first glance, this seemed like a straightforward project. However, it posed several challenges that required strategic thinking and careful planning.
- First, the client did not aggregate their event data by location, necessitating an analysis of individual-level events—such as deliveries, clicks, and opens—for each mailing sent. This involved processing billions of rows of data stored on an outdated and slow on-premises server.
- Second, the release of Apple’s [iOS Mail Privacy Protection](https://www.litmus.com/blog/apple-mail-privacy-protection-for-marketers) feature had inflated email opens, rendering them unreliable for calculating accurate open or click-through rates.

### 💊 Solution

- To address the unreliability of click-through rate calculations based on opens, I recommended using deliveries as the baseline metric for engagement. Specifically, **engagement was measured as the number of clicks per 1,000 delivered emails**, providing a more accurate and consistent metric.
- For the challenges posed by the large dataset and slow server, I proposed **random sampling** of mailings to reduce the volume of data to be processed. This was complemented with **Monte Carlo simulations** (1000 iterations) to ensure robust and reliable results despite the reduced dataset.

### 🛠️ Libraries Used
 - [pandas](https://pandas.pydata.org/)
 - [SQLalchemy](https://www.sqlalchemy.org/) (as a part of a custom package for connecting to the client's MySQL server and retrieving data)
 - [numpy](https://numpy.org/) for random sample generation
 - [tqdm](https://tqdm.github.io/) to track the progress of the simulation
 - [US](https://pypi.org/project/us/) to standartize incosistent U.S. state names into two-letter codes
 - Matplotib, Folium and Tableau for data visualization
### 📋 Findings

