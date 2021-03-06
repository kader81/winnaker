# Winnaker
```
____    __    ____  __  .__   __. .__   __.      ___       __  ___  _______ .______
\   \  /  \  /   / |  | |  \ |  | |  \ |  |     /   \     |  |/  / |   ____||   _  \
 \   \/    \/   /  |  | |   \|  | |   \|  |    /  ^  \    |  '  /  |  |__   |  |_)  |
  \            /   |  | |  . `  | |  . `  |   /  /_\  \   |    <   |   __|  |      /
   \    /\    /    |  | |  |\   | |  |\   |  /  _____  \  |  .  \  |  |____ |  |\  \----.
    \__/  \__/     |__| |__| \__| |__| \__| /__/     \__\ |__|\__\ |_______|| _| `._____|


```

## What is Winnaker ?
Auditing tool for Spinnaker. Real Testing in real browser !

## What do you need?
1. a spinnaker url
2. a sample app
3. a sample pipeline

## Painless Headless Run
1. Build Docker:

	`docker build -t winnaker .`

2. Config :

	edit and replace default values in `./src/config.sh`

3. Run:

	`./run.sh`

## What does default run do ?
- Logs in to `spinnaker` through chromium browser
- Searches for `sampleapp` app
- Searches for `samplepipeline` the pipleline
- Gets the last build status
- Generates screenshot :
	- `./src/outputs/applications.png`
	- `./src/outputs/pipelines.png`
	- `./src/outputs/last_build_status.png`
	- `./src/outputs/login.png`
	- `./src/outputs/stage1.png`
- Any error will result in a non-zero code to the system.
- Error screenshots will be timestaped.


## Options
Config file is located at ./src/config.sh but you can simply add any of the options bellow to your run.sh commnand.

```
optional arguments:
  -h, --help            show this help message and exit
  -s, --start           starts manual execution of the pipline
  -fb, --forcebake      force bake, to be used wth --start
  -a APP, --app APP     the name of application to look for
  -p PIPELINE, --pipeline PIPELINE
                        the name of pipline to test
  -nl, --nologin        will not attempt to login
  -hl, --headless       will run in an xfvb display
```


## Examples :
##### Example 1: Gets the last build status of the default pipleine
`./run.sh`


##### Example 2: Starts default pipleine execution

`./run.sh -s`

##### Example 2: Start the pipleine with force rebake

`./run.sh -s -fb`

##### Example 2: Start build execution on diffrent pipleine than config file

`./run.sh -s -p "deploy to npe"`

##### Example 3 : override default app specified in the config file

use with --caution--, will override the sample app.

`./run.sh -a "differentapp" -p "diffrent pipleine"`


## How tos


#### How to setup winnaker hipchat bot ?
- create a hipchat bot
- grab the post url
it should look like
`https://INSERT_HIPCHAT_BASE_URL.com/v2/room/INSERT_ROOM_ID/notification?auth_token=INSERT_TOKEN`
