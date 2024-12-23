# Content-Based Filtering for Game Recommendations

## Overview
This project implements a content-based filtering approach to recommend games based on similarity between game features and user preferences.

## Methodology
### 1. Dataset Preprocessing
The Steam Store Games dataset was preprocessed to ensure compatibility with the recommendation algorithms. Key preprocessing steps included:

- **Handling Missing Values**: Replaced missing values for features like categories and genres with default or empty values.
- **One-Hot Encoding**: Encoded categorical features (categories, genres, platforms) into numerical representations suitable for similarity calculations.
- **Normalization**: Normalized numerical features such as price, positive ratings, and average playtime for consistent scaling.
- **Textual Embeddings**: Generated embeddings for descriptive fields like game descriptions and tags using TF-IDF to capture semantic information.

### 2. Game-to-Game Recommendation System
- **Similarity Calculation**: A cosine similarity matrix was computed to identify similar games based on feature vectors.
- **Weighted Features**: Features like genres, categories, and platforms were weighted to emphasize their importance.
- **Exploration**: Users can explore games similar to a selected title.

#### Example Recommendations for 'Counterstrike':
1. Team Fortress Classic (Similarity: 1.00)
2. Deathmatch Classic (Similarity: 1.00)
3. Ricochet (Similarity: 0.90)
4. Day of Defeat (Similarity: 0.79)
5. Half-Life Deathmatch: Source (Similarity: 0.79)

### 3. User-Preference-Based Recommendation System
- **Dynamic User Profiles**: Created by averaging the feature vectors of games liked by the user.
- **Cosine Similarity**: Computed between the user profile and all games in the dataset to generate personalized recommendations.
- **Filtering Mechanisms**: Refined recommendations based on user-defined constraints:
  - **Price Range**: Matches recommendations to the user’s budget.
  - **Platform Compatibility**: Filters games to match preferred platforms (e.g., Windows, Mac, Linux).
  - **Age Suitability**: Tailors recommendations to age preferences.

### 4. Evaluation
The performance of the systems was evaluated using **Precision@K** and **Recall@K** metrics to assess relevance and effectiveness.

### 5. Deployment
The system was deployed using [Gradio](https://gradio.app), providing an interactive interface for users to:
- Select a recommendation mode (game-to-game or user-preference-based).
- Input preferences (e.g., budget, platform, favorite games).
- Receive personalized recommendations dynamically.

## Recommendation Algorithms
- **Game-to-Game Recommendations**: Used cosine similarity to find similar titles.
- **User Profile-Based Recommendations**: Averaged the features of liked games to create a user profile vector and calculated cosine similarity with all games.

## Filtering Mechanism
Filters were implemented to refine recommendations based on:
- Price range
- Platform compatibility
- Age suitability

## Experiments
### Dataset
The Steam dataset contains over 10,000 games with features such as categories, genres, platforms, prices, and user ratings. Missing values were replaced with empty strings, and numerical features were normalized.

### User-Preference Recommender
#### Experiment Configurations
Simulated three user profiles:
1. **FPS Enthusiast**: Prefers FPS games on Windows with no budget constraints and a maximum age of 18 for the game.
2. **Strategy Lover**: Prefers strategy games on Mac with a budget under $30 and a maximum age of 16 for the game.
3. **Budget Gamer**: Prefers games under $10 on Linux and a maximum age of 18 for the game.

#### Evaluation Metrics
Used **Precision@K** and **Recall@K** to evaluate recommendation performance, focusing on the relevance of the top-K recommendations relative to the user's preferences.

## Example Results
### Game-to-Game Recommendations for 'Counterstrike':
1. Team Fortress Classic (Similarity: 1.00)
2. Deathmatch Classic (Similarity: 1.00)
3. Ricochet (Similarity: 0.90)
4. Day of Defeat (Similarity: 0.79)
5. Half-Life Deathmatch: Source (Similarity: 0.79)

## Deployment
The interactive system enables users to:
- Select a recommendation mode.
- Input their preferences (budget, platform, favorite games).
- Receive recommendations dynamically via the Gradio interface.
