Script: 
# Defineerime tulemusefaili asukoha
$outputFile = "$env:USERPROFILE\Desktop\testarvuti_info.txt"

# Funktsioon, mis lisab infot faili
function Write-Info {
    param ([string]$info)
    Add-Content -Path $outputFile -Value $info
}

# Puhastame varasema faili, kui see eksisteerib
if (Test-Path $outputFile) {
    Remove-Item $outputFile
}

# 1. Masina nimi, PowerShelli versioon ja Windowsi versioon
Write-Info "=== Süsteemi Info ==="
Write-Info "Masina nimi: $(hostname)"
Write-Info "PowerShelli versioon: $($PSVersionTable.PSVersion)"
Write-Info "Windowsi versioon: $(Get-ComputerInfo -Property CsName, WindowsVersion | Format-Table -AutoSize | Out-String)"

# 2. Võrgu konfiguratsioon
Write-Info "`n=== Võrgu Konfiguratsioon ==="
$networkAdapters = Get-NetAdapter | Where-Object {$_.Status -eq "Up"}
foreach ($adapter in $networkAdapters) {
    $adapterInfo = Get-NetIPConfiguration -InterfaceAlias $adapter.Name
    Write-Info "Adapter: $($adapter.Name)"
    Write-Info "IP-aadress: $($adapterInfo.IPv4Address.IPAddress)"
    Write-Info "Võrgumask: $($adapterInfo.IPv4Address.PrefixLength)"
    Write-Info "Gateway: $($adapterInfo.IPv4DefaultGateway.NextHop)"
    Write-Info "DHCP lubatud: $($adapter.DhcpEnabled)"
    Write-Info "MAC-aadress: $($adapter.MacAddress)"
}

# 3. Protsessori kirjeldus ja RAM
Write-Info "`n=== Protsessori ja RAM-i Info ==="
$systemInfo = Get-WmiObject -Class Win32_ComputerSystem
Write-Info "Protsessor: $($systemInfo.Manufacturer) $($systemInfo.Model)"
Write-Info "RAM kogus: $([math]::Round($systemInfo.TotalPhysicalMemory / 1GB, 2)) GB"

# 4. Graafikakaardi nimi, draiveri versioon, kuupäev ja lahutus
Write-Info "`n=== Graafikakaardi Info ==="
$videoControllers = Get-CimInstance -ClassName Win32_VideoController
foreach ($vc in $videoControllers) {
    Write-Info "Graafikakaart: $($vc.Name)"
    Write-Info "Draiveri versioon: $($vc.DriverVersion)"
    Write-Info "Draiveri kuupäev: $($vc.DriverDate)"
    Write-Info "Resolutsioon: $($vc.CurrentHorizontalResolution)x$($vc.CurrentVerticalResolution)"
}

# 5. Kõvaketaste info
Write-Info "`n=== Kõvaketaste Info ==="
$drives = Get-CimInstance -ClassName Win32_LogicalDisk | Where-Object {$_.DriveType -eq 3}
foreach ($drive in $drives) {
    Write-Info "Ketas: $($drive.DeviceID)"
    Write-Info "Kogumaht: $([math]::Round($drive.Size / 1GB, 2)) GB"
    Write-Info "Vaba ruum kettal C:: $([math]::Round((Get-CimInstance -ClassName Win32_LogicalDisk -Filter 'DeviceID="C:"').FreeSpace / 1GB, 2)) GB"
}

# 6. PCI-siinil olevate seadmete draiverite info
Write-Info "`n=== PCI Seadmed ==="
$pciDevices = Get-CimInstance -ClassName Win32_PnPEntity | Where-Object {$_.PNPDeviceID -like "PCI*"}
foreach ($device in $pciDevices) {
    Write-Info "Seade: $($device.Name)"
    Write-Info "Tootja: $($device.Manufacturer)"
    Write-Info "Draiveri versioon: $($device.DriverVersion)"
}

# 7. Kasutajate info
Write-Info "`n=== Kasutajate Info ==="
$users = Get-CimInstance -ClassName Win32_UserAccount | Where-Object {$_.LocalAccount -eq $true}
foreach ($user in $users) {
    Write-Info "Kasutaja: $($user.Name)"
    Write-Info "Kirjeldus: $($user.Description)"
    Write-Info "Keelatud: $($user.Disabled)"
}

# 8. Käimasolevate protsesside arv
Write-Info "`n=== Protsesside Info ==="
$processes = Get-Process
Write-Info "Käimasolevate protsesside arv: $($processes.Count)"

# 9. 10 viimati käivitatud protsessi
Write-Info "`n10 viimati käivitatud protsessi:"
$recentProcesses = $processes | Where-Object {$_.StartTime -ne $null} | Sort-Object StartTime -Descending | Select-Object -First 10
foreach ($process in $recentProcesses) {
    Write-Info "Protsess: $($process.Name), PID: $($process.Id), Start Time: $($process.StartTime)"
}

# 10. Kuupäev ja kellaaeg
Write-Info "`n=== Kuupäev ja Kellaaeg ==="
Write-Info "Kuupäev ja kellaaeg: $(Get-Date -Format 'yyyy-MM-dd HH:mm:ss')"

Olulisemad käsud:
Write-Info - see funktsioon lisab saadud andmed faili.
Get-ComputerInfo - kogub infot masina nime, PowerShelli ja Windowsi versiooni kohta.
Get-NetAdapter - kuvab võrguadapterite nimekirja ja nende oleku.
Get-NetIPConfiguration - kogub võrguadapteri IP-aadressi, võrgumaski, gateway, DHCP ja MAC-aadressi.
Get-WmiObject -Class Win32_ComputerSystem - Kogub infot protsessori ja RAM-i kohta.
Get-CimInstance -ClassName Win32_VideoController - kogub infot graafikakaardi nime, draiveri versiooni, kuupäeva ja lahutuse kohta.
Get-CimInstance -ClassName Win32_LogicalDisk - Kogub infot kõvaketaste kogumahu ja vaba ruumi kohta
Get-CimInstance -ClassName Win32_PnPEntity - kuvab PCI-siinil olevate seadmete draivrite infot (seadme nimi, tootja ja draiveri versioon).
Get-CimInstance -ClassName Win32_Useraccount - Kogub infot arvutis olevate kasutajate kohta (nimi, kirjeldus, kas lokaalne ja kas keelatud).
Get-Process - Kuvab arvutis käimasolevate protsesside nimekirja ja arvu.
Get-Date - Kuvab arvuti praeguse kuupäeva ja kellaaja.


<img width="955" alt="Praktikum13 1" src="https://github.com/user-attachments/assets/c5899de3-b95a-4738-992b-d4f5b5fec0eb" />
<img width="811" alt="Praktikum13 2" src="https://github.com/user-attachments/assets/2bf25f22-e57c-442b-ad98-2dd698f4fd5b" />
<img width="515" alt="Praktikum13 3" src="https://github.com/user-attachments/assets/03ac7658-4693-4ae9-9999-a6f12fb40440" />

