# PS

```powershell
Get-ChildItem C:\Users -Directory | ForEach-Object {
    $size = (Get-ChildItem $_.FullName -Recurse -File -Force -ErrorAction Stop | Measure-Object -Property Length -Sum).Sum
    [PSCustomObject]@{User=$_.Name; SizeGB=[math]::Round($size/1GB, 2)}
} | Format-Table -AutoSize
```
