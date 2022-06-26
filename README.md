# サーバレスでSecurity Hub 通知
## dynamodb.ymal
初期Controleデータを自動投入が可能です。
また、初期データの制御はパラメータで指定できます。（デフォルト:無効化）

## dynamodb.ymal
Slack通知を行うため、Tokenの取得を行い、パラメータに指定してください。

## stepfunctions.yaml
通常通知を投稿するチャンネル, StepFunctionsのエラーを投稿するチャンネル、Security Hub管理者のSlackIDをパラメータに指定してください。

## スタックの展開
以下のコマンドでスタックを展開してください。

または、AWSコンソールから展開してください。

```
$ aws cloudformation deploy --stack-name dynamo-stack --template-file dynamodb.yaml --capabilities CAPABILITY_IAM

$ aws cloudformation deploy --stack-name asstets-stack --template-file assets.yaml \
--capabilities CAPABILITY_NAMED_IAM \
--parameter-overrides BotUserOAuthToken=BOT_USER_TOKEN 

$ aws cloudformation deploy --stack-name stepfunctions-stack --template-file stepfunctions.yaml --capabilities CAPABILITY_IAM \
--parameter-overrides \
Channel=CHANNEL \
ErrorChannel=ERROR_CHANNEL \
AdminSlackId=ADMIN_SLACK_ID

```

