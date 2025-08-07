# PySpark Quick Reference Guide

## 🚀 Essential Join Types Cheat Sheet

### Basic Join Syntax
```python
df1.join(df2, "join_column", "join_type")
df1.join(df2, df1.col1 == df2.col1, "join_type")
```

### All Join Types
| Join Type | Description | Use Case |
|-----------|-------------|----------|
| `inner` | Only matching records | Default, most common |
| `left` | All left + matching right | Keep all from left table |
| `right` | All right + matching left | Keep all from right table |
| `outer` | All records from both | Complete data analysis |
| `semi` | Left records with right match | Filtering without right columns |
| `anti` | Left records without right match | Find missing records |
| `cross` | Cartesian product | Use with caution! |

## ⚡ Performance Optimization Quick Reference

### Memory Settings
```python
spark.conf.set("spark.executor.memory", "4g")
spark.conf.set("spark.driver.memory", "2g")
spark.conf.set("spark.executor.memoryFraction", "0.8")
```

### Join Optimizations
```python
# Broadcast small tables
df1.join(broadcast(small_df), "key")

# Enable AQE
spark.conf.set("spark.sql.adaptive.enabled", "true")
spark.conf.set("spark.sql.adaptive.skewJoin.enabled", "true")
```

### Partitioning
```python
# Repartition by column
df.repartition("column_name")

# Reduce partitions
df.coalesce(4)

# Optimal shuffle partitions
spark.conf.set("spark.sql.shuffle.partitions", "200")
```

## 📊 Sorting Techniques

### Basic Sorting
```python
df.orderBy("column")                    # Ascending
df.orderBy(col("column").desc())        # Descending
df.orderBy("col1", col("col2").desc())  # Multiple columns
```

### Advanced Sorting
```python
# Handle nulls
df.orderBy(col("column").asc_nulls_last())

# Sort within partitions
df.sortWithinPartitions("column")
```

## 🎯 Window Functions

### Window Specification
```python
from pyspark.sql.window import Window

window = Window.partitionBy("dept").orderBy("salary")
```

### Common Window Functions
```python
# Ranking
df.withColumn("rank", row_number().over(window))
df.withColumn("dense_rank", dense_rank().over(window))

# Lag/Lead
df.withColumn("prev_value", lag("column", 1).over(window))
df.withColumn("next_value", lead("column", 1).over(window))

# Aggregations
df.withColumn("running_sum", sum("column").over(window))
```

## 🔧 Performance Monitoring

### Execution Plans
```python
df.explain()                    # Basic plan
df.explain(True)               # Extended plan
df.explain("cost")             # Cost-based plan
```

### Caching
```python
df.cache()                     # Memory only
df.persist(StorageLevel.MEMORY_AND_DISK)
df.unpersist()                 # Clear cache
```

## 🎓 Best Practices Checklist

### ✅ Do's
- Use schemas for DataFrames
- Cache frequently used DataFrames
- Use broadcast joins for small tables
- Enable AQE for production workloads
- Monitor execution plans
- Partition data by frequently filtered columns

### ❌ Don'ts  
- Don't use collect() on large DataFrames
- Avoid cross joins without filters
- Don't cache everything
- Avoid UDFs when built-in functions exist
- Don't ignore data skew

## 🚀 Advanced Configuration Template

```python
spark = SparkSession.builder \
    .appName("Optimized PySpark App") \
    .config("spark.sql.adaptive.enabled", "true") \
    .config("spark.sql.adaptive.coalescePartitions.enabled", "true") \
    .config("spark.sql.adaptive.skewJoin.enabled", "true") \
    .config("spark.sql.autoBroadcastJoinThreshold", "10MB") \
    .config("spark.sql.shuffle.partitions", "200") \
    .config("spark.executor.memory", "4g") \
    .config("spark.driver.memory", "2g") \
    .config("spark.executor.cores", "4") \
    .config("spark.sql.execution.arrow.pyspark.enabled", "true") \
    .getOrCreate()
```

Ready to master PySpark! 🔥
