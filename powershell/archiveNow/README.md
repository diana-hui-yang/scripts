# Archive Latest Snapshot using PowerShell

Warning: this code is provided on a best effort basis and is not in any way officially supported or sanctioned by Cohesity. The code is intentionally kept simple to retain value as example code. The code in this repository is provided as-is and the author accepts no liability for damages resulting from its use.

This powershell script archives the latest local snapshot to an external target.

## Download the script

Run these commands from PowerShell to download the script(s) into your current directory

```powershell
# Download Commands
$scriptName = 'archiveNow'
$repoURL = 'https://raw.githubusercontent.com/bseltz-cohesity/scripts/master/powershell'
(Invoke-WebRequest -Uri "$repoUrl/$scriptName/$scriptName.ps1").content | Out-File "$scriptName.ps1"; (Get-Content "$scriptName.ps1") | Set-Content "$scriptName.ps1"
(Invoke-WebRequest -Uri "$repoUrl/cohesity-api/cohesity-api.ps1").content | Out-File cohesity-api.ps1; (Get-Content cohesity-api.ps1) | Set-Content cohesity-api.ps1
# End Download Commands
```

## Components

* archiveNow.ps1: the main powershell script
* cohesity-api.ps1: the Cohesity REST API helper module [README](https://github.com/bseltz-cohesity/scripts/tree/master/powershell/cohesity-api)

Place both files in a folder together, then we can run the script like so:

```powershell
./archiveNow.ps1 -vip mycluster `
                 -username myuser `
                 -domain mydomain.net `
                 -jobNames 'NAS Backup', 'SQL Backup' `
                 -vault s3 `
                 -keepFor 180
```

```text
Connected!
NAS Backup (04/18/2020 01:20:02) --> S3 (07/17/2020 01:20:02)
SQL Backup (04/17/2020 23:00:01) --> S3 (07/16/2020 23:00:01)
```

## Running and Scheduling PowerShell Scripts

For additional help running and scheduling Cohesity PowerShell scripts, please see [Running Cohesity PowerShell Scripts](https://github.com/bseltz-cohesity/scripts/blob/master/powershell/Running%20Cohesity%20PowerShell%20Scripts.pdf)