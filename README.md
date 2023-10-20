# Project: Data Modeling with Apache Cassandra

## 1. Introduction

A startup called Sparkify wants to analyze the data they've been collecting on songs and user activity on their new music streaming app. The analysis team is particularly interested in understanding what songs users are listening to. Currently, there is no easy way to query the data to generate the results, since the data reside in a directory of CSV files on user activity on the app.

They'd like a data engineer to create an Apache Cassandra database which can create queries on song play data to answer the questions, and wish to bring you on the project. Your role is to create a database for this analysis. You'll be able to test your database by running queries given to you by the analytics team from Sparkify to create the results.

## 2. Project Overview

In this project, you'll apply what you've learned on data modeling with Apache Cassandra and complete an ETL pipeline using Python. To complete the project, you will need to model your data by creating tables in Apache Cassandra to run queries. You are provided with part of the ETL pipeline that transfers data from a set of CSV files within a directory to create a streamlined CSV file to model and insert data into Apache Cassandra tables.

We have provided you with a project template that takes care of all the imports and provides a structure for ETL pipeline you'd need to process this data.

## 3. Running the Project

### 3.1 Python Environment

We use `miniconda3` to define the Python environment. Please visit the [link](https://docs.conda.io/projects/miniconda/en/latest/miniconda-install.html) for installation instructions of `miniconda3`.

The `conda.yml` list the Project dependencies

```yaml
name: data-modeling-cassandra
channels:
  - conda-forge
  - defaults
dependencies:
  - python=3.9
  - pandas
  - jupyter
  - pip
  - pip:
    - cassandra-driver
```

Run the following command to create a conda environment.

```bash
$ conda env create -f conda.yml
```

Then, activate the environment by running:

```bash
$ conda activate data-modeling-cassandra
```

### 3.2 Apache-Cassandra Local Cluster

We use docker to run an Apache-Cassandra cluster locally. Please visit the [link](https://www.docker.com/products/docker-desktop/) to download `Docker Desktop`.

The `docker-compose.yml` is the configuration file that makes it easy to spin up a cassandra docker container. Check the port mapping and the volume mapping in the YML file.

```yaml
services:
  cassandra:
    image: cassandra:4.1.3
    ports:
      - "9042:9042"
    volumes:
      - "./cassandra:/var/lib/cassandra"
```

To spin up the docker container, execute:

```bash
$ docker-compose up -d
```

To stop it, execute:

```bash
$ docker-compose down
```

## 4. Project Directory Structure and Files

Tree structure

```
.
├── LICENSE
├── Music_App_ETL_and_Apache_Cassandra_Project.ipynb
├── Project_1B_ Project_Template.ipynb
├── README.md
├── conda.yml
├── docker-compose.yml
├── event_data
│   ├── 2018-11-01-events.csv
│   ├── 2018-11-02-events.csv
│   ├── 2018-11-03-events.csv
│   ├── 2018-11-04-events.csv
│   ├── 2018-11-05-events.csv
│   ├── 2018-11-06-events.csv
│   ├── 2018-11-07-events.csv
│   ├── 2018-11-08-events.csv
│   ├── 2018-11-09-events.csv
│   ├── 2018-11-10-events.csv
│   ├── 2018-11-11-events.csv
│   ├── 2018-11-12-events.csv
│   ├── 2018-11-13-events.csv
│   ├── 2018-11-14-events.csv
│   ├── 2018-11-15-events.csv
│   ├── 2018-11-16-events.csv
│   ├── 2018-11-17-events.csv
│   ├── 2018-11-18-events.csv
│   ├── 2018-11-19-events.csv
│   ├── 2018-11-20-events.csv
│   ├── 2018-11-21-events.csv
│   ├── 2018-11-22-events.csv
│   ├── 2018-11-23-events.csv
│   ├── 2018-11-24-events.csv
│   ├── 2018-11-25-events.csv
│   ├── 2018-11-26-events.csv
│   ├── 2018-11-27-events.csv
│   ├── 2018-11-28-events.csv
│   ├── 2018-11-29-events.csv
│   └── 2018-11-30-events.csv
└── images
    └── image_event_datafile_new.jpg
```

## 4.1 Notebooks

- Project_1B_ Project_Template.ipynb
    - Original Notebook with starting code and instructions

- Music_App_ETL_and_Apache_Cassandra_Project.ipynb
    - Final Notebook with implemented code

## 4.2 Data

The `./event_data` directory contains the CSV files partitioned by date with the events data for the music app. This data is preprocessed and ingested into three Apache-Cassandra tables.