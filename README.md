# SALK-Utils

*The lone and level sands stretch far away*

<p align="center">
<img src="https://user-images.githubusercontent.com/59990200/163192337-3a61bd0e-1050-48d7-9cd2-c448cc6f6ce9.JPG" width="300">
</p>

# What Is It?

A PowerShell 7 (only) module for Windows 10 and above. Compiled and written by hand, each script is written with PowerShell and C# and added to a central, portable location to be exported as usable Cmdlets. Just type in a command and run.

You can use get-help for a command you don't understand or to learn about the optional parameters, purpose, or examples. Tasks that may normally be done by hand can be automated or simplified, and terminal autocompletions have been added for improved productivity.

Some of the scripts will be self explanatory and tell you what you need to input in order to get your achieved result. Some will open a windows explorer box to allow you to select an object such as an .Exe on your local file system, or a .txt list of computers on your local file system. This makes each of the commands modular and scalable, and decreases the time spent by the admin trying to hardcode the commands they want.

# How do I ensure everything works?

Read this whole page.

If you are still having issues, please submit an Issue or contact the author.

# The Module

The SALK-Utils PowerShell module has many handmade tools that fill multiple purposes.

- Multithreaded filename search on your local drive
  - `Find-LocalFile`
- Copy a file from your computer to any number of remote computers
  - `Copy-LocalToRemoteList`
- Find a file path(s) on any number of remote computers
  - `Find-FileOnRemoteList`
- Run a command as your user on any number of remote computers
  - `Invoke-CommandToRemoteList`
- Force push SCCM updates on any number of remote computers
  - `Invoke-SCCMInstallToList`
- Run a program with optional parameters on any number of remote computers
  - `Invoke-ProgramOnRemoteList`
- Run a program with optional parameters on any number of remote computers using PSEXEC
  - `Invoke-ProgramOnRemoteListPSEXEC`

- **and more...**

# Aliases

> `tnc` = `Test-NetConnection`

> `ictrl` = `Invoke-CommandToRemoteList`

> `flf` = `Find-LocalFile`

> `fforl` = `Find-FileOnRemoteList`

> `cltrl` = `Copy-LocalToRemoteList`

> `isitl` = `Invoke-SCCMInstallToList`

> `iporl` = `Invoke-ProgramOnRemoteList`

> `iporlp` = `Invoke-ProgramOnRemoteListPSEXEC`

> `np` = `notepad $profile.AllUsersAllHosts`

# How Do I Get It?

Either see below, or contact the author...

> There is no data included in this module that traces to any organization. This portable module can be used in any infrastructure with an Active Directory environment.

***

# Requirements and Dependencies

1. [PowerShell 7](<https://github.com/PowerShell/PowerShell/releases/download/v7.3.0-preview.3/PowerShell-7.3.0-preview.3-win-x64.msi>)
2. [PSReadLine](https://github.com/scubamount/salk--modules/tree/master/mymodules) (optional, but will print errors if left out)
3. An Amd64 processor, running Windows 10 or above
4. RSAT
5. Microsoft SysInternals Suite  (PSTools included in pwsh7 folder)
6. My custom profile (included in module)
7. `Set-ExecutionPolicy -ExecutionPolicy AllSigned -Force -Confirm`
8. My `.cfx` certificate (located in the `pwsh7` folder)

***

# Installation

(1)- Download [PowerShell 7](<https://github.com/PowerShell/PowerShell/releases/download/v7.3.0-preview.3/PowerShell-7.3.0-preview.3-win-x64.msi>) from the link here, or navigate to the Microsoft website and download the `.msi` there. Install as admin.

(2)- Run PowerShell 7 as admin to make edits to your `$profile` or any other local changes.

 If you run PowerShell 7 as your `Superuser` with network credentials, you can now invoke commands across the domain.

(3)- You can add my certificate file by double clicking on it. This is located in the `\pwsh7` folder

(4)- Running PowerShell7 as Admin, change the ExecutionPolicy.

```powershell
Set-ExecutionPolicy -ExecutionPolicy AllSigned -Force -Confirm
```

(5)- Find my module "SALK-Utils". Navigate to the `\\IT\Public\Techs\` drive. Find my name, and then go into the `pwsh7\Modules\` directory. Here you will find `SALK-Utils`.

This directory will constantly be updated with new tools as well as improvements to the current tools. Please do not remove this folder.

> Note: Editing this folder will break the certificate signage I have used, and at that point any tampered files will be considered malware.

(6)- As either Admin or Superuser, Run the `Import-Module` command directing to the `~\\Salk-Utils` folder (full file path)

This will import all of my tools.

```powershell
Import-Module \\full\location\to\folder\SALK-Utils
```

- You will now have all of my tools. If commands are listed out, then the import was successful. Errors? Scroll below...

***

# Usage


- Find the list of commands you can use.

```powershell
Get-Command -Module SALK-Utils
```

- Look at the documentation, help, and examples for a specific command.

```powershell
Get-Help -Command TypeTheCommandHere -Full
```

- Run a command

```powershell
Invoke-CommandToRemoteList
```

***

## You can automatically import my custom Modules as well as custom public Profile

To create a new profile, see below

```powershell
New-Item -Path $PROFILE.AllUsersAllHosts -Type File -Force
```

#### to edit file, run

```powershell
notepad $PROFILE.AllUsersAllHosts
```

Just put in your `Import-Module \\module\here` command  in your `$Profile`, and it will auto launch every time you start PowerShell7.

- to find location of file, run

```powershell
$PROFILE.AllusersAllHosts
```

***

## SYSINTERNALS PSTOOLS

In the `pwsh7` folder, you will find a copy of the folder `PSTools` from Microsoft SysInternals. You can either copy this to your local drive, or download it from the Microsoft website.

For best results, put `PSTools` into `C:\PSTools`, and the scripts will path properly.

It is not essential that you download or utilize the PSTools, but some scripts may not work at all without them.
