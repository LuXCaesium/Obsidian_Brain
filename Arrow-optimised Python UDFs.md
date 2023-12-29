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

Arrow-Optimised Python UDFs significantly improve performance, and at its core lies **Apache Arrow**, a standardised cross-language columnr in-memroy data representation. The UDFs under arrow bypass the serialisation steps leading to higher performance. You can impliment this by doing the following:

```python
@udf(returnType='int', useArrow=True) #An Arrow Python UDF
def arrow_slen(s):
	return len(s)
```

You can also enable Arrow optimisation on all UDFs in a SparkSession:

```python
spark.conf.set("spark.sql.execution.pythonUDF.arrow.enabled", True)

@udf(returnType='int')
def arrow_slen(s):
	return len(s)
```

## Faster (De)serialisation

Apache Arrow is a columnar in-memory data format that provides efficient data interchange. Unlike Pickle, which serialises the entire row as an object, Arrow stores data in a column-oriented format allowing for better compression & memory locality, which is suitable to analytical workloads.
