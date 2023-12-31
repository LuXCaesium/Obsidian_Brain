---
created: 2023-12-31 00:23
tags:
---
---
created: 2023-12-31 00:23
source: [MLOps roadmap 2024](https://medium.com/marvelous-mlops/mlops-roadmap-2024-ff4216b8bc62)

---
# MLOps Learning Roadmap

## 1. Programming
Programming skills are essential for an MLOps engineer. Python is the most common language used for machine learning. Since MLOps engineers collaborate with machine learning engineers and data scientists, learning Python is important.

### 1.1 Python & IDEs
We suggest starting learning Python by reading a proper Python book and practicing the concepts.

### 1.2 Bash basics & command line editors
You will need to understand bash basics to add steps to your CI/CD pipelines, to create docker files, and many more other things.

- **Book suggestion:** [The Linux Command Line, 2nd Edition](https://www.amazon.com/Linux-Command-Line-William-Shotts/dp/1593279523) by William E. Shotts
- **Course suggestion:** [Bash mastery](https://www.udemy.com/course/bash-mastery)
- **VIM tutorial suggestion:** [VIM beginners guide](https://www.freecodecamp.org/news/vim-beginners-guide/)

## 2. Containerisation and Kubernetes
Containers are isolated software environments that help to streamline software development and deployment, regardless of the underlying infrastructure. It is an essential piece of modern software engineering best practices.

### 2.1 Docker
Docker is one of the most popular open-source containerisation platforms, also widely used in MLOps for multiple purposes: code development, model training, and endpoint deployment.

- **Docker roadmap:** [Docker Roadmap](https://roadmap.sh/docker)
- **Tutorial suggestion:** [Full docker tutorial by Techworld by Nana](https://www.youtube.com/watch?v=3c-iBn73dDE)

### 2.2 Kubernetes
Kubernetes is a must to learn for an MLOps engineer. It is widely used for machine learning model training, model endpoint deployment, and serving dashboards.

- **Kubernetes roadmap:** [Kubernetes Roadmap](https://roadmap.sh/kubernetes)
- **Tutorial suggestion:** [Kubernetes course by freecodecamp.com](https://www.youtube.com/watch?v=d6WC5n9G_sM)
- **Course suggestion:** [Kubernetes mastery](https://www.udemy.com/course/kubernetesmastery/)

- **K9s:** A powerful CLI tool that makes managing your Kubernetes clusters easy. [K9s website](https://k9scli.io)

## 3. Machine learning fundamentals
An MLOps engineer works with machine learning engineers and data scientists and should have some basic understanding of machine learning models.

- **Course suggestion:** [MLCourse.ai](https://mlcourse.ai/)
- **Book suggestion:** Applied Machine Learning and AI for Engineers by Jeff Prosise

## 4. MLOps principles
MLOps engineers must be aware of MLOps principles and what the factors are that contribute to MLOps maturity.

**Books:**
- *Designing Machine Learning Systems* by Chip Huyen
- *Introducing MLOps* by Mark Treveil and Dataiku

Check out [MLOps maturity assessment](https://marvelousmlops.substack.com/p/mlops-maturity-assessment)

## 5. MLOps components
MLOps platform consists of multiple MLOps components, such as version control, CI/CD, orchestration, compute, serving, and feature stores. In the end, the MLOps framework is about combining the tools. Check out the [Minimum set of must-haves for MLOps](https://marvelousmlops.substack.com/p/the-minimum-set-of-must-haves-for) article.

- **Book suggestion:** ML Engineering with Python by Andy McMahon

**Suggested courses:**
- [Made with ML MLOps course](https://madewithml.com/courses/mlops/)
- [The full stack 7-steps MLOps framework](https://www.pauliusztin.me/courses/the-full-stack-7-steps-mlops-framework)
- [End-to-end machine learning](https://www.udemy.com/course/sustainable-and-scalable-machine-learning-project-development/)

### 5.1 Version control & CI/CD pipelines
Without version control and CI/CD pipelines, ML model deployments cannot be traceable and reproducible.

**Books:**
- *Learning GitHub Actions* by Brent Laster
- *Learning Git* by Anna Skoulikari

**Tutorials & courses:**
- [Git & GitHub for beginners](https://www.youtube.com/watch?v=RGOj5yH7evk)
- [Taking Python to Production: A Professional Onboarding Guide](https://www.udemy.com/course/setting-up-the-linux-terminal-for-software-development/)

Pre-commit hooks are super useful for keeping your code neat and are an important piece of your CI pipeline. Check out [Welcome to pre-commit heaven](#) article.

### 5.2 Orchestration
Just like in data engineering, orchestration systems like Mage or Airflow are popular for machine learning engineering. There are also ML-specific orchestration tools (that do more than just orchestration), such as Kubeflow or Metaflow. Airflow seems to be still more common in industry.

- **Course suggestion:** [Introduction to Airflow in Python](#)

*Note: ML Engineering with Python book by Andy McMahon and The full stack 7-steps MLOps framework also use Airflow.*

### 5.3 Experiment tracking and model registries
Experiment tracking means logging metadata, parameters, and artifacts that belong to different model training runs. What is stored, depends on the algorithm and your needs. Experiment tracking makes it possible to compare different runs between each other. Models from different experiment runs can be registered and linked to the experiment, which helps traceability.

**MLflow** is probably the most popular tool for model registry and experiment tracking out there. MLflow is open source and integrates with a lot of platforms and tools. Check out [Find your way to MLflow without confusion](#) article.

**Course suggestion:** [MLflow Udemy course](#), [End-to-end machine learning (MLflow piece)](#)

### 5.4 Data lineage and feature stores
Feature stores have become quite popular recently and now can be considered an important component of MLOps infrastructure. A feature store helps to keep track of feature use and allows the sharing of features across models.

Every major cloud provider or ML platform (like Databricks) has a feature store available, so consider using it. If you need an open-source solution, consider Feast as it seems to be the most popular one (based on the number of GitHub stars).

**Tutorial suggestion:** [Creating a feature store with Feast part 1](#), [part 2](#), [part 3](#)

You do not per se need a feature store if you do not have many models sharing the same features. But you do need to track what data was used to produce a model artifact. Consider using DVC for that purpose.

**Course suggestion:** [End-to-end machine learning (DVC piece)](#)

### 5.5 Model training & serving
Where to train your model and how to serve it is probably the most controversial topic in MLOps. The answer to this question would be “it depends”.

Many data science teams rely on cloud-native solutions like AWS Sagemaker, Azure ML, or Vertex AI for training and serving their models.

If your organization relies heavily on Kubernetes and you have a proper team supporting it, consider using it. If you use Airflow for orchestration, it has KubernetesPodOperator that allows you to trigger a model training job on Kubernetes. For endpoint deployment, FastApi is the most common choice.

**Repository suggestion:** [ML deployment k8s FastAPI](#)

**Tutorial suggestion:** [How to build machine learning app with FastAPI](#)

If you have Kubeflow as an orchestrator, you can use Kubeflow pipelines for training and KServe for serving.

**Tutorial suggestions:** [Basic kubeflow pipeline](#), [Building and deploying machine learning pipelines](#), [KServe tutorial](#)

### 5.6 Monitoring & observability
Monitoring and observability are crucial parts of an MLOps platform. Even though these terms can be used interchangeably, there is a difference between them. Check out [ML monitoring vs Observability](#) article.

For ML system observability, the combination of Prometheus and Grafana is probably the most common out there. We suggest checking out [Mastering Prometheus and Grafana](#) course.

When it comes to ML-specific monitoring, like data and model drift, major cloud providers have their own solutions built into ML propositions. There are some open-source solutions available like Evidently.ai or NannyML.

**Course suggestion:** [Machine learning monitoring concepts](#), [Monitoring machine learning in Python](#)

## 6. Infrastructure as code: Terraform
Infrastructure as code is crucial to make your MLOps framework reproducible. Terraform is the most popular and powerful IaC tool. It works with all common cloud providers and platforms.

**Course suggestion:** [Terraform course for beginners](#)

**Short video:** [8 Terraform best practices by Techworld by Nana](#)

**Book suggestion:** [Terraform: Up and Running, 3rd Edition](#) by Yevgeniy Brikman
