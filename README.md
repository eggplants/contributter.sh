# contributter.sh

Contributter on Bash

## Install

```bash
wget -nv https://git.io/Jz1lb -O contributter
sudo install -m 0755 contributter /usr/local/bin/contributter
rm contributter
```

## Usage

```shellsession
$ contributter
contributter - Contributter(https://contributter.potato4d.me) on Tarminal

Usage: contributter <GH-USERNAME> <DAY-BEFORE>
Args:
- GH-USERNAME GitHub's Username
- DAY-BEFORE  n days ago (default: 1)

$ contributter eggplants
eggplants さんの 2021/02/18 の contribution 数: 1 #contributter_report

# n days before
$ contributter eggplants 7
eggplants さんの 2021/02/12 の contribution 数: 14 #contributter_report
```

## License

MIT
