# Zenoss-Toolbox

Note that the version of the toolbox tools (as set in the setup.py) of the 
zenoss_toolbox_2.0.3.zip, is reported as 2.3.1.

zenoss_toolbox.zip should be the same as zenoss_toolbox_2.0.3.zip

zenoss_toolbox_2.0.0.zip and zenoss_toolbox_2.0.3.zip explicitly uploaded

On a Zenoss 4.2.5 (I also have SUP 743 installed) there is no python library module called zodbpickle.
zenoss_toolbox_2.0.0, in zodbscan.py, does an import of:

from pickle import Unpickler as UnpicklerBase

and pickle.py can be found in /opt/zenoss/lib/python2.7 and includes the Unpickler method.

However, toolbox 2.0.3, in zodbscan.py, imports:

from zodbpickle.pickle import Unpickler as UnpicklerBase

and there is no zodbpickle module so you get an import failure when you try to run zodbscan.

If you have this issue, you should be able to install the older 2.0.0 version of the toolbox
and it will replace the newer 2.0.3.

--
[zenoss@zen42 local]$ easy_install zenoss_toolbox_2.0.0.zip
Processing zenoss_toolbox_2.0.0.zip
Running zenoss.toolbox-master/setup.py -q bdist_egg --dist-dir /tmp/easy_install-THpezi/zenoss.toolbox-master/egg-dist-tmp-Oyl7LK
Removing zenoss.toolbox 2.3.1 from easy-install.pth file
Adding zenoss.toolbox 2.0.0 to easy-install.pth file
Installing zodbscan script to /opt/zenoss/bin
Installing zenindextool script to /opt/zenoss/bin
Installing zenrelationscan script to /opt/zenoss/bin
Installing export4 script to /opt/zenoss/bin
Installing zencheckdbstats script to /opt/zenoss/bin
Installing zencatalogscan script to /opt/zenoss/bin
Installing use_scsi script to /opt/zenoss/bin
Installing findposkeyerror script to /opt/zenoss/bin
Installing validate4import script to /opt/zenoss/bin
Installing zennetworkclean script to /opt/zenoss/bin

Installed /opt/zenoss/lib/python2.7/site-packages/zenoss.toolbox-2.0.0-py2.7.egg
Processing dependencies for zenoss.toolbox==2.0.0
Finished processing dependencies for zenoss.toolbox==2.0.0

--

zodbscan then runs fine.

Jane Curry
jane.curry@skills-1st.co.uk
December 21st, 2022

