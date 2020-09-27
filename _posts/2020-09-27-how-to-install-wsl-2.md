---
title: "Welcome to Jekyll!"
date: 2020-9-27 01:15:00 +0900
categories: WSL Windows
---

WSL2를 설치하는 방법에 대하여 알아보자. 

다음 링크의 "Windows Subsystem for Linux Installation Guide for Windows 10" 문서를 참조하였다.

https://docs.microsoft.com/en-us/windows/wsl/install-win10

### 1. Step 1 - 윈도우 리눅스 서브시스템 활성화

WSL은 Windows Subsystem for Linux의 약자로, 윈도우 10 안에서 리눅스 distros를 사용할 수 있게 해준다. 사용을 위해서는 기능 활성화를 해주자.

PowerShell을 관리자 권한으로 실행시키고 다음의 명령줄을 실행한다:

```PowerShell
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
```

만약 WSL 1만 설치하기를 원한다면 여기서 재부팅 후 Step 6로 가면 된다.

### 2. Step 2 - WSL2로 업데이트

WSL 2로 업데이트 하려면 윈도우 10이여야 하며, 다음과 같은 사양을 충족해야 한다.

#### Requirements

- x64 시스템: 버전 **1903** 이상 빌드 **18362** 이상.
- ARM64 시스템: 버전 **2004** 이상 빌드 **19041** 이상.
- 18362보다 낮은 빌드는 WSL 2를 지원하지 않으므로, 윈도우를 업데이트 하여야 한다.

버전을 알고 싶으면 **윈도우 + R** 키를 누르고 **winver** 을 쳐서 실행 시키면 된다.

### 3. Step 3 - 가상머신(Virtual Machine) 기능 켜기

WSL 2를 설치하기 전에, 먼저 **가상 머신 플랫폼** 기능을 활성화 하여야한다.

PowerShell을 관리자 권한으로 실행시키고 다음의 명령줄을 실행한다:

```PowerShell
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
```

컴퓨터를 **재부팅** 하여 WSL 설치와 WSL 2 업그레이드를 완료 한다.

### 4. Step 4 - 리눅스 커널 업데이트 패키지 다운 받기

1. 최신 버전의 패키지를 다운 받는다:
   * https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_x64.msi
   * 만약 ARM64 시스템이라면 위 링크가 아닌 ARM64 패키지를 따로 받아야한다.
2. 다운을 받은 후 설치해서 실행하자.

### Step 5 - WSL 2를 기본 버전으로 설정하기

```PowerShell
wsl --set-default-version 2
```

### Step 6 - Linux 배포판 설치하기

[Microsoft 스토어](https://aka.ms/wslstore) 에서 원하는 배포판을 다운 받아 설치하면 된다.