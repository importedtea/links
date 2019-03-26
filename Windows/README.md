# Media Creation Tool
*Keys: Windows installation, ISO*

The Windows Media Creation Tool is used to create a bootable USB drive to install Windows 10.

You can install it [here](https://www.microsoft.com/en-us/software-download/windows10)

# Windows System Image Manager (SIM)
*Keys: Windows deployment, automate Windows ISO*

Windows System Image Manager, or WSIM/SIM, is a tool used to create an xml file that will let a user bypass the OOBE.

You can download WSIM by first downloading Windows MDT [here](https://docs.microsoft.com/en-us/sccm/mdt/)

Below you can find a few guides on setting up MDT / WSIM, as well as, creating an answer file.

https://www.windowscentral.com/how-create-unattended-media-do-automated-installation-windows-10#bios_partition_setup

https://win10.guru/windows-10-unattended-install-media-part-3-answer-file-for-oobe/

https://systemscenter.ru/waik.en/html/6be39c89-86b7-4d0d-9f04-b28e201c1999.htm

# Remoting

## PowerShell

There are a lot of different methods to remotely connect/share with a different computer than your own.

A few things to keep in mind are the following:

1. Are you on the same LAN/domain?
2. What sort of access do you have to another computer? Domain Admin?
3. Do you usually use RDP to connect to a remote device?

There are a few cmdlets that can help with remoting:

- `Invoke-Command`
- `Enter-PSSession`
- `New-PSSession`
- `Remove-PSSession`
- `Test-WSMan`

Here are some other specifics:

1. Some actions require File and Print Sharing to be enabled.
2. All actions require PSRemoting to be enabled.

Enabling PSRemoting:

```ps
# powershell
Enable-PSRemoting -Force
```

```cmd
# cmd
winrm quickconfig -quiet
```

You can apply PSRemoting by using a GPO, or a tool made my Microsoft called `PSExec` (requires FP Sharing)

If you run into an error:

1. Execute `Test-WSMan -ComputerName [hostname]` from your workstation, if you get an error it's not enabled.
2. Attempt to enter a session with that computer using `Enter-PSSession -ComputerName [hostname]`

## GUI

Launch Remote Desktop Connection from the start menu.
