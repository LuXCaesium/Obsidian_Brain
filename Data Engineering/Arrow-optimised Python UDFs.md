---
created: 2023-12-29 18:14
tags:
  - DataEngineering
  - Python
  - "#Databricks"
---
Source: [Arrow-optimized Python UDFs in Apache Spark™ 3.5](https://www.databricks.com/blog/arrow-optimized-python-udfs-apache-sparktm-35)

# Arrow-Optimised Python UDFs in Apache Spark

Python User-Defined Functions (UDF's) enables users to run arbitrary code against PySpark columns. It uses cloudpickle for de-serialisation and executes row by row.

This de-serialisation, that is the data interchange between worker JVM and spawned Python sub-process which actually executes the UDF, is a major performance bottleneck. 

Arrow-Optimised Python UDFs significantly improve performance, and at its core lies **Apache Arrow**, a standardised cross-language columnar in-memory data representation. The UDFs under arrow bypass the de-serialisation steps leading to higher performance. You can implement this by doing the following:

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

## Faster De-Serialisation

Apache Arrow is a columnar in-memory data format that provides efficient data interchange. Unlike Pickle, which serialises the entire row as an object, Arrow stores data in a column-oriented format allowing for better compression & memory locality, which is suitable to analytical workloads.

## Standardised Type Coercion

UDF type coercion poses challenges when the python values returned by the UDF do not align with the user specified return type. Pickled Python UDF's type coercion relies on None as a fallback for type mismatches, leading to data loss. Arrow has a well defined set of rules for coercion relieving these issues:

```python 
>>> df = spark.createDataFrame(['1', '2'], schema='string')
>>> df.select(udf(lambda x: x, 'int', useArrow=True)('value').alias('str_to_int')).show()
+----------+                                                                    
|str_to_int|
+----------+
|         1|
|         2|
+----------+
>>> df.select(udf(lambda x: x, 'int', useArrow=False)('value').alias('str_to_int')).show()
+----------+
|str_to_int|
+----------+
|      NULL|
|      NULL|
+----------+
```

Above we see that Arrow will successfully coerce integers stored as a string back to integers as specified.