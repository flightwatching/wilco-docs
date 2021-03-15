# Step 2 : Using the XGBoost prediction model on Wilco



XGBoost prediction models are invoked by using the Flightwatching javascript API in an IFT, with the following operation:

`FW.machineLearningPredict('<PREDICTION NAME>', <PARAMS>, { prediction: '<PREDICTION NAME>', reference: <REF SAMPLE>, delta: '<PREDICTION DELTA NAME>'})`

* `<PREDICTION NAME>` : Name of the prediction model
* `<PARAMS>` : Input of the prediction model, in the form of a javascript dictionary object
* `<PREDICTION NAME>` : Name of the sample that will be added and that contains the prediction value
* `<REF SAMPLE>` : Sample that hold the non predicted, reference value
* `<PREDICTION DELTA NAME>` : Name of the sample that will be added and that contains difference between the prediction value and the non predicted value

For example:

`FW.machineLearningPredict('A320_VAR3_v1', {'VAR1': VAR1, 'VAR2': VAR2*1.01}, { prediction: 'VAR3_PREDICTION', reference: VAR3, delta: 'VAR3_PREDICTION_ERROR'})`

means : Launch the machine learning prediction job named A320\_VAR3\_v1 with the inputs :

* VAR1 input : Value of the VAR1 sample
* VAR2 input : Value of the VAR2 sample multiplied by 1.01 \(you can feed the prediction model with any formula, value or variable\)

  , store the predicted value into the sample names VAR3\_PREDICTION, compare the predicted value with the reference value VAR3 anb store the difference in the sample named VAR3\_PREDICTION\_ERROR,

