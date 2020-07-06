# Infrastructure as Code

## Pipenv install

```
$ pipenv install
```

## Cloud Formation Linter

```
$ pipenv run lint
```

## Alias aws-cli

You can run aws-cli in docker with the alias `daws`.

```
$ alias daws='docker run --rm -it -v `pwd`/.aws:/root/.aws -v `pwd`:/aws amazon/aws-cli'
```

## Cloud Formation Validation

```
$ daws cloudformation validate-template --template-body file://template/sample.yaml
```

## Cloud Formation Command Lines

```
$ daws cloudformation create-stack \
--stack-name sample \
--region ap-northeast-1 \
--template-body file://template/sample.yaml \
--parameters ParameterKey=ServiceName,ParameterValue=sample
```

```
$ daws cloudformation update-stack \
--stack-name sample \
--template-body file://template/sample.yaml \
--parameters ServiceName=sample
```

```
$ daws cloudformation cancel-update-stack --stack-name sample
```

```
$ daws cloudformation delete-stack --stack-name sample
```

```
$ daws cloudformation list-stacks --stack-status-filter CREATE_COMPLETE
```

### Relational Database Service

```
$ daws cloudformation create-stack \
--stack-name sample \
--region ap-northeast-1 \
--template-body file://template/sample.yaml \
--parameters ParameterKey=ServiceName,ParameterValue=sample \
ParameterKey=Environment,ParameterValue=prd \
ParameterKey=MasterUsername,ParameterValue=admin \
ParameterKey=MasterUserPassword,ParameterValue=password
```
