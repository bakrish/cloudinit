
This template deploys a Linux VM along with a Cloud-init script for additional provisioning activities.

The script accepts 4 parameters

- Username/Password
- Script Location - A Bash script that contains provisioning commands. It must be available on a public location, so that the file gets downloaded.
- Script Name - A fully qualified path on the VM, into which the above script gets downloaded

Cloud-init gets initialized by way of passing a script into the CustomData property.

var customScript = '#!/bin/sh \n echo Running cloud-init...\n wget ${scriptLocation} -O ${scriptName} \n sh ${scriptName} ${virtualNetworkName} \n\n'
