```
Implementing continuous delivery (CD) is a software development practice that involves automatically and reliably delivering new code changes to production or other environments, often with a focus on minimizing manual intervention and reducing the time between code commits and deployment. Here's a step-by-step guide on how to implement continuous delivery:
```

1. Define Goals

2. Version Control

3. Automate Builds with Continuous Integration

4. Automated Testing

5. Artifact Management

6. Automated Environments

7. Monitoring and Feedback

8. Security and Compliance

9. Define Deployment Strategies

10. Documentation and Training

11. Monitoring and Metrics

12. Continuous Improvement


## GitOps
### Scenario 1: One Application/Repo w/ GitOps

A single application is defined in a single repo.

#### Sprint Strategy
* Sprints are 2 weeks
* There is a release at the end of the sprint

#### Branching Strategy

feature/bugfix/hotfix -> develop -> release/vX.X.X -> main
* A feature or bugfix branch is created based on a ticket
* Features and bugfix branches are merged into develop
* Once all changes from a sprint  are merged into develop, a release branch is created from develop
* After the release branch has been deployed to production, it is merged into main

#### Deployment Strategy
There are 4 envs for the application: dev, qa, stage, prod
* A feature, bugfix, or develop branch shall only be deployed to dev, qa environments only
* release and main shall only be deployed to dev, qa, stage, prod environments
* Main is not deployed, only release branch
* During the sprint, devs can deploy their feature branches to the dev environment
* Develop is deployed automatically to qa and stage when a PR is merged to it
* When a release branch is created, it is deployed to stage automatically; with approval then deploys to prod

During the sprint, all the features/bug fixes are created, developed, tested in dev/qa envs,, and merged into develop. depending on the release planning, a release branch may be created/deployed to prod  mid sprint and/or at the end of the sprint. When a release branch is created, it is deployed to staging, and once approved, deployed to prod.


### Scenario 2: N services/repo for 1 App w/ GitOps
This example has a single application repo, that contains directories for N services that make up the application. All 4 services need to be deployable independently or together based on changes.

```
app-repo
├── service1
│   ├── README.md
│   ├── envs
│   │   ├── dev.yaml
│   │   ├── prod.yaml
│   │   ├── qa.yaml
│   │   └── stage.yaml
│   ├── helm
│   │   ├── dev-values.yaml
│   │   ├── prod-values.yaml
│   │   ├── qa-values.yaml
│   │   └── stage-values.yaml
│   ├── main.py
│   ├── requirements.txt
│   └── test
│       └── pytest.py
├── service2
│   ├── README.md
│   ├── envs
│   │   ├── dev.yaml
│   │   ├── prod.yaml
│   │   ├── qa.yaml
│   │   └── stage.yaml
│   ├── helm
│   │   ├── dev-values.yaml
│   │   ├── prod-values.yaml
│   │   ├── qa-values.yaml
│   │   └── stage-values.yaml
│   ├── main.py
│   ├── requirements.txt
│   └── test
│       └── pytest.py
├── service3
│   ├── README.md
│   ├── envs
│   │   ├── dev.yaml
│   │   ├── prod.yaml
│   │   ├── qa.yaml
│   │   └── stage.yaml
│   ├── helm
│   │   ├── dev-values.yaml
│   │   ├── prod-values.yaml
│   │   ├── qa-values.yaml
│   │   └── stage-values.yaml
│   ├── main.py
│   ├── requirements.txt
│   └── test
│       └── pytest.py
└── service4
    ├── README.md
    ├── envs
    │   ├── dev.yaml
    │   ├── prod.yaml
    │   ├── qa.yaml
    │   └── stage.yaml
    ├── helm
    │   ├── dev-values.yaml
    │   ├── prod-values.yaml
    │   ├── qa-values.yaml
    │   └── stage-values.yaml
    ├── main.py
    ├── requirements.txt
    └── test
        └── pytest.py

```