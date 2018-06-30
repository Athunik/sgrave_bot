### Deploying with web-console

[![Deploy](https://www.herokucdn.com/deploy/button.svg)](https://heroku.com/deploy?template=https://github.com/South-Paw/sgrave-bot)

1. Click the button above.
2. Set SALIEN_CONFIG_V2 ([see note below](#heroku-configuration)).
3. That's all!

To check if it works, visit logs at https://dashboard.heroku.com/apps/[YOUR_APP_NAME]/logs

If you see "Application Error" when going to the webpage of your app, it's okay - the script will still run anyway.

### Deploying with Heroku CLI

```bash
$ git clone https://github.com/South-Paw/sgrave-bot -o upstream
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

### Heroku configuration

`SALIEN_CONFIG_V2` is just an array of config that will be passed to `SalienScript` constructor.

If you only have one account, then your config will look like this:

```JSON
[
    {
        "token": "12345"
    }
]
```

The only mandatory key for each account is `token` and you can add extra keys to this config such as `clan`, `name` or `selectedPlanetId`:

```JSON
[
    {
        "token": "12345",
        "clan": "67890",
        "name": "first_acc",
        "selectedPlanetId": "28"
    }
]
```

If you had two accounts for example;

* one named `first_acc` with a token of `123` and a group of `98712`
* one named `second_acc` with a token of `456` and a group of `67890`

then you would make your config look like this:

```JSON
[
    {
        "token": "123",
        "clan": "98712",
        "name": "first_acc"
    },
    {
        "token": "456",
        "clan": "67890",
        "name": "second_acc"
    }
]
```

### Updating

#### Easy

The easiest way to update script on heroku is to just delete your old app and create new.

You can also link your Heroku app to your Dropbox account. To do that, [download this repository](https://github.com/South-Paw/salien-script-js/archive/master.zip) as a zip archive, and unpack it to the folder created on your Dropbox.

For more info on this, visit: https://devcenter.heroku.com/articles/dropbox-sync

#### Medium

1. Fork this repo on github.
2. In your heroku app control panel, at Deploy tab, connect your app to a forked repository and enable automatic deploys.
3. When update comes, merge changes into your repo on github:
    1. Create new pull request.
    2. Select your repo's master branch as base fork, and South-Paw/salien-script-js master branch as head fork.
    3. Click on a big green button "Merge pull request".

For more info on connecting github account, visit: https://devcenter.heroku.com/articles/github-integration

For more info on syncing fork using web interface, check this tutorial: https://www.sitepoint.com/quick-tip-sync-your-fork-with-the-original-without-the-cli/

#### Hard

If you created your app using web-console, you need to clone heroku repo first

```bash
$ git clone https://git.heroku.com/[APP_NAME].git -o heroku
$ cd [APP_NAME]
$ git remote add upstream https://github.com/South-Paw/salien-script-js.git
```

And then, fetch, merge and push

```bash
$ git fetch upstream
$ git merge remotes/upstream/master
$ git push heroku master
```

---