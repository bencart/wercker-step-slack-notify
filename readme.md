[![wercker status](https://app.wercker.com/status/c1decccd19507e004590d671aa42082b/m "wercker status")](https://app.wercker.com/project/bykey/c1decccd19507e004590d671aa42082b)

# slack-notify

Send a message to a [Slack Channel](https://slack.com/).

### required

* `token` - The trailing part of the incoming web hook url

You can create a slack token by going to the account page on your slack domain:
`<your-subdomain>.slack.com/services` and click 'add New Integration' and select
'incoming webhooks'. Copy the part of the url after https://hooks.slack.com/services/
to use as your token

This token can be used directly in the wercker.yml (not
recommended) or better: as an environment variable. You can add environment
variables to wercker, by going to the settings tab of your application.
In the `pipeline` section you can add environment variables. You can use
those environment variables in the [wercker.yml](http://devcenter.wercker.com/articles/werckeryml/)
just as you would normally in a shell script (with a dollar sign in front of it).

### optional

* `username` - The bot username.
* `channel` - The channel to notify.
* `icon_url` | `icon_emoji` - The icon to use for this bot.
* `icon_url_failed` | `icon_emoji_failed` - The icon to use for this bot, on a failed build or deploy.
* `passed_message` - The message which will be shown on a passed build or deploy.
* `failed_message` - The message which will be shown on a failed build or deploy.

Example
--------

Add `SLACK_TOKEN` as deploy target or application environment variable.


    build:
        after-steps:
            - crub/slack-notify:
                token: $SLACK_TOKEN
                channel: "#general"
                username: wercker
                icon_url: https://avatars3.githubusercontent.com/u/1695193?s=140
                icon_emoji_failed: ":crying_cat_face:"

# License

The MIT License (MIT)

Copyright (c) 2013 wercker

Permission is hereby granted, free of charge, to any person obtaining a copy of
this software and associated documentation files (the "Software"), to deal in
the Software without restriction, including without limitation the rights to
use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of
the Software, and to permit persons to whom the Software is furnished to do so,
subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS
FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR
COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER
IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN
CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

# Changelog

## 0.0.14
- got it working

## 0.0.12
- forked from [sherzberg/slack-notify](https://github.com/sherzberg/wercker-step-slack-notify)

## 0.0.11
- added custom passed/failed message
- change how to specify the channel(Ex. "#room", "@someone")
- change default icon and username

## 0.0.8
- added custom icon url, icon emoji, and username properties

## 0.0.6
- Deploy url added
- the build/deploy words are now used as links instead of showing the full
url
- Show the branch name in the deploy message

## 0.0.5
- Minor change in documentation

## 0.0.4
- updated documentation
- check for redundant hash in channel argument
- tests added
