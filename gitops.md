
# What is GitOps

GitOps is a way to do Kubernetes cluster management and application delivery.  It works by using Git as a single source of truth for declarative infrastructure and applications. Accounting to [Weaveworks](https://www.weave.works/technologies/gitops/) the GitOps can be summarized as these two things:

- An operating model for Kubernetes and other cloud native technologies, providing a set of best practices that unify deployment, management and monitoring for containerized clusters and applications.
- A path towards a developer experience for managing applications; where end-to-end CICD pipelines and Git workflows are applied to both operations, and development.

## The next question pops up our mind Why GitOps? What benefit going to bring this? 

I listed 3 key important benefit Why GitOps? to learn about more refer to [GitOps.tech article](https://www.gitops.tech/#:~:text=GitOps%20is%20a%20way%20of,Git%20and%20Continuous%20Deployment%20tools.)

- What is unique about GitOps is that you don’t have to switch tools for deploying your application. Everything happens in the version control system you use for developing the application anyways.
- Your production environment is down! With GitOps you have a complete history of how your environment changed over time. This makes error recovery as easy as issuing a git revert and watching your environment being restored.
- GitOps allows you to manage deployments completely from inside your environment. For that, your environment only needs access to your repository and image registry. That’s it. You don’t have to give your developers direct access to the environment.

## What shall I use? Argo or Flux or Junkins X?” come up regularly. Here is my point of view

Let us look at [Flux](https://fluxcd.io/), the Flux installation is straight forward and easy you can install using based on [Helm Charts](https://docs.fluxcd.io/en/1.19.0/tutorials/get-started-helm/) and [Kustomize](https://docs.fluxcd.io/en/1.19.0/tutorials/get-started-kustomize/) the deployment of manifest happen true GitOps fashion the Flux pull changes from remote Git repo. If like to trigger changes manually you use fluxctl sycn to synchronization.

ArgoCD is installed as easy as Flux. The major difference is It runs on Kubernetes in its own namespace and all configuration is stored in ConfigMaps, Secrets, and Custom Resources. The benefit of this multi-tenancy (Assing project team to view application related to them) multi-cluster, auto detect the Git repo changes and notify on UI and dry run the changes before apply. 

Jenkins X is a complex and supports multi-tenancy, multi-cluster, build pipelines and ChatOps. I don’t go through the details of this tool and decided to focus on ArgoCD deployment. The reason is [Flux CD joins forces with Argo CD project](https://discuss.kubernetes.io/t/flux-cd-joins-forces-with-argo-cd-project/8678) and bringing bring a unified GitOps experience.

Install and Configure 