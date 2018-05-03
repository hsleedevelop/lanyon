---
layout: post
title: Sonar scanner for Bitbucket pipeline
description: Sonar scanner for Bitbucket pipeline
category: misc
tags: [misc]
---

This is a sample build configuration for PHP. (mod by Theerayooth Kosin)
Check our guides at https://confluence.atlassian.com/x/VYk8Lw for more examples.
Only use spaces to indent your .yml configuration.
-----
You can specify a custom docker image from Docker Hub as your build environment.
Set up your SonarQube server or use public server before setting up the pipeline.

Uncomment below to use SonarQube image
image: sonarqube:latest

Choose Atlassion image
image: atlassian/default-image:latest

### Go with pipeline
```
pipelines:

  # any brance, https://confluence.atlassian.com/bitbucket/branch-workflows-in-bitbucket-pipelines-856697482.html
  default:
    - step:
        script:
          - apt-get --yes --force-yes update
          - apt-get --yes --force-yes install unzip curl php5-cli php-crypt-blowfish php5-mcrypt mcrypt git
          - php -v
          - php -m
          - curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
          - composer install
          - curl --insecure -OL https://sonarsource.bintray.com/Distribution/sonar-scanner-cli/sonar-scanner-2.8.zip
          - unzip sonar-scanner-2.8.zip
          - chmod +x sonar-scanner-2.8/bin/sonar-scanner
          - sonar-scanner-2.8/bin/sonar-scanner -Dsonar.exclusions=sonar-scanner-2.8.zip,sonar-scanner-2.8/**/*,vendor/**/* -Dsonar.login=<admin-user> -Dsonar.password=<admin-password> -Dsonar.projectKey=<project-key> -Dsonar.projectName=<project-name> -Dsonar.projectVersion=1.0 -Dsonar.sources=.  -Dsonar.host.url=http://<your-sonarqube-host>:9000 -Dsonar.sourceEncoding=UTF-8 -Dsonar.analysis.mode=publish
          - echo "http://<your-sonarqube-host>:9000/dashboard/index/<project-name>"
```
