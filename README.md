## Keras_deployment_to_AWS
### Problem statement:
Illustrate Keras model deployment on AWS Sagemaker.
<br/><br/>
<br/><br/>
Solution is categorised into two phases.
* Training phase
* Deployment phase
### 1. Training phase
 One of the great features of Sagemaker is that it is modularized so that the process of training a model is decoupled from deploying the model. Also, one can enter to and exit from any of it's stages! Partly to demonstrate that feature and partly to harness free GPU facility in Google colab, I am building a CNN model on colab and deploying it on Sagemaker platform.
<br> For a non-interactive preview of training notebook, touch here &#8594; [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/manoharkaranth/Keras_deployment_to_AWS/blob/master/Malaria_Detection_TL.ipynb)  or touch the button at the top of _Malaria_Detection_TL.ipynb_ notebook <br/>
<br/><br/> 
### 2. Deployment phase
* Create a notebook instance and create a new notebook and set the kernel to conda_tensorflow_p36.
* Upload trained model weights and json file which was previously saved to Google drive.
* Load the Keras model from disk to memory.
* Export the Keras model to the TensorFlow ProtoBuf format.
* Convert TensorFlow model to a SageMaker readable format.
* - Move the TensorFlow exported model into a directory _export\Servo_.
* - Add the _code_ folder.
* - Tar the entire directory and upload to S3.
* Create an entry_point file "train.py". It can be an empty Python file.
* Deploy the model to an endpoint.
* Test the deployment. If you are testing from outside of Sagemaker, make sure that you attach a policy which can just invoke the endpoint and nothing much. 
* Free up the resources.
      For a non-interactive preview of a notebook containing practical implementation of these steps &#8594;
<br/><br/>
### Way forward:
When we bring a Keras model from outside to Sagemaker, it is imperative to ensure that Tensorflow versions of both platforms are same ( Keras is inbuilt in Tensorflow after Tensorflow version 2.0). More often than not, one has to upgrade tensorflow on Sagemaker as Sagemaker is infamous for carrying older version dependencies. Don't forget to delete the endpoint once your purpose is served because it will cost you money otherwise. When it comes to enhancement of this project, one can create a public HTTP endpoint that can route requests to your Sagemaker endpoint. One way to do this is with an AWS Lambda function fronted by API gateway. API gateway creates APIs and passes with parameter values which will be parsed by the Lambda function. Lambda function can also be exploited to aggregate multiple inferences into one when we have handful of models deployed in production.
<br/><br/>
##### References: AWS documentations.
