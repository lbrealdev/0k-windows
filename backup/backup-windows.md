# Windows Backup — Personal Data

Backup user files from Windows using `robocopy` (built-in, no install needed).

## Prerequisites

- **Destination with enough space:** external HDD, USB drive, or network share
- **Check free space on destination:** right-click the drive → Properties

## Check disk usage per user

Before copying, see how much space each user profile takes so you know what fits.

### PowerShell (size per user in GB)

```powershell
Get-ChildItem C:\Users -Directory | ForEach-Object {
    $size = (Get-ChildItem $_.FullName -Recurse -File -ErrorAction SilentlyContinue | Measure-Object -Property Length -Sum -ErrorAction SilentlyContinue).Sum
    [PSCustomObject]@{User=$_.Name; SizeGB=[math]::Round($size/1GB, 2)}
} | Format-Table -AutoSize
```

### Quick check (GUI)

Right-click `C:\Users\YourUsername` → Properties. Multiply by number of users for a rough total.

## Verify robocopy works

```cmd
robocopy /?
```

Should show the help screen. If not, run `cmd` as Administrator.

## Backup a single user

```cmd
robocopy C:\Users\YOUR_USERNAME D:\backup\YOUR_USERNAME /E /COPY:DAT /R:1 /W:1
```

Replace:
- `YOUR_USERNAME` with the actual folder name under `C:\Users\`
- `D:\backup\` with your destination path

What the flags do:
- `/E` — copy subdirectories, including empty ones
- `/COPY:DAT` — preserve Data, Attributes, Timestamps (no NTFS permissions)
- `/R:1` — 1 retry on locked files
- `/W:1` — wait 1 second between retries

## Backup all users at once

```cmd
robocopy C:\Users D:\backup\Users /E /COPY:DAT /R:1 /W:1 /XD "All Users" "Default User" "Default" "Public"
```

`/XD` excludes system folders that contain no personal data.

## What gets copied

Inside each user folder:
- `Documents`, `Pictures`, `Music`, `Videos`
- `Downloads`, `Desktop`, `Favorites`
- `AppData` (program configs, local email, game saves)

## Verify the result

```cmd
dir D:\backup\YOUR_USERNAME /s | find "File(s)"
```

Compare the file count with the original under `C:\Users\YOUR_USERNAME`.

## Tips

- **Close programs** before starting — open files may be skipped
- **Temporarily disable antivirus** if the backup is very slow
- **Run as Administrator** to access all folders
- The command shows real-time progress and a summary at the end
