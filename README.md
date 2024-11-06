# KO_-Exploratory-Data-Analysis-on-Spotify-2023-Dataset

## I. Intended Learning Outcomes
1. Learn the functions and methods necessary for data cleaning and visualization.
2. Utilize Python functions to create a comprehensive data visualization and wrangling program.

## II. Instructions
Develop a Python script within a Jupyter Notebook to carry out the tasks below. Submit the completed notebook through the designated platform.

### Dataset:
Download the **Spotify 2023** dataset, `spotify-2023.csv`, which includes the following columns:
- `track_name`
- `artist(s)_name`
- `artist_count`
- `released_year`
- `streams`
- `in_spotify_playlists`
- And additional attributes.

Ensure the dataset is in the same directory as your notebook.

### Spotify Data Problem:
Using **data wrangling** and **visualization** techniques, analyze the dataset to answer the following questions. Provide visualizations and concise insights:

#### 1. Data Wrangling Tasks
##### a. Filter and Sort Artist Data
   - Create a DataFrame `artist_df` containing `["artist(s)_name", "artist_count", "streams"]`.
   - Filter to include only artists with more than 10 tracks.
   - Sort by `streams` in descending order and save the resulting DataFrame as `artist_df`.

##### b. Group Release Data by Year
   - Create a DataFrame `release_df` containing `["released_year", "streams"]`.
   - Group by `released_year` and aggregate the sum of `streams`.
   - Filter for years with more than 20 total tracks, and save as `release_df`.

#### 2. Data Visualization Tasks
Create visualizations to examine various aspects of the dataset:

- **Release Year Trends**  
  - A bar chart displaying the number of tracks released per year to identify trends.

- **Top Artists**  
  - A bar chart of the top 10 most frequent artists in the dataset.

- **Platform Presence**  
  - A bar chart comparing the number of tracks in playlists across Spotify, Apple Music, and Deezer.

- **Attributes vs. Streams**  
  - Scatter plots to assess relationships between `streams` and attributes like `bpm`, `danceability`, etc.

- **Heatmap**  
  - A heatmap to show correlations among musical attributes, including `energy`, `acousticness`, and `liveness`.

#### 3. Insights
Provide written interpretations of each key insight from your visualizations.

## III. Setup Instructions

### 1. Install Required Libraries
Ensure you have Python and the following libraries installed: `pandas`, `numpy`, `matplotlib`, and `seaborn`.

To install the libraries:
```bash
pip install pandas numpy matplotlib seaborn
```
### 2. Running the Code
Once you've completed each section of the tasks, run the code in Jupyter Notebook or from the command line to observe the outputs for each task. Below is a brief description of how to run the code for each step:

#### Step-by-step Execution:
1. **Load the Dataset:**
   - Import the dataset into a pandas DataFrame to start data wrangling and visualization.
   - Example:
     ```python
     s_data = pd.read_csv('spotify-2023.csv')
     ```

2. **Data Wrangling:**
   - Filter and clean the data according to the instructions given for each task.
   - Example for filtering artist data:
     ```python
     artist_df = s_data[s_data['artist_count'] > 10].sort_values(by='streams', ascending=False)[["artist(s)_name", "artist_count", "streams"]]
     ```

3. **Data Visualization:**
   - Create visualizations using `matplotlib` and `seaborn` to explore the dataset’s features. 
   - Example for creating a bar chart for top artists:
     ```python
     import matplotlib.pyplot as plt
     artist_df.head(10).plot(kind='bar', x='artist(s)_name', y='streams', title='Top 10 Artists by Streams')
     plt.xlabel('Artist Name')
     plt.ylabel('Streams')
     plt.show()
     ```

4. **Saving Results:**
   - Save the cleaned DataFrames (`artist_df`, `release_df`) as CSV files for future use.
   - Example:
     ```python
     artist_df.to_csv('artist_df.csv', index=False)
     release_df.to_csv('release_df.csv', index=False)
     ```

### 3. Insights
For each of the visualizations, provide a brief written interpretation. Below are a few examples of insights you should look for and document:

- **Release Year Trends:**
  - Analyze how the number of tracks released has changed over time and what that suggests about trends in the music industry. For example, an increasing number of releases in recent years may suggest that music platforms are expanding and artists are more frequently releasing new content.

- **Top Artists:**
  - Identify which artists dominate the platform and discuss why certain artists may have more tracks and higher streams (e.g., popularity, genre, fan base).

- **Platform Presence:**
  - Compare how many tracks are featured on different platforms like Spotify, Apple Music, and Deezer. Insights could discuss the distribution of music across platforms and potential platform dominance.

- **Attributes vs. Streams:**
  - Look for correlations between musical attributes (e.g., `danceability`, `energy`, etc.) and the number of streams. This can help identify what features listeners prefer.

- **Heatmap Analysis:**
  - Discuss which musical attributes are most strongly correlated (e.g., `energy` with `danceability`) and what this might mean for understanding listener preferences.

## IV. Submission
Submit your completed Jupyter Notebook in the designated submission folder. Ensure that:
- Your code is well-commented.
- You follow the instructions for the tasks closely.
- Visualizations are clear and provide meaningful insights.
- Each key insight is explained in the insights section.

Make sure all the required files (`artist_df.csv`, `release_df.csv`, and any generated visualizations) are included in your submission folder.

## V. Example Output
Here is an example of the Python code used to generate the DataFrames and visualizations:

```python
import pandas as pd
import matplotlib.pyplot as plt

# Load the Spotify dataset
s_data = pd.read_csv('spotify-2023.csv')

# Filter artist data and sort by streams
artist_df = s_data[s_data['artist_count'] > 10].sort_values(by='streams', ascending=False)[["artist(s)_name", "artist_count", "streams"]]

# Group release data by year and sum streams
release_df = s_data.groupby("released_year").streams.sum().reset_index()
release_df = release_df[release_df["streams"] > 20]

# Visualize top 10 artists by streams
artist_df.head(10).plot(kind='bar', x='artist(s)_name', y='streams', title='Top 10 Artists by Streams')
plt.xlabel('Artist Name')
plt.ylabel('Streams')
plt.show()

# Save DataFrames as .csv files
artist_df.to_csv('artist_df.csv', index=False)
release_df.to_csv('release_df.csv', index=False)
```
## VI. History
- **V1:** Initial code for data wrangling tasks.
- **V2:** Added visualizations and organized code for clarity.
- **V3:** Completed insights section for each visualization.
- **V4:** Finalized comments and README formatting.
- **V5:** Refined code structure for better performance and readability. Added more detailed explanations in the insights section.
- **V6:** Enhanced visualizations with additional charts and heatmaps for deeper analysis.
- **V7:** Added interactive visualizations with Plotly for improved user experience.
- **V8:** Final adjustments to the README to ensure clarity and completeness. Provided clearer instructions for data setup and running the code.

