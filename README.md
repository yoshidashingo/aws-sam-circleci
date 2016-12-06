[![CircleCI](https://circleci.com/gh/yoshidashingo/aws-sam-circleci.svg?style=svg)](https://circleci.com/gh/yoshidashingo/aws-sam-circleci)

# (Sample) AWS SAM deployment using CircleCI
## Workflow
1. Describe your code.
1. Describe app-spec.yml
1. Describe circle.yml in your repository root.

### circle.yml
```yml:circle.yml
machine:
  timezone: Asia/Tokyo

dependencies:
  override:
    - sudo pip install awscli
  post:
    - aws configure set region $REGION

test:
  override:
    - echo "Nothing to do here"

deployment:
  production:
    branch: master
    commands:
      - zip app.zip index.js
      - aws cloudformation package --template-file app-spec.yml --output-template-file app-spec.deploy --s3-bucket $S3_BUCKET_NAME
      - aws cloudformation deploy --template-file app-spec.deploy --stack-name $STACK_NAME --capabilities CAPABILITY_IAM
```

## Prerequisite
### AWS Permissions
Set AWS credentials to "AWS permissions".
- Access Key ID
- Secret Access Key

### Environment Variables
Set Environment Variables for using in CD pipeline.
- REGION
- S3_BUCKET_NAME
- STACK_NAME

## Misc
### .gitignore of mine.
```
*.DS_Store
*.zip
*.deploy
```
