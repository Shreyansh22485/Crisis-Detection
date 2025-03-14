# Crisis Detection and Mental Health Risk Analysis System

This repository contains an end-to-end system for analyzing mental health crisis signals from social media data, with a focus on Reddit. The solution covers data collection, text cleaning, sentiment analysis, risk classification using TF-IDF and keyword-based approaches, and geospatial visualization.

## Table of Contents
- [Setup and Dependencies](#setup-and-dependencies)
- [Data Extraction & Preprocessing](#data-extraction--preprocessing)
- [Sentiment Analysis & Crisis Risk Classification](#sentiment-analysis--crisis-risk-classification)
- [Crisis Geolocation & Mapping](#crisis-geolocation--mapping)
- [Usage](#usage)
- [License](#license)

## Setup and Dependencies

Install all required packages by running:

```bash
pip install -r requirements.txt
```

Make sure you also download necessary NLTK data in your script or notebook:

```python
import nltk
nltk.download('stopwords')
nltk.download('punkt')
```

## Data Extraction & Preprocessing

The notebook extracts crisis-related posts from mental health subreddits using a set of predefined keywords such as "depressed", "anxiety", "suicidal", etc. Data including post ID, timestamp, title, content, engagement metrics, and more is collected and then cleaned by:
- Removing URLs, special characters, and digits
- Converting text to lowercase  
- Removing stopwords and emojis

The preprocessed data is stored as a CSV file (`crisis_posts.csv`).

## Sentiment Analysis & Crisis Risk Classification

### Sentiment Analysis
- **VADER Sentiment Analyzer** is used to classify each post as Positive, Neutral, or Negative based on the compound sentiment score.

### Crisis Risk Classification
- A **keyword-based approach** determines risk levels:
  - **High Risk:** Direct crisis language such as “I don’t want to be here anymore”
  - **Moderate Concern:** Posts seeking help or discussing struggles
  - **Low Concern:** General discussions about mental health
- **TF-IDF Analysis** is also used to extract high-risk crisis terms from the corpus, which are then used to enhance the risk classification.

Visualizations in the notebook include bar plots for both sentiment and risk distributions, as well as a heatmap showing their relationship.

## Crisis Geolocation & Mapping

- **Location Extraction:**  
  Using regular expressions, an expanded global city list, and Named Entity Recognition (NER) via spaCy, the system extracts location information from post content.

- **Geocoding:**  
  The extracted locations are converted to latitude and longitude coordinates using Nominatim with caching and error handling.

- **Mapping:**  
  An interactive map is generated using Folium. This map includes color-coded markers based on risk levels, popups with details, and a heatmap layer to visualize the concentration of crisis-related discussions. The resulting map is saved as `crisis_heatmap.html`.

## Usage

1. **Clone the Repository:**

   ```bash
   git clone <repository-url>
   cd GSOC/TEST
   ```

2. **Install Dependencies:**

   ```bash
   pip install -r requirements.txt
   ```

3. **Open the Notebook:**

   Open `try.ipynb` in Visual Studio Code or your preferred Jupyter environment.

4. **Run the Notebook:**

   Execute the cells sequentially to collect, process data, perform sentiment and crisis risk analysis, and generate geospatial visualizations.
