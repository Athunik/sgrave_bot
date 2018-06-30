### Heroku Web-App

[![Deploy](https://www.herokucdn.com/deploy/button.svg)](https://heroku.com/deploy?template=https://github.com/Athunik/sgrave_bot)

1. K�ivitage skript ^
2. M��rake oma skriptis SALIEN_CONFIG_V2

Kontrollige oma skripti effektiivsust https://dashboard.heroku.com/apps/[YOUR_APP_NAME]/logs



### Heroku CLI-App

```bash
$ git clone https://github.com/Athunik/sgrave_bot -o upstream
$ cd sgrave-bot
$ heroku create [APP_NAME]
$ heroku config:set "SALIEN_CONFIG_V2=[APP_CONFIG]"
$ git push heroku master
$ heroku ps:scale web=0 salien=1
```

Kontrollige kas skript t��tab v�i mitte..

```bash
$ heroku logs --tail
```



### Seadistamine

Skripti on v�imalik panna ka teisi parameetreid..

```bash
[
    {
        "token": "#",
        "clan": "#",
        "name": "$",
        "selectedPlanetId": "#"
    }
]
```