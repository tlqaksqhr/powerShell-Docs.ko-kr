---
title:  Windows PowerShell SDK 설치
ms.date:  2016-05-11
keywords:  powershell,cmdlet
description:  
ms.topic:  article
author:  jpjofre
manager:  dongill
ms.prod:  powershell
ms.assetid:  c3636b45-61aa-4720-85f0-58312c4fc8f9
---

# Windows PowerShell SDK 설치
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>다음 항목에서는 여러 버전의 Windows에 PowerShell SDK를 설치하는 방법을 설명합니다.</para>
  </introduction>
  <section>
    <title>Windows 8 및 Windows Server 2012용 Windows PowerShell 3.0 SDK 설치</title>
    <content>
      <para>Windows PowerShell 3.0은 Windows 8 및 Windows Server 2012에서 자동으로 설치됩니다. 또한 Windows 8 SDK의 일부로써 Windows PowerShell 3.0의 참조 어셈블리를 다운로드하고 설치할 수 있습니다. 이러한 어셈블리를 사용하여 Windows PowerShell 3.0에 대한 cmdlet, 공급자 및 호스트 프로그램을 작성할 수 있습니다. Windows 8용 Windows SDK를 설치하면 Windows PowerShell 어셈블리가 참조 어셈블리 폴더(\Program Files (x86)\Reference Assemblies\Microsoft\WindowsPowerShell\3.0)에 자동으로 설치됩니다. 자세한 내용은 <externalLink><linkText>Windows 8 SDK 다운로드 사이트</linkText><linkUri>http://msdn.microsoft.com/windows/hardware/hh852363.aspx</linkUri></externalLink>를 참조하세요. Windows PowerShell 코드 샘플은 개발자 센터에서도 제공됩니다. 자세한 내용은 <externalLink><linkText>개발자 센터 사이트</linkText><linkUri>http://code.msdn.microsoft.com/windowsdesktop/</linkUri></externalLink>에서 데스크톱 코드 샘플 페이지를 참조하세요. </para>
      <para>또한 Windows PowerShell 3.0은 다수의 코드 샘플이 포함된 이전 버전인 Windows PowerShell 2.0 SDK와 호환됩니다. Windows PowerShell 2.0 SDK를 다운로드하는 방법에 대한 자세한 내용은 다음을 참조하세요. (2.0 코드 샘플은 Windows 8 및 Windows PowerShell 3.0과 호환되지만 Windows 8 플랫폼에 Windows PowerShell 2.0을 설치할 수 없습니다.) </para>
    </content>
  </section>
  <section>
    <title>Windows 7 및 Windows Server 2008 R2용 Windows PowerShell 3.0 SDK 설치</title>
    <content>
      <para>PowerShell 2.0은 Windows 7 및 Windows Server 2008 R2에서 자동으로 설치됩니다. 또한 이러한 시스템에 PowerShell 3.0을 설치할 수 있습니다. (자세한 내용은 <link xlink:href="6fbb0409-5a54-48ec-95e6-7f8b7d8c4969">Windows PowerShell 설치</link>를 참조하세요.) 위에서 설명한 대로, Windows 7 및 Windows Server 2008 R2에서도 Windows 8 SDK를 설치할 수 있습니다.</para>
    </content>
  </section>
  <section>
    <title>Windows 7, Vista, XP, Server 2003 및 Server 2008용 Windows PowerShell 2.0 SDK 설치</title>
    <content>
      <para><token>mshshort</token> 2.0 SDK는 cmdlet, 공급자 및 호스팅 응용 프로그램을 작성하는 데 필요한 참조 어셈블리를 제공하고 코드 작성을 시작할 때 시작 지점으로 사용할 수 있는 C# 샘플 코드를 제공합니다. </para>
      <para>이 SDK를 설치하려면 <externalLink><linkText>Windows PowerShell 2.0 SDK</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=184611</linkUri></externalLink>를 참조하세요.</para>
    </content>
    <sections>
      <section>
        <title>참조 어셈블리</title>
        <content>
          <para>참조 어셈블리는 기본적으로 <codeInline>c:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\V1.0</codeInline>에 설치됩니다.</para>
          <alert class="note">
            <para>Windows PowerShell 2.0 어셈블리에 대해 컴파일되는 코드는 Windows PowerShell 1.0 설치에 로드할 수 없습니다. 그러나 Windows PowerShell 1.0 어셈블리에 대해 컴파일되는 코드는 Windows PowerShell 2.0 설치에 로드할 수 있습니다.</para>
          </alert>
        </content>
      </section>
      <section>
        <title>샘플</title>
        <content>
          <para>코드 샘플은 기본적으로 <codeInline>C:\Program Files\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\</codeInline>에 설치됩니다.</para>
          <para>다음 섹션에서는 각 샘플의 용도에 대한 간단한 설명을 제공합니다.</para>
        </content>
        <sections>
          <section>
            <title>Cmdlet 예제</title>
            <content>
              <definitionTable>
                <definedTerm>GetProcessSample01</definedTerm>
                <definition>
                  <para>로컬 컴퓨터에 모든 프로세스를 가져오는 간단한 cmdlet을 작성하는 방법을 보여 줍니다.</para>
                </definition>
                <definedTerm>GetProcessSample02</definedTerm>
                <definition>
                  <para>cmdlet에 매개 변수를 추가하는 방법을 보여 줍니다. cmdlet은 프로세스 이름을 하나 이상 가져오고 일치하는 프로세스를 반환합니다.</para>
                </definition>
                <definedTerm>GetProcessSample03</definedTerm>
                <definition>
                  <para>파이프라인에서 입력을 허용하는 매개 변수를 추가하는 방법을 보여 줍니다.</para>
                </definition>
                <definedTerm>GetProcessSample04</definedTerm>
                <definition>
                  <para>종료되지 않는 오류를 처리하는 방법을 보여 줍니다.</para>
                </definition>
                <definedTerm>GetProcessSample05</definedTerm>
                <definition>
                  <para>지정된 프로세스의 목록을 표시하는 방법을 보여 줍니다.</para>
                </definition>
                <definedTerm>SelectObject</definedTerm>
                <definition>
                  <para>특정 개체만 선택하는 필터를 작성하는 방법을 보여 줍니다. </para>
                </definition>
                <definedTerm>SelectString</definedTerm>
                <definition>
                  <para>지정된 패턴에 대한 파일을 검색하는 방법을 보여 줍니다.</para>
                </definition>
                <definedTerm>StopProcessSample01</definedTerm>
                <definition>
                  <para><parameterReference>PassThru</parameterReference> 매개 변수를 구현하는 방법과 <codeEntityReference>Overload:System.Management.Automation.Cmdlet.ShouldProcess</codeEntityReference> 및 <codeEntityReference>Overload:System.Management.Automation.Cmdlet.ShouldContinue</codeEntityReference> 메서드에 대한 호출을 통해 사용자 피드백을 요청하는 방법을 보여 줍니다. cmdlet이 개체를 반환하도록 하려면 사용자는 <parameterReference>PassThru</parameterReference> 매개 변수를 지정합니다. </para>
                </definition>
                <definedTerm>StopProcessSample02</definedTerm>
                <definition>
                  <para>특정 프로세스를 중지하는 방법을 보여 줍니다.</para>
                </definition>
                <definedTerm>StopProcessSample03</definedTerm>
                <definition>
                  <para>매개 변수에 대한 별칭을 선언하는 방법 및 와일드카드를 지원하는 방법을 보여 줍니다.</para>
                </definition>
                <definedTerm>StopProcessSample04</definedTerm>
                <definition>
                  <para>매개 변수 집합을 선언하는 방법, cmdlet에서 입력으로 사용하는 개체, 사용할 기본 매개 변수 집합을 지정하는 방법을 보여 줍니다.</para>
                </definition>
              </definitionTable>
            </content>
          </section>
          <section>
            <title>원격 샘플</title>
            <content>
              <definitionTable>
                <definedTerm>RemoteRunspace01</definedTerm>
                <definition>
                  <para>원격 연결을 설정하는 데 사용되는 원격 runspace를 만드는 방법을 보여 줍니다.</para>
                </definition>
                <definedTerm>RemoteRunspacePool01</definedTerm>
                <definition>
                  <para>원격 runspace 풀을 생성하는 방법과 이 풀을 사용하여 여러 명령을 동시에 실행하는 방법을 보여 줍니다.</para>
                </definition>
                <definedTerm>Serialization01</definedTerm>
                <definition>
                  <para>기존 .NET 클래스를 살펴보고 이 클래스의 선택된 공용 속성의 정보를 직렬화/역직렬화에서 유지되도록 하는 방법을 보여 줍니다.</para>
                </definition>
                <definedTerm>Serialization02</definedTerm>
                <definition>
                  <para>기존 .NET 클래스를 살펴 보고 이 클래스의 인스턴스 정보를 클래스의 공용 속성에서 사용할 수 없을 때 이 정보가 직렬화/역직렬화에서 유지되도록 하는 방법을 보여 줍니다</para>
                </definition>
                <definedTerm>Serialization03</definedTerm>
                <definition>
                  <para>기존 .NET 클래스를 살펴 보고 이 클래스와 파생된 클래스의 인스턴스가 라이브 .NET 개체로 역직렬화(리하이드레이션)되도록 하는 방법을 보여 줍니다.</para>
                </definition>
              </definitionTable>
            </content>
          </section>
          <section>
            <title>이벤트 샘플</title>
            <content>
              <definitionTable>
                <definedTerm>Event01</definedTerm>
                <definition>
                  <para>이벤트 등록용 cmdlet을 ObjectEventRegistrationBase에서 파생시켜 만드는 방법을 보여 줍니다.</para>
                </definition>
                <definedTerm>Event02</definedTerm>
                <definition>
                  <para>원격 컴퓨터에서 생성된 <token>mshshort</token> 이벤트의 알림을 받는 방법을 표시하는 방법을 보여 줍니다. <codeEntityReference>T:System.Management.Automation.Runspaces.Runspace</codeEntityReference> 클래스를 통해 노출되는 PSEventReceived 이벤트를 사용합니다.</para>
                </definition>
              </definitionTable>
            </content>
          </section>
          <section>
            <title>호스팅 응용 프로그램 샘플</title>
            <content>
              <definitionTable>
                <definedTerm>Runspace01</definedTerm>
                <definition>
                  <para><codeEntityReference>T:System.Management.Automation.PowerShell</codeEntityReference> 클래스를 사용하여 <externalLink><linkText>Get-process</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=113324</linkUri></externalLink> cmdlet 동기적으로 실행하는 방법을 보여 줍니다. <externalLink><linkText>Get-process</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=113324</linkUri></externalLink> cmdlet은 로컬 컴퓨터에서 실행 중인 각 프로세스에 대해 <codeEntityReference>T:System.Diagnostics.Process</codeEntityReference> 개체를 반환합니다.</para>
                </definition>
                <definedTerm>Runspace02</definedTerm>
                <definition>
                  <para><codeEntityReference>T:System.Management.Automation.PowerShell</codeEntityReference> 클래스를 사용하여 <externalLink><linkText>Get-process</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=113324</linkUri></externalLink> 및 <externalLink><linkText>Sort-object</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkID=113403</linkUri></externalLink> cmdlet을 동기적으로 실행하는 방법을 보여 줍니다. <externalLink><linkText>Get-process</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=113324</linkUri></externalLink> cmdlet은 로컬 컴퓨터에서 실행 중인 각 프로세스에 대해 <codeEntityReference>T:System.Diagnostics.Process</codeEntityReference> 개체를 반환하고, Sort-Object는 <codeEntityReference>P:System.Diagnostics.Process.Id</codeEntityReference> 속성을 기준으로 개체를 정렬합니다. 이러한 명령의 결과는 <codeEntityReference>T:System.Windows.Forms.DataGridView</codeEntityReference> 컨트롤을 사용하여 표시됩니다</para>
                </definition>
                <definedTerm>Runspace03</definedTerm>
                <definition>
                  <para><codeEntityReference>T:System.Management.Automation.PowerShell</codeEntityReference> 클래스를 사용하여 스크립트를 동기적으로 실행하는 방법과 종료되지 않는 오류를 처리하는 방법을 보여 줍니다. 스크립트는 프로세스 이름 목록을 받은 다음 해당 프로세스를 검색합니다. 스크립트를 실행할 때 생성된 종료되지 않은 오류를 포함하여 스크립트 결과는 콘솔 창에 표시됩니다.</para>
                </definition>
                <definedTerm>Runspace04</definedTerm>
                <definition>
                  <para><codeEntityReference>T:System.Management.Automation.PowerShell</codeEntityReference> 클래스를 사용하여 명령을 실행하는 방법과 명령을 실행할 때 발생한 종료 오류를 파악하는 방법을 보여 줍니다. 두 개의 명령이 실행되는데, 마지막 명령은 유효하지 않은 매개 변수 인수를 전달받습니다. 결과적으로 개체가 반환되지 않고 종료 오류가 발생합니다.</para>
                </definition>
                <definedTerm>Runspace05</definedTerm>
                <definition>
                  <para>runspace를 열 때 스냅인의 cmdlet을 사용할 수 있도록 <codeEntityReference>T:System.Management.Automation.Runspaces.InitialSessionState</codeEntityReference> 개체에 스냅인을 추가하는 방법을 보여 줍니다. 스냅인은 <codeEntityReference>T:System.Management.Automation.PowerShell</codeEntityReference> 개체를 사용하여 동기적으로 실행되는 Get-Proc cmdlet(<legacyLink xlink:href="7b48bf80-cbf0-4cb1-8d5b-3b8d06196598">GetProcessSample01 샘플에 정의됨</legacyLink>)을 제공합니다.</para>
                </definition>
                <definedTerm>Runspace06</definedTerm>
                <definition>
                  <para>runspace를 열 때 모듈이 로드되도록 <codeEntityReference>T:System.Management.Automation.Runspaces.InitialSessionState</codeEntityReference> 개체에 모듈을 추가하는 방법을 보여 줍니다. 모듈은 <codeEntityReference>T:System.Management.Automation.PowerShell</codeEntityReference> 개체를 사용하여 동기적으로 실행되는 Get-Proc cmdlet(<legacyLink xlink:href="481f557d-3344-4d33-b2da-4736a0165181">GetProcessSample02 샘플</legacyLink>에 정의됨)을 제공합니다.</para>
                </definition>
                <definedTerm>Runspace07</definedTerm>
                <definition>
                  <para>runspace를 만든 다음 <codeEntityReference>T:System.Management.Automation.PowerShell</codeEntityReference> 개체를 사용하여 두 cmdlet을 동기적으로 실행하는 runspace를 사용하는 방법을 보여 줍니다.</para>
                </definition>
                <definedTerm>Runspace08</definedTerm>
                <definition>
                  <para><codeEntityReference>T:System.Management.Automation.PowerShell</codeEntityReference> 개체의 파이프라인에 명령 및 인수를 추가하는 방법과 명령을 동기적으로 실행하는 방법을 보여 줍니다.</para>
                </definition>
                <definedTerm>Runspace09</definedTerm>
                <definition>
                  <para><codeEntityReference>T:System.Management.Automation.PowerShell</codeEntityReference> 개체의 파이프라인에 스크립트를 추가하는 방법과 스크립트를 비동기적으로 실행 하는 방법을 보여 줍니다. 이벤트는 스크립트의 출력을 처리하는 데 사용됩니다.</para>
                </definition>
                <definedTerm>Runspace10</definedTerm>
                <definition>
                  <para>기본 초기 세션 상태를 만드는 방법, <codeEntityReference>T:System.Management.Automation.Runspaces.InitialSessionState</codeEntityReference>에 cmdlet을 추가하는 방법, 초기 세션 상태를 사용하는 runspace를 만드는 방법, <codeEntityReference>T:System.Management.Automation.PowerShell</codeEntityReference> 개체를 사용하여 명령을 실행하는 방법을 보여 줍니다.</para>
                </definition>
                <definedTerm>Runspace11</definedTerm>
                <definition>
                  <para><codeEntityReference>T:System.Management.Automation.ProxyCommand</codeEntityReference> 클래스를 사용하여 기존 cmdlet을 호출하지만 사용 가능한 매개 변수 집합을 제한하는 프록시 명령을 만드는 방법을 보여 줍니다. 프록시 명령은 제한된 runspace를 만드는 데 사용되는 초기 세션 상태에 추가됩니다. 즉 사용자는 프록시 명령을 통해서만 cmdlet의 기능에 액세스할 수 있습니다.</para>
                </definition>
                <definedTerm>PowerShell01</definedTerm>
                <definition>
                  <para><codeEntityReference>T:System.Management.Automation.Runspaces.InitialSessionState</codeEntityReference> 개체를 사용하여 제한된 runspace를 만드는 방법을 보여 줍니다.</para>
                </definition>
                <definedTerm>PowerShell02</definedTerm>
                <definition>
                  <para>runspace 풀을 사용하여 여러 명령을 동시에 실행하는 방법을 보여 줍니다.</para>
                </definition>
              </definitionTable>
            </content>
          </section>
          <section>
            <title>호스트 샘플</title>
            <content>
              <definitionTable>
                <definedTerm>Host01</definedTerm>
                <definition>
                  <para>사용자 지정 호스트를 사용하는 호스트 응용 프로그램을 구현하는 방법을 보여 줍니다. 이 샘플에서는 사용자 지정 호스트를 사용하는 runspace가 생성된 다음 "종료"를 호출하는 스크립트를 실행하는 데 사용되는 <codeEntityReference>T:System.Management.Automation.PowerShell</codeEntityReference> API가 사용됩니다. 그런 다음 호스트 응용 프로그램은 스크립트의 출력을 살펴 보고 결과를 출력합니다.</para>
                </definition>
                <definedTerm>Host02</definedTerm>
                <definition>
                  <para>사용자 지정 호스트 구현과 함께 <token>mshshort</token> 런타임을 사용하는 호스트 응용 프로그램을 작성하는 방법을 보여 줍니다. 호스트 응용 프로그램에서는 호스트 문화권을 독일어로 설정하고, <externalLink><linkText>Get-process</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=113324</linkUri></externalLink> cmdlet을 실행하고, 사용자가 pwrsh.exe를 사용하여 확인할 수 있는 결과를 표시한 다음 현재 데이터 및 시간을 독일어로 출력합니다.</para>
                </definition>
                <definedTerm>Host03</definedTerm>
                <definition>
                  <para>명령줄에서 명령을 읽고 명령을 실행한 후 콘솔에 결과를 표시하는 대화형 콘솔 기반 호스트 응용 프로그램을 구축하는 방법을 보여 줍니다.</para>
                </definition>
                <definedTerm>Host04</definedTerm>
                <definition>
                  <para>명령줄에서 명령을 읽고 명령을 실행한 후 콘솔에 결과를 표시하는 대화형 콘솔 기반 호스트 응용 프로그램을 구축하는 방법을 보여 줍니다. 또한 이 호스트 응용 프로그램에서는 사용자가 여러 항목을 지정할 수 있도록 해주는 메시지 표시를 지원합니다.</para>
                </definition>
                <definedTerm>Host05</definedTerm>
                <definition>
                  <para>명령줄에서 명령을 읽고 명령을 실행한 후 콘솔에 결과를 표시하는 대화형 콘솔 기반 호스트 응용 프로그램을 구축하는 방법을 보여 줍니다. 또한 이 호스트 응용 프로그램은 <externalLink><linkText>Enter-PsSession</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=135210</linkUri></externalLink> 및 <externalLink><linkText>Exit-PsSession</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=135212</linkUri></externalLink> cmdlet을 사용하여 원격 컴퓨터에 대한 호출을 지원합니다.</para>
                </definition>
                <definedTerm>Host06</definedTerm>
                <definition>
                  <para>명령줄에서 명령을 읽고 명령을 실행한 후 콘솔에 결과를 표시하는 대화형 콘솔 기반 호스트 응용 프로그램을 구축하는 방법을 보여 줍니다. 또한 이 샘플에서는 토크나이저 API를 사용하여 사용자가 입력하는 텍스트의 색을 지정합니다.</para>
                </definition>
              </definitionTable>
            </content>
          </section>
          <section>
            <title>공급자 샘플</title>
            <content>
              <definitionTable>
                <definedTerm>AccessDBProviderSample01</definedTerm>
                <definition>
                  <para><codeEntityReference>T:System.Management.Automation.Provider.CmdletProvider</codeEntityReference> 클래스에서 직접 파생되는 공급자 클래스를 선언하는 방법을 보여 줍니다. 참조용으로만 설명합니다.</para>
                </definition>
                <definedTerm>AccessDBProviderSample02</definedTerm>
                <definition>
                  <para><codeEntityReference>M:System.Management.Automation.Provider.DriveCmdletProvider.NewDrive(System.Management.Automation.PSDriveInfo)</codeEntityReference> 및 <codeEntityReference>M:System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive(System.Management.Automation.PSDriveInfo)</codeEntityReference> 메서드를 덮어써서 New-PSDrive 및 Remove-PSDrive cmdlet에 대한 호출을 지원하는 방법을 보여 줍니다. 이 샘플의 공급자 클래스는 <codeEntityReference>T:System.Management.Automation.Provider.DriveCmdletProvider</codeEntityReference> 클래스에서 파생됩니다.</para>
                </definition>
                <definedTerm>AccessDBProviderSample03</definedTerm>
                <definition>
                  <para><codeEntityReference>M:System.Management.Automation.Provider.ItemCmdletProvider.GetItem(System.String)</codeEntityReference> 및 <codeEntityReference>M:System.Management.Automation.Provider.ItemCmdletProvider.SetItem(System.String,System.Object)</codeEntityReference> 메서드를 덮어써서 Get-Item 및 Set-Item cmdlet에 대한 호출을 지원하는 방법을 보여 줍니다. 이 샘플의 공급자 클래스는 <codeEntityReference>T:System.Management.Automation.Provider.ItemCmdletProvider</codeEntityReference> 클래스에서 파생됩니다.</para>
                </definition>
                <definedTerm>AccessDBProviderSample04</definedTerm>
                <definition>
                  <para>컨테이너 메서드를 덮어써서 Copy-Item, Get-ChildItem, New-Item 및 Remove-Item cmdlet에 대한 호출을 지원하는 방법을 보여 줍니다. 이러한 메서드는 데이터 저장소에 컨테이너 항목이 포함될 때 구현해야 합니다. 컨테이너는 공통 부모 항목 아래에 있는 자식 항목 그룹입니다. 이 샘플의 공급자 클래스는 <codeEntityReference>T:System.Management.Automation.Provider.ItemCmdletProvider</codeEntityReference> 클래스에서 파생됩니다.</para>
                </definition>
                <definedTerm>AccessDBProviderSample05</definedTerm>
                <definition>
                  <para>컨테이너 메서드를 덮어써서 Move-Item 및 Join-Path cmdlet에 대한 호출을 지원하는 방법을 보여 줍니다. 이러한 메서드는 사용자가 컨테이너 내의 항목을 이동해야 하고 데이터 저장소에 중첩된 컨테이너가 포함되는 경우에 구현해야 합니다. 이 샘플의 공급자 클래스는 <codeEntityReference>T:System.Management.Automation.Provider.NavigationCmdletProvider</codeEntityReference> 클래스에서 파생됩니다.</para>
                </definition>
                <definedTerm>AccessDBProviderSample06</definedTerm>
                <definition>
                  <para>콘텐츠 메서드를 덮어써서 Clear-Content, Get-Content 및 Set-Content cmdlet에 대한 호출을 지원하는 방법을 보여 줍니다. 이러한 메서드는 사용자가 데이터 저장소에 있는 항목의 콘텐츠를 관리해야 하는 경우에 구현해야 합니다. 이 샘플의 공급자 클래스는 <codeEntityReference>T:System.Management.Automation.Provider.NavigationCmdletProvider</codeEntityReference> 클래스에서 파생되며, <codeEntityReference>T:System.Management.Automation.Provider.IContentCmdletProvider</codeEntityReference> 인터페이스를 구현합니다.</para>
                </definition>
              </definitionTable>
            </content>
          </section>
        </sections>
      </section>
    </sections>
  </section>
  <relatedTopics />
</developerConceptualDocument>



<!--HONumber=May16_HO4-->


