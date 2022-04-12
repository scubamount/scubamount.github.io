## Scuba Mount

You can use the [editor on GitHub](https://github.com/scubamount/scubamount.github.io/edit/origin/README.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

Formatted with Markdown (.md) syntax highlighting.
=


## install Visual Studio Code from official Microsoft source

<https://code.visualstudio.com/download>


## fonts:

<https://github.com/tonsky/FiraCode>


## extensions: (run in windows terminal/pwsh)

> `code --list-extensions`

aaron-bond.better-comments

arcticicestudio.nord-visual-studio-code

bmalehorn.vscode-fish

christian-kohler.path-intellisense

DavidAnson.vscode-markdownlint

donjayamanne.githistory

DotJoshJohnson.xml

eamodio.gitlens

esbenp.prettier-vscode

GitHub.copilot

GitHub.vscode-pull-request-github

gitkraken.gitkraken-authentication

ionutvmi.path-autocomplete

ironmansoftware.powershellprotools

JonathanHarty.gruvbox-material-icon-theme

lehni.vscode-fix-checksums

mechatroner.rainbow-csv

ms-vscode.powershell-preview

oderwat.indent-rainbow

PKief.material-icon-theme

PKief.material-product-icons

redhat.vscode-yaml

sainnhe.gruvbox-material

streetsidesoftware.code-spell-checker

VisualStudioExptTeam.vscodeintellicode

vsls-contrib.gistfs

yzhang.markdown-all-in-one

## installation_essentials\custom_vscode_settings.json
copy paste into personal settings.json
## powershell (pwsh) 7+

<https://github.com/PowerShell/PowerShell/releases/tag/v7.3.0-preview.2>

> `New-Item -Path $PROFILE.AllUsersAllHosts -Type File -Force`

### to edit file, run

> `notepad $PROFILE.AllUsersAllHosts`

### to find location of file run

> `$PROFILE.AllusersAllHosts`


## pwsh_modules

> `Set-PSRepository -InstallationPolicy Trusted PSGallery`

> - `Import-Module PowerShellProTools`
> - `Import-Module CimCmdlets`
> - `Import-Module Microsoft.PowerShell.Management`
> - `Import-Module Microsoft.powerShell.Utility`
> - `Import-Module Microsoft.PowerShell.Security`
> - `Import-Module Microsoft.WSMan.Management`
> - `Import-Module ActiveDirectory`
> - `Import-Module PSReadLine`

(if not found then...) #ensure run as admin
#$
> - `Install-Module PowerShellProTools`
> - `Install-Module CimCmdlets`
> - `Install-Module Microsoft.PowerShell.Management`
> - `Install-Module Microsoft.powerShell.Utility`
> - `Install-Module Microsoft.PowerShell.Security`
> - `Install-Module Microsoft.WSMan.Management`
> - `Install-Module ActiveDirectory`
> - `Install-Module PSReadLine`

(if not able to install, then install Visual Studio (not Visual Studio Code), run as Admin, and use the 'Package manager Console')

***

Important note,

 - You can install pwsh modules and WindowsPowershell modules utilizing Visual Studio Package manager Console run as Admin.
 - This allow you to bypass the failed installations while running from other sources
 - VS uses nuget
