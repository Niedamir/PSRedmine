# PSRedmine

## Installation
1. Copy the entire module folder into the Modules directory
   * All users: `C:\Program Files\WindowsPowerShell\Modules\`
   * Per user: `$HOME\Documents\WindowsPowerShell\Modules\`
2. You can just restart your PowerShell session or manually import the module
    ```PowerShell
    Import-Module PSRedmine
    ```

## Basic Usage
Connect, CRUD, Disconnect
```PowerShell
Connect-Redmine demo.redmine.org

New-RedmineResource project -identifier test99 -name testproject
New-RedmineResource version -project_id 475 -name testversion
New-RedmineResource issue -project_id test99 -subject testissue

Search-RedmineResource project -keyword testproject
Search-RedmineResource membership -project_id test99
Search-RedmineResource version -project_id test99 -keyword testversion 
Search-RedmineResource issue -keyword testissue
Search-RedmineResource user -keyword testuser # Administrator only

Get-RedmineResource project test99
Get-RedmineResource project 475
Get-RedmineResource membership 74
Get-RedmineResource version 408
Get-RedmineResource issue 29552
Get-RedmineResource user 20 # Administrator only

Edit-RedmineResource project -id test99 -description 'change description'
Edit-RedmineResource version -id 408 -description 'add desc' -due_date 2018-09-29
Edit-RedmineResource issue -id 29552 -version_id 406

Remove-RedmineResource issue 29552
Remove-RedmineResource version 408
Remove-RedmineResource project test99 # Administrator only
Remove-RedmineResource user 20 # Administrator only

Disconnect-Redmine
```

## Reference
* [Redmine API](http://www.redmine.org/projects/redmine/wiki/Rest_api) wiki page
