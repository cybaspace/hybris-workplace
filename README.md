# SAP Commerce (hybris) tool

## Start setup
To start the setup process just call the following command on console
```bash
curl -s https://raw.githubusercontent.com/cybaspace/hybris-workplace/main/setup |bash
```

## Hybris shortcuts
The interesting part about the hybris shortcuts is you can call them anywhere in your hybris project, doesn't matter if your are in platform directory or extension or anywhere else.

Also you don't have to call `setantenv.sh` anymore - if needed it will be done implicit.

For example you are in the directory of a custom extension and call `yab` (hybris ant build):   
This will first change to platform directory, call `setantenv.sh`, go back to extension directory and then call `ant build`.

### Hybris logging (yl..)
* `ylf`  
  shows the hybris tomcat console logging with `tail -f`
* `yln`  
  shows the hybris tomcat console logging with `tail -f` and the given number of past lines
* `ylg`  
  greps the given pattern from actual hybris tomcat console
* `ylfg`  
  greps the given pattern from upcoming logging of actual hybris tomcat console
* `yls`   
  shows from actual hybris tomcat logging only the next coming server startup message


### Hybris directories (yd..)
* `ydp`  
  cd to hybris platform dir
* `ydy`  
  cd to hybris root dir
* `ydr`  
  cd to project root dir
* `ydt`  
  cd to platform tomcat dir
* `ydd`  
  cd to hybris data dir
* `ydl`  
  cd to hybris log dir
* `ydc`  
  cd to hybris config dir
* `ydb`  
  cd to hybris bin dir
* `yde`  
  cd to the extension dir specified by parameter  
  e.g. `yde myinitialdata`  
  **It can take some seconds to find the correct directory!**


### Hybris unittests (yu..)
* `yup`  
  hybris unit tests with name of package to test (`yup com.hybris.*` <=> `ant unittests -Dtestclasses.packages=com.hybris.*`)
* `yue`  
  hybris unit tests with name of extension to test (`yue mycore` <=> `ant unittests -Dtestclasses.extensions=mycore`)

### Hybris ant operations (ya..)
The hybris ant operations have 3 different contextes:
1. if you are in an extensions root directory (where the `extensioninfo.xml` resides) ant operates on this extension!
1. Last parameter in the call is the name of an extension or platform, then it will change to the extension or platform directory first.  
   e.g. `yacb mecore` or `ya clean mycore` or `yab platform`  
   `platform` is useful if you are in an extension directory, because normally it will operate only on the extension, not on the whole hybris system
1. in every other case it will operate on the project (goto hybris platform dir first)
* `ya`  
  hybris ant with ant command(s) (e.g. `ya clean all`)
* `yab`  
  hybris ant build
* `yacb`  
  hybris ant clean build
* `yaca`  
  hybris ant clean all

### Hybris server (ys..)
* `yss`  
  start hybris server (same as: `hybris/bin/platform/hybrisserver.sh start`)
* `ysp`  
  stop hybris server (same as: `hybris/bin/platform/hybrisserver.sh stop`)
* `ysr`  
  restart hybris server (stop and start / no logging to console / no debug mode)
* `ysd`  
  start hybris server in debug mode
* `ysc`  
  start hybris server with logging to console
