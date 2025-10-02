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

Data is loaded into a staging schema in a Dockerized PostgreSQL database (using pgAdmin for DB management).
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



# Tools & Technologies

Containerization → Docker, Docker Compose

Orchestration → Apache Airflow

Database → PostgreSQL on Docker (pgAdmin for management)

Languages → Python, SQL, DAX query

Testing → Soda (data quality), Pytest (integration)

Visualization → Power BI


# Credits & License

This project is based on MattTheDataEngineer/YT_ELT
, licensed under the MIT License.

My contributions include:

Added Power BI visualizations and KPIs

Used pgAdmin for database management

Created custom dashboards and charts



# Power BI Visualizations

**Video Type and Sum of Views:**


<img width="646" height="436" alt="image" src="https://github.com/user-attachments/assets/87467a18-0839-43a2-9364-4e282b1ab45c" />


As Evident from the chart, youtube shorts rack in substantially higher views compared to normal form content




Views vs Comments count count for each video based on video ID:


<img width="655" height="437" alt="image" src="https://github.com/user-attachments/assets/79eba192-c37f-44eb-a600-86e1e29135c4" />


Likes count surpasses comment count in all the videos




<img width="646" height="439" alt="image" src="https://github.com/user-attachments/assets/891fe525-2b81-424a-adc7-4fea52289da4" />


<img width="797" height="535" alt="image" src="https://github.com/user-attachments/assets/d267bb78-75b9-4b4b-a63f-71859cbd49d7" />


<img width="798" height="490" alt="image" src="https://github.com/user-attachments/assets/596db4dc-fd27-45c5-ab84-10b215b63839" />


<img width="792" height="529" alt="image" src="https://github.com/user-attachments/assets/95d9c80c-870a-4749-877a-104ddbc4449f" />















