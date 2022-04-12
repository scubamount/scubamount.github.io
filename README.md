# SALK-Utils

*The lone and level sands stretch far away* 


# The module

The SALK-Util suite has many handmade tools. 

- Copy a file from your computer to any number of remote computers `Copy-LocalToRemoteList`
- Find a file path(s) on any number of remote computers `Find-FileOnRemoteList`
- Run a command as your user on any number of remote computers `Invoke-CommandToRemoteList`
- Force push SCCM updates on any number of remote computers `Invoke-SCCMInstallToList`
- Run a program with optional parameters on any number of remote computers `Start-ProgramOnRemoteList`
- and more...

> Use `Get-Command -Module SALK-Utils` for a list of commands
> 
> Use `Get-Help -Command <insert module command here> -Full` for my handwritten documentation

## Requirements (instructions below)
1. [PowerShell 7](<https://github.com/PowerShell/PowerShell/releases/download/v7.3.0-preview.3/PowerShell-7.3.0-preview.3-win-x64.msi>)
2. [PSReadLine](https://github.com/scubamount/salk--modules/tree/master/mymodules)
3. RSAT
4. Access to the vpn
5. SysInternals PSTools
6. My custom profile (included in module)
7. `Enable-PSRemoting -Force -SkipNetworkProfileCheck -Confirm`
8. `Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Force -Confirm`
9. My `.cert` (located in the `pwsh7` folder)


## MODULE SETUP
### Navigate to the `IT\Public\Techs` drive
Inside, find my `pwsh7\Modules` directory

There will be a folder named `SALK-Utils`


After locating the SALK-Utils folder, You will need to run this command to import it.

```powershell
Import-Module \\full\location\to\folder\SALK-Utils
```

- You will now have all of my tools. If commands are listed out, then the import was successful. Errors? Scroll below...

It will run a check to see if you are 
1. on Windows
2. Using PowerShell 7 or above

***

### IMPORT CUSTOM PROFILE

__After__ importing the module, you can import the custom SALK powershell profile by entering the code 
```powershell
a
```

That's it. You're all ready to use SALK-Utils.

If you so desire, you can automatically import my custom Modules as well as custom public Profile


***


To create a new profile, see below

```powershell
New-Item -Path $PROFILE.AllUsersAllHosts -Type File -Force
```
### to edit file, run

```powershell
notepad $PROFILE.AllUsersAllHosts
```
### to find location of file, run

```powershell
$PROFILE.AllusersAllHosts
```


***

# SYSINTERNALS PSTOOLS

In the `pwsh7` folder, you will find a copy of the folder `PSTools` from Microsoft SysInternals. You can either copy this to your local drive, or download it from the Microsoft website.

For best results, put `PSTools` into `C:\PSTools`, and the scripts will path properly.



