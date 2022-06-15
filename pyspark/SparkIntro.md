<p style="text-align:center">
    <a href="https://skills.network/?utm_medium=Exinfluencer&utm_source=Exinfluencer&utm_content=000026UJ&utm_term=10006555&utm_id=NA-SkillsNetwork-Channel-SkillsNetworkCoursesIBMBD0225ENSkillsNetwork25716109-2022-01-01" target="_blank">
    <img src="https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/assets/logos/SN_web_lightmode.png" width="200" alt="Skills Network Logo"  />
    </a>
</p>


# **Getting Started With Spark using Python**


Estimated time needed: **15** minutes


![](http://spark.apache.org/images/spark-logo.png)


### The Python API


Spark is written in Scala, which compiles to Java bytecode, but you can write python code to communicate to the java virtual machine through a library called py4j. Python has the richest API, but it can be somewhat limiting if you need to use a method that is not available, or if you need to write a specialized piece of code. The latency associated with communicating back and forth to the JVM can sometimes cause the code to run slower.
An exception to this is the SparkSQL library, which has an execution planning engine that precompiles the queries. Even with this optimization, there are cases where the code may run slower than the native scala version.
The general recommendation for PySpark code is to use the "out of the box" methods available as much as possible and avoid overly frequent (iterative) calls to Spark methods. If you need to write high-performance or specialized code, try doing it in scala.
But hey, we know Python rules, and the plotting libraries are way better. So, it's up to you!


## Objectives


In this lab, we will go over the basics of Apache Spark and PySpark. We will start with creating the SparkContext and SparkSession. We then create an RDD and apply some basic transformations and actions. Finally we demonstrate the basics dataframes and SparkSQL.

After this lab you will be able to:

*   Create the SparkContext and SparkSession
*   Create an RDD and apply some basic transformations and actions to RDDs
*   Demonstrate the use of the basics Dataframes and SparkSQL


***


## Setup


For this lab, we are going to be using Python and Spark (PySpark). These libraries should be installed in your lab environment or in SN Labs.



```python
# Installing required packages
!pip install pyspark
!pip install findspark
```

    Collecting pyspark
      Downloading pyspark-3.2.1.tar.gz (281.4 MB)
    [2K     [90m━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━[0m [32m281.4/281.4 MB[0m [31m1.8 MB/s[0m eta [36m0:00:00[0m00:01[0m00:01[0m
    [?25h  Preparing metadata (setup.py) ... [?25ldone
    [?25hCollecting py4j==0.10.9.3
      Downloading py4j-0.10.9.3-py2.py3-none-any.whl (198 kB)
    [2K     [90m━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━[0m [32m199.0/199.0 kB[0m [31m32.4 MB/s[0m eta [36m0:00:00[0m
    [?25hBuilding wheels for collected packages: pyspark
      Building wheel for pyspark (setup.py) ... [?25ldone
    [?25h  Created wheel for pyspark: filename=pyspark-3.2.1-py2.py3-none-any.whl size=281853625 sha256=dd1dd9059fbf127a5df4fb6fa131696a519c6cd53022db4c43063aa1b2e09821
      Stored in directory: /home/jupyterlab/.cache/pip/wheels/9f/f5/07/7cd8017084dce4e93e84e92efd1e1d5334db05f2e83bcef74f
    Successfully built pyspark
    Installing collected packages: py4j, pyspark
    Successfully installed py4j-0.10.9.3 pyspark-3.2.1
    Collecting findspark
      Downloading findspark-2.0.1-py2.py3-none-any.whl (4.4 kB)
    Installing collected packages: findspark
    Successfully installed findspark-2.0.1



```python
import findspark
findspark.init()
```


```python
# PySpark is the Spark API for Python. In this lab, we use PySpark to initialize the spark context. 
from pyspark import SparkContext, SparkConf
from pyspark.sql import SparkSession
```

## Exercise 1 -  Spark Context and Spark Session


In this exercise, you will create the Spark Context and initialize the Spark session needed for SparkSQL and DataFrames.
SparkContext is the entry point for Spark applications and contains functions to create RDDs such as `parallelize()`. SparkSession is needed for SparkSQL and DataFrame operations.


#### Task 1: Creating the spark session and context



```python
# Creating a spark context class
sc = SparkContext()

# Creating a spark session
spark = SparkSession \
    .builder \
    .appName("Python Spark DataFrames basic example") \
    .config("spark.some.config.option", "some-value") \
    .getOrCreate()
```

    22/06/11 01:45:09 WARN util.NativeCodeLoader: Unable to load native-hadoop library for your platform... using builtin-java classes where applicable
    Setting default log level to "WARN".
    To adjust logging level use sc.setLogLevel(newLevel). For SparkR, use setLogLevel(newLevel).


#### Task 2: Initialize Spark session

To work with dataframes we just need to verify that the spark session instance has been created.



```python
spark
```





    <div>
        <p><b>SparkSession - in-memory</b></p>

<div>
    <p><b>SparkContext</b></p>

    <p><a href="http://jupyterlab-jinfeijoy:4040">Spark UI</a></p>

    <dl>
      <dt>Version</dt>
        <dd><code>v2.4.3</code></dd>
      <dt>Master</dt>
        <dd><code>local[*]</code></dd>
      <dt>AppName</dt>
        <dd><code>pyspark-shell</code></dd>
    </dl>
</div>

    </div>




## Exercise 2: RDDs

In this exercise we work with Resilient Distributed Datasets (RDDs). RDDs are Spark's primitive data abstraction and we use concepts from functional programming to create and manipulate RDDs.


#### Task 1: Create an RDD.

For demonstration purposes, we create an RDD here by calling `sc.parallelize()`\
We create an RDD which has integers from 1 to 30.



```python
data = range(1,30)
# print first element of iterator
print(data[0])
len(data)
xrangeRDD = sc.parallelize(data, 4)

# this will let us know that we created an RDD
xrangeRDD
```

    1





    PythonRDD[1] at RDD at PythonRDD.scala:53



#### Task 2: Transformations


A transformation is an operation on an RDD that results in a new RDD. The transformed RDD is generated rapidly because the new RDD is lazily evaluated, which means that the calculation is not carried out when the new RDD is generated. The RDD will contain a series of transformations, or computation instructions, that will only be carried out when an action is called. In this transformation, we reduce each element in the RDD by 1. Note the use of the lambda function. We also then filter the RDD to only contain elements <10.



```python
subRDD = xrangeRDD.map(lambda x: x-1)
filteredRDD = subRDD.filter(lambda x : x<10)

```

#### Task 3: Actions


A transformation returns a result to the driver. We now apply the `collect()` action to get the output from the transformation.



```python
print(filteredRDD.collect())
filteredRDD.count()
```

    [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]





    10



#### Task 4: Caching Data


This simple example shows how to create an RDD and cache it. Notice the **10x speed improvement**!  If you wish to see the actual computation time, browse to the Spark UI...it's at host:4040.  You'll see that the second calculation took much less time!



```python
import time 

test = sc.parallelize(range(1,50000),4)
test.cache()

t1 = time.time()
# first count will trigger evaluation of count *and* cache
count1 = test.count()
dt1 = time.time() - t1
print("dt1: ", dt1)


t2 = time.time()
# second count operates on cached data only
count2 = test.count()
dt2 = time.time() - t2
print("dt2: ", dt2)

#test.count()
```

    dt1:  0.3746199607849121
    dt2:  0.05443310737609863


## Exercise 3: DataFrames and SparkSQL


In order to work with the extremely powerful SQL engine in Apache Spark, you will need a Spark Session. We have created that in the first Exercise, let us verify that spark session is still active.



```python
spark
```





    <div>
        <p><b>SparkSession - in-memory</b></p>

<div>
    <p><b>SparkContext</b></p>

    <p><a href="http://karthiks-mbp.attlocal.net:4040">Spark UI</a></p>

    <dl>
      <dt>Version</dt>
        <dd><code>v3.1.1</code></dd>
      <dt>Master</dt>
        <dd><code>local[*]</code></dd>
      <dt>AppName</dt>
        <dd><code>PySpark-shell</code></dd>
    </dl>
</div>

    </div>




#### Task 1: Create Your First DataFrame!


You can create a structured data set (much like a database table) in Spark.  Once you have done that, you can then use powerful SQL tools to query and join your dataframes.



```python
# Download the data first into a local `people.json` file
!curl https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBM-BD0225EN-SkillsNetwork/labs/data/people.json >> people.json
```

      % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                     Dload  Upload   Total   Spent    Left  Speed
    100    73  100    73    0     0    164      0 --:--:-- --:--:-- --:--:--   163



```python
# Read the dataset into a spark dataframe using the `read.json()` function
df = spark.read.json("people.json").cache()
```


```python
# Print the dataframe as well as the data schema
df.show()
df.printSchema()
```

    +----+-------+
    | age|   name|
    +----+-------+
    |null|Michael|
    |  30|   Andy|
    |  19| Justin|
    +----+-------+
    
    root
     |-- age: long (nullable = true)
     |-- name: string (nullable = true)
    



```python
# Register the DataFrame as a SQL temporary view
df.createTempView("people")
```

#### Task 2: Explore the data using DataFrame functions and SparkSQL

In this section, we explore the datasets using functions both from dataframes as well as corresponding SQL queries using sparksql. Note the different ways to achieve the same task!



```python
# Select and show basic data columns

df.select("name").show()
df.select(df["name"]).show()
spark.sql("SELECT name FROM people").show()
```

    +-------+
    |   name|
    +-------+
    |Michael|
    |   Andy|
    | Justin|
    +-------+
    
    +-------+
    |   name|
    +-------+
    |Michael|
    |   Andy|
    | Justin|
    +-------+
    
    +-------+
    |   name|
    +-------+
    |Michael|
    |   Andy|
    | Justin|
    +-------+
    



```python
# Perform basic filtering

df.filter(df["age"] > 21).show()
spark.sql("SELECT age, name FROM people WHERE age > 21").show()
```

    +---+----+
    |age|name|
    +---+----+
    | 30|Andy|
    +---+----+
    
    +---+----+
    |age|name|
    +---+----+
    | 30|Andy|
    +---+----+
    



```python
# Perfom basic aggregation of data

df.groupBy("age").count().show()
spark.sql("SELECT age, COUNT(age) as count FROM people GROUP BY age").show()
```

    +----+-----+
    | age|count|
    +----+-----+
    |  19|    1|
    |null|    1|
    |  30|    1|
    +----+-----+
    
    +----+-----+
    | age|count|
    +----+-----+
    |  19|    1|
    |null|    0|
    |  30|    1|
    +----+-----+
    


***


### Question 1 - RDDs


Create an RDD with integers from 1-50. Apply a transformation to multiply every number by 2, resulting in an RDD that contains the first 50 even numbers.



```python
# starter code
# numbers = range(1, 50)
# numbers_RDD = ...
# even_numbers_RDD = numbers_RDD.map(lambda x: ..)
```


```python
# Code block for learners to answer
```

### Question 2 - DataFrames and SparkSQL


Similar to the `people.json` file, now read the `people2.json` file into the notebook, load it into a dataframe and apply SQL operations to determine the average age in our people2 file.



```python
# starter code
# !curl https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBM-BD0225EN-SkillsNetwork/labs/people2.json >> people2.json
# df = spark.read...
# df.createTempView..
# spark.sql("SELECT ...")
```


```python
# Code block for learners to answer
```

Double-click **here** for a hint.

<!-- The hint is below:

1. The SQL query "Select AVG(column_name) from.." can be used to find the average value of a column. 
2. Another possible way is to use the dataframe operations select() and mean()
-->


Double-click **here** for the solution.

<!-- The answer is below:
df = spark.read('people2.json')
df.createTempView("people2")
spark.sql("SELECT AVG(age) from people2")
-->


### Question 3 - SparkSession


Close the SparkSession we created for this notebook



```python
# Code block for learners to answer
```

Double-click **here** for the solution.

<!-- The answer is below:

spark.stop() will stop the spark session

-->


## Authors


[Karthik Muthuraman](https://www.linkedin.com/in/karthik-muthuraman/?utm_medium=Exinfluencer&utm_source=Exinfluencer&utm_content=000026UJ&utm_term=10006555&utm_id=NA-SkillsNetwork-Channel-SkillsNetworkCoursesIBMBD0225ENSkillsNetwork25716109-2022-01-01)


### Other Contributors


[Jerome Nilmeier](https://github.com/nilmeier)


## Change Log


| Date (YYYY-MM-DD) | Version | Changed By | Change Description |
| ----------------- | ------- | ---------- | ------------------ |
| 2021-07-02        | 0.2     | Karthik    | Beta launch        |
| 2021-06-30        | 0.1     | Karthik    | First Draft        |


Copyright © 2021 IBM Corporation. All rights reserved.

