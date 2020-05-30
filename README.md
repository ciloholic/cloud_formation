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

You can run aws-cli in docker with the alias `laws`.

```
$ alias laws='docker run --rm -it -v `pwd`/.aws:/root/.aws -v `pwd`:/aws amazon/aws-cli'
```

## Cloud Formation Validation

```
$ laws cloudformation validate-template --template-body file://template/sample.yaml
```

## Cloud Formation Command Lines

```
$ laws cloudformation create-stack \
--stack-name sample \
--region ap-northeast-1 \
--template-body file://template/sample.yaml \
--parameters ParameterKey=ServiceName,ParameterValue=sample
```

```
$ laws cloudformation update-stack \
--stack-name sample \
--template-body file://template/sample.yaml \
--parameters ServiceName=sample
```

```
$ laws cloudformation cancel-update-stack --stack-name sample
```

```
$ laws cloudformation delete-stack --stack-name sample
```

```
$ laws cloudformation list-stacks --stack-status-filter CREATE_COMPLETE
```

### Relational Database Service

```
$ laws cloudformation create-stack \
--stack-name sample \
--region ap-northeast-1 \
--template-body file://template/sample.yaml \
--parameters ParameterKey=ServiceName,ParameterValue=sample \
ParameterKey=Environment,ParameterValue=prd \
ParameterKey=MasterUsername,ParameterValue=admin \
ParameterKey=MasterUserPassword,ParameterValue=password
```
