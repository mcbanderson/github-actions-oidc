# github-actions-oidc

## About

This repository demonstrates how to setup an OIDC provider and an IAM role in AWS, to enable AWS automation using GitHub Actions. It was developed for a talk at the [AWS Sacramento Meetup](https://www.meetup.com/aws-sacramento/).

[The presentation slides I used for that talk are available here.](https://docs.google.com/presentation/d/19SCvyJLAykL_NStXqFmLPnmPf4VBkk1c78ea3n27Csw/edit?usp=sharing)

## What's Here
This repository contains two resources.

First, `template.yaml` is a CloudFormation template for creating an OIDC Provider and IAM Role. The OIDC Provider is configured for GitHub, and the role is configured to be assumable by the repository specified when creating the CloudFormation Stack.

Second, `.github/workflows/aws.yaml` is a GitHub Actions Workflow which demonstrates how to assume your newly created IAM Role using OIDC.

The CloudFormation template can deployed using the following CLI command.

`aws cloudformation deploy --template-file template.yaml --stack-name gha-oidc-stack --parameter-overrides GitHubOrg=<GitHub user or org> RepositoryName=<GitHub repo> --capabilities CAPABILITY_NAMED_IAM`

## Additional Resources

[GitHub's documentation on configuring OIDC with AWS.](https://docs.github.com/en/actions/deployment/security-hardening-your-deployments/configuring-openid-connect-in-amazon-web-services)

[AWS' documentation on creating OIDC providers.](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_providers_create_oidc.html)
