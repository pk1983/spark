## Building Spark

To build Spark and its example programs, run:

    sbt assembly

## Run Spark on Windows in standalone mode 

If we don’t want with Hadoop, we just want to run it in standalone mode on windows.
Here we’ll see how we can run Spark on Windows machine.

Prerequisites:

    Java6+

    Scala 2.10.x

    Python 2.6 +

    sbt ( In case of building Spark Source code)

    GIT( If you use sbt tool)
    
Windows environment variable setup

    Set SPARK_HOME = Your Spark Path and add %SPARK_HOME%\bin in PATH in environment variables

Though we aren't using Hadoop with Spark, but somewhere it checks for HADOOP_HOME variable in configuration. So to overcome this error,  we need winutils.exe and place it in any location (i.e. C:\winutils\bin\winutils.exe).

    Set HADOOP_HOME = D:\winutils and add add %HADOOP_HOME%\bin in PATH in environment variables

## Start Master and Worker on Windows

In Windows Power Shell, run the following command:

1. Start the Master:

    ./sbin/start-master.bat

Change the command in start-master.bat to your spark path
E:\github\pk1983\spark\bin\spark-class org.apache.spark.deploy.master.Master

2. Start the worker:

    ./sbin/start-worker.bat

Change spark://172.12.100.18:7077 to your actual master url
E:\github\pk1983\spark\bin\spark-class org.apache.spark.deploy.worker.Worker spark://172.12.100.18:7077

3. Start the spark-shell application

    ./bin/spark-shell --master spark://172.12.100.18:7077
    
Change spark://172.12.100.18:7077 to your actual master url

4. See Info logs on spark-shell, run the following

    sc.setLogLevel("INFO")