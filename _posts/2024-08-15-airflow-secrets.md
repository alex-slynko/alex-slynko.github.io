---
title: "Problems with storing secrets as environment variables in Airflow"
date: 2024-08-15
---

Airflow provides three ways to store connections: environment variables, metadata database, and external secret backend.

Environment variables are the simplest way to store secrets. If you run Airflow in Kubernetes, you can use secrets there and mount them as environment variables. This simplifies secrets upgrade since task will get the new secret value on start.

We use it and have two not so obvious problems with it:

1. We have a DAG to validate the connections and secret is needed during the DAG processing. This means that we need to restart the DAG processor to get the new secret value.
2. We have a legacy operator that gets data from some datasource, puts it in Pandas DataFrame, processes it and sends it to another datasource. It uses function for each of the steps and the functions are passed as parameters to the operator. This causes the function being processed in scheduler (not in the worker) and to rotate the value we had to restart the scheduler.
