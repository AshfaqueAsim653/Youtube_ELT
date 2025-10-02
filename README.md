# YouTube ELT Data Pipeline


# Architecture

<img width="1195" height="720" alt="image" src="https://github.com/user-attachments/assets/893412be-0b98-45d1-86d0-2db52c5ce651" />


# Motivation

The goal of this project is to gain hands-on experience with modern data engineering tools like Python, Docker, Airflow, and PostgreSQL by building a fully functional ELT pipeline.

To make the pipeline robust and production-ready:

Data quality testing is implemented with Soda.

Integration testing is done using Pytest.

The pipeline is containerized with Docker and orchestrated with Airflow.

Data visualization and KPIs are added using Power BI.


# Dataset

Source: YouTube Data API

Channel used for this project: MrBeast (project can be replicated for any channel by changing the channel ID).

Variables extracted:

Video ID

Video Title

Upload Date

Duration

Video Views

Likes Count

Comments Count

Video Type (Shorts / Normal)



# Project Summary

The ELT pipeline consists of:

Extract:

Python scripts fetch raw JSON data from the YouTube API.

Load:

Data is loaded into a staging schema in a Dockerized PostgreSQL database (using pgAdmin for DB management instead of DBeaver).

Subsequent API calls update existing records in the database with new values (upsert) to keep the data current.

Transform:

Minor transformations applied in Postgres before loading into the core schema.

Ensures staging and core schemas remain synchronized with the latest API data.

Orchestration:

Airflow DAGs schedule and manage the workflow:

extract_youtube_data → Fetch raw data

load_to_postgres → Load into staging & core schemas, updating existing records as needed

data_quality_tests → Validate data quality with Soda

Visualization:

Power BI dashboards created using ODBC connection to Postgres

KPIs designed for meaningful insights (engagement rate, views over time, Shorts vs Normal performance)

