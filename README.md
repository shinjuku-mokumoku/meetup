![](/assets/images/shinjuku-mokumoku-banner-960x180.png)

# What's Shinjuku Mokumoku Programming?

１人だと勉強をサボりそうなオーガナイザーが **~~強制的に~~ ストイックにプログラミングする** ための時間を作ることを目的に毎週開催されているもくもく会です。

そのため、新宿プログラミングもくもく会では参加しているプログラマー各位が相談したりしながら、以下のようなテーマにそれぞれ取り組みます。

- 新しい言語・フレームワークを触りこむ
- 今後使うかもしれないミドルウェアの特性を掴む
- 分散データストアをとりあえず触って肌感覚を掴む
- 機械学習についてまとまって時間作って学習する
- 数学や統計を学び直す、論文を読む
- OSS活動やプライベートプロダクトを集中して進めたい

また、自身にプレッシャーを与えるためにもcheck-inにてやることを宣言し、check-outにて成果を発表します！

過去の雰囲気 : [shinjuku-mokumoku](https://github.com/shinjuku-mokumoku/shinjuku-mokumoku/meetups)

質問などありましたら、slackの [shinjuku-mokumoku](https://shinjuku-mokumoku.slack.com/) ([登録はこちら](https://join.slack.com/t/shinjuku-mokumoku/shared_invite/enQtNDY1NzY4NzE2NzU0LTQ4OTI2NDEzNTcyNjMzZGE1MDM1M2FmN2IyMTUzNzkxOTI4NzUxYjAxMmQzMDIxYWIwNzg2M2JiZDYwYjU3OTQ)) もしくは、twitter [#shinjukumokumoku](https://twitter.com/hashtag/shinjukumokumoku) にてご連絡ください。

## ToC

- Pitch
  - [Introduction, Closing](https://gitpitch.com/shinjuku-mokumoku/shinjuku-mokumoku)
  - [Boardgame](https://gitpitch.com/shinjuku-mokumoku/shinjuku-mokumoku/master?p=boardgame)
- Community
  - [slack](https://shinjuku-mokumoku.slack.com/) ([join from here](https://join.slack.com/t/shinjuku-mokumoku/shared_invite/enQtNDY1NzY4NzE2NzU0LTQ4OTI2NDEzNTcyNjMzZGE1MDM1M2FmN2IyMTUzNzkxOTI4NzUxYjAxMmQzMDIxYWIwNzg2M2JiZDYwYjU3OTQ)) もしくは、twitter [#shinjukumokumoku](https://twitter.com/hashtag/shinjukumokumoku))
  - [connpass group](https://shinjuku-moku.connpass.com/)
- Organize
  - [connpass event descritpion](connpass.md)
  - [organize workflow](ORGANIZE.md)

## Commands

Create event channel, reminder and poller

```sh
# on slack
/prepare <num>
```

Get channel id

```sh
# on slack
/get_channel_id <channel_name>
```

Generate presenter order

```sh
# on slack
/presenter <num>
```

Generate event template

```sh
docker-compose run node ./scripts/generateNextEvent.js
```

# Development Slash command

## TODO

- [ ] Migarte nextEventGenerate script to cloudfunction
- [ ] Run deploy only functions file changes
- [ ] Generate connpass event via circleci

## Getting Started

requirements

- node 8
- firebase account
- slack token
- github api token

[Install firebase cli and login](https://firebase.google.com/docs/cli/)

```sh
npm install -g firebase-tools
firebase login
# Generated authenticate in $HOME/.config/gcloud
```

Install packages

```sh
npm --prefix "functions" i
```

if you don't have slack api token, get api token from below:

- https://api.slack.com/custom-integrations/legacy-tokens

## Debug function

Run firebase function locally

```sh
npx --prefix "functions" run serve
```

Show firebase function logs

```sh
npm --prefix "functions" logs -- --only <mokumoku_init|get_channel_id>
```

## Set config

[if you haven't set some config, you should set config by blow command](https://firebase.google.com/docs/functions/config-env)

```sh
export SLACK_SLASH_TOKEN_PREPARE=<your_slack_slash_token>
export SLACK_SLASH_TOKEN_PRESENTER=<your_slack_slash_token>
export SLACK_API_TOKEN=<your_slack_api_token>

cd <project_root>
firebase functions:config:set \
slack.slash_token_prepare=$SLACK_SLASH_TOKEN_PREPARE \
slack.slash_token_presenter=$SLACK_SLASH_TOKEN_PRESENTER \
slack.api_token=$SLACK_API_TOKEN

firebase functions:config:get
# show setted configs
```

# Development Slash command

## TODO

- [ ] Migarte nextEventGenerate script to cloudfunction
- [ ] Run deploy only functions file changes
- [ ] Generate connpass event via circleci

## Getting Started

requirements

- node 8
- firebase account
- slack token

[Install firebase cli and login](https://firebase.google.com/docs/cli/)

```sh
npm install -g firebase-tools
firebase login
# Generated authenticate in $HOME/.config/gcloud
```

Install packages

```sh
npm --prefix "functions" i
```

if you don't have slack api token, get api token from below:

- https://api.slack.com/custom-integrations/legacy-tokens

## Debug function

Run firebase function locally

```sh
npx --prefix "functions" run serve
```

Show firebase function logs

```sh
npm --prefix "functions" logs -- --only <mokumoku_init|get_channel_id>
```

## Set config

[if you haven't set some config, you should set config by blow command](https://firebase.google.com/docs/functions/config-env)

```sh
export SLACK_SLASH_TOKEN_PREPARE=<your_slack_slash_token>
export SLACK_SLASH_TOKEN_PRESENTER=<your_slack_slash_token>
export SLACK_API_TOKEN=<your_slack_api_token>

cd <project_root>
firebase functions:config:set \
slack.slash_token_prepare=$SLACK_SLASH_TOKEN_PREPARE \
slack.slash_token_presenter=$SLACK_SLASH_TOKEN_PRESENTER \
slack.api_token=$SLACK_API_TOKEN

firebase functions:config:get
# show setted configs
```
