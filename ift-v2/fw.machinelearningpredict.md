---
description: >-
  Launch a machine-learning prediction job to predict a value from inputs
  (usually sample values) and compare it with an actual value (usually a sample
  value).
---

# FW.machineLearningPredict



```text
FW.machineLearningPredict (jobName, inputs, outputs = {prediction:"", reference:"" , delta:""})
```

* `jobName`: a string that is the name of the machine-learning prediction job
* `inputs`: dictionary holding the names and values of the machine-learning prediction job inputs, typically samples names and values
* `outputs`: configure how to store the results of the prediction
  * `prediction`: string that is the name of the sample that will hold the prediction results
  * `reference`: actual value for comparison with the prediction
  * 'delta' : string that is the name of the sample that will hold the difference between the prediction results and the actual value

Examples of calls:

* `FW.machineLearningPredict('B747_PW901_v1', { 'GEN_LOAD_1':GEN_LOAD_1, 'APU_N1':APU_N1, 'APU_N2':APU_N2 }, { prediction:'APU_EGT_PREDICTION', reference: APU_EGT, delta:'APU_EGT_PREDICTION_ERROR'});`

