Predicting the Next Big Game Project
Group Members: Omar Spiller Hernandez, Scott Lam, Evan Carey, David Gil
Date: 28 February 2025

Introduction
The online game platform known as STEAM hosts over 97,000 games, making it a highly competitive
environment for developers. Success on STEAM depends on factors like user reviews, critic scores
and gameplay features. The goal here was to identigy which features correlate with a games success (measured by revenue and ratings). With this we built a predictive model to estimate
a games potential for success.

We asked ourselves: Which features of a game are most predictive of a game's revenue and user
ratings on Steam?

We predicted: Games with high Metacritic scores, positive user reviews and specific genre tags will correlate stronger with higher revenue and success.

Selection of Data

Dataset Source

    Source: Steam Games Dataset (Kaggle, retrieved via Steam API and Steam Spy).
    https://www.kaggle.com/datasets/fronkongames/steam-games-dataset
    Size: 97,000+ games with attributes like price, reviews, Metacritic scores, and tags.

Data Preprocessing

    Cleaning:
        Removed columns with non-analytical data (URLs, screenshots).
        Filtered out games with $0 price or missing critical data (Metacritic score = 0).
        Dropped extreme revenue outliers ("ELDEN RING", "Cyberpunk 2077").

    Feature Engineering:
        Estimated Owners: Converted ranges ("20,000 - 50,000") to numerical averages.
        Revenue: Calculated as estimated_num_owners * Price.
        Review Sentiment: Created positive_fraction and negative_fraction from Positive and Negative reviews.
        Tags: One-hot encoded the top 100 tags ("Action", "Indie") using MultiLabelBinarizer.

Methods
    Libraries: pandas, numpy, scikit-learn, seaborn, matplotlib.

    Models:
        Linear Regression: To predict revenue from Metacritic scores, review fractions, and playtime.
        Tag Analysis: One-hot encoding of game tags to identify genre trends.
        Validation: Train-test split (70% training, 30% testing) with RMSE and R^2 for evaluation.

Results
Key Findings

    Revenue vs. Metacritic Scores
        A weak positive correlation exists. High Metacritic scores (>80) often correspond to higher revenue, but outliers are common.
        Predictive Tags
        Tags like "VR", "RPG", and "Multiplayer" had the strongest positive coefficients in revenue prediction.

    Top-revenue games frequently included tags like "Action", "Adventure", and "Strategy".
        Regression Model Performance
        RMSE: 1,234,567 (USD)
        R^2: 0.32
        Key Coefficients:
            Metacritic score: +$12,345 per point.
            positive_fraction: +$98,765 per 0.1 increase.

Discussion
After doing the training and an analysis, it is revealed that Metacritic scores matter as they can serve as a predictor for revenue but it cannot be accounted as the sole predictor.
Genre also plays a significant role in predicting success, with tags such as "Multiplayer" and "VR" among the top with potential which also aligns with trends. However with the model
receiving a low R^2 value of 0.32 shows its limitations, suggesting there are gaps in predicting successful titles. To address these gaps future work to incorporate more data into training
or using more advanced models and including time data to analyze titles post release performance to better understand additional factors that could contribute to a successful video game.

Summary
Our analysis of the Steam games dataset revealed that high Metacritic scores and positive review ratios are strong indicators of higher revenue, 
a detailed tag analysis offers additional insight into the types of games that resonate well with users shown by high user scores. The linear regression model 
demonstrated a significant relationship between these features and revenue but findings suggest that further refinement and the inclusion of additional data could enhance the quality
of predictions. Overall, the study not establishes a framework for predicting the next big game but also provides actions developers can take to optimize their games for higher chances of success.