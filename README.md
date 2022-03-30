# useful-aws-commands

This repo is for storing useful AWS commands or other similar items when working with AWS programmatically.

Consideration if / when this grows is to make each one of these a function or wrap it in a make file so that it is simple to call the commands.

## Get KMS Key ARN using KMS Key Alias

```
export ALIAS_NAME=alias/s3-example

export KMS_KEY_ID=$(aws kms list-aliases --region us-east-1 --query 'Aliases[?AliasName=='$ALIAS_NAME'].TargetKeyId' --output text)

export KMS_KEY_ARN=$(aws kms list-keys --region us-east-1 --query "Keys[?KeyId=='$KMS_KEY_ID'].KeyArn" --output text)

echo $KMS_KEY_ARN
```