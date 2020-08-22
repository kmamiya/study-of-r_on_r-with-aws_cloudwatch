# 目的

- ログファイル肥大でストレージ容量を圧迫しないようにする
- AWS上での運用を前提とするので、CloudWatchへ直接ログ出力する

# 実現方法

- AWS-SDKを使用してCloudWatchへログ出力する
- RubyではAWS-SDKを直接呼び出すLoggerクラスよりもFluentd経由でCloudWatchへ出力する実装が一般的なようなので、これを採用する
    - [Collecting and Analyzing Ruby on Rails Logs](https://www.fluentd.org/datasources/rails)
    - [luent-plugin-cloudwatch-logs](https://rubygems.org/gems/fluent-plugin-cloudwatch-logs)
- 実装テスト段階はDockerによる導入を行う

## Fluentdの導入

1. https://docs.fluentd.org/container-deployment/docker-compose
    1. Dockerfileを作成し、Pluginとして [fluent-plugin-cloudwatch-logs](https://rubygems.org/gems/fluent-plugin-cloudwatch-logs) を導入
1. https://hub.docker.com/_/fluentd

## Ruby on Rails -> Fluentdの導入

[Collecting and Analyzing Ruby on Rails Logs](https://www.fluentd.org/datasources/rails)

## Fluentd -> CloudWatch の導入
