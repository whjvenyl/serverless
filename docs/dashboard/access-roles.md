<!--
title: Serverless Dashboard - Access Roles
menuText: Access Roles
menuOrder: 6
layout: Doc
-->

<!-- DOCS-SITE-LINK:START automatically generated  -->

### [Read this on the main serverless docs site](https://www.serverless.com/framework/docs/dashboard/access-roles/)

<!-- DOCS-SITE-LINK:END -->

# Access Roles

You can use the Serverless Framework Dashboard to set up an AWS Access Role to help you secure your service deployments on AWS by enabling the Serverless Framework to issue temporary AWS Access Keys to deploy your services to AWS.

If an Access Role is not configured, the Serverless Framework service will use AWS Access Keys stored in [environment variables](https://serverless.com/framework/docs/providers/aws/guide/credentials/) or [AWS Profiles](https://serverless.com/framework/docs/providers/aws/guide/credentials/) to deploy your service.

With AWS Access Roles the AWS Access Keys are generated by Serverless Framework on every command and the credentials expire after one hour. The Serverless Framework leverages AWS Security Token Service and the AssumeRole API to automate creating and usage of temporary credentials, so your developers can stay productive and work securely without doing this manually.

If you do not use the Serverless Framework Dashboard to set up an AWS Access Role, then you will need to configure your Serverless Framework open source CLI to use the AWS Access Keys stored in [environment variables](https://serverless.com/framework/docs/providers/aws/guide/credentials/) or [AWS Profiles](https://serverless.com/framework/docs/providers/aws/guide/credentials/).

## Link your AWS Account

1. Open the [Dashboard](https://dashboard.serverless.com/)
2. Once logged in, click "**profiles**" near the top of the page.
3. Navigate to the profile you would like to configure with the AWS Access Role.
4. In the **AWS credential access role** tab, expand the "_how to add a role_".
5. Follow the directions which will take you through creating an IAM Role for the Serverless Framework.
6. Click "**save changes**" in the deployment profile to save the IAM Role ARN to the profile.

## Test your configuration

Before you run `serverless deploy` ensure that the Serverless Framework open-source CLI is resolving the new AWS Access Keys from the Serverless Framework Dashboard.

```
serverless info
```

This command requires authentication therefore requires that the AWS Access Keys from the Serverless Framework Dashboard to be resolved. You should expect this command to succeed.

## Use the generated AWS Access Keys in your service

You don't have to do anything in your `serverless.yml` file. When you run `sls deploy` the Serverless Framework will identify the deployment profile associated with the application or stage and it will generate the AWS Access Keys using the associated AWS Access Role automatically.

## Deploy using AWS Access Roles

That’s it! You are now ready to deploy using your AWS Access Roles.

```
serverless deploy
```
