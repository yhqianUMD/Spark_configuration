If the cgishdp2 cluster is stuck and it shows an error of unhealthy nodes in the Hadoop resources website, we can kill the yarn application of the spark programe.
```
yarn application -list
yarn application -kill application_1732554669926_0124
```
