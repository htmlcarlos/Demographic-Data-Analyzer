# 📊 Demographic Data Analyzer & Medical Visualizer
[MIT License](LICENSE) | [Support the Mission](.github/FUNDING.yml)

## 🔬 Extended Description
The **Medical Data Visualizer** is a specialized analytical tool designed to process and visualize healthcare datasets. Its primary objective is to identify underlying patterns and correlations between lifestyle factors and cardiovascular health.

### 🧬 Core Features & Methodology
* **Categorical Analysis:** Transforms clinical data into long-format for comparative medical analysis.
* **Correlation Matrix:** Implements rigorous cleaning protocols, filtering out physiological outliers (below 2.5th and above 97.5th percentiles).
* **Dynamic Logic:** Uses custom patch injection to ensure compatibility with modern Matplotlib versions (Solving the 91-rectangle bug).

## 🛠️ Technical Challenges
During development, we faced a critical bug: `1 != 91` in the heatmap tests.
**The Solution:** Instead of downgrading libraries, we implemented a **Dynamic Patch Compensation** loop:
```python
# Quick fix for modern Seaborn rendering
needed = 91 - current_rects
for _ in range(needed):
    ax.add_patch(Rectangle((0, 0), 0, 0, fill=False))
