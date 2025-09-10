# PS12EXE

## Introduction

`ps12exe` is a PowerShell module that allows you to create an executable file from a `.ps1` script.  

[![CI](https://github.com/steve02081504/ps12exe/actions/workflows/CI.yml/badge.svg)](https://github.com/steve02081504/ps12exe/actions/workflows/CI.yml)
[![PSGallery download num](https://img.shields.io/powershellgallery/dt/ps12exe)](https://www.powershellgallery.com/packages/ps12exe)
[![GitHub issues by-label bug](https://img.shields.io/github/issues/steve02081504/ps12exe/bug?label=bugs)](https://github.com/steve02081504/ps12exe/issues?q=is%3Aissue+is%3Aopen+label%3Abug)
[![Codacy Badge](https://app.codacy.com/project/badge/Grade/ecfd57f5f2eb4ac5bbcbcd525b454f99)](https://app.codacy.com/gh/steve02081504/ps12exe/dashboard?utm_source=gh&utm_medium=referral&utm_content=&utm_campaign=Badge_grade)
[![CodeFactor](https://www.codefactor.io/repository/github/steve02081504/ps12exe/badge/master)](https://www.codefactor.io/repository/github/steve02081504/ps12exe/overview/master)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](http://makeapullrequest.com)

![preview](https://github.com/5Noxi/PS12EXE/blob/master/preview.png?raw=true)

## Installation

```powershell
Install-Module ps12exe #Install ps12exe module
Set-ps12exeContextMenu #Set right-click menu
```

(You can also clone this repository and run `./ps12exe.ps1` directly)

**Hard to upgrade from PS2EXE to ps12exe? No problem!**  
PS2EXE2ps12exe can hooks PS2EXE calls into ps12exe, all you need is just uninstall PS2EXE and install this, then use PS2EXE as normal.

```powershell
Uninstall-Module PS2EXE
Install-Module PS2EXE2ps12exe
```

## Usage

### Right-click menu

Once you have set `Set-ps12exeContextMenu`, you can quickly compile any ps1 file into an exe or open ps12exeGUI on this file by right-clicking on it.  
![contextm](https://github.com/5Noxi/PS12EXE/blob/master/contextmenu.png?raw=true)

### GUI Mode

```powershell
ps12exeGUI
```

### Console Mode

```powershell
ps12exe .\source.ps1 .\target.exe
```

Compiles `source.ps1` into the executable target.exe (if `.\target.exe` is omitted, output is written to `.\source.exe`).

```powershell
'"Hello World!"' | ps12exe
```

Compiles `"Hello World!"` into the executable `.\a.exe`.

```powershell
ps12exe https://raw.githubusercontent.com/steve02081504/ps12exe/master/src/GUI/Main.ps1
```

Compiles `Main.ps1` from the internet into the executable `.\Main.exe`.

### Self-Host WebServer

```powershell
Start-ps12exeWebServer
```

Starts a web server that can be used to compile powerShell scripts online.

## Comparative Advantages

### Quick Comparison

| Comparison Content | ps12exe | [`MScholtes/PS2EXE@678a892`](https://github.com/MScholtes/PS2EXE/tree/678a89270f4ef4b636b69db46b31e1b4e0a9e1c5) |
| --- | --- | --- |
| Pure script repository | All text files except images & dependencies | Contains exe files with open source license |
| Command to generate hello world | `'"Hello World!"' \| ps12exe` | `echo "Hello World!" *> a.ps1; PS2EXE a.ps1; rm a.ps1` |
| Size of the generated hello world executable file | `1024` bytes | `25088` bytes |
| GUI multilingual support | ✔️ | ❌ |
| Syntax check during compilation | ✔️ | ❌ |
| Preprocessing feature | ✔️ | ❌ |
| `-extract` and other special parameter parsing |  Removed | Requires source code modification |
| PR welcome level | Welcome! | 14 PRs, 13 of which were closed |

### Detailed Comparison

Compared to [`MScholtes/PS2EXE@678a892`](https://github.com/MScholtes/PS2EXE/tree/678a89270f4ef4b636b69db46b31e1b4e0a9e1c5), this project brings the following improvements:

| Improvement Content | Description |
| --- | --- |
| Syntax check during compilation | Syntax check during compilation to improve code quality |
| Powerful preprocessing feature | Preprocess the script before compilation, no need to copy and paste all content into the script |
| `-CompilerOptions` parameter | New parameter, allowing you to further customize the generated executable file |
| `-Minifyer` parameter ([GUI](https://github.com/5Noxi/PowerShell-Minifier)) | Preprocess the script before compilation to generate a smaller executable file |
| Support for compiling scripts and included files from URL | Support for downloading icons from URL |
| Optimization of `-noConsole` parameter | Optimized option handling and window title display, you can now set the title of the custom pop-up window |
| Removed exe files | Removed exe files from the code repository |
| Multilingual support, pure script GUI | Better multilingual support, pure script GUI, support for dark mode |
| Separated cs files from ps1 files | Easier to read and maintain |
| More improvements | And more... |

> [!CAUTION]
> Do not store passwords in source code ([*](https://github.com/5Noxi/ps12exe/blob/master/docs/README_EN_US.md#password-security))

More details: [localed readme](https://github.com/5Noxi/ps12exe/blob/master/docs/README_EN_US.md).
