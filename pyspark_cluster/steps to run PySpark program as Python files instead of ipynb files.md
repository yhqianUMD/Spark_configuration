# The following are the steps for running the PySpark program using Python files instead of ipynb files

## Step 1: Export Spark Python variables

```
conda activate py37
export PYSPARK_PYTHON=/home/qiany/.conda/envs/py37/bin/python
export PYSPARK_DRIVER_PYTHON=/home/qiany/.conda/envs/py37/bin/python
```

## Step 2: Zip the folder that contains the code
remove: a zip file:
```
rm -f seaice_step0.zip
```

zip a file:
```
zip -r seaice_step0.zip seaice_step0
```

## Step 3: Ship the zip file and run the PySpark program
```
spark-submit \
--master yarn \
--deploy-mode client \
--py-files seaice_step0.zip   main.py \
--tin-file /local/data/yuehui/pyspark/data/Part3_TopoSim/Part3_TopoSim_test_datasets/OR22_01per_as_10000.off \
--hdfs-dir seaice_step0 \
1> /local/data/yuehui/pyspark/data/Part3_TopoSim/Part3_TopoSim_test_datasets/my_prints.log 2> /local/data/yuehui/pyspark/data/Part3_TopoSim/Part3_TopoSim_test_datasets/spark.log
```

Notes: my_prints.log will store the outputs from the "print" statements in python, while spark.log will store the outputs from Spark console.
