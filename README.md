Q1.Supported ML model deployment pipelines within HSBC's cloud-native GCP/GKE environment, contributing to automated build, validation, deployment, and release processes across controlled environments.

Q2. Worked with cloud-native, containerized workloads on GKE, supporting deployment automation, scalability, IAM/security controls, monitoring, troubleshooting, and production operations for enterprise banking platforms.



These two bullets can be converted into experienced-level interview questions and answers. Based on your resume, your strongest positioning is around GCP/GKE, Kubernetes, CI/CD, Terraform, Docker, monitoring, and cloud-native application deployment; your resume does not explicitly document production ML deployment, so avoid claiming that you built ML platforms end-to-end. 

Q1. What do you understand by an ML deployment pipeline?
Answer:
“An ML deployment pipeline automates the process of taking a trained machine-learning model from development into a controlled deployment environment.

From a DevOps perspective, I would focus on source-code management, containerization, CI/CD, artifact management, infrastructure provisioning, deployment to Kubernetes or a managed cloud service, configuration and secrets, monitoring, and rollback.

The pipeline could look like:

Git → Build/Test → Container Image → Artifact Registry → Security Scan → Deploy → Model Validation → Monitoring.”

Developer / Data Scientist
          |
          v
        Git
          |
          v
       CI Pipeline
          |
     Build + Test
          |
          v
     Docker Image
          |
          v
   Artifact Registry
          |
          v
     GKE / Cloud Run
          |
          v
    Model Endpoint
          |
          v
 Monitoring + Logging

Q2. How would you deploy an ML model on GKE?
Answer:
“I would containerize the model-serving application and publish the image to Artifact Registry. Then I would deploy it to GKE using Kubernetes manifests or Helm.

I would define the Deployment, Service, ConfigMap and Secret as required. For production I would configure resource requests and limits, health probes, autoscaling and appropriate IAM access.

I would integrate the deployment with CI/CD so that model-serving changes are validated and promoted through environments.”

Example:
Git
 |
Jenkins / GitLab CI
 |
Docker Build
 |
Artifact Registry
 |
Helm
 |
GKE
 |
Model Serving Pods
 |
Internal / External Service

Your resume supports the GKE, Docker, CI/CD, Terraform and deployment portions of this approach. Resume (10)
Q3. How would you handle a new model version?
Answer:
“I would version both the model artifact and the application container. I wouldn't simply overwrite the existing production model.

I would deploy the new version alongside the existing version and use a controlled rollout such as canary or blue-green deployment. After validating performance and application health, I would gradually shift traffic.

If there is a problem, I would roll traffic back to the previous model version.”

Model v1 ──────────────── Production
                 \
                  Model v2
                    |
                 Canary
                    |
              Validation
                    |
              Increase traffic
                    |
                 v2 Production

This connects directly with your resume's documented blue-green, canary and rolling deployment experience. Resume (10)
Q4. How would you monitor an ML deployment?
Answer:

I would monitor at several levels:

Infrastructure
- CPU
- Memory
- Disk
- Network
- Pod health
Kubernetes
- Pod restarts
- Deployment availability
- HPA behavior
- Node health
Application/model serving
- Request rate
- Latency
- Error rate
- Model response time
- Timeout rate
ML-specific metrics
- Prediction quality
- Model drift
- Data drift
- Model version
- Inference failures
“I would correlate application and infrastructure metrics with logs so that a model-serving problem can be distinguished from a Kubernetes or infrastructure problem.”

Your resume supports Prometheus, Grafana, Stackdriver and Datadog monitoring experience. Resume (10)
Q5. What would you do if the new model deployment started failing?
Answer:
“First I would determine whether the failure is in the container, Kubernetes deployment, configuration, dependency or model itself.

I would check pod status, events, container logs, resource utilization, readiness and liveness probes, configuration and secrets.

If the new model is causing production impact, I would immediately roll back to the previous known-good version while continuing RCA.”

Useful commands:
kubectl get pods
kubectl describe pod <pod>
kubectl logs <pod>
kubectl get deployment
kubectl rollout status deployment/model-server
kubectl rollout history deployment/model-server
kubectl rollout undo deployment/model-server

2. “Work with cloud-native environments” — Interview Q&A
Q6. What do you mean by a cloud-native environment?
Answer:
“A cloud-native environment uses cloud-managed infrastructure and modern application patterns such as containers, Kubernetes, microservices, Infrastructure as Code, CI/CD, automation, observability and elastic scaling.

In my experience, GKE, Docker, Terraform, Jenkins/GitLab CI/CD, monitoring and automated deployments are key parts of that environment.”

Your resume directly lists GCP, AWS, Docker, Kubernetes/GKE/EKS, Terraform, Jenkins, GitLab CI/CD and monitoring tools. Resume (10)
Q7. What cloud-native technologies have you worked with?
Answer:
“My primary cloud-native experience is around GCP and Kubernetes. I've worked with GKE, Docker, Terraform, Jenkins, GitLab CI/CD and Google Cloud Build. I've also worked with AWS EKS.

For observability I've used Prometheus, Grafana, Stackdriver and Datadog.

I've used these technologies for automated infrastructure provisioning, application deployments, monitoring and production support.”

This is strongly supported by your resume. Resume (10)
Q8. How do you deploy applications in a cloud-native environment?
Answer:
Developer
   |
   v
Git
   |
   v
CI/CD
   |
   +--> Unit Tests
   |
   +--> Security Checks
   |
   v
Docker Build
   |
   v
Artifact Registry
   |
   v
GKE
   |
   +--> Rolling
   +--> Canary
   +--> Blue/Green
   |
   v
Monitoring

“I prefer immutable, repeatable deployments where infrastructure and application configuration are version controlled. The deployment pipeline should provide validation, controlled promotion and rollback.”

Q9. How do Terraform and Kubernetes work together?
Answer:
“I generally use Terraform for infrastructure provisioning and Kubernetes/Helm for application deployment.

For example, Terraform can create the VPC, subnet, GKE cluster, IAM, networking and supporting infrastructure. Kubernetes manifests or Helm can then deploy the applications inside the cluster.”

Terraform
   |
   +-- VPC
   +-- Subnets
   +-- IAM
   +-- GKE
   +-- Supporting infrastructure
             |
             v
           GKE
             |
          Helm/K8s
             |
        Applications

Q10. How do you achieve high availability in a cloud-native application?
Answer:
“I avoid depending on a single instance or failure domain. In Kubernetes I use multiple replicas, appropriate scheduling across zones where required, health probes, autoscaling and load balancing.

At the infrastructure level I use highly available networking and managed services where appropriate.

I also make deployments reversible through versioning and rollback.”

This is particularly relevant to your current resume because your HSBC project explicitly describes multi-zone GKE resilience and fault isolation. Resume (10)
3. Combined interview scenario
Q11. You are asked to support an ML application running on GKE. Design the deployment.
Strong answer
“I would first containerize the model-serving application and maintain the code and deployment configuration in Git.

The CI pipeline would build and test the container, perform security checks and publish the image to Artifact Registry.

Terraform would manage the underlying GCP infrastructure, while Kubernetes/Helm would manage the application deployment.

On GKE I would use multiple replicas, resource requests and limits, readiness and liveness probes, and HPA where appropriate.

For a new model version, I would use a canary or blue-green deployment rather than replacing the existing version directly.

Finally, I would monitor infrastructure, Kubernetes and model-serving metrics and maintain a rollback mechanism.”

Architecture
                    Git
                     |
              Jenkins/GitLab
                     |
          +----------+----------+
          |                     |
      Build/Test          Security Scan
          |                     |
          +----------+----------+
                     |
                Docker Image
                     |
              Artifact Registry
                     |
                  GKE
                     |
             +-------+-------+
             |               |
          Model v1        Model v2
          Current          Canary
             |               |
             +-------+-------+
                     |
                Load Balancer
                     |
                   Users
                     |
              Monitoring

Important point for your interview
If the interviewer asks:
“Have you actually worked on ML deployment pipelines?”

Don't say “Yes, I have extensive ML deployment experience” unless that is genuinely part of your experience.

A credible answer based on your resume would be:
“My direct production experience is stronger on the DevOps and cloud-native platform side rather than on developing ML models. However, I have hands-on experience with the underlying technologies required for ML deployment—GKE, Docker, CI/CD, Terraform, IAM, monitoring and automated deployments. I understand how I would apply those capabilities to a model-serving pipeline, including containerization, artifact management, controlled deployment, autoscaling, monitoring and rollback.”

That answer is particularly strong because it is honest while still demonstrating that your existing experience is directly transferable.
