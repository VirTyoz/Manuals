# General

###### Linux virtual machine with lost network
Set current time

###### 1c aplication server is freeze after hard reboot
re-register the virtual machine

###### Move swap
* Power off the virtual machine.
* Unregister the virtual machine. Right-click the virtual machine in the Inventory and choose Remove from Inventory.
* Open *.vmx


*/vmfs/volumes/datastore_name/virtual_machine_folder/*

```
sched.swap.dir = /vmfs/volumes/datastore_name/dir_name
#sched.swap.derivedName = xxx
```