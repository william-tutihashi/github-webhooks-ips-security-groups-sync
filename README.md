# GitHub Webhooks IPs Security Groups Sync

Creates security groups allowing inbound github webhooks requests and keeps the github webhooks IPs up to date. It supports creating the security groups in multiple VPCs in the same region and set a custom name to them.

You must choose a unique security group name (SecurityGroupName parameter). The script will update security groups matching the name provided, even the ones not created by it.

To deploy, import the cloudformation template an fill the variables. To do so using the AWS CLI in bash, you may adapt and run the following command:
```shell
aws cloudformation deploy \
  --template-file ./stack.yaml \
  --stack-name some-name-for-your-stack \
  --capabilities CAPABILITY_NAMED_IAM \
  --parameter-overrides \
    VpcIds=vpc-xxxxxx,vpc-yyyyyy \
    SecurityGroupName=ALLOW-GITHUB-HOOKS \
    Ports=80,443 \
  --tags Key1=Value1 Key2=Value2 \
  --profile your-aws-profile \
  --region the-target-aws-region
```
