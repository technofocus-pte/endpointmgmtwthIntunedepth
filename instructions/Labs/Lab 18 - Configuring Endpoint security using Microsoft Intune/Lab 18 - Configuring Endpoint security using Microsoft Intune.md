실습 18 - Microsoft Intune을 사용하여 엔드포인트 보안 구성

**요약**

이 실습에서는 Microsoft Intune에서 관리되는 장치에 대한 Microsoft
Defender를 구성하는 정책을 만듭니다.

**필수 조건**

이 실습을 시작하기 전에 다음 실습을 완료해야 합니다:

- 실습 5 - Microsoft Intune에 장치 등록 관리

- 실습 6 - Microsoft Intune에 장치 등록

- 실습 7 - 구성 프로필 만들기 및 배포

**시나리오**

Contoso Developers Group에서 Microsoft Defender를 올바르게 구성했는지
확인하라는 요청을 받았습니다. 다음과 같은 사항이 요청되었습니다:

- 변조 방지 기능을 활성화해야 합니다.

- Windows 보안 앱에서 계정 보호, 앱 및 브라우저 제어, 장치 보안, 장치
  성능 및 상태, 가족 옵션 영역을 숨깁니다.

- 회사 이름과 전화번호를 추가해야 합니다.

- 실시간 보호, 치료 및 검사 설정도 구성해야 합니다.

설정은 등록된 장치(SEA-WS1)와 등록되지 않은 장치(SEA-CL1)에서 테스트를
통해 검증됩니다.

작업 1: Intune에서 Windows 보안 환경 구성

1.  [***SEA-SVR1***](urn:gd:lg:a:select-vm)에 !!
    [**Contoso\Administrator**](urn:gd:lg:a:send-vm-keys)!! 계정으로
    로그인하고, 비밀번호는 !!
    [**Pa55w.rd**](urn:gd:lg:a:send-vm-keys)!!입니다.

2.  타스크바에서 **Microsoft Edge**를 선택합니다.

3.  Microsoft Edge에서 주소 표시줄에 !!
    **https://Intune.microsoft.com!!** 을 입력하고 **Enter** 키를
    누릅니다.

4.  Office 365 테넌트 관리자로 로그인합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image1.png)

5.  탐색 창에서 **Endpoint security를** 선택한 다음 **Antivirus**을
    선택합니다.

> ![](./media/image2.png)

6.  **Endpoint security |Antivirus**  창에서 **+ Create Policy**를
    선택합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)

7.  **Create a profile**창에서 **Platform**으로 **Windows 10, Windows
    11, Windows Server**를 선택합니다.

8.  **Profile** 목록에서 **Windows Security experience**를 선택한 후,
    **Create**를 선택합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

9.  Basics 탭의 **Name**필드에 !! [**Windows Security
    Settings**](urn:gd:lg:a:send-vm-keys)!!을 입력하고 **Next**.를
    선택합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image5.png)

10. **Defender** 에서 다음 설정을 구성합니다:

    - TamperProtection (Device): **On**

> ![A screenshot of a computer Description automatically
> generated](./media/image6.png)

11. **Windows Defender Security Center**에서 다음 설정을 구성합니다.

    - Disable Account Protection UI: **Enable**

    - Disable App Browser UI: **Enable**

    - Disable Device Security UI: **Enable**

    - Disable Family UI: **Enable**

    - Disable Health UI: **Enable**

> ![A screenshot of a computer Description automatically
> generated](./media/image7.png)

12. **Enable Customized Toasts**  옆에서 **Enable을** 선택합니다.

13. **Company name**  필드에서 **Configured**,을 선택한 후 !! [**Contoso
    IT**](urn:gd:lg:a:send-vm-keys)!!를 입력합니다.

14. **Phone**에서 **Configured**을 선택한 후 !!
    [**555-1234**](urn:gd:lg:a:send-vm-keys)!!를 입력하고 **Next**를
    선택합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)

15. **Scope tags** 페이지에서 **Next**를 선택합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image9.png)

16. **Assignments Included groups** 에서 **Add groups**를 선택합니다.
    **Contoso Developer Devices** 그룹을 선택하고 **Select**을 클릭한 후
    **Next**를 선택합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image10.png)

17. **Review + create** 탭에서 정보를 검토하고 **Save**를 선택합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)

작업 2: Intune에서 Microsoft Defender 바이러스 백신 정책 구성

1.  **Endpoint security |Antivirus**  창에서 **Create Policy**를
    선택합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image12.png)

2.  **Create a profile** 창에서 **Platform**으로 **Windows 10, Windows
    11, and Windows Server**를 선택합니다.

3.  **Profile** 목록에서 **Microsoft Defender Antivirus**를 선택한 다음
    **Create**를 선택합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image13.png)

4.  **Basics**탭의 **Name**필드에 !! [**Microsoft Defender Antivirus
    Settings**](urn:gd:lg:a:send-vm-keys)!!을 입력하고 **Next**를
    선택합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image14.png)

5.  **Configuration settings** 탭에서 다음 설정을 구성합니다:

    - Allow Intrusion Prevention System: **Allowed**

    - Allow scanning of all downloaded files and
      attachments: **Allowed**

    - Allow Realtime Monitoring: **Allowed**

> ![](./media/image15.png)

- Check For Signatures Before Running Scan: **Enabled**

- Days to Retain Cleaned Malware: !!**[60](urn:gd:lg:a:send-vm-keys)!!**

> ![A screenshot of a computer Description automatically
> generated](./media/image16.png)

- Schedule Quick Scan
  Time: !!**[60](urn:gd:lg:a:send-vm-keys)!!** (represents 1:00AM)

> ![A screenshot of a computer Description automatically
> generated](./media/image17.png)

- Submit samples consent: **Send safe samples automatically**

> ![A screenshot of a computer Description automatically
> generated](./media/image18.png)

6.  **Configuration settings**  탭에서 **Next**를 선택합니다.

7.  **Scope tags** 페이지에서 **Next**를 선택합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image19.png)

8.  **Assignments**탭의 **Included groups**에서 **Add groups**를
    선택합니다.

9.  **Contoso Developer Devices** 그룹을 선택한 후 **Select**를 선택하고
    **Next**를 선택합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image20.png)

10. **Review + create** 탭에서 정보를 검토하고 **Save**를 선택합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image21.png)

작업 3: 관리되는 장치 동기화

1.  **Microsoft Intune admin center**에서 **Devices**를 선택한 다음
    **All devices**를 선택합니다.

2.  **Devices | All devices**창에서 **SEA-WS1** 을 선택한 다음
    **SEA-WS1**  ​​블레이드의 도구 모음에서 **Sync** 를 선택하고 **Yes**를
    선택합니다.

> ![](./media/image22.png)
>
> 동기화가 완료될 때까지 3~4분 정도 기다리세요.

3.  Microsoft Edge를 닫습니다.

작업 4: 구성 확인

1.  [***SEA-CL1***](urn:gd:lg:a:select-vm)로 전환합니다. 필요한 경우 !!
    [**Contoso\Administrator**](urn:gd:lg:a:send-vm-keys)!! 계정으로
    로그인하고 비밀번호는 !!
    [**Pa55w.rd**](urn:gd:lg:a:send-vm-keys)!!입니다.

2.  [***SEA-CL1***](urn:gd:lg:a:select-vm)에서 시작을 선택하고 !!
    [**Windows Security**](urn:gd:lg:a:send-vm-keys)!!를 입력한 다음
    Windows 보안 아이콘 아래에서 **Open**를 선택합니다.

> ![](./media/image23.png)
>
> 모든 보안 옵션이 표시되는 것을 확인할 수 있습니다. 이는 SEA-CL1이
> Intune에 등록되어 있지 않기 때문입니다.
>
> ![A screenshot of a computer security system Description automatically
> generated](./media/image24.png)

3.  **Windows Security**을 닫고
    [***SEA-CL1***](urn:gd:lg:a:select-vm)에서 로그아웃합니다.

4.  [***SEA-WS1***](urn:gd:lg:a:select-vm)로 전환하고 !!
    **Cindy@M365x27131290.onmicrosoft.com**!! 계정으로 로그인하고,
    비밀번호는 !! **P@55w.rd12345**!! 입니다.

5.  **Start**를 선택하고 !! [**Windows
    Security**](urn:gd:lg:a:send-vm-keys)!!를 입력한 다음 Windows 보안
    아이콘 아래에서 **Open**를 선택합니다.

> ![](./media/image25.png)
>
> Intune 정책에 구성된 모든 제한 영역이 표시되지 않습니다.
> [***SEA-WS1***](urn:gd:lg:a:select-vm)은 보안 설정이 적용된 Intune에
> 등록되어 있습니다.
>
> ![A screenshot of a computer Description automatically
> generated](./media/image26.png)

6.  Close **Windows Security** and sign out
    of [***SEA-WS1***](urn:gd:lg:a:select-vm). **Windows Security** 를
    닫고[***SEA-WS1***](urn:gd:lg:a:select-vm)에서 로그아웃합니다.

**결과**: 이 연습을 완료하면 Intune에서 관리되는 장치에 대한 Microsoft
Defender를 구성하는 정책을 성공적으로 만들고 적용하게 됩니다.
