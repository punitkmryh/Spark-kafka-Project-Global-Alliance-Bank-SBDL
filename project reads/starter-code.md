PySpark
```
from pyspark.sql import SparkSession
from pyspark.sql.functions import *

# Initialize Spark session
spark = SparkSession.builder.master("local[3]").appName("SBDL_Kafka_Pipeline").getOrCreate()

# ... (rest of the Spark application code)

```
