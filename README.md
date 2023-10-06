# sls-mentor-github-action

Github action related to sls-mentor

https://sls-mentor.dev/

### You don't need this action 

Github Actions have everything that you need to run `sls-mentor` out of the box now, to do that simply use the run commands like so, with the right values for `myIAMRoleArn` and `myRegion`:

    name: CI
    on: push
    jobs:
    build:
        runs-on: ubuntu-latest
        steps:
        - uses: actions/checkout@v2
        - name: Run sls-mentor
          uses: sls-mentor/sls-mentor-github-action@v0.6
          with: 
            iam-role: myIAMRoleArn
            aws-region: myRegion

This action executes sls-mentor infrastructure audit on specified AWS account without any previous action/build step.

## Configuring an IAM role for the action 

You should use a Github action role configured with OIDC for Github. 
- Create an IAM role in the AWS console and add Github as a trusted identity: https://docs.github.com/en/actions/deployment/security-hardening-your-deployments/configuring-openid-connect-in-amazon-web-services;
- Assign the least privilege roles you want your Github action to assume. 