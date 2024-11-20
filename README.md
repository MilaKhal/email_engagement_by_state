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

Due to wide confidence intervals, it was diffucult to make any meaningful conclusions based on the mean engagement. 

![image](https://github.com/user-attachments/assets/b30d2f64-1944-4fe9-b76e-4513095411ce)

For more conservative estimates, I used the lower bound of the 95% confidence intervals and organized data from lowest to highest estimate.

![image](https://github.com/user-attachments/assets/2ea7b8b9-c85b-41e5-89e2-61d43e0765b5)

I further plotted lower CI bounds on the map:

![image](https://github.com/user-attachments/assets/cb358ce9-3bbc-4001-8241-e16ae6f20c23)

The visualization revealed an intriguing trend: states with higher engagement rates were predominantly located closer to the West Coast. This suggests that engagement may be influenced more by publishing time than geographic location. All newsletters are sent at 9 AM EST, which corresponds to 8 AM CST and 7 AM MST.

Given the client’s audience of industry professionals, earlier deliveries likely appear at the top of their inboxes while still arriving early enough in the morning to capture their attention. Based on these insights, I recommended experimenting with newsletter delivery times. Publishing one or two hours earlier could potentially increase engagement rates by aligning better with readers' morning routines.
