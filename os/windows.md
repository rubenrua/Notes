WINDOWS
=======



* List HW:

```
c:\> systeminfo
c:\> powershell Get-WmiObject win32_VideoController | Format-List Name
c:\> dxdiag /x <output file>
```

* Deps

* `dumpbin /dependents`
* https://github.com/lucasg/Dependencies
* https://www.dependencywalker.com/

* Install:

  * [winget](https://github.com/microsoft/winget-cli/releases)
  * [Chocolatey](https://chocolatey.org/)
  * [Scoop](https://scoop.sh/)
