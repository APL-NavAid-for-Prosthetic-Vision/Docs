# Oculus Go

## Description
Guide for setting up the oculus go app

## App Installation
* Follow this guide (using a windows computer, not the Jetson)
    * https://scriptable.com/blog/oculus-go-unity-setup-quick-start
    * Skip these steps since the .apk file is prebuilt
        * Step 3
        * Step 4
        * Step 10
        * Step 12-18
        * Step 20-22
    * After step 22, scroll down to “Installing a build from the command line” 
        * Follow those instructions to install the .apk file into the Oculus Go.  
        * apk file location:
            * https://bitbucket.xrcs.jhuapl.edu/projects/SLAMR01/repos/vr/browse/builds 
    * Restart the Oculus Go
    * Find the app on your Oculus Go in the Library, under Unknown Sources.

## Determine Oculus Go ip address
* Ensure Jetson Xavier and Oculus Go are connected to the same wifi network (either adhoctest or home network)
* In oculus app on your phone, hit settings
* Hit Oculus Go device, note mac address under controller
* In Jetson Xavier terminal, "arp -a"
* Find ip address associated with Oculus Go mac address