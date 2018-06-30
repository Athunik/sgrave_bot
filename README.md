### Heroku Web-App

[![Deploy](https://www.herokucdn.com/deploy/button.svg)](https://heroku.com/deploy?template=https://github.com/Athunik/sgrave-bot)

1. K‰ivitage skript ^
2. M‰‰rake oma skriptis SALIEN_CONFIG_V2

Kontrollige oma skripti effektiivsust https://dashboard.heroku.com/apps/[YOUR_APP_NAME]/logs



### Heroku CLI-App

```bash
$ git clone https://github.com/Athunik/sgrave-bot -o upstream
$ cd sgrave-bot
$ heroku create [APP_NAME]
$ heroku config:set "SALIEN_CONFIG_V2=[APP_CONFIG]"
$ git push heroku master
$ heroku ps:scale web=0 salien=1
```

And to check if it works:

```bash
$ heroku logs --tail
```



### Seadistamine

Skripti on vıimalik panna ka teisi parameetreid..

```bash
[
    {
        "token": "12345",
        "clan": "67890",
        "name": "first_acc",
        "selectedPlanetId": "28"
    }
]
```