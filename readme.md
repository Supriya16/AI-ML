# Vertex AI for Machine Learning Operations

## 👋 I'm Mike

I want to share and enable [Vertex AI](https://cloud.google.com/vertex-ai/docs/start/introduction-unified-platform) from [Google Cloud](https://cloud.google.com/vertex-ai) with you.  The goal here is to share a comprehensive set of end-to-end workflows for machine learning that each cover the range of data to model to serving and managing - even automating the flow.  Regardless of your data type, skill level or framework preferences you will find something helpful here. 

<p align="center" width="100%">
   <a href="https://youtu.be/snUEwsft1wY" target="_blank" rel="noopener noreferrer">
      <kbd><img width="50%" src="architectures/thumbnails/playbutton/readme.png"></kbd>
   </a>
</p>
<p align="center">Click to watch on YouTube</p>
<p align="center">Click <a href="https://youtube.com/playlist?list=PLgxF613RsGoUuEjJJxJW2JYyZ8g1qOUou" target="_blank" rel="noopener noreferrer">here</a> to see full playlist for this repository</p>

---
## Considerations

### Data Type

-  Tables: Tabular, structured data in rows and columns
-  Language: Text for translation and/or understanding
-  Vision: Images
-  Video

### Convenience Level

-  Use Pre-Trained APIs
-  Automate building Custom Models
-  End-to-end Custom ML with core tools in the framework of your choice

### Framework Preferences

-  [Scikit-learn](https://scikit-learn.org/stable/index.html)
-  [XGBoost](https://xgboost.readthedocs.io/en/latest/)
-  [Tensorflow](https://www.tensorflow.org/)
-  [Pytorch](https://pytorch.org/)
-  [Spark MLlib](https://spark.apache.org/docs/latest/ml-guide.html)
-  [R](https://www.r-project.org/)
-  [Julia](https://julialang.org/)
-  More!

---
## Overview

This is a series of workflow demonstrations that use the same data source to build and deploy the same machine learning model with different frameworks and automation.  These are meant to help get started in understanding and learning Vertex AI and provide starting points for new projects.  

The demonstrations focus on workflows and don't delve into the specifics of ML frameworks other than how to integrate and automate with Vertex AI. Let me know if you have ideas for more workflows or details to include!

To understand the contents of this repository, the following charts uncover the groupings of the content.

| Direction |
:-------------------------:
![](./architectures/overview/decision.png)

This work focuses on cases where you have training date:

| Overview |
:-------------------------:
![](./architectures/overview/high_level.png)

|AutoML|BigQuery ML|Vertex AI| Forecasting with AutoML, BigQuery ML, OSS Prophet |
:---:|:---:|:---:|:---:
![](./architectures/overview/02_overview.png)|![](./architectures/overview/03_overview.png)|![](./architectures/overview/05_overview.png)|![](./architectures/overview/forecasting_overview.png)

---
## Vetex AI

Vetex AI is a platform for end-to-end model development.  It consist of core components that make the processes of MLOps possible for design patterns of all types.

<p align="center">
  <img alt="Components" src="architectures/slides/readme_arch.png" width="45%">
&nbsp; &nbsp; &nbsp; &nbsp;
  <img alt="Console" src="architectures/slides/readme_console.png" width="45%">
</p>

---
## Interacting with Vertex AI
Many Vertex AI resources can be viewed and monitored directly in the [GCP Console](https://console.cloud.google.com/vertex-ai).  Vertex AI resources are primarily created, modified, with the [Vertex AI API](https://cloud.google.com/vertex-ai/docs/reference).  The API is accessible from the command line with [`gcloud ai`](https://cloud.google.com/sdk/gcloud/reference/ai), [REST](https://cloud.google.com/vertex-ai/docs/reference/rest), [gRPC](https://cloud.google.com/vertex-ai/docs/reference/rpc), or the [client libraries](https://cloud.google.com/vertex-ai/docs/start/client-libraries) (built on top of gRPC) for [Python](https://cloud.google.com/python/docs/reference/aiplatform/latest), [Java](https://cloud.google.com/java/docs/reference/google-cloud-aiplatform/latest/overview), and [Node.js](https://cloud.google.com/nodejs/docs/reference/aiplatform/latest).  

There are additional [API versions](https://cloud.google.com/vertex-ai/docs/reference#versions) available: v1: stable, v1beta: latest preview features. The Vertex AI Python client library is called the [Vertex AI SDK for Python](https://googleapis.dev/python/aiplatform/latest/index.html).

The notebooks in this repository primarily use the Python client with first preference being the `aiplatform` library and occasional use of `aiplatform_v1` and `aiplatform_v1beta1`.  

**Install the Vertex AI Python Client**
```python
pip install google-cloud-aiplatform
```

**Import Vertex AI Python Client versions**
```python
from google.cloud import aiplatform
from google.cloud import aiplatform_v1
from google.cloud import aiplatform_v1beta1
```

**Recommendation**
When reviewing the code in this repository it is recommended to first consult the [Python Client Reference](https://cloud.google.com/python/docs/reference/aiplatform/latest) and the look for futher details in the [Vertex AI SDK for Python](https://googleapis.dev/python/aiplatform/latest/index.html).

**More on using Python with Google Cloud**
- A complete list of [Google Cloud Python Client Libraries](https://github.com/googleapis/google-cloud-python)
- [Getting started with Python](https://cloud.google.com/python/docs/getting-started) in Google Cloud

---
## Setup

The demonstrations are presented in a series of JupyterLab notebooks. These can be reviewed directly in [this repository on GitHub](https://github.com/statmike/vertex-ai-mlops) or cloned to your Jupyter instance on [Vertex AI Workbench](https://cloud.google.com/vertex-ai/docs/workbench/notebook-solution).

### Option 1: Review files directly

Select the files and review them directly in the browser or IDE of your choice.  This can be helpful for general understanding and selecting sections to copy/paste to your project.

### Option 2: Run These Notebooks in a Vertex AI Workbench based Notebook 

TL;DR
> In Google Cloud Console, Select/Create a Project then go to Vertex AI > Workbench > User-Managed Notebooks
> - Create a new notebook and Open JupyterLab
> - Clone this repository using Git Menu, Open and run `00 - Environment Setup.ipynb`

1. Create a Project
   1. [Link](https://console.cloud.google.com/cloud-resource-manager), Alternatively, go to: Console > IAM & Admin > Manage Resources
   1. Click "+ Create Project"
   1. Provide: name, billing account, organization, location
   1. Click "Create"
1. Enable the APIs: Vertex AI API and Notebooks API
   1. [Link](https://console.cloud.google.com/flows/enableapi?apiid=aiplatform.googleapis.com,notebooks.googleapis.com)
      1. Alternatively, go to: 
         1. Console > Vertex AI, then enable API
         1. Then Console > Vertex AI > Workbench, then enable API
1. Create A Notebook
   1. [Link](https://console.cloud.google.com/vertex-ai/workbench), Alternatively, go to: Console > Vertex AI > Workbench
   1. Click User-Managed Notebooks
   1. Click "+ Create Notebook" or "+ New Notebook"
   1. Selections:
      1. Tensorflow Enterprise > Tensorflow Enterprise 2.3 > Without GPUs
      1. Provide: name, region = us-central1, machine type = n1-standard-4
      1. some options may be under "Advanced Options"
   1. Click "Create"
1. Open JupyterLab Notebook Instance
   1. Once the Notebook Instance is started click the "Open JupyterLab" link
   1. Clone This Repository to the Notebook Instance
      1. Use the Git Menu at the top or on the left navigation bar to select "Clone a Repository"
      1. Provide the Clone URI of this repository: [https://github.com/statmike/vertex-ai-mlops.git](https://github.com/statmike/vertex-ai-mlops.git)
      1. In the File Browser you will now have the folder "vertex-ai-mlops" that contains the files from this repository
1. Setup the Notebook Environment for these workflows
   1. Open the notebook vertex-ai-mlops/00 - Environment Setup
   1. Follow the instructions and run the cells

Resources on these items:
- [Google Cloud Projects](https://cloud.google.com/resource-manager/docs/creating-managing-projects)
- [Vertex AI environment](https://cloud.google.com/vertex-ai/docs/start/cloud-environment)
- [Introduction to Notebooks](https://cloud.google.com/notebooks/docs/introduction)
- [Create a Notebooks Instance](https://cloud.google.com/notebooks/docs/create-new)
- [Open Notebooks](https://cloud.google.com/notebooks/docs/create-new#open_the_notebook_2)

---
## Learning Machine Learning
I often get asked "How do I learn about ML?".  There are lots of good answers.  I do have a preferred answer that is offered here.  I believe in a broad understanding of the topic, terminology, problem framing and method selection while also building up fundamental understandings of how everything actually works.  
1. Good overview with terminology, methods, problem framing, and tips for using APIs from TensorFlow.  The [Machine Learning Crash Course](https://developers.google.com/machine-learning/crash-course)
2. Strong Introduction to Fundamentals with Andrew Ng offered by Stanford on Coursera.  [Machine Learning](https://www.coursera.org/learn/machine-learning)
3. Pull it all together with excellent walk-throughs of the core concepts from the [Youtube channel 3Blue1Brown](https://www.youtube.com/c/3blue1brown)
   1. [Neural Networks](https://www.youtube.com/playlist?list=PLZHQObOWTQDNU6R1_67000Dx_ZCJB-3pi) playlist
   2. [Essence of linear algebra](https://www.youtube.com/playlist?list=PLZHQObOWTQDPD3MizzM2xVFitgF8hE_ab) playlist
   3. [Essence of calculus](https://www.youtube.com/playlist?list=PLZHQObOWTQDMsr9K-rj53DwVRMYO3t5Yr) playlist

This is a good review order: 1, 3.1, 3.2, 3.3, 2, 3.1 (again!).  When done with this, remember you are a beginner so begin, have fun, make mistakes and keep optimizing your cost function to boost your knowledge!

A good next step is to use the [curriculums curated by the Tensorflow community](https://www.tensorflow.org/resources/learn-ml).  These are great at balancing coding, math & stats, theory, and project based learning.

---
## More Resources Like This Repository

This is my personal repository of demonstrations I use for learning and sharing Vertex AI.  There are many more resources available.  Within each notebook I have included a resources section and a related training section. 

- GitHub [GoogleCloudPlatform/vertex-ai-samples](https://github.com/GoogleCloudPlatform/vertex-ai-samples)
- GitHub [GoogleCloudPlatform/mlops-with-vertex-ai](https://github.com/GoogleCloudPlatform/mlops-with-vertex-ai)
- [Overview of Data Science on Google Cloud](https://cloud.google.com/data-science)

---
## Vertex AI For ML Training

Add these:
 - tensorboard
 - experiment
 - worker pool

```mermaid
sequenceDiagram
   actor User
   participant Training Code
   participant API
   participant Training Job
   Participant Custom Job
   Participant Hyperparameter Tuning Job
   Note over Training Job, Hyperparameter Tuning Job: Vertex AI Training

   rect rgb(154, 160, 166)
      note right of User: Vertex AI Workbench / Notebook
      Training Code ->> Training Code: Inside
   end
   rect rgb(234, 67, 53)
      note right of User: Python Script
      rect rgb(66, 133, 244)
         note right of Training Code: a
         Training Code ->> API: customJob = aiplatform.CustomJob.from_local_script()
         API ->> Custom Job: customJob.run()
      end
      rect rgb(251, 188, 4)
         note right of Training Code: d
         Training Code ->> API: trainingJob = aiplatform.CustomTrainingJob()
         API ->> Training Job: model = trainingJob.run()
         Training Job -->> Custom Job: creates backing custom job
      end
      rect rgb(52, 168, 83)
         note right of Training Code: g
         Training Code ->> API: customJob = aiplatform.CustomJob.from_local_script()
         Training Code ->> API: tuningJob = aiplatform.HyperparameterTuningJob(customJob)
         API ->> Hyperparameter Tuning Job: tuningJob.run()
      end
   end
   rect rgb(234, 67, 53)
      note right of User: Python Source Distribution
      rect rgb(66, 133, 244)
         note right of Training Code: b
         Training Code ->> API: customJob = aiplatform.CustomJob()
         API ->> Custom Job: customJob.run()
      end
      rect rgb(251, 188, 4)
         note right of Training Code: e
         Training Code ->> API: trainingJob = aiplatform.CustomPythonPackageTrainingJob()
         API ->> Training Job: model = trainingJob.run()
         Training Job -->> Custom Job: creates backing custom job
      end
      rect rgb(52, 168, 83)
         note right of Training Code: h
         Training Code ->> API: customJob = aiplatform.CustomJob
         Training Code ->> API: tuningJob = aiplatform.HyperparameterTuningJob(customJob)
         API ->> Hyperparameter Tuning Job: tuningJob.run()
      end
   end
   rect rgb(234, 67, 53)
      note right of User: Custom Container
      rect rgb(66, 133, 244)
         note right of Training Code: c
         Training Code ->> API: customJob = aiplatform.CustomJob()
         API ->> Custom Job: customJob.run()
      end
      rect rgb(251, 188, 4)
         note right of Training Code: f
         Training Code ->> API: trainingJob = aiplatform.CustomContainerTrainingJob()
         API ->> Training Job: model = trainingJob.run()
         Training Job -->> Custom Job: creates backing custom job
      end
      rect rgb(52, 168, 83)
         note right of Training Code: i
         Training Code ->> API: customJob = aiplatform.CustomJob()
         Training Code ->> API: tuningJob = aiplatform.HyperparameterTuningJob(customJob)
         API ->> Hyperparameter Tuning Job: tuningJob.run()
      end
   end
```
