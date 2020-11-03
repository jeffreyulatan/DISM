# Windows DISM Quick Reference Guide (Deployment Image Servicing and Management)

## Introduction
This is a quick reference guide for common DISM commands specifically for Windows 10, and Windows Server 2019. I made this guide to make it simple for end-users to copy and paste commands to troubleshoot, repair, and manage their systems.

Deployment Image Servicing and Management (DISM.exe) is a command-line tool that can be used to service and prepare Windows images, including those used for [Windows PE](https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/winpe-intro), [Windows Recovery Environment (Windows RE)](https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/windows-recovery-environment--windows-re--technical-reference) and [Windows Setup](https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/windows-setup-technical-reference). DISM can be used to service a Windows image (.wim) or a virtual hard disk (.vhd or .vhdx).

DISM comes built into Windows and is available through the command line or from Windows PowerShell. To learn more about using DISM with PowerShell, see [Deployment Imaging Servicing Management (DISM) Cmdlets in Windows PowerShell](https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/use-dism-in-windows-powershell-s14).

## DISM Image Repair Options

### Cleanup-Image & SFC 
The most commonly run command to repair the common system image. 

    DISM /Online /Cleanup-Image /RestoreHealth

*When you run this command, DISM uses Windows Update to provide the files that are required to fix corruptions. However, if your Windows Update client is already broken, use a running Windows installation as the repair source, or use a Windows side-by-side folder from a network share or from a removable media, such as the Windows DVD, as the source of the files. To do this, run the following command instead:*
```
DISM.exe /Online /Cleanup-Image /RestoreHealth /Source:C:\RepairSource\Windows /LimitAccess
```
After successfully running the DISM command you may now run the System File Checker command *sfc /scannow* to scan Windows for Corruption, and attempt automatic repair. 

    sfc /scannow


> Written with [StackEdit](https://stackedit.io/).

