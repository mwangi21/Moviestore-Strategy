# Moviestore-Strategy
# Movie Data Analysis for Sinemas Investment Insights

##   Requirements

To reproduce the analysis in this project, you will need the following software and Python libraries:

**Software:**

* **Python 3.x:** It is recommended to use Python 3.6 or later.

**Python Libraries:**

You can install these libraries using pip.

* **pandas:** For data manipulation and analysis.
* **matplotlib:** For creating visualizations.
* **seaborn:** For enhanced data visualizations (if used).
* **numpy:** For numerical computations (if used).

**Installation Instructions:**

1.  Ensure you have Python 3.x installed on your system. You can check your Python version by opening a terminal and running:

    ```bash
    python --version
    ```

2.  You can install the required Python libraries using pip. It's highly recommended to create a virtual environment to manage your project dependencies.

    * **Create a virtual environment (optional but recommended):**

        ```bash
        python -m venv .venv  # Create a virtual environment named '.venv'
        source .venv/bin/activate  # On Linux/macOS
        .venv\Scripts\activate  # On Windows
        ```

    * **Install the libraries:**

        ```bash
        pip install pandas matplotlib seaborn numpy  # Install all at once
        #OR
        pip install pandas
        pip install numpy
        pip install matplotlib
        pip install seaborn
        pip install scikit-learn
        pip install scipy
        ```

This repository is organized to facilitate easy access to project files and resources. Below is a guide to help you navigate its contents:

* **Dataset/:** This directory contains the data used in the analysis. 
* **Notebooks/:** This directory contains the Jupyter Notebooks used for data exploration, preparation, analysis, and visualization.
* **.gitignore:** This file specifies any files or directories that should not be tracked by Git.
* **README.md:** This file provides a comprehensive overview of the aviation accident analysis project.
# Project Overview

# Project Overview

With Sinema's strategic decision to enter the movie industry through the establishment of its own movie studio, our team has been assigned to conduct a data-driven exploration of the current film market. Using the datasets provided, we aim to analyze recent trends in the film industry to identify which types of films are performing best across various key performance indicators such as box office revenue, audience ratings, genre popularity, and critical acclaim.

The insights derived from this analysis will guide Sinema's decision-making process for the new studio, helping determine the best types of films to produce in order to maximize return on investment and market success. Ultimately, we aim to make strategic recommendations from these insights.

# Business Understanding

We aim to provide data-backed insights that will inform the company’s entry strategy into the movie industry. We believe this will ensure that the newly established movie studio invests in movie genres that have proven commercial and critical success.

By leveraging proven trends in the film industry, we can ensure that the company reduces the risks associated with new ventures and also position the newly establised studio for early success in a very competitive market.

# Objectives 
The main objectives for the study are:

1.**Quantify Movie Profitability** - Use financial data (production budgets and worldwide gross) to compute Return on Investment (ROI) and identify the most and least profitable films.

2.**Analyze Movie Ratings** - Explore ratings data to understand if and how factors such as runtime, publisher influence critical scores and genre correlate to movie ratings.

3.**Find blockbuster movies globally** - We aim to find movies that performed exceptionally not only domestically but also worldwide using the worldwide_gross data

4.**Investigate the runtime vs movie rating** - Find out whether the average runtime of a movie has any influence on the movie ratings.

# 1. Data Understanding
In this notebook, we explore multiple movie-related datasets to understand their structure and prepare them for further analysis. This includes data from **TMDb**, **The Numbers**, **Box Office Mojo**, and **Rotten Tomatoes**.

First we import the relevant python libraries and loading the datasets.
- `tmdb_movies`: Movies from The Movie Database (TMDb)
- `tn_movie_budgets`: Budget and revenue data from The Numbers
- `rt_reviews`: Movie reviews from Rotten Tomatoes
- `rt_movie_info`: Additional Rotten Tomatoes metadata

We explore each dataset using the imported libraries to get a glimpse of the columns present in each dataset as the shapes of the DataFrames present using methods such as; `.head()`, `.info()`, and `.tail()`.This gives us a brief understanding of what each dataset entails.


# 2. Data cleaning 
In order to perform calculations and visualizations thereafter we first prepare our raw data. We remove missing values. We drop irrelevant columns and merge some datasets with common columns to get a comprehensive view. This is the data cleaning process outlined in the following cells.
  - Cleaning Financial Figures - normalizing the data by removing currency symbols and commas, hence changing the data type to float for easier mathematical calculations.
  - Creating a ROI(Return On Investment) column by subracting production budget from worldwide gross then dividing by production budget. This helps us know which movies were profitable and those that were not.
  - Merging movie datasets - Combining the `tmdb_movies` and `tn_movie_budgets` datasets allows for more comprehensive analysis by utilizing the attributes from TMDb and the financial details from The Numbers.

# 3. Visualizations
  In order to observe trends and patterns from the datasets we construct various visualizations that will help to provide insights later on. We imported the various python libraries required for plotting.

  ## 📊  Top 10 Profitable Movies
  **Visualization of financial data using profit**
  - Comparing worldwide gross with production budget to visualize the profit the movies made.
      ![Profit_vs_worlwidegross](./images/Profit_vs_worlwidegross.png)
  **Visualization of financial data using ROI**

  - Comparing the production budget to ROI enables us to cater for movies like "Deep throat" that had significantly lower production     budgets and did not make alot of profit compared to movies like Avatar but made very high ROI because of the low productuction budget.
    ![ROI_vs_worldwidegross](./images/ROI_vs_worldwidegross.png)
      
  ## 🎬 Comparing the ratings to runtime using Rotten tomatoes data
  We cleaned and merged the `rt_reviews` and `rt_movie_info` datasets using movie `id`. This allowed us to explore relationships between movie ratings, runtime, and publisher reviews. These plots help to identify patterns in critical reviews based on runtime or reviewing source 
  We construct the following visualizations:

  - **Scatter Plot** Shows the distributon of runtime against the rating.
    ![Runtime_vs_rating](./images/Runtime_vs_rating.png)
  - **Bar Plot**  Shows the average Runtime by Rating.
    ![runtimeaverage_vs_rating](./images/runtimeaverage_vs_rating.png)
    
  - **Boxplot** Shows Ratings by Publisher
    ![Publisher_vs_rating](./images/Publisher_vs_rating.png)

    ### Key Findings:
- **Scatter Plot:** Showed that most movies fall within a typical runtime range (80–120 minutes), and their ratings vary with some outliers.
- **Bar Plot of Avg. Runtime by Rating:** Indicates that higher-rated films tend to be slightly longer on average.
- **Boxplot of Ratings by Publisher:** Shows potential bias across different review publishers.

# 4. Statistical analysis.
To confirm our insights we conduct statisctical analysis to confirm whether our conclusions are valid.These incluse:

**linear regression**  and **Z test**
In this section we use different statistical packages in python namely "sklearn", "scipy" and "statsmodels"

![domesticgross_vs_domestic_gross](./images/domesticgross_vs_domestic_gross.png)

### Conclusion
This shows that there's a **positive correlation**.
Positive Correlation:
The regression line typically slopes upward, indicating a positive relationship — as domestic gross increases, worldwide gross tends to increase too.

Fit of the Line (Rough Visual R²):
If most of the data points hug the regression line closely, the relationship is strong, and domestic gross is a good predictor of worldwide gross.
If the points are widely scattered, the relationship is weaker, and other factors (like international appeal, genre, or marketing) also play a big role.

**Outliers**:
You can see some movies far above the line, it means those films performed much better internationally than locally.
If a few are below the line, those movies underperformed internationally compared to their domestic performance.



# 5. Final Insights & Recommendations

### Key Takeaways:
- **Financial Data:** Comparing budget with worldwide gross can be viewed usng either 'Profit' or 'ROI'.
- **Ratings Data:** No clear-cut relationship between runtime and rating, but publishers show different scoring behaviors.
- **Visualizations:** Scatter and regression plots confirmed positive correlations between budget and gross revenue, more specifically domestically and worldwide.
- **Merged Dataset Value:** Combining attributes of (TMDb, RT) with financials (The Numbers) enriched analysis.

Based on the analysis, the following recommendations are made:

* **Invest in High-ROI, Lower-Budget Films**: Prioritize projects with strong creative concepts and efficient production strategies to maximize returns, even with limited budgets.
* **Balance Budget with Revenue Expectations**: Carefully evaluate a film's potential revenue in relation to its budget, and avoid relying solely on high budgets to guarantee success.
* **Prioritize Film Quality and Marketing**: Focus on developing high-quality films with compelling stories and strong production values, and invest in effective marketing to reach the target audience.
* **Conduct Further Genre Analysis**: Perform an in-depth analysis of genre-specific data to identify the most profitable genres and inform production decisions.
* **Monitor Publisher Influence on Reviews**: Be aware of potential differences in rating tendencies among different publishers to better interpret reviews and gauge overall critical reception.

# 6. Limitations
1. Combining attributes from differnt datasets leads to the loss of some several rows of data that could have had an impact on the study.
2. Some financial data on the worlwide and domestic gross may be skewed due to copyright infringment and pirating
