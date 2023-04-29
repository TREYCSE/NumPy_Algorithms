## An example of machine learning deployment from: https://stackoverflow.blog/2020/10/12/how-to-put-machine-learning-models-into-production/
### Now, I’m going to walk you through a sample ML project. In this project,you’re an ML engineer working on a promising project, and you want to design a fail-proof system that can effectively put, monitor, track, and deploy an ML model. 

#### Consider Adstocrat, an advertising agency that provides online companies with efficient ad tracking and monitoring. They have worked with big companies and have recently gotten a contract to build a machine learning system to predict if customers will click on an ad shown on a webpage or not. The contractors have a large volume dataset in a Google Cloud Storage (GCS) bucket and want Adstocrat to develop an end-to-end ML system for them. 

### As the engineer in charge, you have to come up with a design solution before the project kicks off. To approach this problem, ask each of the questions asked earlier and develop a design for this end-to-end system. 

## Data concerns
### First, let’s talk about the data. How is your training data stored?

### The data is stored in a GCS bucket and comes in two forms. The first is a CSV file describing the ad, and the second is the corresponding image of the ad. The data is already in the cloud, so it may be better to build your ML system in the cloud. You’ll get better latency for I/O, easy scaling as data becomes larger (hundreds of gigabytes), and quick setup and configuration for any additional GPUs and TPUs. 

## How large is your data?

### The contractor serves millions of ads every month, and the data is aggregated and stored in the cloud bucket at the end of every month. So now you know your data is large (hundreds of gigabytes of images), so your hunch of building your system in the cloud is stronger. 

## How will you retrieve the data for training?

## Since data is stored in the GCS bucket, it can be easily retrieved and consumed by models built on the Google Cloud Platform. So now you have an idea of which cloud provider to use.

## How will you retrieve data for prediction?

#### In terms of inference data, the contractors informed you that inference will be requested by their internal API, as such data for prediction will be called by a REST API. This gives you an idea of the target platform for the project. 

## Frameworks and tools for the project
#### #### There are many combinations of tools you can use at this stage, and the choice of one tool may affect the others. In terms of programming languages for prototyping, model building, and deployment, you can decide to choose the same language for these three stages or use different ones according to your research findings. For instance, Java is a very efficient language for backend programming, but cannot be compared to a versatile language like Python when it comes to machine learning. 

#### After consideration, you decide to use Python as your programming language, Tensorflow for model building because you will be working with a large dataset that includes images, and Tensorflow Extended (TFX), an open-source tool released and used internally at Google, for building your pipelines. What about the other aspects of the model building like model analysis, monitoring, serving, and so on? What tools do you use here? Well, TFX pretty much covers it all!

#### TFX provides a bunch of frameworks, libraries, and components for defining, launching, and monitoring machine learning models in production. The components available in TFX let you build efficient ML pipelines specifically designed to scale from the start. These components has built-in support for ML modeling, training, serving, and even managing deployments to different targets.


#### TFX is also compatible with our choice of programming language (Python), as well as your choice of deep learning model builder (Tensorflow), and this will encourage consistency across your team. Also, since TFX and Tensorflow were built by Google, it has first-class support in the Google Cloud Platform. And remember, your data is stored in GCS. 

## Are the choice of tools open-source or closed?
#### Python and TFX and Tensorflow are all open-source, and they are the major tools for building your system. In terms of computing  power and storage, you are using all GCP which is a paid and managed cloud service. This has its pros and cons and may depend on your use case as well. Some of the pros to consider when considering using managed cloud services are:

        They are cost-efficient
        Quick setup and deployment
        Efficient backup and recovery
        Some of the cons are:

        Security issue, especially for sensitive data
        Internet connectivity may affect work since everything runs online
        Recurring costs
        Limited control over tools
        In general, for smaller businesses like startups, it is usually cheaper and better to use managed cloud services for your projects. 

## How many platforms/targets support the tool?

#### TFX and Tensorflow run anywhere Python runs, and that’s a lot of places. Also, models built with Tensorflow can easily be saved and served in the browsers using Tensorflow.js, in mobile devices and IoT using Tensorflow lite, in the cloud, and even on-prem.

## Feedback and Iteration concerns
#### How do we get feedback from a model in production?

#### TFX supports a feedback mechanism that can be easily used to manage model versioning as well as rolling out new models. Custom feedback can be built around this tool to effectively track models in production. A TFX Component called TensorFlow Model Analysis (TFMA) allows you to easily evaluate new models against current ones before deployment. 

#### Looking back at the answers above, you can already begin to picture what your final ML system design will look like. And getting this part before model building or data exploration is very important. 

## Conclusion
### Effectively putting an ML model in production does not have to be hard if all the boxes are ticked before embarking on a project. This is very important in an ML project you’ll embark on and should be prioritized! 