---
created: 2023-12-29 18:14
tags:
  - DataEngineering
  - Python
  - "#Databricks"
---
Source: [Arrow-optimized Python UDFs in Apache Spark™ 3.5](https://www.databricks.com/blog/arrow-optimized-python-udfs-apache-sparktm-35)

# Arrow-Optimised Python UDFs in Apache Spark

In Apache Spark, Python User-Defined Functions (UDFs) are one of the most popular features, and allow users to craft custom functions for their own data processing needs. However currently they rely on cloudpickle for serialisation & deserialisation, which present performance bottlenecks when dealing with large data inputs/outputs.

Arrow-Optimised Python UDFs significantly improve performance, and at its core lies **Apache Arrow**, a standardised cross-language columnr in-memroy data representation.
