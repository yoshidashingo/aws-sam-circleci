[![CircleCI](https://circleci.com/gh/yoshidashingo/aws-sam-circleci.svg?style=svg)](https://circleci.com/gh/yoshidashingo/aws-sam-circleci)

# (Sample) AWS SAM deployment using CircleCI
## Workflow
1. Describe your app code.
1. Describe your Infra Spec(app-spec.yml)
1. Describe circle.yml in your repository root.

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
