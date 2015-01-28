# Introduction

Configuration repo for [Planet Birmingham](http://planet.birmingham.io), using [Planet Venus](http://intertwingly.net/code/venus/) as the provider.

# Instructions

## Initial setup

1. `git clone https://github.com/BirminghamIO/planet.birmingham.io`
2. `cd planet.birmingham.io`
3. `git clone https://github.com/rubys/venus.git`

Possible extra stuff

1. `sudo apt-get install xsltproc`

Building the pages (from the `planet.birmingham.io` directory)

1. `python ./venus/planet.py birminghamio.ini`
2. `firefox html/index.html`

(Once happy that this works, stick "`cd /path/to/planet.birmingham.io && python ./venus/planet.py birminghamio.ini`" in cron hourly or something.)

## Adding new blogs

Adding new blogs is a question of editing `birminghamio.ini` and adding a new section which looks like:

    [http://url/for/website/feed]
    name = Site Owner's Name
    twitter = Twitter Username
    glyphicon = Bootstrap Glyphicon

Note that you can't put the URL of the website *itself* in; it has to be the URL for the feed. You can inspect the site for the feed URL, or use https://pypi.python.org/pypi/feedfinder or similar tools.

## Editing templates

Edit `templates/birminghamio/index.html.tmpl` to change the look of the site. Note that while changing the templates, you can run `python ./venus/planet.py -o birminghamio.ini` (note the `-o`) which will regenerate the site from the cache without hitting the network, which is a lot faster.
