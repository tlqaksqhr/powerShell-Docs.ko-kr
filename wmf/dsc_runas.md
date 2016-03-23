# DSC 리소스의 자동 RunAs 지원
DSC RunAs 자격 증명 지원
--------------------------------

WMF 5.0 Preview 2015년 4월에서는 PsDscRunAsCredential 속성을 사용하여 지정된 자격 증명 집합으로 **모든** DSC 리소스를 실행할 수 있습니다. 특정 사용자 컨텍스트에서 MSI 패키지 설치, 사용자의 레지스트리 하이브 액세스, 사용자의 특정 로컬 디렉터리 액세스, 네트워크 공유 액세스 등의 시나리오를 사용합니다.

다음에서는 DSC의 PsDscRunAsCredential 속성을 사용하여 사용자의 명령 프롬프트 배경색을 변경하는 예제를 보여 줍니다.

구성 ChangeCmdBackGroundColor

{

    Node ("localhost")

    {

        Registry CmdPath

        {

            Key = "HKEY\_CURRENT\_USER\\\\Software\\Microsoft\\\\Command Processor"

            ValueName = "DefaultColor"

            ValueData = '1F'

            ValueType = "DWORD"

            Ensure = "Present"

            Force = $true

            Hex = $true

            PsDscRunAsCredential = get-credential

        }

    }

}

$configData = @{

AllNodes = @(

@{

NodeName="localhost";

CertificateFile = "C:\\publicKeys\\targetNode.cer"

}

)

}

ChangeCmdBackGroundColor -ConfigurationData $configData

## 알려진 문제

다음은 이번 릴리스에서 DSC RunAs 자격 증명 기능의 알려진 문제입니다.

-   WindowsProcess 리소스에서 RunAs 자격 증명을 지원하지 않습니다.

<!--HONumber=Mar16_HO2-->
