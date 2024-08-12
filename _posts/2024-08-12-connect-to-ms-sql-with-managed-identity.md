---
title: "Connect to MS SQL using pyodbc with Managed Identity"
date: 2024-08-12
---

## Introduction

Azure Managed Identity provides a secure way to connect to Azure resources without storing credentials in your code.
For some reason, there is no good documentation on how to do it from Python, so I decided to write this article to keep the info for myself.

## ODBC connection string

This one is easy. You can find the connection string in the Azure Portal. Go to your Azure SQL Database, click on "Connection strings" and copy the ODBC connection string.

And it won't work.

The reason is that pyodbc uses slightly different connection string format. You need to replace `Authentication=ActiveDirectoryIntegrated;` with `Authentication=ActiveDirectoryMsi;`

Test the connection string using `pyodbc` from the container:

```python
import pyodbc

conn_str = (
    "DRIVER={ODBC Driver 18 for SQL Server};"
    "SERVER=<host>;DATABASE=<database>;"
    "Authentication=ActiveDirectoryMsi;"
)

conn = pyodbc.connect(conn_str)
cursor = conn.cursor()
cursor.execute("SELECT 1")
row = cursor.fetchone()
print(row)
```

## SQLAlchemy connection string

You can directly convert the ODBC connection string to the SQLAlchemy connection string.
It would look like:

```
    mssql+pyodc://<identity-name>@<host>/<database>?Authentication=ActiveDirectoryMsi&driver={ODBC+Driver+18+for+SQL+Server}
```

One thing to note is that you need to add `driver=ODBC Driver 18 for SQL Server` to the connection string. It is possible to set it in the environment variable, but I found it easier to set it in the connection string. Because the upgrade is done using the code changes, not the combination of the code changes and the environment changes.