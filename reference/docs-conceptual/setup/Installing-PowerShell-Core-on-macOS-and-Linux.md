# <a name="installing-powershell-core-on-macos-and-linux"></a><span data-ttu-id="f0054-101">macOS 및 Linux에서 PowerShell Core 설치</span><span class="sxs-lookup"><span data-stu-id="f0054-101">Installing PowerShell Core on macOS and Linux</span></span>

<span data-ttu-id="f0054-102">[Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 17.04][u17], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux(RHEL) 7][rhel7], [OpenSUSE 42.2][opensuse], [Fedora 25][fed25], [Fedora 26][fed26], [Arch Linux][arch] 및 [macOS 10.12][mac]를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-102">Supports [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 17.04][u17], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.2][opensuse], [Fedora 25][fed25], [Fedora 26][fed26], [Arch Linux][arch], and [macOS 10.12][mac].</span></span>

<span data-ttu-id="f0054-103">공식적으로 지원되지 않는 Linux 배포의 경우 [PowerShell AppImage][lai]를 사용해 보세요.</span><span class="sxs-lookup"><span data-stu-id="f0054-103">For Linux distributions that are not officially supported, you can try using the [PowerShell AppImage][lai].</span></span> <span data-ttu-id="f0054-104">또한 Linux [`tar.gz` 보관][tar]을 사용하여 PowerShell 이진 파일을 직접 배포해 볼 수도 있지만 OS에 따라 별도의 단계로 필요한 종속성을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-104">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="f0054-105">모든 패키지는 GitHub [릴리스][] 페이지에 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-105">All packages are available on our GitHub [releases][] page.</span></span> <span data-ttu-id="f0054-106">패키지가 설치되면 터미널에서 `pwsh`를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-106">Once the package is installed, run `pwsh` from a terminal.</span></span>

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

## <a name="ubuntu-1404"></a><span data-ttu-id="f0054-107">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="f0054-107">Ubuntu 14.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1404"></a><span data-ttu-id="f0054-108">패키지 리포지토리를 통해 설치 - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="f0054-108">Installation via Package Repository - Ubuntu 14.04</span></span>

<span data-ttu-id="f0054-109">PowerShell Core for Linux는 간편한 설치(및 업데이트)를 위해 패키지 리포지토리로 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-109">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span> <span data-ttu-id="f0054-110">기본 설정 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-110">This is the preferred method.</span></span>

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

<span data-ttu-id="f0054-111">Microsoft 리포지토리를 superuser로 등록하고 나면 그 이후부터는 `sudo apt-get upgrade powershell`을 사용하여 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-111">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1404"></a><span data-ttu-id="f0054-112">직접 다운로드를 통해 설치 - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="f0054-112">Installation via Direct Download - Ubuntu 14.04</span></span>

<span data-ttu-id="f0054-113">[릴리스][] 페이지의 Debian 패키지 `powershell_6.0.0-1.ubuntu.14.04_amd64.deb`를 Ubuntu 컴퓨터에 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-113">Download the Debian package `powershell_6.0.0-1.ubuntu.14.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.ubuntu.14.04_amd64.deb
```

<span data-ttu-id="f0054-114">그런 다음 터미널에서 다음을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-114">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.0-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="f0054-115">`dpkg -i`는 종속성 미충족으로 인해 실패하며 다음 명령 `apt-get install -f`가 이를 해결한 후 PowerShell 패키지 구성을 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-115">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1404"></a><span data-ttu-id="f0054-116">제거 - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="f0054-116">Uninstallation - Ubuntu 14.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a><span data-ttu-id="f0054-117">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="f0054-117">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="f0054-118">패키지 리포지토리를 통해 설치 - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="f0054-118">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="f0054-119">PowerShell Core for Linux는 간편한 설치(및 업데이트)를 위해 패키지 리포지토리로 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-119">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="f0054-120">기본 설정 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-120">This is the preferred method.</span></span>

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

<span data-ttu-id="f0054-121">Microsoft 리포지토리를 superuser로 등록하고 나면 그 이후부터는 `sudo apt-get upgrade powershell`을 사용하여 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-121">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="f0054-122">직접 다운로드를 통해 설치 - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="f0054-122">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="f0054-123">[릴리스][] 페이지의 Debian 패키지 `powershell_6.0.0-1.ubuntu.16.04_amd64.deb`를 Ubuntu 컴퓨터에 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-123">Download the Debian package `powershell_6.0.0-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine:</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.ubuntu.16.04_amd64.deb
```

<span data-ttu-id="f0054-124">그런 다음 터미널에서 다음을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-124">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="f0054-125">`dpkg -i`는 종속성 미충족으로 인해 실패하며 다음 명령 `apt-get install -f`가 이를 해결한 후 PowerShell 패키지 구성을 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-125">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="f0054-126">제거 - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="f0054-126">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1704"></a><span data-ttu-id="f0054-127">Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="f0054-127">Ubuntu 17.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1704"></a><span data-ttu-id="f0054-128">패키지 리포지토리를 통해 설치 - Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="f0054-128">Installation via Package Repository - Ubuntu 17.04</span></span>

<span data-ttu-id="f0054-129">PowerShell Core for Linux는 간편한 설치(및 업데이트)를 위해 패키지 리포지토리로 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-129">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="f0054-130">기본 설정 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-130">This is the preferred method.</span></span>

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

<span data-ttu-id="f0054-131">Microsoft 리포지토리를 superuser로 등록하고 나면 그 이후부터는 `sudo apt-get upgrade powershell`을 사용하여 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-131">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1704"></a><span data-ttu-id="f0054-132">직접 다운로드를 통해 설치 - Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="f0054-132">Installation via Direct Download - Ubuntu 17.04</span></span>

<span data-ttu-id="f0054-133">[릴리스][] 페이지의 Debian 패키지 `powershell_6.0.0-1.ubuntu.17.04_amd64.deb`를 Ubuntu 컴퓨터에 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-133">Download the Debian package `powershell_6.0.0-1.ubuntu.17.04_amd64.deb` from the [releases][] page onto the Ubuntu machine:</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.ubuntu.17.04_amd64.deb
```

<span data-ttu-id="f0054-134">그런 다음 터미널에서 다음을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-134">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.0-1.ubuntu.17.04_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="f0054-135">`dpkg -i`는 종속성 미충족으로 인해 실패하며 다음 명령 `apt-get install -f`가 이를 해결한 후 PowerShell 패키지 구성을 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-135">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1704"></a><span data-ttu-id="f0054-136">제거 - Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="f0054-136">Uninstallation - Ubuntu 17.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-8"></a><span data-ttu-id="f0054-137">Debian 8</span><span class="sxs-lookup"><span data-stu-id="f0054-137">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="f0054-138">패키지 리포지토리를 통해 설치 - Debian 8</span><span class="sxs-lookup"><span data-stu-id="f0054-138">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="f0054-139">PowerShell Core for Linux는 간편한 설치(및 업데이트)를 위해 패키지 리포지토리로 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-139">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="f0054-140">기본 설정 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-140">This is the preferred method.</span></span>

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

<span data-ttu-id="f0054-141">Microsoft 리포지토리를 superuser로 등록하고 나면 그 이후부터는 `sudo apt-get upgrade powershell`을 사용하여 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-141">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-8"></a><span data-ttu-id="f0054-142">직접 다운로드를 통해 설치 - Debian 8</span><span class="sxs-lookup"><span data-stu-id="f0054-142">Installation via Direct Download - Debian 8</span></span>

<span data-ttu-id="f0054-143">[릴리스][] 페이지의 Debian 패키지 `powershell_6.0.0-1.debian.8_amd64.deb`를 Debian 컴퓨터에 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-143">Download the Debian package `powershell_6.0.0-1.debian.8_amd64.deb` from the [releases][] page onto the Debian machine:</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.debian.8_amd64.deb
```

<span data-ttu-id="f0054-144">그런 다음 터미널에서 다음을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-144">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.0-1.debian.8_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="f0054-145">`dpkg -i`는 종속성 미충족으로 인해 실패하며 다음 명령 `apt-get install -f`가 이를 해결한 후 PowerShell 패키지 구성을 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-145">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-8"></a><span data-ttu-id="f0054-146">제거 - Debian 8</span><span class="sxs-lookup"><span data-stu-id="f0054-146">Uninstallation - Debian 8</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-9"></a><span data-ttu-id="f0054-147">Debian 9</span><span class="sxs-lookup"><span data-stu-id="f0054-147">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="f0054-148">패키지 리포지토리를 통해 설치 - Debian 9</span><span class="sxs-lookup"><span data-stu-id="f0054-148">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="f0054-149">PowerShell Core for Linux는 간편한 설치(및 업데이트)를 위해 패키지 리포지토리로 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-149">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="f0054-150">기본 설정 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-150">This is the preferred method.</span></span>

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

<span data-ttu-id="f0054-151">Microsoft 리포지토리를 superuser로 등록하고 나면 그 이후부터는 `sudo apt-get upgrade powershell`을 사용하여 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-151">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="f0054-152">직접 다운로드를 통해 설치 - Debian 9</span><span class="sxs-lookup"><span data-stu-id="f0054-152">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="f0054-153">[릴리스][] 페이지의 Debian 패키지 `powershell_6.0.0-1.debian.9_amd64.deb`를 Debian 컴퓨터에 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-153">Download the Debian package `powershell_6.0.0-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine:</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.debian.9_amd64.deb
```

<span data-ttu-id="f0054-154">그런 다음 터미널에서 다음을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-154">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="f0054-155">`dpkg -i`는 종속성 미충족으로 인해 실패하며 다음 명령 `apt-get install -f`가 이를 해결한 후 PowerShell 패키지 구성을 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-155">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-9"></a><span data-ttu-id="f0054-156">제거 - Debian 9</span><span class="sxs-lookup"><span data-stu-id="f0054-156">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="f0054-157">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="f0054-157">CentOS 7</span></span>

> <span data-ttu-id="f0054-158">이 패키지는 Oracle Linux 7에서도 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-158">This package also works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="f0054-159">패키지 리포지토리를 통해 설치(권장) - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="f0054-159">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="f0054-160">PowerShell Core for Linux는 간편한 설치(및 업데이트)를 위해 공식 Microsoft 리포지토리로 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-160">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="f0054-161">Microsoft 리포지토리를 superuser로 등록하고 나면 `sudo yum update powershell`을 사용하여 PowerShell을 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-161">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="f0054-162">직접 다운로드를 통해 설치 - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="f0054-162">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="f0054-163">[CentOS 7][]을 사용하여 [릴리스][] 페이지의 RPM 패키지 `powershell-6.0.0-1.rhel.7.x86_64.rpm`을 CentOS 컴퓨터로 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-163">Using [CentOS 7][], download the RPM package `powershell-6.0.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine:</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="f0054-164">그런 다음 터미널에서 다음을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-164">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="f0054-165">또한 다운로드의 중간 단계 없이 RPM을 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-165">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="f0054-166">제거 - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="f0054-166">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="f0054-168">Red Hat Enterprise Linux(RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="f0054-168">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="f0054-169">패키지 리포지토리(권장)를 통해 설치 - Red Hat Enterprise Linux(RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="f0054-169">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="f0054-170">PowerShell Core for Linux는 간편한 설치(및 업데이트)를 위해 공식 Microsoft 리포지토리로 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-170">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="f0054-171">Microsoft 리포지토리를 superuser로 등록하고 나면 `sudo yum update powershell`을 사용하여 PowerShell을 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-171">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="f0054-172">직접 다운로드를 통해 설치 - Red Hat Enterprise Linux(RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="f0054-172">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="f0054-173">[릴리스][] 페이지의 RPM 패키지 `powershell-6.0.0-1.rhel.7.x86_64.rpm`을 Red Hat Enterprise Linux 컴퓨터로 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-173">Download the RPM package `powershell-6.0.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine:</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.debian.9_amd64.deb
```

<span data-ttu-id="f0054-174">그런 다음 터미널에서 다음을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-174">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="f0054-175">또한 다운로드의 중간 단계 없이 RPM을 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-175">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="f0054-176">제거 - Red Hat Enterprise Linux(RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="f0054-176">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse-422"></a><span data-ttu-id="f0054-177">OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="f0054-177">OpenSUSE 42.2</span></span>

> <span data-ttu-id="f0054-178">**참고:** PowerShell Core를 설치하는 경우 `zypper`는 다음 오류를 보고할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-178">**Note:** When installing PowerShell Core, `zypper` may report the following error:</span></span>
>
> ```text
> Problem: nothing provides libcurl needed by powershell-6.0.1-1.rhel.7.x86_64
>  Solution 1: do not install powershell-6.0.1-1.rhel.7.x86_64
>  Solution 2: break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies
> ```
>
> <span data-ttu-id="f0054-179">이 경우 다음 명령이 설치된 대로 `libcurl4` 패키지를 보여 주는지 확인하여 호환되는 `libcurl` 라이브러리가 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-179">In this case, verify that a compatible `libcurl` library is present by checking that the following command shows the `libcurl4` package as installed:</span></span>
>
> ```sh
> zypper search --file-list --match-exact '/usr/lib64/libcurl.so.4'
> ```
>
> <span data-ttu-id="f0054-180">그런 다음, `powershell` 패키지를 설치할 때 `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` 솔루션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-180">Then choose the `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` solution when installing the `powershell` package.</span></span>

### <a name="installation-via-package-repository-preferred---opensuse-422"></a><span data-ttu-id="f0054-181">패키지 리포지토리를 통해 설치(권장) - OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="f0054-181">Installation via Package Repository (preferred) - OpenSUSE 42.2</span></span>

<span data-ttu-id="f0054-182">PowerShell Core for Linux는 간편한 설치(및 업데이트)를 위해 공식 Microsoft 리포지토리로 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-182">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---opensuse-422"></a><span data-ttu-id="f0054-183">직접 다운로드를 통해 설치 - OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="f0054-183">Installation via Direct Download - OpenSUSE 42.2</span></span>

<span data-ttu-id="f0054-184">[릴리스][] 페이지의 RPM 패키지 `powershell-6.0.0-1.rhel.7.x86_64.rpm`을 OpenSUSE 컴퓨터에 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-184">Download the RPM package `powershell-6.0.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the OpenSUSE machine:</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install powershell-6.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="f0054-185">또한 다운로드의 중간 단계 없이 RPM을 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-185">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---opensuse-422"></a><span data-ttu-id="f0054-186">제거 - OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="f0054-186">Uninstallation - OpenSUSE 42.2</span></span>

```sh
sudo zypper remove powershell
```

## <a name="fedora-25"></a><span data-ttu-id="f0054-187">Fedora 25</span><span class="sxs-lookup"><span data-stu-id="f0054-187">Fedora 25</span></span>

### <a name="installation-via-package-repository-preferred---fedora-25"></a><span data-ttu-id="f0054-188">패키지 리포지토리를 통해 설치(권장) - Fedora 25</span><span class="sxs-lookup"><span data-stu-id="f0054-188">Installation via Package Repository (preferred) - Fedora 25</span></span>

<span data-ttu-id="f0054-189">PowerShell Core for Linux는 간편한 설치(및 업데이트)를 위해 공식 Microsoft 리포지토리로 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-189">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---fedora-25"></a><span data-ttu-id="f0054-190">직접 다운로드를 통해 설치 - Fedora 25</span><span class="sxs-lookup"><span data-stu-id="f0054-190">Installation via Direct Download - Fedora 25</span></span>

<span data-ttu-id="f0054-191">[릴리스][] 페이지의 RPM 패키지 `powershell-6.0.0-1.rhel.7.x86_64.rpm`을 Fedora 컴퓨터에 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-191">Download the RPM package `powershell-6.0.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine:</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="f0054-192">그런 다음 터미널에서 다음을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-192">Then execute the following in the terminal:</span></span>

```sh
sudo dnf install powershell-6.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="f0054-193">또한 다운로드의 중간 단계 없이 RPM을 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-193">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-25"></a><span data-ttu-id="f0054-194">제거 - Fedora 25</span><span class="sxs-lookup"><span data-stu-id="f0054-194">Uninstallation - Fedora 25</span></span>

```sh
sudo dnf remove powershell
```

## <a name="fedora-26"></a><span data-ttu-id="f0054-195">Fedora 26</span><span class="sxs-lookup"><span data-stu-id="f0054-195">Fedora 26</span></span>

### <a name="installation-via-package-repository-preferred---fedora-26"></a><span data-ttu-id="f0054-196">패키지 리포지토리를 통해 설치(권장) - Fedora 26</span><span class="sxs-lookup"><span data-stu-id="f0054-196">Installation via Package Repository (preferred) - Fedora 26</span></span>

<span data-ttu-id="f0054-197">PowerShell Core for Linux는 간편한 설치(및 업데이트)를 위해 공식 Microsoft 리포지토리로 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-197">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---fedora-26"></a><span data-ttu-id="f0054-198">직접 다운로드를 통해 설치 - Fedora 26</span><span class="sxs-lookup"><span data-stu-id="f0054-198">Installation via Direct Download - Fedora 26</span></span>

<span data-ttu-id="f0054-199">[릴리스][] 페이지의 RPM 패키지 `powershell-6.0.0-1.rhel.7.x86_64.rpm`을 Fedora 컴퓨터에 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-199">Download the RPM package `powershell-6.0.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine:</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="f0054-200">그런 다음 터미널에서 다음을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-200">Then execute the following in the terminal:</span></span>

```sh
sudo dnf update
sudo dnf install compat-openssl10
sudo dnf install powershell-6.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="f0054-201">또한 다운로드의 중간 단계 없이 RPM을 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-201">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf update
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-26"></a><span data-ttu-id="f0054-202">제거 - Fedora 26</span><span class="sxs-lookup"><span data-stu-id="f0054-202">Uninstallation - Fedora 26</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="f0054-203">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="f0054-203">Arch Linux</span></span>

<span data-ttu-id="f0054-204">PowerShell은 [Arch Linux][] 사용자 리포지토리(AUR)에 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-204">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="f0054-205">[최신 태깅 릴리스][arch-release]를 사용하여 컴파일할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-205">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="f0054-206">[최신 마스터 커밋][arch-git]에서 컴파일할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-206">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="f0054-207">[최신 릴리스 이진 파일][arch-bin]을 사용하여 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-207">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="f0054-208">AUR의 패키지는 커뮤니티에서 유지 관리되며 공식적인 지원은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-208">Packages in the AUR are community maintained - there is no official support.</span></span>

<span data-ttu-id="f0054-209">AUR에서 패키지를 설치하는 방법에 대한 자세한 내용은 [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) 또는 [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile) 커뮤니티를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f0054-209">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="linux-appimage"></a><span data-ttu-id="f0054-211">Linux AppImage</span><span class="sxs-lookup"><span data-stu-id="f0054-211">Linux AppImage</span></span>

<span data-ttu-id="f0054-212">최신 Linux 배포를 사용하여 [릴리스][] 페이지의 AppImage `powershell-6.0.0-x86_64.AppImage`를 Linux 컴퓨터로 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-212">Using a recent Linux distribution, download the AppImage `powershell-6.0.0-x86_64.AppImage` from the [releases][] page onto the Linux machine.</span></span>

<span data-ttu-id="f0054-213">그런 다음 터미널에서 다음을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-213">Then execute the following in the terminal:</span></span>

```bash
chmod a+x powershell-6.0.0-x86_64.AppImage
./powershell-6.0.0-x86_64.AppImage
```

<span data-ttu-id="f0054-214">[AppImage][]를 사용하면 PowerShell을 설치하지 않고 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-214">The [AppImage][] lets you run PowerShell without installing it.</span></span> <span data-ttu-id="f0054-215">PowerShell 및 종속성(.NET Core의 시스템 종속성 포함)을 하나의 통합 패키지로 묶은 이식 가능한 응용 프로그램입니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-215">It is a portable application that bundles PowerShell and its dependencies (including .NET Core's system dependencies) into one cohesive package.</span></span> <span data-ttu-id="f0054-216">이 패키지는 사용자의 Linux 배포판과 독립적으로 작동하며 단일 이진 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-216">This package works independently of the user's Linux distribution, and is a single binary.</span></span>

[appimage]: http://appimage.org/

## <a name="macos-1012"></a><span data-ttu-id="f0054-218">macOS 10.12</span><span class="sxs-lookup"><span data-stu-id="f0054-218">macOS 10.12</span></span>

### <a name="installation-via-homebrew-preferred---macos-1012"></a><span data-ttu-id="f0054-219">Homebrew를 통해 설치(권장) - macOS 10.12</span><span class="sxs-lookup"><span data-stu-id="f0054-219">Installation via Homebrew (preferred) - macOS 10.12</span></span>

<span data-ttu-id="f0054-220">[Homebrew][brew]는 macOS의 누락 패키지 관리자입니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-220">[Homebrew][brew] is the missing package manager for macOS.</span></span> <span data-ttu-id="f0054-221">`brew` 명령이 없을 경우 [해당 지침][brew]에 따라 Homebrew를 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-221">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

<span data-ttu-id="f0054-222">Homebrew를 설치했으면 PowerShell을 쉽게 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-222">Once you've installed Homebrew, installing PowerShell is easy.</span></span> <span data-ttu-id="f0054-223">먼저 더 많은 패키지를 설치할 수 있도록 [Homebrew-Cask][cask]를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-223">First, install [Homebrew-Cask][cask], so you can install more packages:</span></span>

```sh
brew tap caskroom/cask
```

<span data-ttu-id="f0054-224">이제 PowerShell을 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-224">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="f0054-225">PowerShell의 새 버전이 릴리스되면 Homebrew의 공식을 업데이트하고 PowerShell을 업그레이드하기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-225">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask reinstall powershell
```

> <span data-ttu-id="f0054-226">참고: [Cask의 이 문제](https://github.com/caskroom/homebrew-cask/issues/29301)로 인해 현재 업그레이드를 위해서는 재설치를 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-226">Note: because of [this issue in Cask](https://github.com/caskroom/homebrew-cask/issues/29301), you currently have to do a reinstall to upgrade.</span></span>

[brew]: http://brew.sh/
[cask]: https://caskroom.github.io/

### <a name="installation-via-direct-download---macos-1012"></a><span data-ttu-id="f0054-227">직접 다운로드를 통해 설치 - macOS 10.12</span><span class="sxs-lookup"><span data-stu-id="f0054-227">Installation via Direct Download - macOS 10.12</span></span>

<span data-ttu-id="f0054-228">macOS 10.12를 사용하여 [릴리스][] 페이지의 PKG 패키지 `powershell-6.0.0-osx.10.12-x64.pkg`를 macOS 컴퓨터로 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-228">Using macOS 10.12, download the PKG package `powershell-6.0.0-osx.10.12-x64.pkg` from the [releases][] page onto the macOS machine.</span></span>

<span data-ttu-id="f0054-229">파일을 두 번 클릭하고 메시지를 따르거나 터미널에서 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-229">Either double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-6.0.0-osx.10.12-x64.pkg -target /
```

### <a name="uninstallation---macos-1012"></a><span data-ttu-id="f0054-230">제거 - macOS 10.12</span><span class="sxs-lookup"><span data-stu-id="f0054-230">Uninstallation - macOS 10.12</span></span>

<span data-ttu-id="f0054-231">Homebrew를 사용하여 PowerShell을 설치한 경우에는 제거가 간편합니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-231">If you installed PowerShell with Homebrew, uninstallation is easy:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="f0054-232">직접 다운로드를 통해 PowerShell을 설치한 경우에는 PowerShell을 수동으로 제거해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-232">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="f0054-233">추가 PowerShell 경로(예: 사용자 프로필 경로)를 제거하려면 이 문서의 아래에 나오는 [경로][paths] 섹션을 참조하고 `sudo rm`를 사용하여 원하는 경로를 제거하세요.</span><span class="sxs-lookup"><span data-stu-id="f0054-233">To uninstall the additional PowerShell paths (such as the user profile path) please see the [paths][paths] section below in this document and remove the desired the paths with `sudo rm`.</span></span> <span data-ttu-id="f0054-234">(참고: Homebrew를 사용하여 설치한 경우에는 필요하지 않습니다.)</span><span class="sxs-lookup"><span data-stu-id="f0054-234">(Note: this is not necessary if you installed with Homebrew.)</span></span>

[paths]:#paths

## <a name="kali"></a><span data-ttu-id="f0054-235">Kali</span><span class="sxs-lookup"><span data-stu-id="f0054-235">Kali</span></span>

### <a name="installation"></a><span data-ttu-id="f0054-236">설치</span><span class="sxs-lookup"><span data-stu-id="f0054-236">Installation</span></span>

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

### <a name="run-powershell-in-latest-kali-kali-gnulinux-rolling-without-installing-it"></a><span data-ttu-id="f0054-237">PowerShell을 설치하지 않고 최신 Kali(Kali GNU/Linux 롤링)에서 실행</span><span class="sxs-lookup"><span data-stu-id="f0054-237">Run PowerShell in latest Kali (Kali GNU/Linux Rolling) without installing it</span></span>

```sh
# Grab the latest App Image
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-x86_64.AppImage

# Make executable
chmod a+x powershell-6.0.0-x86_64.AppImage

# Start PowerShell
./powershell-6.0.0-x86_64.AppImage
```

### <a name="uninstallation---kali"></a><span data-ttu-id="f0054-238">제거 - Kali</span><span class="sxs-lookup"><span data-stu-id="f0054-238">Uninstallation - Kali</span></span>

```sh
sudo dpkg -r powershell-6.0.0-x86_64.AppImage
```

## <a name="raspbian"></a><span data-ttu-id="f0054-239">Raspbian</span><span class="sxs-lookup"><span data-stu-id="f0054-239">Raspbian</span></span>

<span data-ttu-id="f0054-240">현재 PowerShell은 Raspbian Stretch에서만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-240">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

### <a name="installation"></a><span data-ttu-id="f0054-241">설치</span><span class="sxs-lookup"><span data-stu-id="f0054-241">Installation</span></span>

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

### <a name="uninstallation---raspbian"></a><span data-ttu-id="f0054-242">제거 - Raspbian</span><span class="sxs-lookup"><span data-stu-id="f0054-242">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="f0054-243">이진 아카이브</span><span class="sxs-lookup"><span data-stu-id="f0054-243">Binary Archives</span></span>

<span data-ttu-id="f0054-244">고급 배포 시나리오를 지원하기 위해 macOS 및 Linux 플랫폼에 PowerShell 이진 `tar.gz` 아카이브가 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-244">PowerShell binary `tar.gz` archives are provided for macOS and Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="f0054-245">종속성</span><span class="sxs-lookup"><span data-stu-id="f0054-245">Dependencies</span></span>

<span data-ttu-id="f0054-246">Linux의 경우 PowerShell이 모든 Linux 배포판을 위한 이식 가능한 이진 파일을 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-246">For Linux, PowerShell builds portable binaries for all Linux distributions.</span></span>
<span data-ttu-id="f0054-247">하지만 .NET Core 런타임의 경우 다양한 배포판에 대한 여러 종속성이 필요하므로 PowerShell가 동일한 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-247">But .NET Core runtime requires different dependencies on different distributions, and hence PowerShell does the same.</span></span>

<span data-ttu-id="f0054-248">다음 차트에서는 공식적으로 지원되는 여러 Linux 배포판에 대한 .NET Core 2.0 종속성을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-248">The following chart shows the .NET Core 2.0 dependencies on different Linux distributions that are officially supported.</span></span>

| <span data-ttu-id="f0054-249">OS</span><span class="sxs-lookup"><span data-stu-id="f0054-249">OS</span></span>                 | <span data-ttu-id="f0054-250">종속성</span><span class="sxs-lookup"><span data-stu-id="f0054-250">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="f0054-251">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="f0054-251">Ubuntu 14.04</span></span>       | <span data-ttu-id="f0054-252">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="f0054-252">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="f0054-253">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="f0054-253">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="f0054-254">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="f0054-254">Ubuntu 16.04</span></span>       | <span data-ttu-id="f0054-255">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="f0054-255">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="f0054-256">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="f0054-256">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="f0054-257">Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="f0054-257">Ubuntu 17.04</span></span>       | <span data-ttu-id="f0054-258">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="f0054-258">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="f0054-259">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="f0054-259">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="f0054-260">Debian 8(Jessie)</span><span class="sxs-lookup"><span data-stu-id="f0054-260">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="f0054-261">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="f0054-261">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="f0054-262">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="f0054-262">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="f0054-263">Debian 9(Stretch)</span><span class="sxs-lookup"><span data-stu-id="f0054-263">Debian 9 (Stretch)</span></span> | <span data-ttu-id="f0054-264">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="f0054-264">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="f0054-265">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="f0054-265">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="f0054-266">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="f0054-266">CentOS 7</span></span> <br> <span data-ttu-id="f0054-267">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="f0054-267">Oracle Linux 7</span></span> <br> <span data-ttu-id="f0054-268">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="f0054-268">RHEL 7</span></span> <br> <span data-ttu-id="f0054-269">OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="f0054-269">OpenSUSE 42.2</span></span> <br> <span data-ttu-id="f0054-270">Fedora 25</span><span class="sxs-lookup"><span data-stu-id="f0054-270">Fedora 25</span></span> | <span data-ttu-id="f0054-271">libunwind, libcurl, openssl-libs, libicu</span><span class="sxs-lookup"><span data-stu-id="f0054-271">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="f0054-272">Fedora 26</span><span class="sxs-lookup"><span data-stu-id="f0054-272">Fedora 26</span></span>          | <span data-ttu-id="f0054-273">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span><span class="sxs-lookup"><span data-stu-id="f0054-273">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="f0054-274">공식적으로 지원되지 않는 Linux 배포판에서 PowerShell 이진 파일을 배포하려면 별도의 단계를 거쳐 대상 OS에 필요한 종속성을 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-274">In order to deploy PowerShell binaries on Linux distributions that are not officially supported, you would need to install the necessary dependencies for the target OS in separate steps.</span></span> <span data-ttu-id="f0054-275">예를 들어 [Amazon Linux dockerfile][amazon-dockerfile]은 먼저 종속성을 설치한 후 Linux `tar.gz` 아카이브를 추출합니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-275">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="f0054-276">설치 - 이진 아카이브</span><span class="sxs-lookup"><span data-stu-id="f0054-276">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="f0054-277">Linux</span><span class="sxs-lookup"><span data-stu-id="f0054-277">Linux</span></span>

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

#### <a name="macos"></a><span data-ttu-id="f0054-278">macOS</span><span class="sxs-lookup"><span data-stu-id="f0054-278">macOS</span></span>

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

### <a name="uninstallation---binary-archives"></a><span data-ttu-id="f0054-279">제거 - 이진 아카이브</span><span class="sxs-lookup"><span data-stu-id="f0054-279">Uninstallation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="f0054-280">Linux</span><span class="sxs-lookup"><span data-stu-id="f0054-280">Linux</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

#### <a name="macos"></a><span data-ttu-id="f0054-281">macOS</span><span class="sxs-lookup"><span data-stu-id="f0054-281">macOS</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="f0054-282">경로</span><span class="sxs-lookup"><span data-stu-id="f0054-282">Paths</span></span>

* <span data-ttu-id="f0054-283">`$PSHOME`은 `/opt/microsoft/powershell/6.0.0/`입니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-283">`$PSHOME` is `/opt/microsoft/powershell/6.0.0/`</span></span>
* <span data-ttu-id="f0054-284">사용자 프로필은 `~/.config/powershell/profile.ps1`에서 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-284">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="f0054-285">기본 프로필은 `$PSHOME/profile.ps1`에서 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-285">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="f0054-286">사용자 프로필은 `~/.local/share/powershell/Modules`에서 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-286">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="f0054-287">공유 모듈은 `/usr/local/share/powershell/Modules`에서 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-287">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="f0054-288">기본 모듈은 `$PSHOME/Modules`에서 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-288">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="f0054-289">PSReadline 기록은 `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`에 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-289">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="f0054-290">프로필은 PowerShell의 호스트별 구성을 계속 사용하므로 기본 호스트별 프로필은 동일한 위치의 `Microsoft.PowerShell_profile.ps1`에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-290">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="f0054-291">Linux 및 macOS에서는 [XDG 기본 디렉터리 사양][xdg-bds]이 계속 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-291">On Linux and macOS, the [XDG Base Directory Specification][xdg-bds] is respected.</span></span>

<span data-ttu-id="f0054-292">macOS는 BSD에서 파생된 것이므로 `/opt` 대신 `/usr/local`이 접두사로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-292">Note that because macOS is a derivation of BSD, instead of `/opt`, the prefix used is `/usr/local`.</span></span> <span data-ttu-id="f0054-293">따라서 `$PSHOME`은 `/usr/local/microsoft/powershell/6.0.0/`이며 symlink는 `/usr/local/bin/pwsh`에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0054-293">Thus, `$PSHOME` is `/usr/local/microsoft/powershell/6.0.0/`, and the symlink is placed at `/usr/local/bin/pwsh`.</span></span>

[릴리스]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html