docker-ce (Docker Community Edition)
--------------------------------------------------------

(Adapted from SlackBuilds.org and Vincent Batts' original scripts.)

Here's how to install the static release of Docker CE on Slackware.


First, go to the download page for docker-ce for static builds:

https://download.docker.com/linux/static/stable/x86_64/

Download the .tgz package.


Then, with the .tgz package in the same directory as the
docker-ce.SlackBuild script
to a Slackware .txz:

./docker-ce.SlackBuild

This will produce a Slackware compatible .txz package.  

You'll find the output package in the /tmp directory.


Then, install the package (again as root):

cd /tmp
upgradepkg --install-new docker-ce-17.12.0-x86_64-1ricardson.txz


To have the docker daemon start and stop with your host,
add to /etc/rc.d/rc.local:

```
  if [ -x /etc/rc.d/rc.docker ]; then
    /etc/rc.d/rc.docker start
  fi
```

and to /etc/rc.d/rc.local_shutdown (creating it if needed):

```
  if [ -x /etc/rc.d/rc.docker ]; then
    /etc/rc.d/rc.docker stop
  fi
```


Enjoy!  :-)

