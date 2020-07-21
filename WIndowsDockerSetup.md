Docker 설치가이드
================

필수사항 : Windows 10 버전 2004(OS 빌드 19041 이상)
winver.exe로 확인

``` powershell
# 관리자 쉘([윈도우키]–[X키] > [A키]) 실행
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
Invoke-WebRequest https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_x64.msi -o $env:USERPROFILE\Downloads\wsl_update_x64.msi
msiexec.exe /i $env:USERPROFILE\Downloads\wsl_update_x64.msi /qn /norestart
Restart-Computer -Force

# 관리자 쉘([윈도우키]–[X키] > [A키]) 실행
https://www.microsoft.com/store/productId/9NBLGGH4MSV6
wsl --set-default-version 2
wsl -l --all
wsl sudo apt update
wsl sudo apt upgrade
Invoke-WebRequest https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_x64.msi -o $env:USERPROFILE\Downloads\wsl_update_x64.msi
msiexec.exe /i $env:USERPROFILE\Downloads\wsl_update_x64.msi /qn /norestart
Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))
choco install docker-desktop
Restart-Computer -Force
```

참고자료
* https://docs.microsoft.com/en-us/windows/wsl/install-win10
* https://docs.docker.com/docker-for-windows/wsl
