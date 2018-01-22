# <a name="installing-powershell-core-on-macos-and-linux"></a><span data-ttu-id="cb5b5-101">macOS 및 Linux에서 PowerShell Core 설치</span><span class="sxs-lookup"><span data-stu-id="cb5b5-101">Installing PowerShell Core on macOS and Linux</span></span>

<span data-ttu-id="cb5b5-102">[Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 17.04][u17], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux(RHEL) 7][rhel7], [OpenSUSE 42.2][opensuse], [Fedora 25][fed25], [Fedora 26][fed26], [Arch Linux][arch] 및 [macOS 10.12][mac]를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-102">Supports [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 17.04][u17], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.2][opensuse], [Fedora 25][fed25], [Fedora 26][fed26], [Arch Linux][arch], and [macOS 10.12][mac].</span></span>

<span data-ttu-id="cb5b5-103">공식적으로 지원되지 않는 Linux 배포의 경우 [PowerShell AppImage][lai]를 사용해 보세요.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-103">For Linux distributions that are not officially supported, you can try using the [PowerShell AppImage][lai].</span></span>
<span data-ttu-id="cb5b5-104">또한 Linux [`tar.gz` 보관][tar]을 사용하여 PowerShell 이진 파일을 직접 배포해 볼 수도 있지만 OS에 따라 별도의 단계로 필요한 종속성을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-104">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="cb5b5-105">모든 패키지는 GitHub [릴리스][] 페이지에 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="cb5b5-106">패키지가 설치되면 터미널에서 `pwsh`를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-106">Once the package is installed, run `pwsh` from a terminal.</span></span>

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

## <a name="ubuntu-1404"></a><span data-ttu-id="cb5b5-107">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="cb5b5-107">Ubuntu 14.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1404"></a><span data-ttu-id="cb5b5-108">패키지 리포지토리를 통해 설치 - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="cb5b5-108">Installation via Package Repository - Ubuntu 14.04</span></span>

<span data-ttu-id="cb5b5-109">PowerShell Core for Linux는 간편한 설치(및 업데이트)를 위해 패키지 리포지토리로 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-109">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="cb5b5-110">기본 설정 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-110">This is the preferred method.</span></span>

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

<span data-ttu-id="cb5b5-111">Microsoft 리포지토리를 superuser로 등록하고 나면 그 이후부터는 `sudo apt-get upgrade powershell`을 사용하여 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-111">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1404"></a><span data-ttu-id="cb5b5-112">직접 다운로드를 통해 설치 - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="cb5b5-112">Installation via Direct Download - Ubuntu 14.04</span></span>

<span data-ttu-id="cb5b5-113">[릴리스][] 페이지의 Debian 패키지 `powershell_6.0.0-rc-1.ubuntu.14.04_amd64.deb`를 Ubuntu 컴퓨터에 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-113">Download the Debian package `powershell_6.0.0-rc-1.ubuntu.14.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="cb5b5-114">그런 다음 터미널에서 다음을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-114">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.0-rc-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="cb5b5-115">`dpkg -i`는 종속성 미충족으로 인해 실패하며 다음 명령 `apt-get install -f`가 이를 해결한 후 PowerShell 패키지 구성을 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-115">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1404"></a><span data-ttu-id="cb5b5-116">제거 - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="cb5b5-116">Uninstallation - Ubuntu 14.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a><span data-ttu-id="cb5b5-117">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="cb5b5-117">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="cb5b5-118">패키지 리포지토리를 통해 설치 - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="cb5b5-118">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="cb5b5-119">PowerShell Core for Linux는 간편한 설치(및 업데이트)를 위해 패키지 리포지토리로 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-119">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="cb5b5-120">기본 설정 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-120">This is the preferred method.</span></span>

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

<span data-ttu-id="cb5b5-121">Microsoft 리포지토리를 superuser로 등록하고 나면 그 이후부터는 `sudo apt-get upgrade powershell`을 사용하여 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-121">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="cb5b5-122">직접 다운로드를 통해 설치 - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="cb5b5-122">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="cb5b5-123">[릴리스][] 페이지의 Debian 패키지 `powershell_6.0.0-rc-1.ubuntu.16.04_amd64.deb`를 Ubuntu 컴퓨터에 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-123">Download the Debian package `powershell_6.0.0-rc-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="cb5b5-124">그런 다음 터미널에서 다음을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-124">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.0-rc-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="cb5b5-125">`dpkg -i`는 종속성 미충족으로 인해 실패하며 다음 명령 `apt-get install -f`가 이를 해결한 후 PowerShell 패키지 구성을 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-125">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="cb5b5-126">제거 - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="cb5b5-126">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1704"></a><span data-ttu-id="cb5b5-127">Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="cb5b5-127">Ubuntu 17.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1704"></a><span data-ttu-id="cb5b5-128">패키지 리포지토리를 통해 설치 - Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="cb5b5-128">Installation via Package Repository - Ubuntu 17.04</span></span>

<span data-ttu-id="cb5b5-129">PowerShell Core for Linux는 간편한 설치(및 업데이트)를 위해 패키지 리포지토리로 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-129">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="cb5b5-130">기본 설정 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-130">This is the preferred method.</span></span>

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

<span data-ttu-id="cb5b5-131">Microsoft 리포지토리를 superuser로 등록하고 나면 그 이후부터는 `sudo apt-get upgrade powershell`을 사용하여 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-131">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1704"></a><span data-ttu-id="cb5b5-132">직접 다운로드를 통해 설치 - Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="cb5b5-132">Installation via Direct Download - Ubuntu 17.04</span></span>

<span data-ttu-id="cb5b5-133">[릴리스][] 페이지의 Debian 패키지 `powershell_6.0.0-rc-1.ubuntu.17.04_amd64.deb`를 Ubuntu 컴퓨터에 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-133">Download the Debian package `powershell_6.0.0-rc-1.ubuntu.17.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="cb5b5-134">그런 다음 터미널에서 다음을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-134">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.0-rc-1.ubuntu.17.04_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="cb5b5-135">`dpkg -i`는 종속성 미충족으로 인해 실패하며 다음 명령 `apt-get install -f`가 이를 해결한 후 PowerShell 패키지 구성을 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-135">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1704"></a><span data-ttu-id="cb5b5-136">제거 - Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="cb5b5-136">Uninstallation - Ubuntu 17.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-8"></a><span data-ttu-id="cb5b5-137">Debian 8</span><span class="sxs-lookup"><span data-stu-id="cb5b5-137">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="cb5b5-138">패키지 리포지토리를 통해 설치 - Debian 8</span><span class="sxs-lookup"><span data-stu-id="cb5b5-138">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="cb5b5-139">PowerShell Core for Linux는 간편한 설치(및 업데이트)를 위해 패키지 리포지토리로 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-139">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="cb5b5-140">기본 설정 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-140">This is the preferred method.</span></span>

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

<span data-ttu-id="cb5b5-141">Microsoft 리포지토리를 superuser로 등록하고 나면 그 이후부터는 `sudo apt-get upgrade powershell`을 사용하여 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-141">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-8"></a><span data-ttu-id="cb5b5-142">직접 다운로드를 통해 설치 - Debian 8</span><span class="sxs-lookup"><span data-stu-id="cb5b5-142">Installation via Direct Download - Debian 8</span></span>

<span data-ttu-id="cb5b5-143">[릴리스][] 페이지의 Debian 패키지 `powershell_6.0.0-rc-1.debian.8_amd64.deb`를 Debian 컴퓨터에 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-143">Download the Debian package `powershell_6.0.0-rc-1.debian.8_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="cb5b5-144">그런 다음 터미널에서 다음을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-144">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.0-rc-1.debian.8_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="cb5b5-145">`dpkg -i`는 종속성 미충족으로 인해 실패하며 다음 명령 `apt-get install -f`가 이를 해결한 후 PowerShell 패키지 구성을 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-145">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-8"></a><span data-ttu-id="cb5b5-146">제거 - Debian 8</span><span class="sxs-lookup"><span data-stu-id="cb5b5-146">Uninstallation - Debian 8</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-9"></a><span data-ttu-id="cb5b5-147">Debian 9</span><span class="sxs-lookup"><span data-stu-id="cb5b5-147">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="cb5b5-148">패키지 리포지토리를 통해 설치 - Debian 9</span><span class="sxs-lookup"><span data-stu-id="cb5b5-148">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="cb5b5-149">PowerShell Core for Linux는 간편한 설치(및 업데이트)를 위해 패키지 리포지토리로 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-149">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="cb5b5-150">기본 설정 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-150">This is the preferred method.</span></span>

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

<span data-ttu-id="cb5b5-151">Microsoft 리포지토리를 superuser로 등록하고 나면 그 이후부터는 `sudo apt-get upgrade powershell`을 사용하여 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-151">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="cb5b5-152">직접 다운로드를 통해 설치 - Debian 9</span><span class="sxs-lookup"><span data-stu-id="cb5b5-152">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="cb5b5-153">[릴리스][] 페이지의 Debian 패키지 `powershell_6.0.0-rc-1.debian.9_amd64.deb`를 Debian 컴퓨터에 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-153">Download the Debian package `powershell_6.0.0-rc-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="cb5b5-154">그런 다음 터미널에서 다음을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-154">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.0-rc-1.debian.9_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="cb5b5-155">`dpkg -i`는 종속성 미충족으로 인해 실패하며 다음 명령 `apt-get install -f`가 이를 해결한 후 PowerShell 패키지 구성을 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-155">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-9"></a><span data-ttu-id="cb5b5-156">제거 - Debian 9</span><span class="sxs-lookup"><span data-stu-id="cb5b5-156">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="cb5b5-157">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="cb5b5-157">CentOS 7</span></span>

> <span data-ttu-id="cb5b5-158">이 패키지는 Oracle Linux 7에서도 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-158">This package also works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="cb5b5-159">패키지 리포지토리를 통해 설치(권장) - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="cb5b5-159">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="cb5b5-160">PowerShell Core for Linux는 간편한 설치(및 업데이트)를 위해 공식 Microsoft 리포지토리로 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-160">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="cb5b5-161">Microsoft 리포지토리를 superuser로 등록하고 나면 `sudo yum update powershell`을 사용하여 PowerShell을 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-161">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="cb5b5-162">직접 다운로드를 통해 설치 - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="cb5b5-162">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="cb5b5-163">[CentOS 7][]을 사용하여 [릴리스][] 페이지의 RPM 패키지 `powershell-6.0.0_rc-1.rhel.7.x86_64.rpm`을 CentOS 컴퓨터로 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-163">Using [CentOS 7][], download the RPM package `powershell-6.0.0_rc-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="cb5b5-164">그런 다음 터미널에서 다음을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-164">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.0_rc-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="cb5b5-165">또한 다운로드의 중간 단계 없이 RPM을 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-165">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0-rc/powershell-6.0.0_rc-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="cb5b5-166">제거 - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="cb5b5-166">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="cb5b5-168">Red Hat Enterprise Linux(RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="cb5b5-168">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="cb5b5-169">패키지 리포지토리(권장)를 통해 설치 - Red Hat Enterprise Linux(RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="cb5b5-169">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="cb5b5-170">PowerShell Core for Linux는 간편한 설치(및 업데이트)를 위해 공식 Microsoft 리포지토리로 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-170">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="cb5b5-171">Microsoft 리포지토리를 superuser로 등록하고 나면 `sudo yum update powershell`을 사용하여 PowerShell을 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-171">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="cb5b5-172">직접 다운로드를 통해 설치 - Red Hat Enterprise Linux(RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="cb5b5-172">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="cb5b5-173">[릴리스][] 페이지의 RPM 패키지 `powershell-6.0.0_rc-1.rhel.7.x86_64.rpm`을 Red Hat Enterprise Linux 컴퓨터로 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-173">Download the RPM package `powershell-6.0.0_rc-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="cb5b5-174">그런 다음 터미널에서 다음을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-174">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.0_rc-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="cb5b5-175">또한 다운로드의 중간 단계 없이 RPM을 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-175">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0-rc/powershell-6.0.0_rc-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="cb5b5-176">제거 - Red Hat Enterprise Linux(RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="cb5b5-176">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse-422"></a><span data-ttu-id="cb5b5-177">OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="cb5b5-177">OpenSUSE 42.2</span></span>

> <span data-ttu-id="cb5b5-178">**참고:** PowerShell Core를 설치할 때 OpenSUSE에서 아무 것도 `libcurl`을 제공하지 않는다고 보고할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-178">**Note:** When installing PowerShell Core, OpenSUSE may report that nothing provides `libcurl`.</span></span>
<span data-ttu-id="cb5b5-179">`libcurl`은 지원되는 버전의 OpenSUSE에 이미 설치되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-179">`libcurl` should already be installed on supported versions of OpenSUSE.</span></span>
<span data-ttu-id="cb5b5-180">`zypper search libcurl`을 실행하여 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-180">Run `zypper search libcurl` to confirm.</span></span>
<span data-ttu-id="cb5b5-181">오류에 2개의 '솔루션'이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-181">The error will present 2 'solutions'.</span></span> <span data-ttu-id="cb5b5-182">PowerShell Core 설치를 계속하려면 '솔루션 2'를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-182">Choose 'Solution 2' to continue installing PowerShell Core.</span></span>

### <a name="installation-via-package-repository-preferred---opensuse-422"></a><span data-ttu-id="cb5b5-183">패키지 리포지토리를 통해 설치(권장) - OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="cb5b5-183">Installation via Package Repository (preferred) - OpenSUSE 42.2</span></span>

<span data-ttu-id="cb5b5-184">PowerShell Core for Linux는 간편한 설치(및 업데이트)를 위해 공식 Microsoft 리포지토리로 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-184">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---opensuse-422"></a><span data-ttu-id="cb5b5-185">직접 다운로드를 통해 설치 - OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="cb5b5-185">Installation via Direct Download - OpenSUSE 42.2</span></span>

<span data-ttu-id="cb5b5-186">[릴리스][] 페이지의 RPM 패키지 `powershell-6.0.0_rc-1.rhel.7.x86_64.rpm`을 OpenSUSE 컴퓨터에 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-186">Download the RPM package `powershell-6.0.0_rc-1.rhel.7.x86_64.rpm` from the [releases][] page onto the OpenSUSE machine.</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install powershell-6.0.0_rc-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="cb5b5-187">또한 다운로드의 중간 단계 없이 RPM을 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-187">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0-rc/powershell-6.0.0_rc-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---opensuse-422"></a><span data-ttu-id="cb5b5-188">제거 - OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="cb5b5-188">Uninstallation - OpenSUSE 42.2</span></span>

```sh
sudo zypper remove powershell
```

## <a name="fedora-25"></a><span data-ttu-id="cb5b5-189">Fedora 25</span><span class="sxs-lookup"><span data-stu-id="cb5b5-189">Fedora 25</span></span>

### <a name="installation-via-package-repository-preferred---fedora-25"></a><span data-ttu-id="cb5b5-190">패키지 리포지토리를 통해 설치(권장) - Fedora 25</span><span class="sxs-lookup"><span data-stu-id="cb5b5-190">Installation via Package Repository (preferred) - Fedora 25</span></span>

<span data-ttu-id="cb5b5-191">PowerShell Core for Linux는 간편한 설치(및 업데이트)를 위해 공식 Microsoft 리포지토리로 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-191">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---fedora-25"></a><span data-ttu-id="cb5b5-192">직접 다운로드를 통해 설치 - Fedora 25</span><span class="sxs-lookup"><span data-stu-id="cb5b5-192">Installation via Direct Download - Fedora 25</span></span>

<span data-ttu-id="cb5b5-193">[릴리스][] 페이지의 RPM 패키지 `powershell-6.0.0_rc-1.rhel.7.x86_64.rpm`을 Fedora 컴퓨터에 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-193">Download the RPM package `powershell-6.0.0_rc-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="cb5b5-194">그런 다음 터미널에서 다음을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-194">Then execute the following in the terminal:</span></span>

```sh
sudo dnf install powershell-6.0.0_rc-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="cb5b5-195">또한 다운로드의 중간 단계 없이 RPM을 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-195">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0-rc/powershell-6.0.0_rc-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-25"></a><span data-ttu-id="cb5b5-196">제거 - Fedora 25</span><span class="sxs-lookup"><span data-stu-id="cb5b5-196">Uninstallation - Fedora 25</span></span>

```sh
sudo dnf remove powershell
```

## <a name="fedora-26"></a><span data-ttu-id="cb5b5-197">Fedora 26</span><span class="sxs-lookup"><span data-stu-id="cb5b5-197">Fedora 26</span></span>

### <a name="installation-via-package-repository-preferred---fedora-26"></a><span data-ttu-id="cb5b5-198">패키지 리포지토리를 통해 설치(권장) - Fedora 26</span><span class="sxs-lookup"><span data-stu-id="cb5b5-198">Installation via Package Repository (preferred) - Fedora 26</span></span>

<span data-ttu-id="cb5b5-199">PowerShell Core for Linux는 간편한 설치(및 업데이트)를 위해 공식 Microsoft 리포지토리로 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-199">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---fedora-26"></a><span data-ttu-id="cb5b5-200">직접 다운로드를 통해 설치 - Fedora 26</span><span class="sxs-lookup"><span data-stu-id="cb5b5-200">Installation via Direct Download - Fedora 26</span></span>

<span data-ttu-id="cb5b5-201">[릴리스][] 페이지의 RPM 패키지 `powershell-6.0.0_rc-1.rhel.7.x86_64.rpm`을 Fedora 컴퓨터에 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-201">Download the RPM package `powershell-6.0.0_rc-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="cb5b5-202">그런 다음 터미널에서 다음을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-202">Then execute the following in the terminal:</span></span>

```sh
sudo dnf update
sudo dnf install compat-openssl10
sudo dnf install powershell-6.0.0_rc-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="cb5b5-203">또한 다운로드의 중간 단계 없이 RPM을 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-203">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf update
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0-rc/powershell-6.0.0_rc-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-26"></a><span data-ttu-id="cb5b5-204">제거 - Fedora 26</span><span class="sxs-lookup"><span data-stu-id="cb5b5-204">Uninstallation - Fedora 26</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="cb5b5-205">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="cb5b5-205">Arch Linux</span></span>

<span data-ttu-id="cb5b5-206">PowerShell은 [Arch Linux][] 사용자 리포지토리(AUR)에 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-206">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="cb5b5-207">[최신 태깅 릴리스][arch-release]를 사용하여 컴파일할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-207">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="cb5b5-208">[최신 마스터 커밋][arch-git]에서 컴파일할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-208">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="cb5b5-209">[최신 릴리스 이진 파일][arch-bin]을 사용하여 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-209">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="cb5b5-210">AUR의 패키지는 커뮤니티에서 유지 관리되며 공식적인 지원은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-210">Packages in the AUR are community maintained - there is no official support.</span></span>

<span data-ttu-id="cb5b5-211">AUR에서 패키지를 설치하는 방법에 대한 자세한 내용은 [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) 또는 [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile) 커뮤니티를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-211">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="linux-appimage"></a><span data-ttu-id="cb5b5-213">Linux AppImage</span><span class="sxs-lookup"><span data-stu-id="cb5b5-213">Linux AppImage</span></span>

<span data-ttu-id="cb5b5-214">최신 Linux 배포를 사용하여 [릴리스][] 페이지의 AppImage `powershell-6.0.0-rc-x86_64.AppImage`를 Linux 컴퓨터로 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-214">Using a recent Linux distribution, download the AppImage `powershell-6.0.0-rc-x86_64.AppImage` from the [releases][] page onto the Linux machine.</span></span>

<span data-ttu-id="cb5b5-215">그런 다음 터미널에서 다음을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-215">Then execute the following in the terminal:</span></span>

```bash
chmod a+x powershell-6.0.0-rc-x86_64.AppImage
./powershell-6.0.0-rc-x86_64.AppImage
```

<span data-ttu-id="cb5b5-216">[AppImage][]를 사용하면 PowerShell을 설치하지 않고 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-216">The [AppImage][] lets you run PowerShell without installing it.</span></span>
<span data-ttu-id="cb5b5-217">PowerShell 및 종속성(.NET Core의 시스템 종속성 포함)을 하나의 통합 패키지로 묶은 이식 가능한 응용 프로그램입니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-217">It is a portable application that bundles PowerShell and its dependencies (including .NET Core's system dependencies) into one cohesive package.</span></span>
<span data-ttu-id="cb5b5-218">이 패키지는 사용자의 Linux 배포판과 독립적으로 작동하며 단일 이진 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-218">This package works independently of the user's Linux distribution, and is a single binary.</span></span>

[appimage]: http://appimage.org/

## <a name="macos-1012"></a><span data-ttu-id="cb5b5-220">macOS 10.12</span><span class="sxs-lookup"><span data-stu-id="cb5b5-220">macOS 10.12</span></span>

### <a name="installation-via-homebrew-preferred---macos-1012"></a><span data-ttu-id="cb5b5-221">Homebrew를 통해 설치(권장) - macOS 10.12</span><span class="sxs-lookup"><span data-stu-id="cb5b5-221">Installation via Homebrew (preferred) - macOS 10.12</span></span>

<span data-ttu-id="cb5b5-222">[Homebrew][brew]는 macOS의 누락 패키지 관리자입니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-222">[Homebrew][brew] is the missing package manager for macOS.</span></span>
<span data-ttu-id="cb5b5-223">`brew` 명령이 없을 경우 [해당 지침][brew]에 따라 Homebrew를 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-223">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

<span data-ttu-id="cb5b5-224">Homebrew를 설치했으면 PowerShell을 쉽게 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-224">Once you've installed Homebrew, installing PowerShell is easy.</span></span>
<span data-ttu-id="cb5b5-225">먼저 더 많은 패키지를 설치할 수 있도록 [Homebrew-Cask][cask]를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-225">First, install [Homebrew-Cask][cask], so you can install more packages:</span></span>

```sh
brew tap caskroom/cask
```

<span data-ttu-id="cb5b5-226">이제 PowerShell을 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-226">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="cb5b5-227">PowerShell의 새 버전이 릴리스되면 Homebrew의 공식을 업데이트하고 PowerShell을 업그레이드하기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-227">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask reinstall powershell
```

> <span data-ttu-id="cb5b5-228">참고: [Cask의 이 문제](https://github.com/caskroom/homebrew-cask/issues/29301)로 인해 현재 업그레이드를 위해서는 재설치를 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-228">Note: because of [this issue in Cask](https://github.com/caskroom/homebrew-cask/issues/29301), you currently have to do a reinstall to upgrade.</span></span>

[brew]: http://brew.sh/
[cask]: https://caskroom.github.io/

### <a name="installation-via-direct-download---macos-1012"></a><span data-ttu-id="cb5b5-229">직접 다운로드를 통해 설치 - macOS 10.12</span><span class="sxs-lookup"><span data-stu-id="cb5b5-229">Installation via Direct Download - macOS 10.12</span></span>

<span data-ttu-id="cb5b5-230">macOS 10.12를 사용하여 [릴리스][] 페이지의 PKG 패키지 `powershell-6.0.0-rc-osx.10.12-x64.pkg`를 macOS 컴퓨터로 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-230">Using macOS 10.12, download the PKG package `powershell-6.0.0-rc-osx.10.12-x64.pkg` from the [releases][] page onto the macOS machine.</span></span>

<span data-ttu-id="cb5b5-231">파일을 두 번 클릭하고 메시지를 따르거나 터미널에서 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-231">Either double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-6.0.0-rc-osx.10.12-x64.pkg -target /
```

### <a name="uninstallation---macos-1012"></a><span data-ttu-id="cb5b5-232">제거 - macOS 10.12</span><span class="sxs-lookup"><span data-stu-id="cb5b5-232">Uninstallation - macOS 10.12</span></span>

<span data-ttu-id="cb5b5-233">Homebrew를 사용하여 PowerShell을 설치한 경우에는 제거가 간편합니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-233">If you installed PowerShell with Homebrew, uninstallation is easy:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="cb5b5-234">직접 다운로드를 통해 PowerShell을 설치한 경우에는 PowerShell을 수동으로 제거해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-234">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="cb5b5-235">추가 PowerShell 경로(예: 사용자 프로필 경로)를 제거하려면 이 문서의 아래에 나오는 [경로][paths] 섹션을 참조하고 `sudo rm`를 사용하여 원하는 경로를 제거하세요.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-235">To uninstall the additional PowerShell paths (such as the user profile path) please see the [paths][paths] section below in this document and remove the desired the paths with `sudo rm`.</span></span>
<span data-ttu-id="cb5b5-236">(참고: Homebrew를 사용하여 설치한 경우에는 필요하지 않습니다.)</span><span class="sxs-lookup"><span data-stu-id="cb5b5-236">(Note: this is not necessary if you installed with Homebrew.)</span></span>

[paths]:#paths

## <a name="kali"></a><span data-ttu-id="cb5b5-237">Kali</span><span class="sxs-lookup"><span data-stu-id="cb5b5-237">Kali</span></span>

### <a name="installation"></a><span data-ttu-id="cb5b5-238">설치</span><span class="sxs-lookup"><span data-stu-id="cb5b5-238">Installation</span></span>

```sh
# Install prerequisites
apt-get install libunwind8 libicu55
wget http://security.debian.org/debian-security/pool/updates/main/o/openssl/libssl1.0.0_1.0.1t-1+deb8u6_amd64.deb
dpkg -i libssl1.0.0_1.0.1t-1+deb8u6_amd64.deb

# Install PowerShell
dpkg -i powershell_6.0.0-rc-1.ubuntu.16.04_amd64.deb

# Start PowerShell
pwsh
```

### <a name="run-powershell-in-latest-kali-kali-gnulinux-rolling-without-installing-it"></a><span data-ttu-id="cb5b5-239">PowerShell을 설치하지 않고 최신 Kali(Kali GNU/Linux 롤링)에서 실행</span><span class="sxs-lookup"><span data-stu-id="cb5b5-239">Run PowerShell in latest Kali (Kali GNU/Linux Rolling) without installing it</span></span>

```sh
# Grab the latest App Image
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0-rc/powershell-6.0.0-rc-x86_64.AppImage

# Make executable
chmod a+x powershell-6.0.0-rc-x86_64.AppImage

# Start PowerShell
./powershell-6.0.0-rc-x86_64.AppImage
```

### <a name="uninstallation---kali"></a><span data-ttu-id="cb5b5-240">제거 - Kali</span><span class="sxs-lookup"><span data-stu-id="cb5b5-240">Uninstallation - Kali</span></span>

```sh
dpkg -r powershell_6.0.0-rc-1.ubuntu.16.04_amd64.deb
```

## <a name="raspbian"></a><span data-ttu-id="cb5b5-241">Raspbian</span><span class="sxs-lookup"><span data-stu-id="cb5b5-241">Raspbian</span></span>

<span data-ttu-id="cb5b5-242">현재 PowerShell은 Raspbian Stretch에서만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-242">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

### <a name="installation"></a><span data-ttu-id="cb5b5-243">설치</span><span class="sxs-lookup"><span data-stu-id="cb5b5-243">Installation</span></span>

```sh
# Install prerequisites
sudo apt-get install libunwind8

# Grab the latest tar.gz
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0-rc/powershell-6.0.0-rc-linux-arm32.tar.gz

# Make folder to put powershell
mkdir ~/powershell

# Unpack the tar.gz file
tar -xvf ./powershell-6.0.0-rc-linux-arm32.tar.gz -C ~/powershell

# Start PowerShell
~/powershell/pwsh
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="cb5b5-244">제거 - Raspbian</span><span class="sxs-lookup"><span data-stu-id="cb5b5-244">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="cb5b5-245">이진 아카이브</span><span class="sxs-lookup"><span data-stu-id="cb5b5-245">Binary Archives</span></span>

<span data-ttu-id="cb5b5-246">고급 배포 시나리오를 지원하기 위해 macOS 및 Linux 플랫폼에 PowerShell 이진 `tar.gz` 아카이브가 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-246">PowerShell binary `tar.gz` archives are provided for macOS and Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="cb5b5-247">종속성</span><span class="sxs-lookup"><span data-stu-id="cb5b5-247">Dependencies</span></span>

<span data-ttu-id="cb5b5-248">Linux의 경우 PowerShell이 모든 Linux 배포판을 위한 이식 가능한 이진 파일을 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-248">For Linux, PowerShell builds portable binaries for all Linux distributions.</span></span>
<span data-ttu-id="cb5b5-249">하지만 .NET Core 런타임의 경우 다양한 배포판에 대한 여러 종속성이 필요하므로 PowerShell가 동일한 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-249">But .NET Core runtime requires different dependencies on different distributions, and hence PowerShell does the same.</span></span>

<span data-ttu-id="cb5b5-250">다음 차트에서는 공식적으로 지원되는 여러 Linux 배포판에 대한 .NET Core 2.0 종속성을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-250">The following chart shows the .NET Core 2.0 dependencies on different Linux distributions that are officially supported.</span></span>

| <span data-ttu-id="cb5b5-251">OS</span><span class="sxs-lookup"><span data-stu-id="cb5b5-251">OS</span></span>                 | <span data-ttu-id="cb5b5-252">종속성</span><span class="sxs-lookup"><span data-stu-id="cb5b5-252">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="cb5b5-253">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="cb5b5-253">Ubuntu 14.04</span></span>       | <span data-ttu-id="cb5b5-254">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="cb5b5-254">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="cb5b5-255">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="cb5b5-255">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="cb5b5-256">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="cb5b5-256">Ubuntu 16.04</span></span>       | <span data-ttu-id="cb5b5-257">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="cb5b5-257">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="cb5b5-258">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="cb5b5-258">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="cb5b5-259">Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="cb5b5-259">Ubuntu 17.04</span></span>       | <span data-ttu-id="cb5b5-260">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="cb5b5-260">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="cb5b5-261">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="cb5b5-261">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="cb5b5-262">Debian 8(Jessie)</span><span class="sxs-lookup"><span data-stu-id="cb5b5-262">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="cb5b5-263">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="cb5b5-263">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="cb5b5-264">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="cb5b5-264">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="cb5b5-265">Debian 9(Stretch)</span><span class="sxs-lookup"><span data-stu-id="cb5b5-265">Debian 9 (Stretch)</span></span> | <span data-ttu-id="cb5b5-266">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="cb5b5-266">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="cb5b5-267">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="cb5b5-267">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="cb5b5-268">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="cb5b5-268">CentOS 7</span></span> <br> <span data-ttu-id="cb5b5-269">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="cb5b5-269">Oracle Linux 7</span></span> <br> <span data-ttu-id="cb5b5-270">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="cb5b5-270">RHEL 7</span></span> <br> <span data-ttu-id="cb5b5-271">OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="cb5b5-271">OpenSUSE 42.2</span></span> <br> <span data-ttu-id="cb5b5-272">Fedora 25</span><span class="sxs-lookup"><span data-stu-id="cb5b5-272">Fedora 25</span></span> | <span data-ttu-id="cb5b5-273">libunwind, libcurl, openssl-libs, libicu</span><span class="sxs-lookup"><span data-stu-id="cb5b5-273">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="cb5b5-274">Fedora 26</span><span class="sxs-lookup"><span data-stu-id="cb5b5-274">Fedora 26</span></span>          | <span data-ttu-id="cb5b5-275">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span><span class="sxs-lookup"><span data-stu-id="cb5b5-275">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="cb5b5-276">공식적으로 지원되지 않는 Linux 배포판에서 PowerShell 이진 파일을 배포하려면 별도의 단계를 거쳐 대상 OS에 필요한 종속성을 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-276">In order to deploy PowerShell binaries on Linux distributions that are not officially supported, you would need to install the necessary dependencies for the target OS in separate steps.</span></span>
<span data-ttu-id="cb5b5-277">예를 들어 [Amazon Linux dockerfile][amazon-dockerfile]은 먼저 종속성을 설치한 후 Linux `tar.gz` 아카이브를 추출합니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-277">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="cb5b5-278">설치 - 이진 아카이브</span><span class="sxs-lookup"><span data-stu-id="cb5b5-278">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="cb5b5-279">Linux</span><span class="sxs-lookup"><span data-stu-id="cb5b5-279">Linux</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.0.0-rc/powershell-6.0.0-rc-linux-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/6.0.0-rc

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.0.0-rc

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/6.0.0-rc/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/6.0.0-rc/pwsh /usr/bin/pwsh
```

#### <a name="macos"></a><span data-ttu-id="cb5b5-280">macOS</span><span class="sxs-lookup"><span data-stu-id="cb5b5-280">macOS</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.0.0-rc/powershell-6.0.0-rc-osx-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /usr/local/microsoft/powershell/6.0.0-rc

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /usr/local/microsoft/powershell/6.0.0-rc

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/6.0.0-rc/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /usr/local/microsoft/powershell/6.0.0-rc/pwsh /usr/local/bin/pwsh
```

### <a name="uninstallation---binary-archives"></a><span data-ttu-id="cb5b5-281">제거 - 이진 아카이브</span><span class="sxs-lookup"><span data-stu-id="cb5b5-281">Uninstallation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="cb5b5-282">Linux</span><span class="sxs-lookup"><span data-stu-id="cb5b5-282">Linux</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

#### <a name="macos"></a><span data-ttu-id="cb5b5-283">macOS</span><span class="sxs-lookup"><span data-stu-id="cb5b5-283">macOS</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="cb5b5-284">경로</span><span class="sxs-lookup"><span data-stu-id="cb5b5-284">Paths</span></span>

* <span data-ttu-id="cb5b5-285">`$PSHOME`은 `/opt/microsoft/powershell/6.0.0-rc/`입니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-285">`$PSHOME` is `/opt/microsoft/powershell/6.0.0-rc/`</span></span>
* <span data-ttu-id="cb5b5-286">사용자 프로필은 `~/.config/powershell/profile.ps1`에서 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-286">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="cb5b5-287">기본 프로필은 `$PSHOME/profile.ps1`에서 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-287">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="cb5b5-288">사용자 프로필은 `~/.local/share/powershell/Modules`에서 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-288">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="cb5b5-289">공유 모듈은 `/usr/local/share/powershell/Modules`에서 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-289">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="cb5b5-290">기본 모듈은 `$PSHOME/Modules`에서 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-290">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="cb5b5-291">PSReadline 기록은 `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`에 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-291">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="cb5b5-292">프로필은 PowerShell의 호스트별 구성을 계속 사용하므로 기본 호스트별 프로필은 동일한 위치의 `Microsoft.PowerShell_profile.ps1`에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-292">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="cb5b5-293">Linux 및 macOS에서는 [XDG 기본 디렉터리 사양][xdg-bds]이 계속 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-293">On Linux and macOS, the [XDG Base Directory Specification][xdg-bds] is respected.</span></span>

<span data-ttu-id="cb5b5-294">macOS는 BSD에서 파생된 것이므로 `/opt` 대신 `/usr/local`이 접두사로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-294">Note that because macOS is a derivation of BSD, instead of `/opt`, the prefix used is `/usr/local`.</span></span>
<span data-ttu-id="cb5b5-295">따라서 `$PSHOME`은 `/usr/local/microsoft/powershell/6.0.0-rc/`이며 symlink는 `/usr/local/bin/pwsh`에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb5b5-295">Thus, `$PSHOME` is `/usr/local/microsoft/powershell/6.0.0-rc/`, and the symlink is placed at `/usr/local/bin/pwsh`.</span></span>

[릴리스]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
