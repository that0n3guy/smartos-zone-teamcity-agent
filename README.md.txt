## Description
This repo contains several scripts to help with running a PHP webserver and Teamcity for testing.  **These are designed to be used on a "java" smartos instance** (http://wiki.joyent.com/wiki/display/jpc2/Java+Instance).

### Setup an nginx virtual host each time you run a build:
Have teamcity run:

```
wget https://raw.githubusercontent.com/that0n3guy/smartos-zone-teamcity-agent/master/create_site_simple.sh
bash create_site_simple.sh path/to/web/root www.domainhere.com
rm create_site_simple.sh
```

The `path/to/web/root` is where you want the nginx virtual host file to point at.  This will setup the nginx virtual host file and set the permissions withing the web root.

### Fix java's ssl issue 
This is swiped from: https://www.ailis.de/~k/uploads/scripts/import-startssl

Simply run `bash fix-ssl-error.sh` as root.

If your on windows, see: https://github.com/haron/startssl-java

