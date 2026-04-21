# Data-Engineering-Group-Project

This project uses PySpark and the MovieLens dataset to build a simple medallion-style pipeline with Bronze, Silver, and Gold layers. The main deliverable in this repo is the notebook `Phase_4_Pipline_architecture_and_governance.ipynb`, which documents the pipeline and runs the transformations.

## Data Source

MovieLens dataset from GroupLens:
https://grouplens.org/datasets/movielens/

The notebook expects these raw source files in the Bronze layer:

- `movies.csv`
- `ratings.csv`
- `tags.csv`
- `links.csv`

## Project Files

- `Phase_4_Pipline_architecture_and_governance.ipynb`: main Spark notebook for ingestion, cleaning, governance notes, and Gold-layer outputs
- `DataEngineeringPhase2_ER_Diagram.drawio (1).png`: ERD image used for project documentation

## What the Notebook Does

- Starts a local Spark session in Colab
- Mounts Google Drive for data access
- Reads MovieLens CSV files from the Bronze path
- Applies schema enforcement, timestamp conversion, safe casting, etc.
- Produces Silver-layer datasets for cleaned movies, ratings, tags, and exploded genres
- Builds Gold-layer outputs for top-rated movies

## How to Run

1. Open `Phase_4_Pipline_architecture_and_governance.ipynb` in Google Colab.
2. Make sure the MovieLens CSV files are available in your Bronze location.
3. Update the path variables in the notebook to match your storage locations:
	- `bronze_path`
	- `silver_path`
	- `gold_path`
4. Run the notebook from top to bottom.

The notebook is currently set up to use Google Drive paths under `/content/drive/MyDrive/`.

## Current Outputs

The pipeline writes these outputs:

- Silver: `cleaned_movies_parquet`, `cleaned_ratings_csv`, `tagged_high_csv`, `movies_exploded_parquet`
- Gold: `top_20_movies`

