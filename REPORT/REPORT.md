# LES 2025 - Automation-SecOps module report - José Rodrigues [uc2021235353]

## Phase 1 - The CI Foundation - Building the Container

```yaml'
name: CI Pipeline

on:
  push:
    branches: ["main"]

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout repository
        uses: actions/checkout@v4

      - name: Set up Docker Buildx
        uses: docker/setup-buildx-action@v3

      - name: Build the Docker image
        uses: docker/build-push-action@v5
        with:
          context: .
          push: false
          tags: juice-shop-image:latest
```

Sections:
- `on`: Specifies the events that trigger the workflow. Here, it is set to run on a push to the main branch.
- `jobs`: This section contains all the jobs that will be executed as part of the workflow.
- `build`: This is the name of the job that will be run.
- `runs-on`: This specifies the type of virtual machine/runner to use, which is ubuntu-latest in this case.
- `steps`: This section lists the individual steps that will be executed in the job.
  - `Checkout repository`: This step uses the `actions/checkout@v4` to check out the repository code.
  - `Set up Docker Buildx`: This step uses the `docker/setup-buildx-action@v3` to set up Docker Buildx, which is a tool for building Docker images.
  - `Build the Docker image`: This step uses the `docker/build-push-action@v5` to build the Docker image with the specified context and tags.

GitHub Actions images:

![Running the action](phase1-1.png)
Running the action

![Successful run](phase1-2.png)
Successful run


## Phase 2 - Integrating SAST and SCA Scanning

Report: Analyze the new content of the ci.yml and describe the work performed by each
of the jobs. How do GitHub actions know where to find what is defined in “uses”
clauses? Select two of the clauses and explain them.

## Phase 3 - Container Image Security Scanning

Report: Explain, in your own words, why this error is occurring and identify the source of the
threat. Why is this threat dangerous? Provide evidence that you located the threat. Why does the
build workflow continue and finish despite these errors?

,

Report: Analyze the new content of the ci.yml and describe the work performed by each of the
jobs. What is the final output of the workflow deployed in the pipeline? Explain and justify the
results you obtained in a clear way, providing evidence for why you got that outcome.

## Phase 4 - Implementing Security Gates and Breaking the Build

Report: Analyze the new content of the ci.yml and describe the work performed by each of the
jobs. What is the final output of the workflow deployed in the pipeline? Explain and justify the
results you obtained in a clear way, providing evidence for why you got that outcome.

Report: For each of the gates previously discussed, describe and analyze their output in a
pragmatic way, giving your personal thoughts of the outcome obtained.