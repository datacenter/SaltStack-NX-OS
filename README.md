
# Cisco NXOS and SaltStack
## Early Field Trial (EFT) New Feature Support
Several new features have been comitted into the SaltStack open project.  Details on the new functionality can be accessed using the following links.

1. NX-OS Proxy and GuestShell Minion Installation Guide: https://github.com/saltstack/salt/blob/develop/doc/topics/installation/nxos.rst
1. Combined SSH and NX-API Minion Workflows: https://github.com/saltstack/salt/pull/49496
1. NX-OS Upgrade Execution and State Modules: https://github.com/saltstack/salt/pull/50588

This feature content is available in the latest `development` branch and not yet part of an official release.

To test out the new features follow these steps:

* Install SaltStack Master From `development` branch
  * Follow steps from this guide: https://docs.saltstack.com/en/latest/topics/development/hacking.html

* Follow steps outlined in the NX-OS Proxy and Guestshell Minion Installation Guide
  * https://github.com/saltstack/salt/blob/develop/doc/topics/installation/nxos.rst

## GuestShell Only Steps

If running the minion inside the GuestShell, exectute the following steps to sync the code down to the minion running inside the GuestShell.

* Make sure the minion is running inside the GuestShell and the key is accepted on the SaltStack Master.
* Copy the following files from your SaltStack Git Repository to the GuestShell Minion

```
salt-cp 'n9k-guestshell' <path_to_salt_git_clone>/salt/grains/nxos.py /usr/lib/python2.7/site-packages/salt/grains/nxos.py
salt-cp 'n9k-guestshell' <path_to_salt_git_clone>/salt/modules/nxos.py /usr/lib/python2.7/site-packages/salt/modules/nxos.py
salt-cp 'n9k-guestshell' <path_to_salt_git_clone>/salt/modules/nxos_upgrade.py /usr/lib/python2.7/site-packages/salt/modules/nxos_upgrade.py
salt-cp 'n9k-guestshell' <path_to_salt_git_clone>/salt/proxy/nxos.py /usr/lib/python2.7/site-packages/salt/proxy/nxos.py
salt-cp 'n9k-guestshell' <path_to_salt_git_clone>/salt/states/nxos.py /usr/lib/python2.7/site-packages/salt/states/nxos.py
salt-cp 'n9k-guestshell' <path_to_salt_git_clone>/salt/states/nxos_upgrade.py /usr/lib/python2.7/site-packages/salt/states/nxos_upgrade.py
salt-cp 'n9k-guestshell' <path_to_salt_git_clone>/salt/utils/nxos.py /usr/lib/python2.7/site-packages/salt/utils/nxos.py
salt-cp 'n9k-guestshell' <path_to_salt_git_clone>/salt/exceptions/exceptions.py /usr/lib/python2.7/site-packages/salt/exceptions.py
```

* Complete the process by restarting the SaltStack minion running in the Guestshell
