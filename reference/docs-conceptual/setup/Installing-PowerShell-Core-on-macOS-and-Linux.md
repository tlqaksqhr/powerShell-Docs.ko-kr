# <a name="installing-powershell-core-on-macos-and-linux"></a>macOS 및 Linux에서 PowerShell Core 설치

[Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 17.04][u17], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux(RHEL) 7][rhel7], [OpenSUSE 42.2][opensuse], [Fedora 25][fed25], [Fedora 26][fed26], [Arch Linux][arch] 및 [macOS 10.12][mac]를 지원합니다.

공식적으로 지원되지 않는 Linux 배포의 경우 [PowerShell AppImage][lai]를 사용해 보세요. 또한 Linux [`tar.gz` 보관][tar]을 사용하여 PowerShell 이진 파일을 직접 배포해 볼 수도 있지만 OS에 따라 별도의 단계로 필요한 종속성을 설정해야 합니다.

모든 패키지는 GitHub [릴리스][] 페이지에 제공됩니다. 패키지가 설치되면 터미널에서 `pwsh`를 실행합니다.

[u14]: #ubuntu-1404
[u16]: #ubuntu-1604
[u17]: #ubuntu-1704
[deb8]: #debian-8
[deb9]: #debian-9
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse-422
[fed25]: #fedora-25
[fed26]: #fedora-26
[arch]: #arch-linux
[lai]: #linux-appimage
[mac]: #macos-1012
[tar]: #binary-archives

## <a name="ubuntu-1404"></a>Ubuntu 14.04

### <a name="installation-via-package-repository---ubuntu-1404"></a>패키지 리포지토리를 통해 설치 - Ubuntu 14.04

PowerShell Core for Linux는 간편한 설치(및 업데이트)를 위해 패키지 리포지토리로 게시됩니다. 기본 설정 방법입니다.

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

Microsoft 리포지토리를 superuser로 등록하고 나면 그 이후부터는 `sudo apt-get upgrade powershell`을 사용하여 업데이트해야 합니다.

### <a name="installation-via-direct-download---ubuntu-1404"></a>직접 다운로드를 통해 설치 - Ubuntu 14.04

[릴리스][] 페이지의 Debian 패키지 `powershell_6.0.0-1.ubuntu.14.04_amd64.deb`를 Ubuntu 컴퓨터에 다운로드합니다.

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.ubuntu.14.04_amd64.deb
```

그런 다음 터미널에서 다음을 실행합니다.

```sh
sudo dpkg -i powershell_6.0.0-1.ubuntu.14.04_amd64.deb
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
curl https://packages.microsoft.com/config/ubuntu/16.04/prod.list | sudo tee /etc/apt/sources.list.d/microsoft.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

Microsoft 리포지토리를 superuser로 등록하고 나면 그 이후부터는 `sudo apt-get upgrade powershell`을 사용하여 업데이트해야 합니다.

### <a name="installation-via-direct-download---ubuntu-1604"></a>직접 다운로드를 통해 설치 - Ubuntu 16.04

[릴리스][] 페이지의 Debian 패키지 `powershell_6.0.0-1.ubuntu.16.04_amd64.deb`를 Ubuntu 컴퓨터에 다운로드합니다.

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.ubuntu.16.04_amd64.deb
```

그런 다음 터미널에서 다음을 실행합니다.

```sh
sudo dpkg -i powershell_6.0.0-1.ubuntu.16.04_amd64.deb
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
curl https://packages.microsoft.com/config/ubuntu/17.04/prod.list | sudo tee /etc/apt/sources.list.d/microsoft.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

Microsoft 리포지토리를 superuser로 등록하고 나면 그 이후부터는 `sudo apt-get upgrade powershell`을 사용하여 업데이트해야 합니다.

### <a name="installation-via-direct-download---ubuntu-1704"></a>직접 다운로드를 통해 설치 - Ubuntu 17.04

[릴리스][] 페이지의 Debian 패키지 `powershell_6.0.0-1.ubuntu.17.04_amd64.deb`를 Ubuntu 컴퓨터에 다운로드합니다.

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.ubuntu.17.04_amd64.deb
```

그런 다음 터미널에서 다음을 실행합니다.

```sh
sudo dpkg -i powershell_6.0.0-1.ubuntu.17.04_amd64.deb
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

[릴리스][] 페이지의 Debian 패키지 `powershell_6.0.0-1.debian.8_amd64.deb`를 Debian 컴퓨터에 다운로드합니다.

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.debian.8_amd64.deb
```

그런 다음 터미널에서 다음을 실행합니다.

```sh
sudo dpkg -i powershell_6.0.0-1.debian.8_amd64.deb
sudo apt-get install -f
```

> `dpkg -i`는 종속성 미충족으로 인해 실패하며 다음 명령 `apt-get install -f`가 이를 해결한 후 PowerShell 패키지 구성을 완료합니다.

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

[릴리스][] 페이지의 Debian 패키지 `powershell_6.0.0-1.debian.9_amd64.deb`를 Debian 컴퓨터에 다운로드합니다.

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.debian.9_amd64.deb
```

그런 다음 터미널에서 다음을 실행합니다.

```sh
sudo dpkg -i powershell_6.0.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

> `dpkg -i`는 종속성 미충족으로 인해 실패하며 다음 명령 `apt-get install -f`가 이를 해결한 후 PowerShell 패키지 구성을 완료합니다.

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

[CentOS 7][]을 사용하여 [릴리스][] 페이지의 RPM 패키지 `powershell-6.0.0-1.rhel.7.x86_64.rpm`을 CentOS 컴퓨터로 다운로드합니다.

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

그런 다음 터미널에서 다음을 실행합니다.

```sh
sudo yum install powershell-6.0.0-1.rhel.7.x86_64.rpm
```

또한 다운로드의 중간 단계 없이 RPM을 설치할 수 있습니다.

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
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

[릴리스][] 페이지의 RPM 패키지 `powershell-6.0.0-1.rhel.7.x86_64.rpm`을 Red Hat Enterprise Linux 컴퓨터로 다운로드합니다.

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.debian.9_amd64.deb
```

그런 다음 터미널에서 다음을 실행합니다.

```sh
sudo yum install powershell-6.0.0-1.rhel.7.x86_64.rpm
```

또한 다운로드의 중간 단계 없이 RPM을 설치할 수 있습니다.

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a>제거 - Red Hat Enterprise Linux(RHEL) 7

```sh
sudo yum remove powershell
```

## <a name="opensuse-422"></a>OpenSUSE 42.2

> **참고:** PowerShell Core를 설치하는 경우 `zypper`는 다음 오류를 보고할 수 있습니다.
>
> ```text
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
> 그런 다음, `powershell` 패키지를 설치할 때 `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` 솔루션을 선택합니다.

### <a name="installation-via-package-repository-preferred---opensuse-422"></a>패키지 리포지토리를 통해 설치(권장) - OpenSUSE 42.2

PowerShell Core for Linux는 간편한 설치(및 업데이트)를 위해 공식 Microsoft 리포지토리로 게시됩니다.

```sh
# Register the Microsoft signature key
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

# Add the Microsoft Product feed
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/zypp/repos.d/microsoft.repo

# Install PowerShell
sudo zypper install powershell

# Start PowerShell
pwsh
```

### <a name="installation-via-direct-download---opensuse-422"></a>직접 다운로드를 통해 설치 - OpenSUSE 42.2

[릴리스][] 페이지의 RPM 패키지 `powershell-6.0.0-1.rhel.7.x86_64.rpm`을 OpenSUSE 컴퓨터에 다운로드합니다.

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install powershell-6.0.0-1.rhel.7.x86_64.rpm
```

또한 다운로드의 중간 단계 없이 RPM을 설치할 수 있습니다.

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---opensuse-422"></a>제거 - OpenSUSE 42.2

```sh
sudo zypper remove powershell
```

## <a name="fedora-25"></a>Fedora 25

### <a name="installation-via-package-repository-preferred---fedora-25"></a>패키지 리포지토리를 통해 설치(권장) - Fedora 25

PowerShell Core for Linux는 간편한 설치(및 업데이트)를 위해 공식 Microsoft 리포지토리로 게시됩니다.

```sh
# Register the Microsoft signature key
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Update the list of products
sudo dnf update

# Install PowerShell
sudo dnf install -y powershell

# Start PowerShell
pwsh
```

### <a name="installation-via-direct-download---fedora-25"></a>직접 다운로드를 통해 설치 - Fedora 25

[릴리스][] 페이지의 RPM 패키지 `powershell-6.0.0-1.rhel.7.x86_64.rpm`을 Fedora 컴퓨터에 다운로드합니다.

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

그런 다음 터미널에서 다음을 실행합니다.

```sh
sudo dnf install powershell-6.0.0-1.rhel.7.x86_64.rpm
```

또한 다운로드의 중간 단계 없이 RPM을 설치할 수 있습니다.

```sh
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-25"></a>제거 - Fedora 25

```sh
sudo dnf remove powershell
```

## <a name="fedora-26"></a>Fedora 26

### <a name="installation-via-package-repository-preferred---fedora-26"></a>패키지 리포지토리를 통해 설치(권장) - Fedora 26

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

### <a name="installation-via-direct-download---fedora-26"></a>직접 다운로드를 통해 설치 - Fedora 26

[릴리스][] 페이지의 RPM 패키지 `powershell-6.0.0-1.rhel.7.x86_64.rpm`을 Fedora 컴퓨터에 다운로드합니다.

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

그런 다음 터미널에서 다음을 실행합니다.

```sh
sudo dnf update
sudo dnf install compat-openssl10
sudo dnf install powershell-6.0.0-1.rhel.7.x86_64.rpm
```

또한 다운로드의 중간 단계 없이 RPM을 설치할 수 있습니다.

```sh
sudo dnf update
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-26"></a>제거 - Fedora 26

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

최신 Linux 배포를 사용하여 [릴리스][] 페이지의 AppImage `powershell-6.0.0-x86_64.AppImage`를 Linux 컴퓨터로 다운로드합니다.

그런 다음 터미널에서 다음을 실행합니다.

```bash
chmod a+x powershell-6.0.0-x86_64.AppImage
./powershell-6.0.0-x86_64.AppImage
```

[AppImage][]를 사용하면 PowerShell을 설치하지 않고 실행할 수 있습니다. PowerShell 및 종속성(.NET Core의 시스템 종속성 포함)을 하나의 통합 패키지로 묶은 이식 가능한 응용 프로그램입니다. 이 패키지는 사용자의 Linux 배포판과 독립적으로 작동하며 단일 이진 파일입니다.

[appimage]: http://appimage.org/

## <a name="macos-1012"></a>macOS 10.12

### <a name="installation-via-homebrew-preferred---macos-1012"></a>Homebrew를 통해 설치(권장) - macOS 10.12

[Homebrew][brew]는 macOS의 누락 패키지 관리자입니다. `brew` 명령이 없을 경우 [해당 지침][brew]에 따라 Homebrew를 설치해야 합니다.

Homebrew를 설치했으면 PowerShell을 쉽게 설치할 수 있습니다. 먼저 더 많은 패키지를 설치할 수 있도록 [Homebrew-Cask][cask]를 설치합니다.

```sh
brew tap caskroom/cask
```

이제 PowerShell을 설치할 수 있습니다.

```sh
brew cask install powershell
```

PowerShell의 새 버전이 릴리스되면 Homebrew의 공식을 업데이트하고 PowerShell을 업그레이드하기만 하면 됩니다.

```sh
brew update
brew cask reinstall powershell
```

> 참고: [Cask의 이 문제](https://github.com/caskroom/homebrew-cask/issues/29301)로 인해 현재 업그레이드를 위해서는 재설치를 수행해야 합니다.

[brew]: http://brew.sh/
[cask]: https://caskroom.github.io/

### <a name="installation-via-direct-download---macos-1012"></a>직접 다운로드를 통해 설치 - macOS 10.12

macOS 10.12를 사용하여 [릴리스][] 페이지의 PKG 패키지 `powershell-6.0.0-osx.10.12-x64.pkg`를 macOS 컴퓨터로 다운로드합니다.

파일을 두 번 클릭하고 메시지를 따르거나 터미널에서 설치합니다.

```sh
sudo installer -pkg powershell-6.0.0-osx.10.12-x64.pkg -target /
```

### <a name="uninstallation---macos-1012"></a>제거 - macOS 10.12

Homebrew를 사용하여 PowerShell을 설치한 경우에는 제거가 간편합니다.

```sh
brew cask uninstall powershell
```

직접 다운로드를 통해 PowerShell을 설치한 경우에는 PowerShell을 수동으로 제거해야 합니다.

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

추가 PowerShell 경로(예: 사용자 프로필 경로)를 제거하려면 이 문서의 아래에 나오는 [경로][paths] 섹션을 참조하고 `sudo rm`를 사용하여 원하는 경로를 제거하세요. (참고: Homebrew를 사용하여 설치한 경우에는 필요하지 않습니다.)

[paths]:#paths

## <a name="kali"></a>Kali

### <a name="installation"></a>설치

```sh
# Download & Install prerequisites
sudo apt-get install libunwind8 libicu55
wget http://security.debian.org/debian-security/pool/updates/main/o/openssl/libssl1.0.0_1.0.1t-1+deb8u6_amd64.deb
sudo dpkg -i libssl1.0.0_1.0.1t-1+deb8u6_amd64.deb

# Download & Install PowerShell
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.ubuntu.16.04_amd64.deb
sudo dpkg -i powershell_6.0.0-1.ubuntu.16.04_amd64.deb

# Start PowerShell
pwsh
```

### <a name="run-powershell-in-latest-kali-kali-gnulinux-rolling-without-installing-it"></a>PowerShell을 설치하지 않고 최신 Kali(Kali GNU/Linux 롤링)에서 실행

```sh
# Grab the latest App Image
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-x86_64.AppImage

# Make executable
chmod a+x powershell-6.0.0-x86_64.AppImage

# Start PowerShell
./powershell-6.0.0-x86_64.AppImage
```

### <a name="uninstallation---kali"></a>제거 - Kali

```sh
sudo dpkg -r powershell-6.0.0-x86_64.AppImage
```

## <a name="raspbian"></a>Raspbian

현재 PowerShell은 Raspbian Stretch에서만 지원됩니다.

### <a name="installation"></a>설치

```sh
# Install prerequisites
sudo apt-get install libunwind8

# Grab the latest tar.gz
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-linux-arm32.tar.gz

# Make folder to put powershell
mkdir ~/powershell

# Unpack the tar.gz file
tar -xvf ./powershell-6.0.0-linux-arm32.tar.gz -C ~/powershell

# Start PowerShell
~/powershell/pwsh
```

### <a name="uninstallation---raspbian"></a>제거 - Raspbian

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a>이진 아카이브

고급 배포 시나리오를 지원하기 위해 macOS 및 Linux 플랫폼에 PowerShell 이진 `tar.gz` 아카이브가 제공됩니다.

### <a name="dependencies"></a>종속성

Linux의 경우 PowerShell이 모든 Linux 배포판을 위한 이식 가능한 이진 파일을 빌드합니다.
하지만 .NET Core 런타임의 경우 다양한 배포판에 대한 여러 종속성이 필요하므로 PowerShell가 동일한 작업을 수행합니다.

다음 차트에서는 공식적으로 지원되는 여러 Linux 배포판에 대한 .NET Core 2.0 종속성을 보여줍니다.

| OS                 | 종속성 |
| ------------------ | ------------ |
| Ubuntu 14.04       | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52 |
| Ubuntu 16.04       | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55 |
| Ubuntu 17.04       | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57 |
| Debian 8(Jessie)  | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52 |
| Debian 9(Stretch) | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57 |
| CentOS 7 <br> Oracle Linux 7 <br> RHEL 7 <br> OpenSUSE 42.2 <br> Fedora 25 | libunwind, libcurl, openssl-libs, libicu |
| Fedora 26          | libunwind, libcurl, openssl-libs, libicu, compat-openssl10 |

공식적으로 지원되지 않는 Linux 배포판에서 PowerShell 이진 파일을 배포하려면 별도의 단계를 거쳐 대상 OS에 필요한 종속성을 설치해야 합니다. 예를 들어 [Amazon Linux dockerfile][amazon-dockerfile]은 먼저 종속성을 설치한 후 Linux `tar.gz` 아카이브를 추출합니다.

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a>설치 - 이진 아카이브

#### <a name="linux"></a>Linux

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-linux-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/6.0.0

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.0.0

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/6.0.0/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/6.0.0/pwsh /usr/bin/pwsh
```

#### <a name="macos"></a>macOS

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-osx-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /usr/local/microsoft/powershell/6.0.0

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /usr/local/microsoft/powershell/6.0.0

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/6.0.0/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /usr/local/microsoft/powershell/6.0.0/pwsh /usr/local/bin/pwsh
```

### <a name="uninstallation---binary-archives"></a>제거 - 이진 아카이브

#### <a name="linux"></a>Linux

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

#### <a name="macos"></a>macOS

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

## <a name="paths"></a>경로

* `$PSHOME`은 `/opt/microsoft/powershell/6.0.0/`입니다.
* 사용자 프로필은 `~/.config/powershell/profile.ps1`에서 읽습니다.
* 기본 프로필은 `$PSHOME/profile.ps1`에서 읽습니다.
* 사용자 프로필은 `~/.local/share/powershell/Modules`에서 읽습니다.
* 공유 모듈은 `/usr/local/share/powershell/Modules`에서 읽습니다.
* 기본 모듈은 `$PSHOME/Modules`에서 읽습니다.
* PSReadline 기록은 `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`에 기록됩니다.

프로필은 PowerShell의 호스트별 구성을 계속 사용하므로 기본 호스트별 프로필은 동일한 위치의 `Microsoft.PowerShell_profile.ps1`에 있습니다.

Linux 및 macOS에서는 [XDG 기본 디렉터리 사양][xdg-bds]이 계속 사용됩니다.

macOS는 BSD에서 파생된 것이므로 `/opt` 대신 `/usr/local`이 접두사로 사용됩니다. 따라서 `$PSHOME`은 `/usr/local/microsoft/powershell/6.0.0/`이며 symlink는 `/usr/local/bin/pwsh`에 있습니다.

[릴리스]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html