# <a name="installing-powershell-core-on-linux"></a><span data-ttu-id="115de-101">Linux에서 PowerShell Core 설치</span><span class="sxs-lookup"><span data-stu-id="115de-101">Installing PowerShell Core on Linux</span></span>

<span data-ttu-id="115de-102">[Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 17.04][u17], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux(RHEL) 7][rhel7], [OpenSUSE 42.2][opensuse], [Fedora 25][fed25], [Fedora 26][fed26] 및 [Arch Linux][arch]를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="115de-102">Supports [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 17.04][u17], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.2][opensuse], [Fedora 25][fed25], [Fedora 26][fed26], and [Arch Linux][arch].</span></span>

<span data-ttu-id="115de-103">공식적으로 지원되지 않는 Linux 배포의 경우 [PowerShell AppImage][lai]를 사용해 보세요.</span><span class="sxs-lookup"><span data-stu-id="115de-103">For Linux distributions that are not officially supported, you can try using the [PowerShell AppImage][lai].</span></span>
<span data-ttu-id="115de-104">또한 Linux [`tar.gz` 보관][tar]을 사용하여 PowerShell 이진 파일을 직접 배포해 볼 수도 있지만 OS에 따라 별도의 단계로 필요한 종속성을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="115de-104">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="115de-105">모든 패키지는 GitHub [릴리스][] 페이지에 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="115de-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="115de-106">패키지가 설치되면 터미널에서 `pwsh`를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="115de-106">Once the package is installed, run `pwsh` from a terminal.</span></span>

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
[tar]: #binary-archives

## <a name="ubuntu-1404"></a><span data-ttu-id="115de-107">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="115de-107">Ubuntu 14.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1404"></a><span data-ttu-id="115de-108">패키지 리포지토리를 통해 설치 - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="115de-108">Installation via Package Repository - Ubuntu 14.04</span></span>

<span data-ttu-id="115de-109">PowerShell Core for Linux는 간편한 설치(및 업데이트)를 위해 패키지 리포지토리로 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="115de-109">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="115de-110">기본 설정 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="115de-110">This is the preferred method.</span></span>

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

<span data-ttu-id="115de-111">슈퍼 사용자로 Microsoft 리포지토리를 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="115de-111">As superuser, register the Microsoft repository.</span></span>
<span data-ttu-id="115de-112">그 이후에는 `sudo apt-get upgrade powershell`을 사용하여 설치를 업데이트하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="115de-112">From then on, you just need to use `sudo apt-get upgrade powershell` to update the installation.</span></span>

### <a name="installation-via-direct-download---ubuntu-1404"></a><span data-ttu-id="115de-113">직접 다운로드를 통해 설치 - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="115de-113">Installation via Direct Download - Ubuntu 14.04</span></span>

<span data-ttu-id="115de-114">[릴리스][] 페이지의 Debian 패키지 `powershell_6.0.2-1.ubuntu.14.04_amd64.deb`를 Ubuntu 컴퓨터에 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="115de-114">Download the Debian package `powershell_6.0.2-1.ubuntu.14.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="115de-115">그런 다음 터미널에서 다음을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="115de-115">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="115de-116">`dpkg -i`는 종속성 미충족으로 인해 실패하며 다음 명령 `apt-get install -f`가 이를 해결한 후 PowerShell 패키지 구성을 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="115de-116">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1404"></a><span data-ttu-id="115de-117">제거 - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="115de-117">Uninstallation - Ubuntu 14.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a><span data-ttu-id="115de-118">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="115de-118">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="115de-119">패키지 리포지토리를 통해 설치 - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="115de-119">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="115de-120">PowerShell Core for Linux는 간편한 설치(및 업데이트)를 위해 패키지 리포지토리로 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="115de-120">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="115de-121">기본 설정 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="115de-121">This is the preferred method.</span></span>

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

<span data-ttu-id="115de-122">Microsoft 리포지토리를 superuser로 등록하고 나면 그 이후부터는 `sudo apt-get upgrade powershell`을 사용하여 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="115de-122">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="115de-123">직접 다운로드를 통해 설치 - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="115de-123">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="115de-124">[릴리스][] 페이지의 Debian 패키지 `powershell_6.0.2-1.ubuntu.16.04_amd64.deb`를 Ubuntu 컴퓨터에 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="115de-124">Download the Debian package `powershell_6.0.2-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="115de-125">그런 다음 터미널에서 다음을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="115de-125">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="115de-126">`dpkg -i`는 종속성 미충족으로 인해 실패하며 다음 명령 `apt-get install -f`가 이를 해결한 후 PowerShell 패키지 구성을 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="115de-126">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="115de-127">제거 - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="115de-127">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1704"></a><span data-ttu-id="115de-128">Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="115de-128">Ubuntu 17.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1704"></a><span data-ttu-id="115de-129">패키지 리포지토리를 통해 설치 - Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="115de-129">Installation via Package Repository - Ubuntu 17.04</span></span>

<span data-ttu-id="115de-130">PowerShell Core for Linux는 간편한 설치(및 업데이트)를 위해 패키지 리포지토리로 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="115de-130">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="115de-131">기본 설정 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="115de-131">This is the preferred method.</span></span>

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

<span data-ttu-id="115de-132">Microsoft 리포지토리를 superuser로 등록하고 나면 그 이후부터는 `sudo apt-get upgrade powershell`을 사용하여 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="115de-132">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1704"></a><span data-ttu-id="115de-133">직접 다운로드를 통해 설치 - Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="115de-133">Installation via Direct Download - Ubuntu 17.04</span></span>

<span data-ttu-id="115de-134">[릴리스][] 페이지의 Debian 패키지 `powershell_6.0.2-1.ubuntu.17.04_amd64.deb`를 Ubuntu 컴퓨터에 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="115de-134">Download the Debian package `powershell_6.0.2-1.ubuntu.17.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="115de-135">그런 다음 터미널에서 다음을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="115de-135">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.17.04_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="115de-136">`dpkg -i`는 종속성 미충족으로 인해 실패하며 다음 명령 `apt-get install -f`가 이를 해결한 후 PowerShell 패키지 구성을 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="115de-136">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1704"></a><span data-ttu-id="115de-137">제거 - Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="115de-137">Uninstallation - Ubuntu 17.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-8"></a><span data-ttu-id="115de-138">Debian 8</span><span class="sxs-lookup"><span data-stu-id="115de-138">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="115de-139">패키지 리포지토리를 통해 설치 - Debian 8</span><span class="sxs-lookup"><span data-stu-id="115de-139">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="115de-140">PowerShell Core for Linux는 간편한 설치(및 업데이트)를 위해 패키지 리포지토리로 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="115de-140">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="115de-141">기본 설정 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="115de-141">This is the preferred method.</span></span>

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

<span data-ttu-id="115de-142">Microsoft 리포지토리를 superuser로 등록하고 나면 그 이후부터는 `sudo apt-get upgrade powershell`을 사용하여 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="115de-142">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-8"></a><span data-ttu-id="115de-143">직접 다운로드를 통해 설치 - Debian 8</span><span class="sxs-lookup"><span data-stu-id="115de-143">Installation via Direct Download - Debian 8</span></span>

<span data-ttu-id="115de-144">[릴리스][] 페이지의 Debian 패키지 `powershell_6.0.2-1.debian.8_amd64.deb`를 Debian 컴퓨터에 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="115de-144">Download the Debian package `powershell_6.0.2-1.debian.8_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="115de-145">그런 다음 터미널에서 다음을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="115de-145">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.debian.8_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="115de-146">`dpkg -i`는 충족되지 않은 종속성으로 인해 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="115de-146">Please note that `dpkg -i` will fail with unmet dependencies.</span></span>
> <span data-ttu-id="115de-147">다음 명령인 `apt-get install -f`는 이러한 종속성을 해결하고 PowerShell 패키지 구성을 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="115de-147">The next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-8"></a><span data-ttu-id="115de-148">제거 - Debian 8</span><span class="sxs-lookup"><span data-stu-id="115de-148">Uninstallation - Debian 8</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-9"></a><span data-ttu-id="115de-149">Debian 9</span><span class="sxs-lookup"><span data-stu-id="115de-149">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="115de-150">패키지 리포지토리를 통해 설치 - Debian 9</span><span class="sxs-lookup"><span data-stu-id="115de-150">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="115de-151">PowerShell Core for Linux는 간편한 설치(및 업데이트)를 위해 패키지 리포지토리로 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="115de-151">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="115de-152">기본 설정 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="115de-152">This is the preferred method.</span></span>

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

<span data-ttu-id="115de-153">Microsoft 리포지토리를 superuser로 등록하고 나면 그 이후부터는 `sudo apt-get upgrade powershell`을 사용하여 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="115de-153">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="115de-154">직접 다운로드를 통해 설치 - Debian 9</span><span class="sxs-lookup"><span data-stu-id="115de-154">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="115de-155">[릴리스][] 페이지의 Debian 패키지 `powershell_6.0.2-1.debian.9_amd64.deb`를 Debian 컴퓨터에 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="115de-155">Download the Debian package `powershell_6.0.2-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="115de-156">그런 다음 터미널에서 다음을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="115de-156">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.debian.9_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="115de-157">`dpkg -i`는 충족되지 않은 종속성으로 인해 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="115de-157">Please note that `dpkg -i` will fail with unmet dependencies.</span></span>
> <span data-ttu-id="115de-158">다음 명령인 `apt-get install -f`는 이러한 종속성을 해결하고 PowerShell 패키지 구성을 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="115de-158">The next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-9"></a><span data-ttu-id="115de-159">제거 - Debian 9</span><span class="sxs-lookup"><span data-stu-id="115de-159">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="115de-160">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="115de-160">CentOS 7</span></span>

> <span data-ttu-id="115de-161">이 패키지는 Oracle Linux 7에서도 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="115de-161">This package also works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="115de-162">패키지 리포지토리를 통해 설치(권장) - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="115de-162">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="115de-163">PowerShell Core for Linux는 간편한 설치(및 업데이트)를 위해 공식 Microsoft 리포지토리로 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="115de-163">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="115de-164">Microsoft 리포지토리를 superuser로 등록하고 나면 `sudo yum update powershell`을 사용하여 PowerShell을 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="115de-164">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="115de-165">직접 다운로드를 통해 설치 - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="115de-165">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="115de-166">[CentOS 7][]을 사용하여 [릴리스][] 페이지의 RPM 패키지 `powershell-6.0.2-1.rhel.7.x86_64.rpm`을 CentOS 컴퓨터로 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="115de-166">Using [CentOS 7][], download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="115de-167">그런 다음 터미널에서 다음을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="115de-167">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="115de-168">또한 다운로드의 중간 단계 없이 RPM을 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="115de-168">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="115de-169">제거 - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="115de-169">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="115de-171">Red Hat Enterprise Linux(RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="115de-171">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="115de-172">패키지 리포지토리(권장)를 통해 설치 - Red Hat Enterprise Linux(RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="115de-172">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="115de-173">PowerShell Core for Linux는 간편한 설치(및 업데이트)를 위해 공식 Microsoft 리포지토리로 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="115de-173">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="115de-174">Microsoft 리포지토리를 superuser로 등록하고 나면 `sudo yum update powershell`을 사용하여 PowerShell을 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="115de-174">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="115de-175">직접 다운로드를 통해 설치 - Red Hat Enterprise Linux(RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="115de-175">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="115de-176">[릴리스][] 페이지의 RPM 패키지 `powershell-6.0.2-1.rhel.7.x86_64.rpm`을 Red Hat Enterprise Linux 컴퓨터로 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="115de-176">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="115de-177">그런 다음 터미널에서 다음을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="115de-177">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="115de-178">또한 다운로드의 중간 단계 없이 RPM을 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="115de-178">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="115de-179">제거 - Red Hat Enterprise Linux(RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="115de-179">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse-422"></a><span data-ttu-id="115de-180">OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="115de-180">OpenSUSE 42.2</span></span>

> [!NOTE]
> <span data-ttu-id="115de-181">PowerShell Core를 설치할 때 `zypper`에서 다음 오류를 보고할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="115de-181">When installing PowerShell Core, `zypper` may report the following error:</span></span>
>
> ```Output
> Problem: nothing provides libcurl needed by powershell-6.0.1-1.rhel.7.x86_64
>  Solution 1: do not install powershell-6.0.1-1.rhel.7.x86_64
>  Solution 2: break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies
> ```
>
> <span data-ttu-id="115de-182">이 경우 다음 명령이 설치된 대로 `libcurl4` 패키지를 보여 주는지 확인하여 호환되는 `libcurl` 라이브러리가 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="115de-182">In this case, verify that a compatible `libcurl` library is present by checking that the following command shows the `libcurl4` package as installed:</span></span>
>
> ```sh
> zypper search --file-list --match-exact '/usr/lib64/libcurl.so.4'
> ```
>
> <span data-ttu-id="115de-183">그런 다음, PowerShell 패키지를 설치할 때 `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` 솔루션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="115de-183">Then choose the `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` solution when installing the PowerShell package.</span></span>

### <a name="installation-via-package-repository-preferred---opensuse-422"></a><span data-ttu-id="115de-184">패키지 리포지토리를 통해 설치(권장) - OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="115de-184">Installation via Package Repository (preferred) - OpenSUSE 42.2</span></span>

<span data-ttu-id="115de-185">PowerShell Core for Linux는 간편한 설치(및 업데이트)를 위해 공식 Microsoft 리포지토리로 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="115de-185">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---opensuse-422"></a><span data-ttu-id="115de-186">직접 다운로드를 통해 설치 - OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="115de-186">Installation via Direct Download - OpenSUSE 42.2</span></span>

<span data-ttu-id="115de-187">[릴리스][] 페이지의 RPM 패키지 `powershell-6.0.2-1.rhel.7.x86_64.rpm`을 OpenSUSE 컴퓨터에 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="115de-187">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the OpenSUSE machine.</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="115de-188">또한 다운로드의 중간 단계 없이 RPM을 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="115de-188">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---opensuse-422"></a><span data-ttu-id="115de-189">제거 - OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="115de-189">Uninstallation - OpenSUSE 42.2</span></span>

```sh
sudo zypper remove powershell
```

## <a name="fedora-25"></a><span data-ttu-id="115de-190">Fedora 25</span><span class="sxs-lookup"><span data-stu-id="115de-190">Fedora 25</span></span>

### <a name="installation-via-package-repository-preferred---fedora-25"></a><span data-ttu-id="115de-191">패키지 리포지토리를 통해 설치(권장) - Fedora 25</span><span class="sxs-lookup"><span data-stu-id="115de-191">Installation via Package Repository (preferred) - Fedora 25</span></span>

<span data-ttu-id="115de-192">PowerShell Core for Linux는 간편한 설치(및 업데이트)를 위해 공식 Microsoft 리포지토리로 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="115de-192">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---fedora-25"></a><span data-ttu-id="115de-193">직접 다운로드를 통해 설치 - Fedora 25</span><span class="sxs-lookup"><span data-stu-id="115de-193">Installation via Direct Download - Fedora 25</span></span>

<span data-ttu-id="115de-194">[릴리스][] 페이지의 RPM 패키지 `powershell-6.0.2-1.rhel.7.x86_64.rpm`을 Fedora 컴퓨터에 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="115de-194">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="115de-195">그런 다음 터미널에서 다음을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="115de-195">Then execute the following in the terminal:</span></span>

```sh
sudo dnf install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="115de-196">또한 다운로드의 중간 단계 없이 RPM을 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="115de-196">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-25"></a><span data-ttu-id="115de-197">제거 - Fedora 25</span><span class="sxs-lookup"><span data-stu-id="115de-197">Uninstallation - Fedora 25</span></span>

```sh
sudo dnf remove powershell
```

## <a name="fedora-26"></a><span data-ttu-id="115de-198">Fedora 26</span><span class="sxs-lookup"><span data-stu-id="115de-198">Fedora 26</span></span>

### <a name="installation-via-package-repository-preferred---fedora-26"></a><span data-ttu-id="115de-199">패키지 리포지토리를 통해 설치(권장) - Fedora 26</span><span class="sxs-lookup"><span data-stu-id="115de-199">Installation via Package Repository (preferred) - Fedora 26</span></span>

<span data-ttu-id="115de-200">PowerShell Core for Linux는 간편한 설치(및 업데이트)를 위해 공식 Microsoft 리포지토리로 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="115de-200">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---fedora-26"></a><span data-ttu-id="115de-201">직접 다운로드를 통해 설치 - Fedora 26</span><span class="sxs-lookup"><span data-stu-id="115de-201">Installation via Direct Download - Fedora 26</span></span>

<span data-ttu-id="115de-202">[릴리스][] 페이지의 RPM 패키지 `powershell-6.0.2-1.rhel.7.x86_64.rpm`을 Fedora 컴퓨터에 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="115de-202">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="115de-203">그런 다음 터미널에서 다음을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="115de-203">Then execute the following in the terminal:</span></span>

```sh
sudo dnf update
sudo dnf install compat-openssl10
sudo dnf install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="115de-204">또한 다운로드의 중간 단계 없이 RPM을 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="115de-204">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf update
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-26"></a><span data-ttu-id="115de-205">제거 - Fedora 26</span><span class="sxs-lookup"><span data-stu-id="115de-205">Uninstallation - Fedora 26</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="115de-206">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="115de-206">Arch Linux</span></span>

<span data-ttu-id="115de-207">PowerShell은 [Arch Linux][] 사용자 리포지토리(AUR)에 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="115de-207">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="115de-208">[최신 태깅 릴리스][arch-release]를 사용하여 컴파일할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="115de-208">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="115de-209">[최신 마스터 커밋][arch-git]에서 컴파일할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="115de-209">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="115de-210">[최신 릴리스 이진 파일][arch-bin]을 사용하여 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="115de-210">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="115de-211">AUR의 패키지는 커뮤니티에서 유지 관리되며 공식적인 지원은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="115de-211">Packages in the AUR are community maintained - there is no official support.</span></span>

<span data-ttu-id="115de-212">AUR에서 패키지를 설치하는 방법에 대한 자세한 내용은 [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) 또는 [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile) 커뮤니티를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="115de-212">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="linux-appimage"></a><span data-ttu-id="115de-214">Linux AppImage</span><span class="sxs-lookup"><span data-stu-id="115de-214">Linux AppImage</span></span>

<span data-ttu-id="115de-215">최신 Linux 배포를 사용하여 [릴리스][] 페이지의 AppImage `powershell-6.0.1-x86_64.AppImage`를 Linux 컴퓨터로 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="115de-215">Using a recent Linux distribution, download the AppImage `powershell-6.0.1-x86_64.AppImage` from the [releases][] page onto the Linux machine.</span></span>

<span data-ttu-id="115de-216">그런 다음 터미널에서 다음을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="115de-216">Then execute the following in the terminal:</span></span>

```bash
chmod a+x powershell-6.0.1-x86_64.AppImage
./powershell-6.0.1-x86_64.AppImage
```

<span data-ttu-id="115de-217">[AppImage][]를 사용하면 PowerShell을 설치하지 않고 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="115de-217">The [AppImage][] lets you run PowerShell without installing it.</span></span>
<span data-ttu-id="115de-218">PowerShell 및 종속성(.NET Core의 시스템 종속성 포함)을 하나의 통합 패키지로 묶은 이식 가능한 응용 프로그램입니다.</span><span class="sxs-lookup"><span data-stu-id="115de-218">It is a portable application that bundles PowerShell and its dependencies (including .NET Core's system dependencies) into one cohesive package.</span></span>
<span data-ttu-id="115de-219">이 패키지는 사용자의 Linux 배포와 독립적으로 작동하는 단일 이진 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="115de-219">This package  is a single binary that works independently of the user's Linux distribution.</span></span>

[appimage]: http://appimage.org/

## <a name="kali"></a><span data-ttu-id="115de-221">Kali</span><span class="sxs-lookup"><span data-stu-id="115de-221">Kali</span></span>

### <a name="installation"></a><span data-ttu-id="115de-222">설치</span><span class="sxs-lookup"><span data-stu-id="115de-222">Installation</span></span>

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

### <a name="run-powershell-in-latest-kali-kali-gnulinux-rolling-without-installing-it"></a><span data-ttu-id="115de-223">PowerShell을 설치하지 않고 최신 Kali(Kali GNU/Linux 롤링)에서 실행</span><span class="sxs-lookup"><span data-stu-id="115de-223">Run PowerShell in latest Kali (Kali GNU/Linux Rolling) without installing it</span></span>

```sh
# Grab the latest App Image
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-x86_64.AppImage

# Make executable
chmod a+x powershell-6.0.2-x86_64.AppImage

# Start PowerShell
./powershell-6.0.2-x86_64.AppImage
```

### <a name="uninstallation---kali"></a><span data-ttu-id="115de-224">제거 - Kali</span><span class="sxs-lookup"><span data-stu-id="115de-224">Uninstallation - Kali</span></span>

```sh
sudo dpkg -r powershell_6.0.2-1.ubuntu.16.04_amd64.deb
```

## <a name="raspbian"></a><span data-ttu-id="115de-225">Raspbian</span><span class="sxs-lookup"><span data-stu-id="115de-225">Raspbian</span></span>

<span data-ttu-id="115de-226">현재 PowerShell은 Raspbian Stretch에서만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="115de-226">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="115de-227">또한 [Pi Zero](https://github.com/dotnet/coreclr/issues/10605) 등의 다른 장치에는 지원되지 않는 프로세서가 있기 때문에 CoreCLR(및 PowerShell Core)은 Pi 2 및 Pi 3 장치에서만 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="115de-227">Also CoreCLR (and thus PowerShell Core) will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="115de-228">[Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/)를 다운로드하고 [설치 지침](https://www.raspberrypi.org/documentation/installation/installing-images/README.md)에 따라 Pi에 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="115de-228">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation"></a><span data-ttu-id="115de-229">설치</span><span class="sxs-lookup"><span data-stu-id="115de-229">Installation</span></span>

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

<span data-ttu-id="115de-230">필요에 따라 심볼 링크를 만들어 “pwsh” 이진 파일의 경로를 지정하지 않고 PowerShell을 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="115de-230">Optionally you can create a symbolic link to be able to start PowerShell without specifying path to the "pwsh" binary</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="115de-231">제거 - Raspbian</span><span class="sxs-lookup"><span data-stu-id="115de-231">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="115de-232">이진 아카이브</span><span class="sxs-lookup"><span data-stu-id="115de-232">Binary Archives</span></span>

<span data-ttu-id="115de-233">고급 배포 시나리오를 지원하기 위해 Linux 플랫폼을 위한 PowerShell 이진 `tar.gz` 보관이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="115de-233">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="115de-234">종속성</span><span class="sxs-lookup"><span data-stu-id="115de-234">Dependencies</span></span>

<span data-ttu-id="115de-235">PowerShell은 모든 Linux 배포를 위한 이식 가능한 이진 파일을 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="115de-235">PowerShell builds portable binaries for all Linux distributions.</span></span>
<span data-ttu-id="115de-236">하지만 .NET Core 런타임의 경우 다양한 배포판에 대한 여러 종속성이 필요하므로 PowerShell가 동일한 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="115de-236">But .NET Core runtime requires different dependencies on different distributions, and hence PowerShell does the same.</span></span>

<span data-ttu-id="115de-237">다음 차트는 여러 Linux 배포에서 공식적으로 지원되는 .NET Core 2.0 종속성을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="115de-237">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="115de-238">OS</span><span class="sxs-lookup"><span data-stu-id="115de-238">OS</span></span>                 | <span data-ttu-id="115de-239">종속성</span><span class="sxs-lookup"><span data-stu-id="115de-239">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="115de-240">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="115de-240">Ubuntu 14.04</span></span>       | <span data-ttu-id="115de-241">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="115de-241">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="115de-242">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="115de-242">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="115de-243">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="115de-243">Ubuntu 16.04</span></span>       | <span data-ttu-id="115de-244">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="115de-244">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="115de-245">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="115de-245">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="115de-246">Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="115de-246">Ubuntu 17.04</span></span>       | <span data-ttu-id="115de-247">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="115de-247">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="115de-248">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="115de-248">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="115de-249">Debian 8(Jessie)</span><span class="sxs-lookup"><span data-stu-id="115de-249">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="115de-250">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="115de-250">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="115de-251">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="115de-251">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="115de-252">Debian 9(Stretch)</span><span class="sxs-lookup"><span data-stu-id="115de-252">Debian 9 (Stretch)</span></span> | <span data-ttu-id="115de-253">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="115de-253">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="115de-254">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="115de-254">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="115de-255">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="115de-255">CentOS 7</span></span> <br> <span data-ttu-id="115de-256">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="115de-256">Oracle Linux 7</span></span> <br> <span data-ttu-id="115de-257">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="115de-257">RHEL 7</span></span> <br> <span data-ttu-id="115de-258">OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="115de-258">OpenSUSE 42.2</span></span> <br> <span data-ttu-id="115de-259">Fedora 25</span><span class="sxs-lookup"><span data-stu-id="115de-259">Fedora 25</span></span> | <span data-ttu-id="115de-260">libunwind, libcurl, openssl-libs, libicu</span><span class="sxs-lookup"><span data-stu-id="115de-260">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="115de-261">Fedora 26</span><span class="sxs-lookup"><span data-stu-id="115de-261">Fedora 26</span></span>          | <span data-ttu-id="115de-262">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span><span class="sxs-lookup"><span data-stu-id="115de-262">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="115de-263">공식적으로 지원되지 않는 Linux 배포에 PowerShell 이진 파일을 배포하려면 별도의 단계를 통해 대상 OS에 필요한 종속성을 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="115de-263">To deploy PowerShell binaries on Linux distributions that are not officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span>
<span data-ttu-id="115de-264">예를 들어 [Amazon Linux dockerfile][amazon-dockerfile]은 먼저 종속성을 설치한 후 Linux `tar.gz` 아카이브를 추출합니다.</span><span class="sxs-lookup"><span data-stu-id="115de-264">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="115de-265">설치 - 이진 아카이브</span><span class="sxs-lookup"><span data-stu-id="115de-265">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="115de-266">Linux</span><span class="sxs-lookup"><span data-stu-id="115de-266">Linux</span></span>

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

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="115de-267">이진 보관 제거</span><span class="sxs-lookup"><span data-stu-id="115de-267">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="115de-268">경로</span><span class="sxs-lookup"><span data-stu-id="115de-268">Paths</span></span>

* <span data-ttu-id="115de-269">`$PSHOME`은 `/opt/microsoft/powershell/6.0.2/`입니다.</span><span class="sxs-lookup"><span data-stu-id="115de-269">`$PSHOME` is `/opt/microsoft/powershell/6.0.2/`</span></span>
* <span data-ttu-id="115de-270">사용자 프로필은 `~/.config/powershell/profile.ps1`에서 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="115de-270">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="115de-271">기본 프로필은 `$PSHOME/profile.ps1`에서 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="115de-271">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="115de-272">사용자 프로필은 `~/.local/share/powershell/Modules`에서 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="115de-272">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="115de-273">공유 모듈은 `/usr/local/share/powershell/Modules`에서 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="115de-273">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="115de-274">기본 모듈은 `$PSHOME/Modules`에서 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="115de-274">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="115de-275">PSReadline 기록은 `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`에 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="115de-275">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="115de-276">프로필은 PowerShell의 호스트별 구성을 계속 사용하므로 기본 호스트별 프로필은 동일한 위치의 `Microsoft.PowerShell_profile.ps1`에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="115de-276">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="115de-277">PowerShell은 Linux의 [XDG 기본 디렉터리 사양][xdg-bds]을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="115de-277">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[릴리스]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
