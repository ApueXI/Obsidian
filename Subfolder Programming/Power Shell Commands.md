## 🗂 File and Directory Management

|Purpose|Command (short)|Full Cmdlet|
|---|---|---|
|List directory|`ls`|`Get-ChildItem`|
|List hidden files|`ls -Force`|`Get-ChildItem -Force`|
|Change directory|`cd path`|`Set-Location path`|
|Print current directory|`pwd`|`Get-Location`|
|Make new directory|`mkdir name`|`New-Item -ItemType Directory`|
|Copy file/folder|`cp src dest`|`Copy-Item src dest`|
|Move/rename file/folder|`mv src dest`|`Move-Item src dest`|
|Delete file/folder|`rm path`|`Remove-Item path`|

---

## 📄 File Contents and Text

|Purpose|Command (short)|Full Cmdlet|
|---|---|---|
|View file contents|`cat file`|`Get-Content file`|
|Write to a file|`echo text > file`|`Set-Content file text`|
|Append to a file|`echo text >> file`|`Add-Content file text`|
|Search text in files|`Select-String pattern file`|–|

---

## 🔎 System Information

|Purpose|Command|
|---|---|
|List processes|`Get-Process`|
|Stop a process|`Stop-Process -Id PID`|
|System info|`Get-ComputerInfo`|
|Environment variables|`Get-ChildItem Env:`|

---

## 🖥 Network Utilities

|Purpose|Command|
|---|---|
|Test connectivity|`Test-Connection hostname`|
|DNS lookup|`Resolve-DnsName domain`|
|View IP config|`Get-NetIPAddress`|

---

|Alias|Cmdlet|
|---|---|
|`ls`|`Get-ChildItem`|
|`cat`|`Get-Content`|
|`mv`|`Move-Item`|
|`cp`|`Copy-Item`|
|`rm`|`Remove-Item`|
|`pwd`|`Get-Location`|
|`cd`|`Set-Location`|
|`echo`|`Write-Output`|

## 🔧 Package Management (PowerShell 5+)

|Purpose|Command|
|---|---|
|Install a module|`Install-Module name`|
|List installed modules|`Get-InstalledModule`|
|Update a module|`Update-Module name`|

---

## 🛠 General Utilities

|Purpose|Command|
|---|---|
|Clear terminal|`Clear-Host` (or `cls`)|
|View command history|`Get-History`|
|Repeat last command|`Invoke-History`|
|Aliases for commands|`Get-Alias`|

---

## 🔁 Loops and Conditionals

- **If statement:**
    
    ```PowerShell
    if ($var -eq 10) { Write-Output "Ten!" }
    ```
    
- **For loop:**
    
    ```PowerShell
    for ($i=0; $i -lt 5; $i++) { Write-Output $i }
    ```
    
- **Foreach loop:**
    
    ```PowerShell
    foreach ($item in $array) { Write-Output $item }
    ```
    

---

## 📚 Help System

|Purpose|Command|
|---|---|
|Get help on a command|`Get-Help CommandName`|
|Update help files|`Update-Help`|

---

## 🔎 Common Aliases

---

### ✅ Pro Tip

Use `Get-Command` to find all available commands or search by keyword:

```PowerShell
Get-Command *network*
```

  