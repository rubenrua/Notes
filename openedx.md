OpenEDX
=======

Sites
-----

* https://github.com/edx/edx-platform/wiki/Sites-powered-by-Open-edX
* https://mooc.campusdomar.es/
* https://iedra.uned.es/ (https://unedabierta.uned.es/)
* https://www.urjcx.urjc.es/
*

LINKS
-------

* WIKI: https://openedx.atlassian.net/
* GITHub: https://github.com/edx/configuration

* Install: https://openedx.atlassian.net/wiki/display/OpenOPS/Native+Open+edX+Ubuntu+12.04+64+bit+Installation
* Managing OpenEdX Tips and Tricks: https://openedx.atlassian.net/wiki/display/OpenOPS/Managing+OpenEdX+Tips+and+Tricks
* Migrations: https://openedx.atlassian.net/wiki/display/OPEN/Updating+Open+edX
* Load Test: https://github.com/edx/edx-load-tests

TIPS
----

* Login
```
sudo -H -u edxapp bash
cd
source ~/edxapp_env
```

* Check Status:
```
/edx/bin/supervisorctl status
```

* Create Admin:
```
cd /edx/app/edxapp/edx-platform/
sudo -u www-data /edx/bin/python.edxapp ./manage.py lms --settings aws create_user -s -p edx -e user@example.com
sudo -u www-data /edx/bin/python.edxapp ./manage.py lms --settings aws changepassword user
sudo -u www-data /edx/bin/python.edxapp ./manage.py lms --settings aws shell

from django.contrib.auth.models import User
me = User.objects.get(username="user")
me.is_superuser = True
me.is_staff = True
me.save()
```

* Compile assets manually
```
sudo -H -u edxapp bash
source /edx/app/edxapp/edxapp_env
cd /edx/app/edxapp/edx-platform
paver update_assets lms --settings=aws
paver update_assets cms --settings=aws
# if restart necesary
/edx/bin/supervisorctl status
/edx/bin/supervisorctl restart lms
/edx/bin/supervisorctl restart cms
tail -f /edx/var/log/{l,c}ms/edx.log

```


* Update platform
```
/edx/bin/update -h
/edx/bin/update -v configuration open-release/hawthorn.master-urjcx
/edx/bin/update -v edx-platform open-release/hawthorn.master-urjcx
```
