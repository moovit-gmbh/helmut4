# How-to: Upgrade to latest snapshot-release
This guide is intended to help and show how to upgrade a previous (stable) Helmut4 instance to a newer, current snapshot version. This guideline tries to combine all the related preparations and security precautions that are necessary to do this


## I - General recommendations
We strongly advise to always install an update on a development (staging) system first and check it with various stream and workflow tests


## II - Latest version & change-log
The latest snapshot-version can be found on our github page.
We strongly recommend that you only install the snapshot versions, as we do not support development versions that are used in production environments.

## IIa - Container versions
The versions of the corresponding containers can be found here: Container-Snapshot-Versions

## III - Create a Helmut backup
An update can be created within Helmut with no need of any other tools. This task is quite easy & straight forwarded.
Navigate to the preferences page and click the backup button.

![DataImage81](https://user-images.githubusercontent.com/58689860/148954552-56875a3f-e828-4dc4-9b7d-eeb401898d5e.png)

A window appears in which various parameters can be selected, which are then saved.
If you are not sure, you can select everything (we do not recommend selecting jobs and license)

![DataImage82](https://user-images.githubusercontent.com/58689860/148954663-8921701e-3878-4ff9-99d9-b7e68cfcaf15.png)

## IIIa - Sanity backup
If you want to be on the safe side, you can create a snapshot of your host computer (virtual machine), which can be used to restore the system in no time at all.

## IV - Update process part ONE - client
Before we can update the server, the client application must first be updated. Since new versions are often associated with Adobe extensions, it is necessary that these are up to date.
We strongly recommend doing a clean uninstall of the client for Windows and Mac.

We have two (basic) scripts, which will help you with this procedure.

[Windows script](https://moovit.jitbit.com/helpdesk/KB/View/40622281-windows-batch-script-update-helmut-client)<br>
[Macintosh script](https://moovit.jitbit.com/helpdesk/KB/View/41460385-mac-shell-script-update-helmut-client)

In general we recommend to remove the extensions from Adobe's CEP & local user temp folder as on windows side to delete the local stream-engine.

The latest version of the client installer is part of the server update - if you want to get this in advance, don't hesitate to write us a ticket.

## Va - Update process part TWO - server - stand-alone installation
Since all clients are running the latest version, we can proceed with updating the server.
This task is quite simple and straightforward.

```
#open a ssh session to the server
ssh username@ip-address

#switch to super user
sudo su

#run helmut update command (as described on github)
helmut-snapshot 4.0.7-release-0

#enter your docker-portainer password (default: admin)


#wait till the update is finished
#the first start of all containers after a update can take up to 4 minutes - be patient


#quiet session
exit
```

![DataImage65](https://user-images.githubusercontent.com/58689860/148955261-6263aed0-6738-4617-9bc3-87e2bbdcdc80.png)

## Vb - Update process part TWO - server - cluster installation
The process for a cluster environment is almost identical to that for a standalone environment. The difference is that the update process must be triggered on the server where the portainer instance is running.

This can be identified quite easily - open port 9000 on all servers - if the machine is a slave, this message will be displayed in the stack.

![DataImage67](https://user-images.githubusercontent.com/58689860/148955348-d4d42768-f773-42c4-aa8f-c4b675388be4.jpg)

The stack on the master has an additional "editor" tab, the configuration of which is as follows:

![DataImage55](https://user-images.githubusercontent.com/58689860/148955389-63dfd968-69b8-4965-8c27-674bb8854dd8.png)

The server on which the current stack configuration is displayed is the one on which the update must be performed.


## VI - Verify & check the update

After the successful update, give the system one to two minutes to allow all containers to start. We also recommend that you clear the cache & cookies of the active web-browser, as this can lead to display/connection problems.

First, please open the debugger and run some standard streams such as connected, custom user or creating/opening projects.
If these work without problems, this is proof that the update has been successfully completed.

As a next step, we recommend that you check all the streams and replace any deprecated nodes with the corresponding newer version.

This task will take some time, but it does not necessarily have to be done immediately - however, we suggest that it be done in the foreseeable future.

After these steps, we recommend creating a backup again and saving it.
If the test system runs without problems for some time, the update can be safely installed on the production system.

The procedure here is the same - however, a time period outside the daily production cycle should be chosen for this.
