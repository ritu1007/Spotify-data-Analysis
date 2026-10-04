# Spotify-data-Analysis
This project demonstrates an end-to-end cloud-based data engineering and analytics pipeline for analyzing Spotify music data using AWS services.

The pipeline ingests raw Spotify datasets into Amazon S3, processes and transforms the data using AWS Glue, catalogs the datasets using the AWS Glue Data Catalog, and performs serverless SQL analysis using Amazon Athena. The resulting insights are presented through interactive Amazon QuickSight dashboards.

## Architecture

Spotify Dataset → Amazon S3 → AWS Glue → S3 Processed Data → Glue Data Catalog → Amazon Athena → Amazon QuickSight
Architecture Flow

#### 1.Data Ingestion

Collected Spotify datasets containing information about tracks, artists, albums, genres, popularity, and other attributes.
Uploaded raw datasets into Amazon S3.

#### 2.Data Processing

Used AWS Glue to create ETL jobs for processing the raw data.
Performed data cleansing, transformation, standardization, and handling of missing or duplicate records.
Generated curated datasets for downstream analysis.

#### 3.Data Cataloging

Used AWS Glue Crawlers to automatically discover the schema of datasets stored in S3.
Created tables in the AWS Glue Data Catalog.

#### 4.Data Analysis

Used Amazon Athena to query the curated datasets directly from S3 using SQL.
Performed aggregations and analytical queries to identify trends and patterns in Spotify data.

#### 5.Visualization

Connected Amazon QuickSight with the analytical dataset.
Built interactive dashboards containing charts, filters and visualizations.

## 📂 Data Pipeline

#### 1. Raw Data Layer

Raw Spotify datasets are uploaded to an S3 bucket.

S3
└── spotify-data
    └── raw
        ├── tracks.csv
        ├── artists.csv
        ├── albums.csv
        └── genres.csv

#### 2. ETL Layer

AWS Glue processes the raw datasets and performs:
Data cleansing
Null value handling
Duplicate removal
Data type standardization
Column transformations
Data aggregation
Creation of derived attributes
The transformed datasets are written back to S3.

S3
└── spotify-data
    ├── raw
    └── processed
        ├── tracks
        ├── artists
        ├── albums
        └── genres

#### 3. Analytics Layer

AWS Glue Crawlers scan the processed datasets and create tables in the Glue Data Catalog.
Amazon Athena then queries these tables using SQL.

Example:

SELECT
    artist_name,
    COUNT(*) AS total_tracks,
    AVG(popularity) AS avg_popularity
FROM spotify_tracks
GROUP BY artist_name
ORDER BY avg_popularity DESC;

#### 📊 Analysis Performed

The project analyzes Spotify data to identify:
🎤 Top-performing artists
🎵 Most popular tracks
💿 Album performance
🎶 Genre distribution
📈 Popularity trends
⭐ Average track popularity
🔢 Number of tracks per artist
📊 Artist and album-level statistics
🔍 Relationships between different Spotify attributes

#### 📈 QuickSight Dashboard

The processed data is visualized using Amazon QuickSight:
Top tracks
Genre distribution
Popularity analysis
Top artists
