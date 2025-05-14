실습 22: Configuration Manager를 사용하여 클라우드 연결 및 공동 관리
구성

**요약**

이 실습에서는 Microsoft Endpoint Configuration Manager와 Microsoft
Intune을 사용하여 클라우드 연결을 활성화하고 공동 관리를 구성합니다.

**필수 조건**

이 실습을 시작하기 전에 다음 랩을 완료해야 합니다.:

- 실습 1 - Microsoft Entra ID에서 ID 관리

- 실습 2 - Azure AD Connect를 사용하여 ID 동기화

- 실습 3 - Microsoft Entra ID 조인 구성 및 관리

- 실습 5 - Intune에 디바이스 등록 관리

**시나리오**

Contoso는 Microsoft Endpoint Configuration Manager 구현과 Microsoft
Intune을 모두 보유하고 있습니다. 두 서비스 간의 통합을 구성하고 관리되는
Windows 장치에 대한 공동 관리를 활성화해야 합니다. Cloud Attach를
활성화하고 공동 관리를 구성한 다음 SEA-CL1을 사용하여 설정을 검증합니다.

작업 1: 환경 준비

1.  [***SEA-SVR1***](urn:gd:lg:a:select-vm)로 전환하고
    [**Contoso\Administrator**](urn:gd:lg:a:send-vm-keys)로 로그인하며
    비밀번호는 !! [**Pa55w.rd**](urn:gd:lg:a:send-vm-keys)!!입니다.

2.  서버 관리자에서 **Tools**를 선택한 다음 **Active Directory Users and
    Computers**를 선택합니다.

> ![](./media/image1.png)

3.  탐색 창에서 **Seattle Clients**를 선택합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)

4.  **SEA-CL1**을 마우스 오른쪽 버튼으로 클릭한 다음 **Move**를
    선택합니다.

> ![A computer screen shot of a computer Description automatically
> generated](./media/image3.png)

5.  **Move** 대화 **Entra clients**를 선택한 다음 **OK**를 선택합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

6.  **Active Directory Users and Computers**를 닫습니다.

7.  타스크바에서 **Start**를 마우스 오른쪽 버튼으로 클릭하고 **Windows
    Powershell (Admin)**을 선택합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image5.png)

8.  **Windows PowerShell**  창에서 다음 명령을 입력한 다음 **Enter**
    키를 누릅니다:

> !!**Start**-ADSyncSyncCycle -PolicyType **Initial**!!
>
> ![A screenshot of a computer screen Description automatically
> generated](./media/image6.png)

9.  PowerShell 창을 닫습니다.

10. [***SEA-CL1***](urn:gd:lg:a:select-vm)로 전환합니다.

11. 타스크바에서 **Start**를 마우스 오른쪽 버튼으로 클릭하고 **Shut down
    or sign out**을 선택한 다음 **Restart**을 선택합니다.

> ![](./media/image7.png)
>
> **참고**: 재부팅하면 SEA-CL1에서 하이브리드 Azure AD 조인이
> 시작됩니다.

12. [***SEA-CL1***](urn:gd:lg:a:select-vm) 이 재시작되면
    [**Contoso\Administrator**](urn:gd:lg:a:send-vm-keys)계정으로
    로그인하고 비밀번호는
    [**Pa55w.rd**](urn:gd:lg:a:send-vm-keys)입니다.

13. 타스크바에서 **Start를** 마우스 오른쪽 버튼으로 클릭하고 **Windows
    Terminal (Admin)**을 선택합니다.

> ![](./media/image8.png)

14. **Windows PowerShell** 창에서 다음 명령을 입력하고 **Enter** 키를
    누릅니다:

15. !!dsregcmd /status!!

> !!dsregcmd /**status**!!

16. **Device State**아래의 출력에서 **AzureAdJoined : YES**와
    **DomainJoined : YES**가 표시되는지 확인합니다.

> ![](./media/image9.png)
>
> **참고**: 장치가 아직 Azure AD에 가입되지 않은 경우 Azure AD Connect
> 동기화가 완료될 때까지 기다린 후 SEA-CL1을 reboot하세요.

17. [***SEA-CL1***](urn:gd:lg:a:select-vm)의 모든 창을 닫습니다.

작업 2: 장치 컬렉션 만들기

1.   [***SEA-CFG1***](urn:gd:lg:a:select-vm)로 전환하고
    [**Contoso\Administrator**](urn:gd:lg:a:send-vm-keys)로 로그인하며
    암호는 [**Pa55w.rd**](urn:gd:lg:a:send-vm-keys)입니다.

2.  작업 표시줄에서 **Configuration Manager Console**을 선택하세요.
    Microsoft Endpoint Configuration Manager 콘솔이 열립니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image10.png)

3.  **Assets and Compliance** 작업 영역에서 **Device Collections를**
    선택합니다.

4.  **Device Collections** 을 마우스 오른쪽 버튼으로 클릭하고 **Create
    Device Collection**를 선택합니다. Create Device Collection Wizard가
    열립니다.

> ![](./media/image11.png)

5.  **General** 페이지에서 다음을 구성한 후 **Next**:를 선택합니다:

    - Name: !\![**Co-managed Devices**](urn:gd:lg:a:send-vm-keys)!!

    - Limiting collection: **All Desktop and Server Clients**

> ![](./media/image12.png)
>
> ![](./media/image13.png)
>
> ![](./media/image14.png)

6.  **Membership Rules**  페이지에서 **Next**를 선택합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image15.png)

7.  구성 관리자 경고에서 **OK**를 선택합니다. 직접 구성원은 이후
    단계에서 추가합니다.

> ![A screenshot of a computer error Description automatically
> generated](./media/image16.png)

8.  **Summary**페이지에서 **Next**를 선택한 다음 **Completion**
    페이지에서 **Close**를 선택합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image17.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image18.png)

작업 3: 기존 컬렉션에 장치 할당

1.  **Assets and Compliance** 작업 영역에서 **Devices**를 선택합니다.

> 나열된 장치를 확인합니다. 녹색 원 안에 흰색 확인 표시가 있는 장치는
> 현재 활성화되어 있습니다.

2.  세부 정보 창에서 **SEA-CL1**을 선택합니다.

3.  **SEA-CL1**을 마우스 오른쪽 버튼으로 클릭하고 **Add Selected
    Items**를 가리킨 다음 **Add Selected Items to Existing Device
    Collection**를 선택합니다.

> ![](./media/image19.png)

4.  **Select Collection**  대화 상자에서 **Co-managed Devices**를 선택한
    다음 **OK**를 선택합니다.

> ![](./media/image20.png)

5.  확인하려면 **Assets and Compliance** 작업 영역에서 **Device
    Collections** 을 선택한 다음 **Co-managed Devices**를 두 번
    클릭합니다.

> ![](./media/image21.png)
>
> ![](./media/image22.png)
>
> **SEA-CL1**이 이 컬렉션의 구성원으로 나열되어야 합니다.

작업 4: 클라우드 연결 Endpoint Configuration Manager

1.  Microsoft Endpoint Configuration Manager 콘솔에서 **Administration**
    작업 영역을 선택합니다.

> ![](./media/image23.png)

2.  **Administration** 작업 영역에서 **Cloud Services** 를 확장한 다음
    **Cloud Attach**을 선택합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image24.png)

3.  리본 메뉴에서 **Configure Cloud Attach**을 선택합니다. **Cloud
    Attach Configuration Wizard**가 열립니다.

> ![](./media/image25.png)
>
> ![](./media/image26.png)

4.  **Cloud Attach Configuration Wizard**의 **Cloud attach** 페이지에서
    **Sign In**을 선택합니다.

5.  Sign in
    as [**admin@M365x19242953.onmicrosoft.com**](urn:gd:lg:a:send-vm-keys) with
    the password [**9whL~;H8ke=D1^95%D**](urn:gd:lg:a:send-vm-keys).

6.  **Cloud attach** 페이지에서 **Customize settings**을 선택하고
    **Next**를 선택합니다.

> ![](./media/image27.png)

7.  **Create AAD Application** 경고에서 **Yes**를 선택합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image28.png)

8.  **Configure upload** 페이지에서 기본값을 수락하고 **Next**를
    선택합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image29.png)

9.  **Enablement**페이지에서 **Automatic enrollment in Intune** 옆의
    **Pilot**을 선택합니다.

10. **Enablement**페이지에서 **Intune Auto Enrollment** 옆의
    **Browse**를 선택합니다.

> ![](./media/image30.png)

11. **Select Collection**  대화 상자에서 **Co-managed Devices** 를
    선택한 후 **OK**를 선택합니다. **Next**을 선택합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image31.png)

12. **Summary** 페이지에서 **Next**을 선택한 다음 **Completion**
    페이지에서 **Close**를 선택합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image32.png)

작업 5: 워크로드 구성

1.  Microsoft Endpoint Configuration Manager 콘솔에서
    **Administration**  작업 영역을 선택합니다.

2.  **Administration** 작업 영역에서 **Cloud Services**를 확장한 다음
    **Cloud Attach**을 선택합니다.

3.  세부 정보 창에서 **CoMgmtSettingsProd** 를 선택한 다음 리본에서
    **Properties**를 선택합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image33.png)
>
> **CoMgmtSettingsProd Properties** 상자가 열립니다.

4.  **Workloads**를 선택합니다. **Workloads** 페이지에서 다음 워크로드에
    대해 슬라이더를 **Pilot Intune**으로 드래그합니다:

    - **Compliance policies**

    - **Client apps**

    - **Windows Update policies**

> ![](./media/image34.png)

5.  **Staging page**를 선택합니다. **Staging**  페이지에서 **Compliance
    policies**, **Client Apps**및 **Windows Update Policies** 옆의
    **Browse**를 선택하고 각 작업에 대해 **Co-managed Devices** 컬렉션을
    선택합니다.

6.  **OK를** 선택하여 **CoMgmtSettingsProd Properties** 상자를 닫습니다.

> ![](./media/image35.png)

작업 6: SEA-CL1이 공동 관리되는지 확인

1.  [***SEA-SVR1***](urn:gd:lg:a:select-vm)로 전환합니다.

2.  작업 표시줄에서 **Microsoft Edge**를 선택하고 주소 표시줄에
    [**https://entra.microsoft.com**](https://entra.microsoft.com)을
    입력한 다음 **Enter**키를 누릅니다.

3.  [**admin@M365x19242953.onmicrosoft.com**](urn:gd:lg:a:send-vm-keys)사용자로
    로그인하고 비밀번호를 사용합니다.

4.  **Stay signed in?** 메시지가 나타나면 **No**를 선택합니다.

> Microsoft Entra 관리 센터가 열립니다.

5.  Microsoft Entra 관리 센터의 탐색 창에서 **Identity** 를 선택합니다.

> ![](./media/image36.png)

6.  **Devices|All devices**  페이지에서 **SEA-CL1** 이 나열되어 있고
    **Join Type** 가 **Microsoft Entr hybrid Join**인지 확인합니다.

> ![](./media/image37.png)

7.  Microsoft Edge에서 다른 탭을 열고 주소 표시줄에
    [**https://intune.microsoft.com**](https://intune.microsoft.com)을
    입력한 다음 **Enter** 키를 누릅니다.

8.  탐색 창에서 **Devices**를 선택한 다음 **All devices**를 선택합니다.

9.  **Managed by**설정이 **Co-managed**로 설정된 **SEA-CL1**이 나열되어
    있는지 확인합니다.

> ![](./media/image38.png)
>
> 표시되는 데 시간이 걸릴 수 있습니다. 필요에 따라 세부 정보 창을 새로
> 고치세요. 기기가 다른 이름으로 표시될 수 있습니다. 기기를 클릭하여
> **SEA-CL1**로 표시되는지 확인하세요.

10. **SEA-CL1**을 선택하고 details pane에서 아래로 스크롤하여 공동 관리
    상태 관련 정보를 확인합니다.

11. Microsoft Edge를 닫습니다.

**결과**: 이 연습을 완료하면 Microsoft Endpoint Configuration Manager와
Microsoft Intune을 사용하여 Cloud Attach를 성공적으로 활성화하고 공동
관리를 구성할 수 있습니다.
