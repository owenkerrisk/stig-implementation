# stig-implementation

.USAGE Put any usage instructions here. Example syntax: PS C:> .\STIG-ID-WN10-AU-000500.ps1 #>

Define the registry path and value
$registryPath = "HKLM:\SOFTWARE\Policies\Microsoft\Windows\EventLog\Application" $valueName = "MaxSize" $valueData = 32768 # 0x00008000 in hexadecimal

Check if the registry path exists, if not create it
if (-not (Test-Path $registryPath)) { New-Item -Path $registryPath -Force }

Set the MaxSize value
Set-ItemProperty -Path $registryPath -Name $valueName -Value $valueData -Type DWord

Output success message
Write-Host "Registry value '$valueName' set to '$valueData' at '$registryPath'."
