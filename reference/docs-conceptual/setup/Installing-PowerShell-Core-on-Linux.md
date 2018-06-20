# <a name="installing-powershell-core-on-linux"></a>Linux에서 PowerShell Core 설치

[Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 17.04][u17], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.2][opensuse], [Fedora 27][fedora], [Fedora 28][fedora] 및 [Arch Linux][arch]를 지원합니다.

공식적으로 지원되지 않는 Linux 배포의 경우 [PowerShell AppImage][lai]를 사용해 보세요.
또한 Linux [`tar.gz` 보관][tar]을 사용하여 PowerShell 이진 파일을 직접 배포해 볼 수도 있지만 OS에 따라 별도의 단계로 필요한 종속성을 설정해야 합니다.

모든 패키지는 GitHub [릴리스][] 페이지에 제공됩니다.
패키지가 설치되면 터미널에서 `pwsh`를 실행합니다.

[u14]: #ubuntu-1404
[u16]: #ubuntu-1604
[u17]: #ubuntu-1704
[deb8]: #debian-8
[deb9]: #debian-9
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse-422
[fedora]: #fedora
[arch]: #arch-linux
[lai]: #linux-appimage
[tar]: #binary-archives

## <a name="ubuntu-1404"></a>Ubuntu 14.04

### <a name="installation-via-package-repository---ubuntu-1404"></a>패키지 리포지토리를 통해 설치 - Ubuntu 14.04

PowerShell Core for Linux는 간편한 설치(및 업데이트)를 위해 패키지 리포지토리로 게시됩니다.
기본 설정 방법입니다.

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
curl https://packages.microsoft.com/config/ubuntu/14.04/prod.list | sudo tee /etc/apt/sources.list.d/microsoft.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

슈퍼 사용자로 Microsoft 리포지토리를 등록합니다.
그 이후에는 `sudo apt-get upgrade powershell`을 사용하여 설치를 업데이트하면 됩니다.

### <a name="installation-via-direct-download---ubuntu-1404"></a>직접 다운로드를 통해 설치 - Ubuntu 14.04

[릴리스][] 페이지의 Debian 패키지 `powershell_6.0.2-1.ubuntu.14.04_amd64.deb`를 Ubuntu 컴퓨터에 다운로드합니다.

그런 다음 터미널에서 다음을 실행합니다.

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> `dpkg -i`는 종속성 미충족으로 인해 실패하며 다음 명령 `apt-get install -f`가 이를 해결한 후 PowerShell 패키지 구성을 완료합니다.

### <a name="uninstallation---ubuntu-1404"></a>제거 - Ubuntu 14.04

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a>Ubuntu 16.04

### <a name="installation-via-package-repository---ubuntu-1604"></a>패키지 리포지토리를 통해 설치 - Ubuntu 16.04

PowerShell Core for Linux는 간편한 설치(및 업데이트)를 위해 패키지 리포지토리로 게시됩니다.
기본 설정 방법입니다.

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
sudo curl -o /etc/apt/sources.list.d/microsoft.list https://packages.microsoft.com/config/ubuntu/16.04/prod.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

Microsoft 리포지토리를 superuser로 등록하고 나면 그 이후부터는 `sudo apt-get upgrade powershell`을 사용하여 업데이트해야 합니다.

### <a name="installation-via-direct-download---ubuntu-1604"></a>직접 다운로드를 통해 설치 - Ubuntu 16.04

[릴리스][] 페이지의 Debian 패키지 `powershell_6.0.2-1.ubuntu.16.04_amd64.deb`를 Ubuntu 컴퓨터에 다운로드합니다.

그런 다음 터미널에서 다음을 실행합니다.

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> `dpkg -i`는 종속성 미충족으로 인해 실패하며 다음 명령 `apt-get install -f`가 이를 해결한 후 PowerShell 패키지 구성을 완료합니다.

### <a name="uninstallation---ubuntu-1604"></a>제거 - Ubuntu 16.04

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1704"></a>Ubuntu 17.04

### <a name="installation-via-package-repository---ubuntu-1704"></a>패키지 리포지토리를 통해 설치 - Ubuntu 17.04

PowerShell Core for Linux는 간편한 설치(및 업데이트)를 위해 패키지 리포지토리로 게시됩니다.
기본 설정 방법입니다.

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
sudo curl -o /etc/apt/sources.list.d/microsoft.list https://packages.microsoft.com/config/ubuntu/17.04/prod.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

Microsoft 리포지토리를 superuser로 등록하고 나면 그 이후부터는 `sudo apt-get upgrade powershell`을 사용하여 업데이트해야 합니다.

### <a name="installation-via-direct-download---ubuntu-1704"></a>직접 다운로드를 통해 설치 - Ubuntu 17.04

[릴리스][] 페이지의 Debian 패키지 `powershell_6.0.2-1.ubuntu.17.04_amd64.deb`를 Ubuntu 컴퓨터에 다운로드합니다.

그런 다음 터미널에서 다음을 실행합니다.

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.17.04_amd64.deb
sudo apt-get install -f
```

> `dpkg -i`는 종속성 미충족으로 인해 실패하며 다음 명령 `apt-get install -f`가 이를 해결한 후 PowerShell 패키지 구성을 완료합니다.

### <a name="uninstallation---ubuntu-1704"></a>제거 - Ubuntu 17.04

```sh
sudo apt-get remove powershell
```

## <a name="debian-8"></a>Debian 8

### <a name="installation-via-package-repository---debian-8"></a>패키지 리포지토리를 통해 설치 - Debian 8

PowerShell Core for Linux는 간편한 설치(및 업데이트)를 위해 패키지 리포지토리로 게시됩니다.
기본 설정 방법입니다.

```sh
# Install system components
sudo apt-get update
sudo apt-get install curl apt-transport-https

# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Product feed
sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-jessie-prod jessie main" > /etc/apt/sources.list.d/microsoft.list'

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

Microsoft 리포지토리를 superuser로 등록하고 나면 그 이후부터는 `sudo apt-get upgrade powershell`을 사용하여 업데이트해야 합니다.

### <a name="installation-via-direct-download---debian-8"></a>직접 다운로드를 통해 설치 - Debian 8

[릴리스][] 페이지의 Debian 패키지 `powershell_6.0.2-1.debian.8_amd64.deb`를 Debian 컴퓨터에 다운로드합니다.

그런 다음 터미널에서 다음을 실행합니다.

```sh
sudo dpkg -i powershell_6.0.2-1.debian.8_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> `dpkg -i`는 충족되지 않은 종속성으로 인해 실패합니다.
> 다음 명령인 `apt-get install -f`는 이러한 종속성을 해결하고 PowerShell 패키지 구성을 완료합니다.

### <a name="uninstallation---debian-8"></a>제거 - Debian 8

```sh
sudo apt-get remove powershell
```

## <a name="debian-9"></a>Debian 9

### <a name="installation-via-package-repository---debian-9"></a>패키지 리포지토리를 통해 설치 - Debian 9

PowerShell Core for Linux는 간편한 설치(및 업데이트)를 위해 패키지 리포지토리로 게시됩니다.
기본 설정 방법입니다.

```sh
# Install system components
sudo apt-get update
sudo apt-get install curl gnupg apt-transport-https

# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Product feed
sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-stretch-prod stretch main" > /etc/apt/sources.list.d/microsoft.list'

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

Microsoft 리포지토리를 superuser로 등록하고 나면 그 이후부터는 `sudo apt-get upgrade powershell`을 사용하여 업데이트해야 합니다.

### <a name="installation-via-direct-download---debian-9"></a>직접 다운로드를 통해 설치 - Debian 9

[릴리스][] 페이지의 Debian 패키지 `powershell_6.0.2-1.debian.9_amd64.deb`를 Debian 컴퓨터에 다운로드합니다.

그런 다음 터미널에서 다음을 실행합니다.

```sh
sudo dpkg -i powershell_6.0.2-1.debian.9_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> `dpkg -i`는 충족되지 않은 종속성으로 인해 실패합니다.
> 다음 명령인 `apt-get install -f`는 이러한 종속성을 해결하고 PowerShell 패키지 구성을 완료합니다.

### <a name="uninstallation---debian-9"></a>제거 - Debian 9

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a>CentOS 7

> 이 패키지는 Oracle Linux 7에서도 작동합니다.

### <a name="installation-via-package-repository-preferred---centos-7"></a>패키지 리포지토리를 통해 설치(권장) - CentOS 7

PowerShell Core for Linux는 간편한 설치(및 업데이트)를 위해 공식 Microsoft 리포지토리로 게시됩니다.

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

Microsoft 리포지토리를 superuser로 등록하고 나면 `sudo yum update powershell`을 사용하여 PowerShell을 업데이트해야 합니다.

### <a name="installation-via-direct-download---centos-7"></a>직접 다운로드를 통해 설치 - CentOS 7

[CentOS 7][]을 사용하여 [릴리스][] 페이지의 RPM 패키지 `powershell-6.0.2-1.rhel.7.x86_64.rpm`을 CentOS 컴퓨터로 다운로드합니다.

그런 다음 터미널에서 다음을 실행합니다.

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

또한 다운로드의 중간 단계 없이 RPM을 설치할 수 있습니다.

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a>제거 - CentOS 7

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a>Red Hat Enterprise Linux(RHEL) 7

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a>패키지 리포지토리(권장)를 통해 설치 - Red Hat Enterprise Linux(RHEL) 7

PowerShell Core for Linux는 간편한 설치(및 업데이트)를 위해 공식 Microsoft 리포지토리로 게시됩니다.

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

Microsoft 리포지토리를 superuser로 등록하고 나면 `sudo yum update powershell`을 사용하여 PowerShell을 업데이트해야 합니다.

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a>직접 다운로드를 통해 설치 - Red Hat Enterprise Linux(RHEL) 7

[릴리스][] 페이지의 RPM 패키지 `powershell-6.0.2-1.rhel.7.x86_64.rpm`을 Red Hat Enterprise Linux 컴퓨터로 다운로드합니다.

그런 다음 터미널에서 다음을 실행합니다.

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

또한 다운로드의 중간 단계 없이 RPM을 설치할 수 있습니다.

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a>제거 - Red Hat Enterprise Linux(RHEL) 7

```sh
sudo yum remove powershell
```

## <a name="opensuse-422"></a>OpenSUSE 42.2

> [!NOTE]
> PowerShell Core를 설치할 때 `zypper`에서 다음 오류를 보고할 수 있습니다.
>
> ```Output
> Problem: nothing provides libcurl needed by powershell-6.0.1-1.rhel.7.x86_64
>  Solution 1: do not install powershell-6.0.1-1.rhel.7.x86_64
>  Solution 2: break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies
> ```
>
> 이 경우 다음 명령이 설치된 대로 `libcurl4` 패키지를 보여 주는지 확인하여 호환되는 `libcurl` 라이브러리가 있는지 확인합니다.
>
> ```sh
> zypper search --file-list --match-exact '/usr/lib64/libcurl.so.4'
> ```
>
> 그런 다음, PowerShell 패키지를 설치할 때 `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` 솔루션을 선택합니다.

### <a name="installation-via-package-repository-preferred---opensuse-422"></a>패키지 리포지토리를 통해 설치(권장) - OpenSUSE 42.2

PowerShell Core for Linux는 간편한 설치(및 업데이트)를 위해 공식 Microsoft 리포지토리로 게시됩니다.

```sh
# Register the Microsoft signature key
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

# Add the Microsoft Product feed
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/zypp/repos.d/microsoft.repo

# Update the list of products
sudo zypper update

# Install PowerShell
sudo zypper install powershell

# Start PowerShell
pwsh
```

### <a name="installation-via-direct-download---opensuse-422"></a>직접 다운로드를 통해 설치 - OpenSUSE 42.2

[릴리스][] 페이지의 RPM 패키지 `powershell-6.0.2-1.rhel.7.x86_64.rpm`을 OpenSUSE 컴퓨터에 다운로드합니다.

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

또한 다운로드의 중간 단계 없이 RPM을 설치할 수 있습니다.

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---opensuse-422"></a>제거 - OpenSUSE 42.2

```sh
sudo zypper remove powershell
```

## <a name="fedora"></a>Fedora

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a>패키지 리포지토리를 통해 설치(권장) - Fedora 27, Fedora 28

PowerShell Core for Linux는 간편한 설치(및 업데이트)를 위해 공식 Microsoft 리포지토리로 게시됩니다.

```sh
# Register the Microsoft signature key
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Update the list of products
sudo dnf update

# Install a system component
sudo dnf install compat-openssl10

# Install PowerShell
sudo dnf install -y powershell

# Start PowerShell
pwsh
```

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a>직접 다운로드를 통해 설치 - Fedora 27, Fedora 28

[릴리스][] 페이지의 RPM 패키지 `powershell-6.0.2-1.rhel.7.x86_64.rpm`을 Fedora 컴퓨터에 다운로드합니다.

그런 다음 터미널에서 다음을 실행합니다.

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

또한 다운로드의 중간 단계 없이 RPM을 설치할 수 있습니다.

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a>제거 - Fedora 27, Fedora 28

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a>Arch Linux

PowerShell은 [Arch Linux][] 사용자 리포지토리(AUR)에 제공됩니다.

* [최신 태깅 릴리스][arch-release]를 사용하여 컴파일할 수 있습니다.
* [최신 마스터 커밋][arch-git]에서 컴파일할 수 있습니다.
* [최신 릴리스 이진 파일][arch-bin]을 사용하여 설치할 수 있습니다.

AUR의 패키지는 커뮤니티에서 유지 관리되며 공식적인 지원은 없습니다.

AUR에서 패키지를 설치하는 방법에 대한 자세한 내용은 [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) 또는 [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile) 커뮤니티를 참조하세요.

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="linux-appimage"></a>Linux AppImage

최신 Linux 배포를 사용하여 [릴리스][] 페이지의 AppImage `powershell-6.0.1-x86_64.AppImage`를 Linux 컴퓨터로 다운로드합니다.

그런 다음 터미널에서 다음을 실행합니다.

```bash
chmod a+x powershell-6.0.1-x86_64.AppImage
./powershell-6.0.1-x86_64.AppImage
```

[AppImage][]를 사용하면 PowerShell을 설치하지 않고 실행할 수 있습니다.
PowerShell 및 종속성(.NET Core의 시스템 종속성 포함)을 하나의 통합 패키지로 묶은 이식 가능한 응용 프로그램입니다.
이 패키지는 사용자의 Linux 배포와 독립적으로 작동하는 단일 이진 파일입니다.

[appimage]: http://appimage.org/

## <a name="kali"></a>Kali

### <a name="installation"></a>설치

```sh
# Download & Install prerequisites
sudo apt-get install libunwind8 libicu55
wget http://security.debian.org/debian-security/pool/updates/main/o/openssl/libssl1.0.0_1.0.1t-1+deb8u6_amd64.deb
sudo dpkg -i libssl1.0.0_1.0.1t-1+deb8u6_amd64.deb

# Install PowerShell
sudo dpkg -i powershell_6.0.2-1.ubuntu.16.04_amd64.deb

# Start PowerShell
pwsh
```

### <a name="run-powershell-in-latest-kali-kali-gnulinux-rolling-without-installing-it"></a>PowerShell을 설치하지 않고 최신 Kali(Kali GNU/Linux 롤링)에서 실행

```sh
# Grab the latest App Image
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-x86_64.AppImage

# Make executable
chmod a+x powershell-6.0.2-x86_64.AppImage

# Start PowerShell
./powershell-6.0.2-x86_64.AppImage
```

### <a name="uninstallation---kali"></a>제거 - Kali

```sh
sudo dpkg -r powershell_6.0.2-1.ubuntu.16.04_amd64.deb
```

## <a name="raspbian"></a>Raspbian

현재 PowerShell은 Raspbian Stretch에서만 지원됩니다.

또한 [Pi Zero](https://github.com/dotnet/coreclr/issues/10605) 등의 다른 장치에는 지원되지 않는 프로세서가 있기 때문에 CoreCLR(및 PowerShell Core)은 Pi 2 및 Pi 3 장치에서만 작동합니다.

[Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/)를 다운로드하고 [설치 지침](https://www.raspberrypi.org/documentation/installation/installing-images/README.md)에 따라 Pi에 설치합니다.

### <a name="installation"></a>설치

```sh
# Install prerequisites
sudo apt-get install libunwind8

# Grab the latest tar.gz
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-linux-arm32.tar.gz

# Make folder to put powershell
mkdir ~/powershell

# Unpack the tar.gz file
tar -xvf ./powershell-6.0.2-linux-arm32.tar.gz -C ~/powershell

# Start PowerShell
~/powershell/pwsh
```

필요에 따라 심볼 링크를 만들어 “pwsh” 이진 파일의 경로를 지정하지 않고 PowerShell을 시작할 수 있습니다.

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a>제거 - Raspbian

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a>이진 아카이브

고급 배포 시나리오를 지원하기 위해 Linux 플랫폼을 위한 PowerShell 이진 `tar.gz` 보관이 제공됩니다.

### <a name="dependencies"></a>종속성

PowerShell은 모든 Linux 배포를 위한 이식 가능한 이진 파일을 빌드합니다.
하지만 .NET Core 런타임의 경우 다양한 배포판에 대한 여러 종속성이 필요하므로 PowerShell가 동일한 작업을 수행합니다.

다음 차트는 여러 Linux 배포에서 공식적으로 지원되는 .NET Core 2.0 종속성을 보여 줍니다.

| OS                 | 종속성 |
| ------------------ | ------------ |
| Ubuntu 14.04       | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52 |
| Ubuntu 16.04       | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55 |
| Ubuntu 17.04       | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57 |
| Debian 8(Jessie)  | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52 |
| Debian 9(Stretch) | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57 |
| CentOS 7 <br> Oracle Linux 7 <br> RHEL 7 <br> OpenSUSE 42.2 | libunwind, libcurl, openssl-libs, libicu |
| Fedora 27 <br> Fedora 28 | libunwind, libcurl, openssl-libs, libicu, compat-openssl10 |

공식적으로 지원되지 않는 Linux 배포에 PowerShell 이진 파일을 배포하려면 별도의 단계를 통해 대상 OS에 필요한 종속성을 설치해야 합니다.
예를 들어 [Amazon Linux dockerfile][amazon-dockerfile]은 먼저 종속성을 설치한 후 Linux `tar.gz` 아카이브를 추출합니다.

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a>설치 - 이진 아카이브

#### <a name="linux"></a>Linux

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-linux-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/6.0.2

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.0.2

# Set execute permissions
sudo chmod +x /opt/microsoft/powershell/6.0.2/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/6.0.2/pwsh /usr/bin/pwsh
```

### <a name="uninstalling-binary-archives"></a>이진 보관 제거

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a>경로

* `$PSHOME`은 `/opt/microsoft/powershell/6.0.2/`입니다.
* 사용자 프로필은 `~/.config/powershell/profile.ps1`에서 읽습니다.
* 기본 프로필은 `$PSHOME/profile.ps1`에서 읽습니다.
* 사용자 프로필은 `~/.local/share/powershell/Modules`에서 읽습니다.
* 공유 모듈은 `/usr/local/share/powershell/Modules`에서 읽습니다.
* 기본 모듈은 `$PSHOME/Modules`에서 읽습니다.
* PSReadline 기록은 `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`에 기록됩니다.

프로필은 PowerShell의 호스트별 구성을 계속 사용하므로 기본 호스트별 프로필은 동일한 위치의 `Microsoft.PowerShell_profile.ps1`에 있습니다.

PowerShell은 Linux의 [XDG 기본 디렉터리 사양][xdg-bds]을 따릅니다.

[릴리스]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
