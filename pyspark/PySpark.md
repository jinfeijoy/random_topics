# PySpark (Course Material for Cousera Pyspark Course)
## Hadoop
* Hadoop
  * Situations not for Hadoop:
    * Processing transactions (random access)
    * When work cannot be parallelized
    * When there are dependencies in the data
    * Low latency data access
    * Processing lots of small files
    * Intensive calculations with little data 
      * Hive (built on the top of hadoop): provide sql-like query and provide users with strong statistical functions    
      * Pig: was popular for its multi query approach to cut down the number of times that the data is scanned
* MapReduce: processing technique for distributed computing
  * Map and Reduce
    * Input file (input data is a file that is saved in the hadoop file system HDFS)
    * Map: process data into key value pairs (key is the name and value is content)
    * Further data sorting and organizing
    * Reducer: aggregates and computes a set of result and produces a final output
    * MapReduce keeps track of its task by creating a unique key
  * How MapReduce work:
    * ![image](https://user-images.githubusercontent.com/16402963/173707170-e892845b-30a5-4184-8e90-36a84446f4b7.png) 
* Hadoop Ecosystem
  * MapReduce is used for making Big Data magageable by processing them in clusters; Yet Another Resource Negotiator (YARN) is the resource manager across clusters..
  * ![image](https://user-images.githubusercontent.com/16402963/173707529-c5b59088-a996-436a-90ab-5ea7f4024d0e.png)
* HDFS (Hadoop Distributed File System)
  * Blocks: 
    * Minimum amount of data that can be read or written
    * Provides fault tolerance
    * Default size is 64MB or 128MB
  * Replication: save copy of blocks in racks for backup purpose
  * Rack awareness helps reduce the network traffic and improve cluster performance
  * Read and Write Operations: allows write once read many operations
* HIVE
  * Hive is data warehouse software within Hadoop that is designed for reading, writing and managing tabular-type datasets and data analysis. 
* HBASE
  * works well with real-time data and random read and write access to Big Data
  * HBase is used for write-heavy applications to process large amount of data and provide analytics in real time.
  * Difference between HDFS and HBASE:
    * ![image](https://user-images.githubusercontent.com/16402963/173711304-0b9ab68f-b605-4b00-8850-a4fd520ee21e.png)
 
## Apache Spark
* ![image](https://user-images.githubusercontent.com/16402963/173941242-c348d1df-4623-423d-aa74-9e73507ef2d5.png)
* RDD (Resilient Distributed Dataset)
  * Spark's primary data abstraction
  * Immutable (cannot be changed once created)
  * ![image](https://user-images.githubusercontent.com/16402963/173942246-c44616e2-5a2b-46ae-94d2-88270192ba41.png)
  * Creating an RDD in Spark:
    * Use an external or local file from Hadoop-supported file system such as: HDFS/Cassandra/HBase/Amazon S3
    * Create an RDD from a collection: 
       ```
       data = [1,2,3,4,5]
       distData = sc.parallelize(data
       ``` 
    * Apply a transformation on an existing RDD to create a new RDD

## DataFrames and SparkSQL
* DataFrames
    ```
    mtcars = pd.read_csv('mtcars.csv')
    sdf = spark.createDataFrame(mtcars)
    sdf.printSchema()
    sdf.show(5)
    sdf.select('mpf').show(5) #mpf is 1 column
    sdf.filter(sdf['mpf']<18).show(5)
    car_count = sdf.groupby(['cyl']).agg({'wt':'count'})\.sort('count(wt)',ascending=False).show(5)
    ```
 * SparkSQL
    ```
    # create dataframe
    df = spark.read.json('people.json')
    # create temp view
    df.createTempView('people')
    spark.sql("SELECT * FROM people").show()

    df.createGlobalTempView('people')
    # create global temp view
    spark.sql("SELECT * FROM global_temp.people").show()

    ```

## Reference
* [Spark with Python (PySpark) Tutorial For Beginners](https://sparkbyexamples.com/pyspark-tutorial/)
* [Coursera Pyspark Tutorial](https://www.coursera.org/learn/introduction-to-big-data-with-spark-hadoop/home/week/3)(June14 - June18: Week2 - Week4 )
  
