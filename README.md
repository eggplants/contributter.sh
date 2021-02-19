# contributter.sh
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

## License

MIT
