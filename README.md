## Keras_deployment_to_AWS
### Problem statement:
Illustrate Keras deployment on AWS Sagemaker.
<br/><br/>
<br/><br/>
Solution is categorised into two phases.
* Training phase
* Deployment phase
### 1. Training phase
 One of the great features of Sagemaker is that it is modularized so that the process of training a model is decoupled from deploying the model. Also, one can enter to and exit from any of it's stages! Partly to demonstrate that feature and partly to harness free GPU facility in Google colab, I am building a CNN model on colab and deploying it on Sagemaker platform.
<br> For a non-interactive preview of training notebook, touch the button at the top of _Malaria_Detection_TL.ipynb_ notebook or touch here &#8594; [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/manoharkaranth/Keras_deployment_to_AWS/blob/master/Malaria_Detection_TL.ipynb)<br/>
<br/><br/> 
### 2. Deployment phase
* Create a notebook instance and create a new notebook and set the kernel to conda_tensorflow_p36.
* Upload trained model weights and json file which was previously saved to Google drive.
* Load the Keras model from disk to memory.
* Export the Keras model to the TensorFlow ProtoBuf format.
* Convert TensorFlow model to a SageMaker readable format.
- Move the TensorFlow exported model into a directory _export\Servo_.
- Add the _code_ folder.
- Tar the entire directory and upload to S3.
* Create an entry_point file "train.py". It can be an empty Python file.
* Deploy the model to an endpoint.
* Test the deployment.
For a non-interactive preview of a notebook containing implementation of these steps &#8594;
<br/><br/>
### Way forward: We can enhance this with a Lambda function and an API gateway. Primarily, an endpoint is not exposed to 
