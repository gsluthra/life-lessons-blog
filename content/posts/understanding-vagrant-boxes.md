+++

title = "Understanding Vagrant Boxes and VMs"
description = "Clearing the confusion around Vagrant boxes"
author = "Gurpreet Luthra"
date = 2015-10-03T02:13:50Z
images = ["/images/general/snow-jeep.jpg"]
aliases = [
    "/2015/10/03/understanding-vagrant-boxes.html/",
    "/2015/10/03/understanding-vagrant-boxes.html"
]


tags = [
    "programming",
    "technical",
    "devops",
]

+++

![On top of Mt Billing in Dharamshala, India](/images/general/snow-jeep.jpg "On top of Mt Billing in Dharamshala, India")

Vagrant is an awesome tool for developers to get their own sandboxed environments to play with.
To understand more about **Why Vagrant**, you could read my earlier blog post:
[Vagrant: An interesting approach to setup development environments FAST](/2012/12/16/vagrant-an-interesting-approach-dev).
But, because Vagrant does a lot of things auto-magically under the hoods, most of the times people are left confused
when they want to delete or add boxes or VMs. I will try and explain the relationships between Base Boxes, VMs, Virtual Box
Instances, etc in this post.

**Note:** The term *box* is loosely used by many people, and hence the confusion has risen even further.

There are 3 different entities involved in running a Vagrant *box*:

1. **Base Boxes:** The .box file is a packaged vagrant box for distribution. You can get boxes from [http://www.vagrantbox.es/](http://www.vagrantbox.es/) or people may provide boxes via FTP, Dropbox, or via any other file distribution system on the internet. The base box file path is mentioned in the Vagrantfile using the variable [config.vm.box_url](http://docs.vagrantup.com/v2/vagrantfile/machine_settings.html). This may point to a local file on your machine, or a URL from where vagrant should download the box. The base box is your starting point (FIRST TIME). The base box may be a fresh OS, or may be an OS with certain softwares pre-installed; depending on what the person, distributing the box, wanted to package into it. Read more here: [Base Boxes](http://docs.vagrantup.com/v2/boxes/base.html)
2. **Installed Boxes:** This is the list of Vagrant boxes installed on your machine. You can see this list by executing the command [vagrant box list](http://docs.vagrantup.com/v2/cli/box.html). You can think of them as vagrant templates available to you for creating machines to work with. These boxes can only be created from base boxes. Usually, you would download a base box, then install it using the *vagrant box add* command, and from then on you don't need the base box, and you can freely delete the base box (to free space on your hard disk). Any new machine you create, only needs one of the installed boxes to create itself from it. The installed boxes are usually placed by Vagrant in the *\<user-home-dir\>/.vagrant.d/boxes* folder. Any project on your machine, can use these boxes as base templates to spin off machines. **Note:** When you fire a *vagrant box remove* command, you are in effect removing the box template from your machine. After that you can only add it back using a base box (.box file).
3. **Machines:** When you fire the [vagrant up](http://docs.vagrantup.com/v2/cli/up.html) command, you are asking for a VM to be started (based on the *Vagrantfile* specification in the current directory). This is the Virtual Box Machine Instance that you are spinning off to work with. When you fire the [vagrant halt](http://docs.vagrantup.com/v2/cli/halt.html) command, you are shutting down the current VM (based on the Vagrantfile specification in the current directory). You can also confirm this if you launch your Virtual Box GUI -- it will show you a running machine when you say *vagrant up*, and a shut down machine when you say *vagrant halt*. These machines are usually stored in a hidden *.vagrant* folder in the same directory from where you fired the *vagrant up* command. **Note:** When you perform a [vagrant destroy](http://docs.vagrantup.com/v2/cli/destroy.html), you are destroying the VM (and not the template box from which you created this machine). Usually this VM is called "*default*".

The confusion actually occurs because of the way *vagrant up* command behaves. When you do a *vagrant up*, Vagrant will bring up the VM which was halted earlier. But, if the VM was destroyed (using vagrant destroy), or was never created in the first place, then Vagrant will **create** the VM from the installed box template. Hence, when you do *vagrant destroy*, followed by *vagrant up*, you are in fact creating a new VM from the installed template boxes. Therefore, its common for people to only do a *vagrant halt* (or suspend) so that they can start off from where they left. You will choose to *destroy* only if you don't care about any changes in the VM, and want to free the space occupied by the VM on your disk.

In development mode, since most code changes are done on your local file-system, and developers use Vagrant just to "run" the code, it is OK if they destroy the VM, at the end of your work day. The next time you perform a *vagrant up*, it will recreate the VM, [provision](http://docs.vagrantup.com/v2/provisioning/index.html) it, and run with the latest code (think of them like [Phoenix boxes](http://martinfowler.com/bliki/PhoenixServer.html)).

Note that, the *vagrant up* command will also download the base box and install it as a box template if it detects that this is the first time this box is being brought up. After this, you can choose to delete the downloaded .box file (or store it on some long-term disk store), since its not being used in your vagrant workflow. Vagrant required the .box file only to install and create a box template in your machine. All further VM creations will use the installed boxes.

Hopefully this explanation clears up any doubts you have about the relationship between .box files, vagrant boxes, Virtual Box Machines, etc.

_Originally posted on my older blog post here: [Understanding Vagrant Boxes and VMs](http://techie-notebook.blogspot.com/2015/10/understanding-vagrant-boxes-vms.html)_
