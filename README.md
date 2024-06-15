# AWS CodeBuildでCodeArtifactを利用する

AWS CodeBuildでCodeArtifactを利用するための`buildspec.yml`です。

```yaml
version: 0.2
phases:
  pre_build:
    commands:
      - aws codeartifact login --tool npm --domain $AWS_DOMAIN --domain-owner $AWS_ACCOUNT_ID --repository $REPOSITORY_NAME
  build:
    commands:
      - npm install sample-package@1.0.0
  post_build:
    commands:
      - node index.js
      - echo completed on `date`
````
