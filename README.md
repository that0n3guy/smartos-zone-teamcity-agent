## Description
This repo contains several scripts to help with running a PHP webserver and Teamcity for testing.  **These are designed to be used on a "java" smartos instance** (http://wiki.joyent.com/wiki/display/jpc2/Java+Instance).

### Setup an nginx virtual host each time you run a build:

* `-d` is for domain
* `-w` is for web directory (ie web root)
* `-p` is for fastcgi_param paramaters (you can set environment variables with this).  You can add more than one as well.  See my second example below.  Don't use spacing or funky characters.


Have teamcity run:
```
wget https://raw.githubusercontent.com/that0n3guy/smartos-zone-teamcity-agent/master/create_site_simple.sh
bash create_site_simple.sh -w /home/admin/BuildAgent/work/path/goes/here -d test.example.com -p myvariable=valuehere
rm create_site_simple.sh
```

I run mine like so:
```
wget https://raw.githubusercontent.com/that0n3guy/smartos-zone-teamcity-agent/master/create_site_simple.sh
bash create_site_simple.sh -w %teamcity.build.checkoutDir% -d test.example.com -p servertype=testing -p anothervariable=hello
rm create_site_simple.sh
```


The `path/to/web/root` is where you want the nginx virtual host file to point at.  This will setup the nginx virtual host file and set the permissions withing the web root.

### Fix java's ssl issue 
This is swiped from: https://www.ailis.de/~k/uploads/scripts/import-startssl

Simply run `bash fix-ssl-error.sh` as root.

If your on windows, see: https://github.com/haron/startssl-java

