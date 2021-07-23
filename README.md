# Introduction

In this project, I'll apply what I've learned on data modeling with Apache
Cassandra course (part of Udacity Data Engineering Nanodegree) and complete an
ETL pipeline using Python. To complete the project, I will need to model the data
by creating tables in Apache Cassandra to run queries. The deliverable is an
ETL pipeline that transfers data from a set of CSV files within a directory
to create a streamlined CSV file to model and insert data into Apache Cassandra tables.

# Background

A startup called Sparkify wants to analyze the data they've been collecting on
songs and user activity on their new music streaming app. The analysis team is
particularly interested in understanding what songs users are listening to.
Currently, there is no easy way to query the data to generate the results, since
the data reside in a directory of CSV files on user activity on the app.

They'd like a data engineer to create an Apache Cassandra database which can
create queries on song play data to answer the questions. The requirement is to 
create a database for this analysis.

# Datasets

For this project, I'll be working with one dataset: event_data. The directory
of CSV files partitioned by date. Here are examples of filepaths to two files
in the dataset:

```
event_data/2018-11-08-events.csv
event_data/2018-11-09-events.csv
```

# Development environment
This project can be implemented on a local machine using Python3 and Docker. The 
instructions here assume that VS Code is used as a development environment,
especially the way `ipython` kernel is setup instead of using `jupyter notebook`.
It is good practice not to contaminate your global Python installation by
installing dependencies that are specific to this project. The first step 
therefore is to create a virtual Python environment. We will utilise the most
basic approach by creating an environment using `venv` module. At the root of 
the project run the following commands.

```shell
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
ipython kernel install --user --name=dend-c1-data-modeling-with-cassandra
```

Now that the virtual environment is ready. The next step is to spin up a single
node `Cassandra` cluster. The cleanest way is to run an official `Docker` container
and we can do so by deploying the stack.

```shell
docker stack deploy -c cassandra-stack.yml cassandra
```
If the `Docker` engine is not running in `swarm` mode then it is also possible to
use `docker-compose` to deploy this stack.
