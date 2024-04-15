---
title: "Continuous Integration"
linkTitle: "Continuous Integration"
weight: 4
description: Get started with Snowflake emulator in continuous integration (CI) environments
---

## Introduction

This guide explains how to set up the LocalStack Snowflake emulator in a continuous integration (CI) environment. You can use the emulator to test your Snowflake integration without connecting to the real Snowflake instance.

To install the LocalStack Snowflake emulator, you need to set up the LocalStack CLI and pull the Docker image. After starting the Docker container, an endpoint (`snowflake.localhost.localstack.cloud`) is made available to connect to the emulated Snowflake instance, which you can use to test your data integrations in CI environments.

## Configure the LocalStack CI Key

Before you begin, set up the LocalStack CI key to activate the Snowflake emulator in your CI environment. LocalStack requires a CI Key for use in continuous integration (CI) or similar machine environments. Each instance startup in a CI or comparable environment consumes one CI token.

To create a CI key, follow these steps:

1. Open the [LocalStack Web Application](https://app.localstack.cloud).
2. Click the [**CI Keys**](https://app.localstack.cloud/workspace/ci-keys) on the left navigation pane.
3. Navigate to the **Generate CI Key** tab, enter a description, and click **Generate CI Key**.
4. Copy the generated CI key and set it as the `LOCALSTACK_API_KEY` environment variable in your CI environment.

## Setup the CI configuration

The following examples demonstrate how to set up the emulator in GitHub Actions, CircleCI, and GitLab CI.

{{< tabpane >}}
{{< tab header="GitHub Actions" lang="yaml" >}}
name: LocalStack Test
on: [ push, pull_request ]

jobs:
  localstack-action-test:
    name: 'Test LocalStack GitHub Action'
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3

      - name: Start LocalStack Snowflake emulator
        run:
          docker pull localstack/snowflake:latest &
          pip install localstack
          IMAGE_NAME=localstack/snowflake localstack start -d
          echo "Waiting for LocalStack startup..."
          localstack wait -t 15
          echo "Startup complete"
        env:
          LOCALSTACK_API_KEY: ${{ secrets.LOCALSTACK_API_KEY }}
{{< /tab >}}
{{< tab header="CircleCI" lang="yaml" >}}
version: 2.1

orbs:
  python: circleci/python@2.0.3

jobs:
  example-job:
    machine:
      image: ubuntu-2004:2022.04.1

    steps:
      - checkout

      - run:
          name: Start LocalStack
          command: |
            pip3 install localstack
            docker pull localstack/snowflake
            IMAGE_NAME=localstack/snowflake localstack start -d                     

            echo "Waiting for LocalStack startup..."  
            localstack wait -t 30                     
            echo "Startup complete"      

workflows:
  version: 2
  build:
    jobs:
      - example-job
{{< /tab >}}
{{< tab header="GitLab CI" lang="yaml" >}}
image: docker:20.10.16

stages:
  - test

test:
  stage: test
  variables:
    DOCKER_HOST: tcp://docker:2375
    DOCKER_TLS_CERTDIR: ""
    LOCALSTACK_API_KEY: $LOCALSTACK_API_KEY

  services:
    - name: docker:20.10.16-dind
      alias: docker
      command: ["--tls=false"]

  before_script:
    - apk update
    - apk add gcc musl-dev linux-headers py3-pip python3 python3-dev
    - python3 -m pip install localstack
  script:
    - docker pull localstack/snowflake:latest
    - dind_ip="$(getent hosts docker | cut -d' ' -f1)"
    - echo "${dind_ip} localhost.localstack.cloud " >> /etc/hosts
    - DOCKER_HOST="tcp://${dind_ip}:2375" IMAGE_NAME=localstack/snowflake localstack start -d
    - localstack wait -t 15
{{< /tab >}}
{{< /tabpane >}}
