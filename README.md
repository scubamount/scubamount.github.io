# SALK-Utils

*The lone and level sands stretch far away* 


<p align="center">
<img src="https://user-images.githubusercontent.com/59990200/163192337-3a61bd0e-1050-48d7-9cd2-c448cc6f6ce9.JPG" width="300">
</p>

# What is it?

A PowerShell 7 (only) module for Windows 10 and above. Compiled and written by hand, each script is written with PowerShell and C# and added to a central, portable location to be exported as usable Cmdlets. Just type in a command and run. 

You can use get-help for a command you don't understand or to learn about the optional parameters, purpose, or examples. Tasks that may normally be done by hand can be automated or simplified, and terminal autocompletions have been added for improved productivity.

# How do I ensure everything works?

Read this whole page.

If you are still having issues, please submit an Issue or contact the author.



# The Module

The SALK-Utils suite has many handmade tools. 

- Copy a file from your computer to any number of remote computers 
  - `Copy-LocalToRemoteList`
- Find a file path(s) on any number of remote computers 
  - `Find-FileOnRemoteList`
- Run a command as your user on any number of remote computers 
  - `Invoke-CommandToRemoteList`
- Force push SCCM updates on any number of remote computers 
  - `Invoke-SCCMInstallToList`
- Run a program with optional parameters on any number of remote computers 
  - `Start-ProgramOnRemoteList`
- **and more...**

> Use `Get-Command -Module SALK-Utils` for a list of commands
> 
> Use `Get-Help -Command <insert module command here> -Full` for my handwritten documentation

# Requirements and Dependencies
1. [PowerShell 7](<https://github.com/PowerShell/PowerShell/releases/download/v7.3.0-preview.3/PowerShell-7.3.0-preview.3-win-x64.msi>)
2. [PSReadLine](https://github.com/scubamount/salk--modules/tree/master/mymodules)
3. An Amd64 processor, running Windows 10 or above
4. RSAT
5. Access to the vpn
6. SysInternals PSTools
7. My custom profile (included in module)
8. `Enable-PSRemoting -Force -SkipNetworkProfileCheck -Confirm`
9. `Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Force -Confirm`
10. My `.cert` (located in the `pwsh7` folder)


# Installation
### Navigate to the `IT\Public\Techs` drive
Inside, find my `pwsh7\Modules` directory

There will be a folder named `SALK-Utils`


After locating the SALK-Utils folder, You will need to run this command to import it.

```powershell
Import-Module \\full\location\to\folder\SALK-Utils
```

- You will now have all of my tools. If commands are listed out, then the import was successful. Errors? Scroll below...

It will run a check to see if you are 
1. on Windows with an Amd64 processor
2. Using PowerShell 7 or above

***

# Installation continued...

__After__ importing the module, you can import the custom SALK powershell profile by entering the code 
```powershell
Import-SALKProfiles
```

***


# That's it. You're all ready to use SALK-Utils.


***

### If you so desire, you can automatically import my custom Modules as well as custom public Profile


To create a new profile, see below

```powershell
New-Item -Path $PROFILE.AllUsersAllHosts -Type File -Force
```
#### to edit file, run

```powershell
notepad $PROFILE.AllUsersAllHosts
```

Just put in your `Import-Module \\module\here` and `Import-SALKProfiles` commands on separate lines in your 'Profile', and it will auto launch every time you start PowerShell.

#### to find location of file, run

```powershell
$PROFILE.AllusersAllHosts
```


***

## SYSINTERNALS PSTOOLS

In the `pwsh7` folder, you will find a copy of the folder `PSTools` from Microsoft SysInternals. You can either copy this to your local drive, or download it from the Microsoft website.

For best results, put `PSTools` into `C:\PSTools`, and the scripts will path properly.



