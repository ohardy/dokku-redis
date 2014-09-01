# Redis plugin for Dokku

Project: https://github.com/progrium/dokku

## Installation

```
cd /var/lib/dokku/plugins
git clone https://github.com/ohardy/dokku-redis redis
dokku plugins-install
```


## Commands
```
$ dokku help
    redis:flushall
    redis:dbsize
    redis:del           <key>
    redis:get           <key>
    redis:set           <key> <value>
    redis:info
    redis:monitor
    redis:ping
    redis:keys          [<pattern>]
    redis:env                        Get generated environment variables
    redis:url                        Get REDIS_URL for <app>
    redis:dump          > dump.rdb   Dump database
    redis:restore       < dump.rdb   Restore database
    redis:admin_console              Launch a Redis console as admin user
    redis:restart                    Restart the Redis docker container and linked app
    redis:start                      Start the Redis docker container if it isn't running
    redis:stop                       Stop the Redis docker container
    redis:status                     Shows status of Redis
    redis:update                     Update this plugin
    redis:migrate                    Migrate
```

## Updating this plugin
Dokku doesn't handle plugin update. I made a pull request to dokku for that (https://github.com/progrium/dokku/pull/669)

So, each time you update this plugin with `git pull`, you need to call:
```
$ dokku redis:migrate
```

## Info
This plugin adds following environment variables to your app automatically:

* REDIS_URL
* REDIS_HOST
* REDIS_PORT

## Usage

### Start Redis:
```
$ dokku redis:start                 # Server side
..or..
$ ssh dokku@server redis:start      # Client side

```

### Stop Redis:
```
$ dokku redis:stop                 # Server side
..or..
$ ssh dokku@server redis:stop      # Client side

```

### Restart Redis:
```
$ dokku redis:restart                 # Server side
..or..
$ ssh dokku@server redis:restart      # Client side

```

### Dump database:
```
$ dokku redis:dump > dump.rdb # Server side
..or..
$ ssh dokku@server redis:dump > dump.rdb # Client side
```

### Restore database from SQL:
```
$ dokku redis:restore < dump.rdb # Server side
..or..
$ ssh dokku@server redis:restore < dump.rdb # Client side
```
