실습 20: Autopilot을 사용하여 Windows 11 배포

**요약**

이 실습에서는 사용자 주도 모드를 사용하여 Windows 11 기기에 Autopilot을
프로비저닝하는 방법을 알아봅니다.

**필수 조건**

이 실습을 시작하기 전에 다음 실습을 완료해야 합니다.

- 실습 01 - Microsoft Entra ID에서 ID 관리

- 실습 02 - Azure AD Connect를 사용하여 ID 동기화

- 실습 11 - Microsoft 배포 도구 키트를 사용하여 Windows 11 배포

**시나리오**

Contoso IT는 Autopilot을 사용하여 새 Windows 11 장치를 배포할
계획입니다. 장치에는 Windows 11이 기본 설치되어 있습니다. 사용자는
OOBE(초기 설정) 중에 Microsoft Entra ID 자격 증명을 사용하여 장치를
연결하고 켜고 최소한의 질문에 답변할 수 있어야 합니다. 이 프로세스는
Entra ID 도메인에 자동으로 등록되고 가입됩니다. Hyper-V를 사용하여 최근
설치 및 구성한 SEA-WS4를 사용하여 환경을 구성하고 테스트해 달라는 요청을
받았습니다.

작업 1: Microsoft Entra 관리 센터에서 그룹 생성

1.  Switch and Sign in to [***SEA-SVR1***](urn:gd:lg:a:select-vm) as
    !!  with the password [**Pa55w.rd**](urn:gd:lg:a:send-vm-keys) and
    close **Server Manager**.**Contoso\Administrator**!! with the
    password !\![**Pa55w.rd**]()!!  and close **Server Manager**.
    [***SEA-SVR1***](urn:gd:lg:a:select-vm)에 !! 계정으로 로그인하고
    암호 [**Pa55w.rd**](urn:gd:lg:a:send-vm-keys) 를 입력한 후 **Server
    Manager**. **Contoso\Administrator**!!를 닫고 암호 !!Pa55w.rd!!를
    입력한 후 Server Manager를 닫습니다.

2.  작업 표시줄에서 **Microsoft Edge**를 선택합니다.

3.  Microsoft Edge의 주소창에 !! HYPERLINK "https://entra.microsoft.com"
    **ttps://entra.microsoft.com**!!을 입력하고 **Enter** 키를 누르세요.
    메시지가 표시되면
    [**admin@M365xXXXXXXXX.onmicrosoft.com**](mailto:admin@M365xXXXXXXXX.onmicrosoft.com)!!과
    비밀번호를 사용하여 로그인합니다.

![](./media/image1.png)

4.  탐색 창에서 **Identity**를 선택합니다.

5.  **Identity**에서 **Groups**.를 선택합니다.

> ![](./media/image2.png)

6.  **Groups | All groups**  블레이드에서 **New group**을 선택합니다.

> ![](./media/image3.png)

7.  **New Group** 블레이드의 **Group type** 목록에서 **Security**를
    선택합니다.

8.  **Group name** 상자에 !! HYPERLINK "http://urn:gd:lg:a:send-vm-keys"
    **IT Devices**!!를 입력합니다.

9.  **Group description**상자에 !! HYPERLINK
    "http://urn:gd:lg:a:send-vm-keys"IT **Department Devices**!!를
    입력합니다.

10. **Membership type**  목록에서 **Dynamic Device**를 선택합니다.

11. **Add dynamic query**를 선택합니다.

> ![](./media/image4.png)

12. **Dynamic membership rules** 블레이드에서 **Rule syntax** 상자 위에
    있는 **Edit**을 선택합니다.

> ![](./media/image5.png)

13. Edit rule syntax텍스트 상자에 다음과 같은 간단한 멤버십 규칙을
    추가하고**OK**를 선택합니다.

14. !!(device.devicePhysicalIDs -any (\_ -contains "\[ZTDId\]"))!!

> ![](./media/image6.png)

15. **Save**를 선택하여 **Dynamic membership rules**을 닫은 다음
    **Create**를 선택하여 그룹을 만듭니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image7.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)
>
> ![](./media/image9.png)

작업 2: 장치별 쉼표로 구분된 값(CSV) 파일 생성

1.  [***SEA-SVR2***](urn:gd:lg:a:select-vm)로 전환하고
    [**Contoso\Administrator**](urn:gd:lg:a:send-vm-keys)계정으로
    로그인하고 비밀번호는 !! HYPERLINK "http://urn:gd:lg:a:send-vm-keys"
    **Pa55w.rd**!!.

> ![A screenshot of a computer Description automatically
> generated](./media/image10.png)

2.  작업 표시줄에서 **Hyper-V Manager** 를 선택합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)

3.  가상 머신에서 **SEA-WS4**를 마우스 오른쪽 버튼으로 클릭하고
    **Connect**를 선택합니다.

> ![](./media/image12.png)

4.  **SEA-WS4** 창에서 **Start**.를 선택합니다. 컴퓨터가 시작되면 창을
    최대화합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image13.png)

5.  **SEA-WS4**에 [**Administrator**](urn:gd:lg:a:send-vm-keys) 계정으로
    로그인하고 비밀번호는 !! HYPERLINK "http://urn:gd:lg:a:send-vm-keys"
    **Pa55w.rd**!!입니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image14.png)

6.  **Start**를 마우스 오른쪽 버튼으로 클릭하고 **Windows Terminal
    (Admin)**을 선택한 다음 **User Account Control** 프롬프트에서
    **Yes**를 선택합니다.

> ![](./media/image15.png)
>
> ![A screenshot of a computer error Description automatically
> generated](./media/image16.png)

7.  Windows PowerShell 명령줄 프롬프트에서 다음 cmdlet을 입력한 다음
    **Enter** 키를 누릅니다:

> !! Install-Script -Name Get-WindowsAutoPilotInfo!!

![A screenshot of a computer Description automatically
generated](./media/image17.png)

8.  세 번의 메시지가 표시됩니다. 메시지가 나타날 때마다 Y를 입력하고
    **Enter** 키를 누르세요.

> ![](./media/image18.png)

9.  Windows PowerShell 명령줄 프롬프트에서 다음 cmdlet을 입력한 다음
    **Enter** 키를 누릅니다.

> !!**Set**-ExecutionPolicy *RemoteSigned*!!

10. 메시지가 표시되면 Y를 입력하고 Enter 키를 누릅니다.

11. Windows PowerShell 명령줄 프롬프트에 다음 cmdlet을 입력하고
    **Enter** 키를 누릅니다.

> !!Get-WindowsAutoPilotInfo.ps1 -OutputFile C:\Computer.csv!!
>
> ![](./media/image19.png)

12. Windows PowerShell 명령줄 프롬프트에서 다음 명령을 입력하고
    **Enter** 키를 누른 다음 파일 내용을 검토합니다.:

13. **type** !!C:\Computer.csv!!

> ![](./media/image20.png)

14. Windows PowerShell 명령줄 프롬프트에 다음 명령을 입력하고
    **Enter**키를 누릅니다. 그러면 파일이 **SEA-SVR2**로 복사됩니다:

15. copy !!c:\computer.csv \\sea-svr2\labfiles!!

> ![A screenshot of a computer screen Description automatically
> generated](./media/image21.png)

16. Windows PowerShell 명령 프롬프트를 닫습니다.

작업 3: Windows Autopilot 배포 프로필 작업

1.  [***SEA-SVR1***](urn:gd:lg:a:select-vm)로 전환합니다.

> ![](./media/image22.png)

2.  **Microsoft Edge**에서 새 탭을 열고 !! 하이퍼링크
    "https://intune.microsoft.com" **https://intune.microsoft.com**!!로
    이동합니다. 메시지가 표시되면
    [**admin@M365xXXXXXXX.onmicrosoft.com**](mailto:admin@M365xXXXXXXX.onmicrosoft.com)!!
    및 비밀번호를 사용하여 로그인합니다.

3.  **Microsoft Intune admin center**에서 **Devices**를 선택합니다.

4.  **Device enrollment** 섹션에서 **Enroll devices**을 선택합니다.

5.  세부 정보 창에서 **Windows Autopilot Deployment Program**으로
    스크롤한 다음 **Devices**를 선택합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image23.png)

6.  메뉴 표시줄의 **Windows Autopilot devices** 블레이드에서
    **Import**를 선택하고 **folder icon** 을 선택한 다음, !! HYPERLINK
    "http://urn:gd:lg:a:send-vm-keys"\\SEA-SVR2\Labfiles!!로 이동하여
    **Computer.csv**를 선택하고 **Open**을 선택한 다음 **Import**를
    선택합니다.

> ![](./media/image24.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image25.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image26.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image27.png)
>
> **참고**: 가져오기 과정은 최대 15분 정도 소요될 수 있지만, 일반적으로
> 약 5분 정도 소요됩니다.
>
> **중요**: 프로세스가 완료된 후 장치가 표시되지 않을 수 있습니다. 이
> 경우, **Sync** 버튼을 선택하고 몇 분 정도 기다린 후 " **Refresh를**
> 선택하세요.

7.  **X**를 선택하여 **Windows Autopilot devices**  블레이드를 닫습니다.

> ![](./media/image28.png)

8.  Windows 등록 블레이드의 세부 정보 창에서 **Deployment Profiles**을
    선택합니다.

> ![](./media/image29.png)

9.  **Windows AutoPilot deployment profiles**  블레이드에서 **Create
    profile**를 선택한 다음 **Windows PC**를 선택합니다.

> ![](./media/image30.png)

10. **Basics**  탭의 **Name**텍스트 상자에 !! HYPERLINK
    "http://urn:gd:lg:a:send-vm-keys" **Contoso profile1**!!을
    입력합니다.

11. **Convert all targeted devices to Autopilot**에서 **No**를 선택한 후
    **Next**를 선택합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image31.png)

12. **Out-of-box experience (OOBE)** 탭에서 **Deployment mode** 가
    **User-Driven**로 설정되어 있는지 확인합니다.

13. **Join to Microsoft Entra ID as**이 **Microsoft Entra Joined**으로
    설정되어 있는지 확인합니다.

14. 다음 옵션이 설정되어 있는지 확인하니다:

    - Microsoft Software License Terms: **Hide**

    - Privacy Settings: **Hide**

    - Hide change account options: **Hide**

    - User account type: **Administrator**.

    - Allow pre-provisioned deployment: **No**

    - Language (Region): **Operating system default**

    - Automatically configure keyboard: **Yes**

    - Apply device name template: **No**

15. **Next**를 선택합니다.

> ![](./media/image32.png)

16. **Assignments**탭의 **Included groups** 에서 **Add groups**를
    선택합니다.

17. **IT Devices** 그룹을 선택하고 **Select**를 클릭합니다. **Next**를
    선택합니다.

> ![](./media/image33.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image34.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image35.png)

18. **Review + create**  블레이드에서 정보를 검토한 다음 **Create**를
    선택합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image36.png)
>
> ![](./media/image37.png)

작업 4: PC 재설정

1.  [***SEA-SVR2***](urn:gd:lg:a:select-vm)로 전환합니다. **SEA-WS4**
    컴퓨터는 여전히 최대화되어 있어야 합니다.

> ![](./media/image38.png)

2.  **SEA-WS4**에서 시작을 선택하고 !! HYPERLINK
    "http://urn:gd:lg:a:send-vm-keys"reset!!을 입력한 후 **Reset this
    PC**를 선택합니다.

> ![](./media/image39.png)

3.  이 **Reset this PC** 섹션에서 **Reset PC**를 선택합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image40.png)

4.  **Remove everything**를 선택한 다음 **Local reinstall**를
    선택합니다.

> ![A blue screen with white text Description automatically
> generated](./media/image41.png)
>
> ![A blue screen with white text Description automatically
> generated](./media/image42.png)

5.  **Next**를 선택한 다음 **Reset**를 선택합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image43.png)
>
> ![A blue screen with white text Description automatically
> generated](./media/image44.png)
>
> **참고**: 일반적으로 이 작업은 물리적 장치를 새로 배포하는 데 필요하지
> 않습니다. 장치의 자동 조종 정보는 제조업체에서 제공하거나 OOBE(초기화)
> 전에 장치에서 얻을 수 있습니다. 이 실습에서는 새 장치의 OOBE를
> 시뮬레이션하기 위해 재설정을 시작해야 합니다.
>
> **참고:** 이 프로세스는 45~60분 정도 소요될 수 있으며, 프로세스 중에
> 여러 번 재부팅됩니다. 강사는 이 작업이 완료되는 동안 다음 모듈을
> 진행할 수 있습니다. 다음 실습 세션에서 작업 5를 완료하기 위해 다시
> 방문합니다.

작업 5: Autopilot 배포 확인

1.  **Contoso Corp. Sign-in Page**에서 !! HYPERLINK
    "mailto:Cindy@M365x19242953.onmicrosoft.com"
    **Cindy@M365x19242953.onmicrosoft.com**!!을 입력하고 Next를
    선택합니다.

2.  Password 페이지에서 !! HYPERLINK "mailto:P@55w.rd1234"
    **P@55w.rd1234**!!를 입력하고 **Sign in**을 선택합니다.

3.  **Use Windows Hello with your account** 페이지에서 **OK**를
    선택합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image45.png)

4.  **Verify your identity** 페이지에서 텍스트 확인 방법을 선택합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image46.png)

5.  **Enter code** 페이지에서 모바일 기기에 문자 메시지로 전송된 코드를
    입력한 다음 **Verify**를 선택합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image47.png)

6.  **Setup up a PIN**  대화 상자에서 **New PIN**  및 **Confirm
    PIN** 필드에 [**102938**](urn:gd:lg:a:send-vm-keys)을 입력한 다음
    확인을 선택합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image48.png)

7.  **All set!** 페이지에서 **OK**를 선택합니다.

8.  **Start**을 선택하고 **Settings**를 선택합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image49.png)

9.  **Accounts**를 선택한 다음 **Access work or school**를 선택합니다.
    장치가 Contoso의 Azure AD에 연결되어 있는지 확인합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image50.png)

10. **Connected to Contoso's Azure AD** 을 선택하고 **Info**를
    선택합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image51.png)

11. **Managed by Contoso**  페이지에서 아래로 스크롤한 다음 **Sync**를
    선택합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image52.png)
>
> ![](./media/image53.png)

12. **SEA-WS4**에서 **Settings**  창을 닫습니다.

13. [***SEA-SVR1***](urn:gd:lg:a:select-vm)로 전환합니다.

14. Microsoft Entra 관리 센터에서 **Identity**, **Devices**, **All
    devices를** 차례로 선택합니다.

> ![](./media/image54.png)
>
> 새 기기의 이름이 " **DESKTOP-**"으로 시작하는 것을 확인할 수 있습니다.
> 또한, Join Type은 Cindy White를 소유자로 하는 **Microsoft Entra ID
> joined** 되어 있습니다.

15. Autopilot 기기를 선택하세요. 상단 메뉴 막대에서 관리 옵션을
    확인합니다.

> 기기를**Retire, Wipe, Sync** 및 **Restart**할 수 있습니다.

16. 메뉴 막대 끝에 있는 줄임표를 선택하고 추가 관리 기능을 확인합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image55.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image56.png)
>
> 추가 기능으로는 새로 시작, 자동 조종 재설정, 빠른 검사, 전체 검사 등이
> 있습니다.

17. Microsoft Edge를 닫습니다.

**결과**: 이 연습을 완료하면 사용자 주도 모드를 사용하여 Windows 11
기기에 자동 조종 기능을 프로비저닝하게 됩니다.
