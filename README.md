# contributter.sh

[![Cron contributter](https://github.com/eggplants/contributter.sh/actions/workflows/cron.yml/badge.svg)](https://github.com/eggplants/contributter.sh/actions/workflows/cron.yml)

Contributter on Bash

## Install

```bash
$ wget -nv https://raw.githubusercontent.com/eggplants/contributter.sh/main/contributter
$ sudo install -m 0755 contributter /usr/local/bin/contributter
$ rm contributter
```

## Usage

```bash
$ contributter
contributter - Contributter(https://contributter.potato4d.me) on Tarminal

Usage: contributter <GH-USERNAME> <DAY-BEFORE>
Args:
- GH-USERNAME GitHub's Username
- DAY-BEFORE  n days ago (default: 1)
```


## Example

- basic

```bash
$ contributter eggplants
eggplants さんの 2021/02/18 の contribution 数: 1 #contributter_report
```

- n days before

```bash
$ contributter eggplants 7
eggplants さんの 2021/02/12 の contribution 数: 14 #contributter_report
```

- post on twitter

```bash
$ gem install twurl
$ twurl authorize \
    --consumer-key XXXXXXXXXXXXXXXXXXXXXXXXX \
    --consumer-secret XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
$ twurl -X POST -d "status=$(contributter eggplants)" /1.1/statuses/update.json
```

- cron

```bash
$ crontab -e
1 0 * * *       twurl -X POST -d "status=$(contributter eggplants)" /1.1/statuses/update.json
```

- post on Twitter with GitHub Action at 00:01 JST

```yml
name: Cron contributter

on:
  schedule:
    - cron: "1 15 * * *"

jobs:
  build:
    runs-on: ubuntu-latest
    env:
      MY_SCREEN_NAME: egpl0
      MY_LANGUAGE: ja
      CONSUMER_KEY: ${{ secrets.CONSUMER_KEY }}
      CONSUMER_SECRET: ${{ secrets.CONSUMER_SECRET }}
      ACCESS_TOKEN: ${{ secrets.ACCESS_TOKEN }}
      ACCESS_TOKEN_SECRET: ${{ secrets.ACCESS_TOKEN_SECRET }}
    steps:
      - name: Setup tweet.sh
        run: |
          sudo apt install curl jq nkf openssl -y
          curl -s https://raw.githubusercontent.com/piroor/tweet.sh/trunk/tweet.sh > tweet.sh
          chmod +x tweet.sh
      - name: Setup contributter.sh
        run: |
          curl -s https://raw.githubusercontent.com/eggplants/contributter.sh/master/contributter > contributter.sh
          chmod +x contributter.sh
      - name: Post on Twitter
        run: |
          echo ${MY_SCREEN_NAME}
          ./tweet.sh post "$(./contributter.sh eggplants)"
```

## License

MIT
