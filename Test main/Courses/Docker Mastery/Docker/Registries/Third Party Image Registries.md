I've mentioned Docker Hub, Docker Enterprise Edition DTR (Docker Trusted Registry), and Docker Registry as three options for storing your images, but there are many 3rd party options out there.

[Quay.io](http://Quay.io) is a popular choice, and is very comparable to Docker Hub as a cloud-based image registry.  Sysdig did a [Docker Usage Report in April 2017](https://sysdig.com/blog/sysdig-docker-usage-report-2017/) based off their users that shows Quay as the most popular cloud-based choice.

If you're on [AWS](https://aws.amazon.com/ecr/), [Azure](https://azure.microsoft.com/en-us/services/container-registry/), or [Google Cloud](https://cloud.google.com/container-registry/), they all have their own registry options that are well integrated with their toolset.

If you want a self-hosted option, there's [Docker EE](https://www.docker.com/enterprise-edition#/container_management), [Quay Enterprise](https://quay.io/plans/?tab=enterprise), and also GitLab, which comes with [GitLab Container Registry](https://about.gitlab.com/2016/05/23/gitlab-container-registry/), among others.

There's a much larger list of registries over at the [Awesome Docker](https://github.com/veggiemonk/awesome-docker#hosting-images-registries) list.