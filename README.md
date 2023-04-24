# SALK-Utils

*The lone and level sands stretch far away*

<p align="center">
<img src="https://user-images.githubusercontent.com/59990200/163873700-9b29e4a6-0a69-41a7-8936-9ee6ed1286eb.png" width="300">
</p>

# What Is It?

This PowerShell 7 module is a comprehensive collection of user-friendly admin utilities designed to optimize processes and enhance efficiency across core infrastructures. Each script can leverage C# and .NET classes, and is packaged as a NuGet module published to a redundantly backed-up location, facilitating seamless importation as usable Cmdlets and advanced functions.

Documentation for each command can be accessed using the `get-help` function, providing details on optional parameters, purpose, or examples. Tasks that are typically performed manually can be streamlined and automated, delivering plug-and-play tools that improve productivity. The inclusion of terminal autocompletions and alias dotfile examples further enhances user experience.

Commands may prompt the user for input or utilize a Windows dialog/explorer box to facilitate object selection, such as .Exe files on the local file system or .txt or .csv lists of computers. This results in frictionless, modular, and scalable commands, reducing the time required to hardcode commands and enabling admins to focus on their core tasks.

Certain scripts possess added functionality, allowing them to function independently of the module, with redundant functions included for this purpose.

Of particular note, the `ictr` script includes a `cRED` function, which performs a check to enable execution via a NON-elevated shell. Network administrator credentials are prompted for and encrypted for use solely during execution of the command. This implementation drastically enhances system security by preventing PowerShell from exposing network administrator credentials to the network.

# The Module

The SALK-Utils PowerShell module comprises of a set of custom-made tools with diverse functionalities. These tools are:

* `cRED`:
  * Facilitates the execution of requests for elevated network admin credentials, which are encrypted and stored until the end of the session (automatic inclusion in some scripts).
* `Find-LocalFile`:
  * Proof of concept, allows for a multithreaded filename search on a local drive.
* `Copy-LocalToRemoteList`:
  * Enables verbose file copying/overwrite from a local computer to any scalable number of remote computers.
* `Find-FileToRemoteList`:
  * Locates file path(s) based on named parameters on any scalable number of remote computers.
* `Invoke-CommandToRemoteList` and `Invoke-CommandToRemote`:
  * Allow running a command as the user on any scalable number of remote computers, or a single computer utilizing a custom integrated fast ping and credentials check.
* `Invoke-SCCMInstallToList`:
  * Facilitates the forced push of SCCM installation on any scalable number of remote computers.
* `Invoke-ProgramToRemoteList`:
  * Allows running a program from the local machine with optional parameters to be executed on any scalable number of remote computers.
* `Invoke-ProgramToRemoteListPSEXEC`:
  * Allows running a program from the local machine with optional parameters on any scalable number of remote computers using Microsoft Sysinternals PSEXEC.
* `Set-AutoLogonAndAD`
  * Invokes a command to any scalable list of remote machines that copies an encryption executable and uses regex syntax to change the password based on dynamic hostname, changes the password in Active Directory, deletes and adds fresh registry files, and then executes the encryption process on the auto logon machine. It records each action to a local log.
* `Copy-UserToAnotherComputer`
  * Invokes a command to a remote secondary machine which copies the user folder over from a remote primary machine and overwrites the user folder
* `Set-ChangeADPassword`
  * Quickly change the password of a user

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

> There is no data included in this module that traces to any organization. This portable module can be used in any infrastructure with an Azure/Active Directory or on premises Active Directory environment.

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

1. Download [PowerShell 7](https://github.com/PowerShell/PowerShell/releases/download/v7.3.0-preview.3/PowerShell-7.3.0-preview.3-win-x64.msi) or obtain the `.msi` from the Microsoft website, and install it as an administrator.
2. Launch PowerShell 7 with administrative privileges to modify your `$profile` or perform other local changes. Running PowerShell 7 with your network credentials as the `Superuser` allows you to invoke commands across the network.
3. Double-click on the certificate file located in the `\pwsh7` folder to add it to your system.
4. Change the ExecutionPolicy while running PowerShell 7 as an administrator to run the scripts in this repository.

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

This directory is frequently updated with additional tools and enhanced versions of existing tools. Please refrain from deleting this directory.

It is important to note that any modifications to this directory will compromise the certificate signature, and any tampered files will be deemed malicious.

To import all the available tools, execute the `Import-Module` command as either an Admin or Superuser.

```powershell
Install-Module SALK-Utils; Import-Module SALK-Utils
```

- You will now have all of my tools *for your current session of powershell*. If commands are listed out, then the import was successful. Errors? Scroll below...

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

## SYSINTERNALS PSTOOLS - optional

The `pwsh7` folder contains a replica of Microsoft SysInternals' `PSTools` folder, which you can either download from Microsoft's website or copy to your local drive.

To ensure optimal performance, it is recommended to place `PSTools` in `C:\PSTools` to facilitate proper pathing of the scripts.

Although not mandatory, failure to use the `PSTools` may cause certain scripts to malfunction.
