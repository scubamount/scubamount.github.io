# SALK-Utils

*The lone and level sands stretch far away*

<p align="center">
<img src="https://user-images.githubusercontent.com/59990200/163873700-9b29e4a6-0a69-41a7-8936-9ee6ed1286eb.png" width="300">
</p>

# What Is It?

This PowerShell 7 module is a comprehensive collection of user-friendly admin utilities designed to optimize processes and enhance efficiency across core infrastructures. Written in PowerShell, each script leverages C# and .NET classes, and is packaged as a NuGet module published to a redundantly backed-up location, facilitating seamless importation as usable Cmdlets and advanced functions.

Documentation for each command can be accessed using the `get-help` function, providing details on optional parameters, purpose, documentation, or examples. Tasks that are typically performed manually can be streamlined and automated, delivering plug-and-play tools that improve productivity. The inclusion of terminal autocompletions and alias dotfile examples further enhances user experience.

Commands may prompt the user for input or utilize a Windows dialog/explorer box to facilitate object selection, such as .Exe files on the local file system or .txt or .csv lists of computers. This results in frictionless, modular, and scalable commands, reducing the time required to hardcode commands and enabling admins to focus on their core tasks.

Certain scripts possess added functionality, allowing them to function independently of the module, with redundant functions included for this purpose.

Of particular note, the `ictr` script includes a `cRED` function, which performs a check to enable execution via a NON-elevated shell. Network administrator credentials are prompted for and encrypted for use solely during execution of the command. This implementation drastically enhances system security by preventing PowerShell from exposing network administrator credentials to the network.

# How do I ensure everything works?

Please submit an Issue or contact the author if you have any questions or suggestions.

# The Module

The SALK-Utils PowerShell module comprises of a set of custom-made tools with diverse functionalities. These tools are:

* `cRED`:
  * facilitates the execution of requests for elevated network admin credentials, which are encrypted and stored until the end of the session (automatic inclusion in some scripts).
* `Find-LocalFile`:
  * allows for a multithreaded filename search on a local drive.
* `Copy-LocalToRemoteList`:
  * enables file copying from a local computer to any number of remote computers.
* `Find-FileToRemoteList`:
  * locates file path(s) on any number of remote computers.
* `Invoke-CommandToRemoteList` and `Invoke-CommandToRemote`:
  * allow running a command as the user on any number of remote computers, or a single computer.
* `Invoke-SCCMInstallToList`:
  * facilitates the forced push of SCCM updates on any number of remote computers.
* `Invoke-ProgramToRemoteList`:
  * allows running a program with optional parameters on any number of remote computers.
* `Invoke-ProgramToRemoteListPSEXEC`:
  * allows running a program with optional parameters on any number of remote computers using Microsoft Sysinternals PSEXEC.

The module also includes multiple test scripts that are not yet ready to be executed.

# Aliases

> `ictrl` = `Invoke-CommandToRemoteList`
>
> `ictr` = `Invoke-CommandToRemote`
>
> `flf` = `Find-LocalFile`
>
> `fftrl` = `Find-FileToRemoteList`
>
> `cltrl` = `Copy-LocalToRemoteList`
>
> `isitl` = `Invoke-SCCMInstallToList`
>
> `iptrl` = `Invoke-ProgramToRemoteList`
>
> `iptrlp` = `Invoke-ProgramToRemoteListPSEXEC`
>
> `salad` = `Set-AutoLogonandAD`
>
> `scap` = `Set-ChangeADPassword`
>
> `cRED` = `cRED`
>
> `aa` = `winget upgrade --all`
>
> `cutac` = `Copy-UserToAnotherComputer`

# How Do I Get It?

Either see below, or contact the author...

> There is no data included in this module that traces to any organization. This portable module can be used in any infrastructure with an Azure/Active Directory or on prem AD environment.

---

# Requirements and Dependencies

1. [PowerShell 7](https://github.com/PowerShell/PowerShell/releases/download/v7.3.0-preview.3/PowerShell-7.3.0-preview.3-win-x64.msi)
2. [PSReadLine](https://github.com/scubamount/salk--modules/tree/master/mymodules) module (optional, but will print errors if left out)
3. An Amd64 (x86) processor, running Windows 10 or above
4. RSAT
5. Microsoft SysInternals Suite  (PSTools included in pwsh7 folder) (optional, only needed for PSEXEC commands)
6. My custom profile (included in module)
7. Allowance through `Set-ExecutionPolicy`
   1. (or) My `.cfx` certificate

---

# Installation

(1)- Download [PowerShell 7](https://github.com/PowerShell/PowerShell/releases/download/v7.3.0-preview.3/PowerShell-7.3.0-preview.3-win-x64.msi) from the link here, or navigate to the Microsoft website and download the `.msi` there. Install as admin.

(2)- Run PowerShell 7 as admin to make edits to your `$profile` or any other local changes.

 If you run PowerShell 7 as your `Superuser` with network credentials, you can now invoke commands across the network.

(3)- You can add my certificate file by double clicking on it. This is located in the `\pwsh7` folder

(4)- Running PowerShell7 as Admin, change the ExecutionPolicy.

```powershell
Set-ExecutionPolicy -ExecutionPolicy AllSigned -Force -Confirm
```

(5)- Run these commands to ensure you are up to date and can install the NuGet PowerShell repository

```powershell
[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12

Set-PSRepository -Name PSGallery -InstallationPolicy Trusted

Install-PackageProvider -Name NuGet -Force

Install-Module PowerShellGet -AllowPrerelease -Repository PSGallery -Force

Install-Module PackageManagement -Force

# And finally, register the PowerShell repository as trusted so you can download and import the module
Register-PSRepository -Name ScubaMount -PublishLocation '\\network\location\to\"Modules"' -SourceLocation '\\network\location\to\"Modules"' -InstallationPolicy Trusted

Install-Module SALK-Utils

Import-Module SALK-Utils
```

(6)- Find my module package, "SALK-Utils". (Location hidden for now. Contact me for info.)

This directory will constantly be updated with new tools as well as improvements to the current tools. Please do not remove this folder.

> Note: Editing this folder will break the certificate signage I have used, and at that point any tampered files will be considered malware.

(7)- As either Admin or Superuser, Run the `Import-Module` command

This will import all of my tools.

```powershell
Install-Module SALK-Utils; Import-Module SALK-Utils
```

- You will now have all of my tools *for your current session of powershell*. If commands are listed out, then the import was successful. Errors? Scroll below...

---

# Usage

- Find the list of commands you can use.

```powershell
Get-Command -Module SALK-Utils
```

- Look at the documentation, help, and examples for a specific command.

```powershell
Get-Help -Command PutCommandNameHere -Full
```

- Run one of the commands

```powershell
Invoke-CommandToRemoteList
```

---

## You can automatically import my custom Modules as well as custom public Profile

To create a new profile, see below

```powershell
New-Item -Path $PROFILE -Type File -Force
```

#### to edit file, run

`notepad $PROFILE`

Just put in your `Import-Module SALK-Utils` command in your `$PROFILE`, and it will auto launch every time you start PowerShell7.

- to find location of file, run

```powershell
$PROFILE
```

---

## SYSINTERNALS PSTOOLS - optional

In the `pwsh7` folder, you will find a copy of the folder `PSTools` from Microsoft SysInternals. You can either copy this to your local drive, or download it from the Microsoft website.

For best results, put `PSTools` into `C:\PSTools`, and the scripts will path properly.

It is not essential that you download or utilize the PSTools, but some scripts may not work at all without them.
