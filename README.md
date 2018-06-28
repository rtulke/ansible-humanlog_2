# ansible humanlog 2

This Ansible callback plugin for human-readable result logging for Ansible.

Requirements
------------

Tested in: Ansible 1.9, 2.0, 2.1, 2.2, 2.3, 2.5

Bugfixes
--------

In Ansible 2.5.3 there is a small bug in task_queue_manager.py To fix this, open the file task_queue_manager.py see below.

**RedHat Fix:**
```bash
vim /usr/lib/python2.6/site-packages/ansible/executor/task_queue_manager.py +213
```

**Debian Fix:**

```bash
vim /usr/lib/python2.7/dist-packages/ansibl/eexecutor/task_queue_manager.py +213
```
and replace the line:

```bash
-                                       " see the 2.4 porting guide for details." % self.callback_obj._load_name, version="2.9")
+                                       " see the 2.4 porting guide for details." % callback_obj._load_name, version="2.9")
```

Versions
--------

* Modified from: https://github.com/n0ts/ansible-human_log
* Inspired from: https://github.com/redhat-openstack/khaleesi/blob/master/plugins/callbacks/human_log.py 
* Original from: https://gist.github.com/cliffano/9868180
* Newest on:     https://github.com/rtulke/ansible-humanlog_2
 
Installation:
-------------
* download https://raw.githubusercontent.com/rtulke/ansible-humanlog_2/master/human_log2.py or use git

```bash
git clone https://github.com/rtulke/ansible-humanlog_2.git
mkdir -p /usr/share/ansible_plugins/callback_plugins
cp ./ansible-humanlog_2/human_log2.py /usr/share/ansible_plugins/callback_plugins
```

Ansible Systemwide Configuration
--------------------------------

```bash
vim /etc/ansible/ansible.cfg
```

jump to the plugins path settings, like below:

```
action_plugins     = /usr/share/ansible_plugins/action_plugins
connection_plugins = /usr/share/ansible_plugins/connection_plugins
lookup_plugins     = /usr/share/ansible_plugins/lookup_plugins
vars_plugins       = /usr/share/ansible_plugins/vars_plugins
filter_plugins     = /usr/share/ansible_plugins/filter_plugins
```
and add the callback plugin path:

```
callback_plugins   = /usr/share/ansible_plugins/callback_plugins
```
