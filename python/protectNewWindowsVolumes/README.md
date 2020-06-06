# Add New Volumes to Windows File-based Protection Job Using Python

Warning: this code is provided on a best effort basis and is not in any way officially supported or sanctioned by Cohesity. The code is intentionally kept simple to retain value as example code. The code in this repository is provided as-is and the author accepts no liability for damages resulting from its use.

This script includes new volumes for physical windows servers in a file-based protection job.

## Download the script

You can download the scripts using the following commands:

```bash
# download commands
curl -O https://raw.githubusercontent.com/bseltz-cohesity/scripts/master/python/protectNewWindowsVolumes/protectNewWindowsVolumes.py
curl -O https://raw.githubusercontent.com/bseltz-cohesity/scripts/master/python/pyhesity.py
chmod +x protectNewWindowsVolumes.py
# end download commands
```

## Components

* protectNewWindowsVolumes.py: the main powershell script
* pyhesity.py: the Cohesity REST API helper module

Place both files in a folder together and run the main script like so:

```bash
./protectNewWindowsVolumes.py -v mycluster \
                              -u myuser \
                              -d mydomain.net \
                              -j 'My Backup Job' \
                              -e 'E:\' \
                              -e 'F:\' \
                              -x excludes.txt
```

## Parameters

* -v, --vip: DNS or IP of the Cohesity cluster to connect to
* -u, --username: username to authenticate to Cohesity cluster
* -d, --domain: (optional) domain of username, defaults to local
* -j, --jobname: name of the job to add the server to
* -e, --exclude: (optional) volume path to exclude (use multiple times for multiple paths)
* -x, --excludefile: (optional) a text file full of exclude file paths