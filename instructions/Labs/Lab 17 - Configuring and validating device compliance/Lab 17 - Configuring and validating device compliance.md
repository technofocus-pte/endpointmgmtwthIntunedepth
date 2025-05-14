Lab17 - 장치 규정 준수 구성 및 검증

**요약**

이 실습에서는 관리되는 기기의 상태를 확인하는 데 사용되는 규정 준수 정책
및 관련 조건부 액세스 규칙을 구성하여 기기 규정 준수를 검증합니다.

**필수 조건**

이 실습을 시작하기 전에 다음 실습을 완료해야 합니다:

- 실습 1 - Microsoft Entra ID에서 ID 관리

- 실습 2 - Microsoft Entra Connect를 사용하여 ID 동기화

- 실습 5 - Microsoft Intune에 장치 등록 관리

- 실습 6 - Microsoft Intune에 장치 등록

- 실습 7 - 구성 프로필 생성 및 배포

연습 1: 규정 준수 정책 구성

**시나리오**

Contoso는 Microsoft Intune에 등록된 Windows 기기가 최소 구성 사양을
충족하는지 확인하고자 합니다. 필요한 사양은 다음과 같습니다:

- 최소 Windows 운영 체제 버전: 10.0.19041.329

- Microsoft Defender Antimalware 필수

장치가 이러한 요구 사항을 충족하면 준수로 표시됩니다. 장치가 이러한 요구
사항을 충족하지 않으면 비준수로 표시됩니다.

작업 1: 준수 정책 생성 및 할당

1.  [***SEA-SVR1***](urn:gd:lg:a:select-vm)에 !!
    [**Contoso\Administrator**](urn:gd:lg:a:send-vm-keys)!! 계정으로
    로그인하고, 비밀번호는 !!
    [**Pa55w.rd**](urn:gd:lg:a:send-vm-keys)!!입니다.

2.  타스크바에서 **Microsoft Edge**를 선택합니다. Microsoft Edge의 주소
    표시줄에 !! **https://Intune.microsoft.com**!!을 입력하고
    **Enter**키를 누릅니다.

3.  **Office 365 Tenant Admin credentials**으로 로그인합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image1.png)

4.  탐색 창에서 **Devices**를 선택한 다음 장치 관리에서 **Compliance**를
    선택합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)

5.  **Compliance | Policies**  블레이드의 세부 정보 창에서 **+ Create
    Policy**를 선택합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)

6.  **Create a policy** 블레이드에서 다음 값을 입력하고 **Create**를
    선택합니다:

    - Platform: **Windows 10 and later**

> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

7.  **Basics** 탭에서 다음 값을 입력하고 **Next**를 선택합니다:

    - Name: !!**[Compliance1](urn:gd:lg:a:send-vm-keys)!!**

> ![](./media/image5.png)

8.  **Compliance settings**  탭에서 **Device Health** 를 확장하고 사용
    가능한 설정을 검토합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image6.png)

9.  **Compliance settings** 탭에서 **Device Properties**을 확장합니다.
    **Minimum OS version**필드에 !!
    [**10.0.19041.329**](urn:gd:lg:a:send-vm-keys)!!를 입력합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image7.png)

10. **Compliance settings** 탭에서 **System Security**를 확장합니다.
    **Microsoft Defender Antimalware** 설정을 **Require**로 설정하고
    **Next**를 선택합니다.

> ![](./media/image8.png)

11. **Actions for noncompliance**탭에서 **Mark device
    noncompliant**작업이 기본 설정으로 **immediately** 설정되어 있는지
    확인합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image9.png)
>
> 장치가 비준수로 표시되는 일수를 설정하는 방법과 추가 작업을 구성하는
> 방법을 검토합니다.

12. **Next**를 선택합니다. **Assignments**탭에서 **Add groups**를
    선택합니다. **Windows Devices**를 선택하고 **Select**를 선택한 후
    **Next**를 선택합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image10.png)
>
> **참고:** **Windows 장치 그룹**은 구성 프로필 생성 및 배포 - 실습에서
> 생성되었습니다.

13. **Create를 선택합니다**.

> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)

14. 탐색 메뉴에서 **Devices**를 선택한 다음 장치 탐색 창에서
    **Compliance**를 선택합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image12.png)

15. **Compliance** 페이지에서 **Compliance settings**.를 선택합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image13.png)

16. **Compliance policy settings** 페이지에서 **Mark devices with no
    compliance policy assigned as**옆의 **Not Compliant**를 선택한 다음
    **Save**를 선택합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image14.png)
>
> 이 설정을 사용하면 규정 준수 정책이 할당되지 않은 모든 장치가 **Not
> compliant**으로 설정됩니다.

**결과**: 이 연습을 완료하면 규정 준수 정책을 성공적으로 구성하게
됩니다.

연습 2: 규정 준수를 강제하는 조건부 액세스 정책 생성

**시나리오**

사용자가 규정 미준수로 표시된 기기를 사용하는 경우 이메일에 액세스할 수
없어야 합니다. 이 규칙을 적용하는 조건부 액세스 정책을 구성하고 예상대로
작동하는지 확인하라는 요청을 받았습니다.

작업 1: 조건부 액세스 정책 만들기

1.  [***SEA-SVR1***](urn:gd:lg:a:select-vm)의 **Microsoft Intune admin
    center** 에서 **Devices**를 선택한 다음 **Conditional access를**
    선택합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image15.png)

2.  **Policies**를 클릭한 다음 **+ New policy**를 선택합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image16.png)

3.  **New** 블레이드의 **Name** 텍스트 상자에 !! Conditional1!!을 입력한
    다음 **0 users or workload identities selected**을 선택합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image17.png)

4.  **Users and groups**  블레이드에서 **All users** 라디오 버튼을
    선택합니다.

> ![A screenshot of a computer screen Description automatically
> generated](./media/image18.png)

5.  **New** 만들기 블레이드에서 **No target resources selected**를
    선택하고, **Select apps** 라디오 버튼을 선택하고, !! **Office 365
    Exchange Online**!!을 선택한 다음 **Select**를 클릭합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image19.png)

6.  **New** 블레이드의 **Conditions** 섹션에서 **0 conditions
    selected**을 선택합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image20.png)

7.  조건 목록의 **Device platforms**에서 **Not configured**을
    선택합니다. **Configure**섹션에서 **Yes**를 선택하고, **Select
    device platforms** 라디오 버튼을 선택한 후 **Windows**확인란을
    선택하고 **Done**를 선택합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image21.png)

8.  **New**블레이드의 **Access controls**아래에 있는 **Grant**섹션에서
    **0 controls selected**를 선택합니다.

9.  **Require device to be marked as compliant**  확인란을 선택한 다음
    **Select**를 선택합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image22.png)

10. **New**  블레이드에서 **Enable policy**  옵션에 대해 **On**를 선택한
    다음 **Create**를 선택합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image23.png)

11. Microsoft Edge를 닫습니다.

작업 2: 조건부 액세스 정책이 작동하는지 확인

1.  [***SEA-WS3***](urn:gd:lg:a:select-vm)으로 전환하고 !!
    [**Admin**](urn:gd:lg:a:send-vm-keys)!! 계정으로 로그인하고
    비밀번호는 !! [**Pa55w.rd**](urn:gd:lg:a:send-vm-keys)!!입니다.

2.  [***SEA-WS3***](urn:gd:lg:a:select-vm)의 작업 표시줄에서 **Microsoft
    Edge**를 선택합니다. Microsoft Edge에서
    [**outlook.office.com**](urn:gd:lg:a:send-vm-keys)을 입력하고 Enter
    키를 누릅니다.

3.  계정 선택 대화 상자에서 !!
    **Cindy@M365xXXXXXXX.onmicrosoft.com**!!을 선택합니다.

4.  **Enter password** 페이지에서 !! **P@55w.rd12345**!!를 입력하고
    **Sign in**을 선택합니다. Microsoft Edge에서 비밀번호 저장 메시지가
    나타나면 **Update**를 선택합니다.

> ![A screenshot of a computer error Description automatically
> generated](./media/image24.png)

5.  **"** **Sign in with your work account"**라는 메시지가 표시되는지
    확인합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image25.png)

6.  **More details**를 선택합니다. 차단 사유에 대한 자세한 정보를
    확인하실 수 있습니다.

> ![A screenshot of a computer error Description automatically
> generated](./media/image26.png)
>
> **참고**: SEA-WS3는 Microsoft Entra ID에 가입되어 있지 않고 Microsoft
> Intune에서 관리되지 않으므로 호환되는 것으로 표시되지 않습니다.

7.  브라우저 창을 **닫습니다**.

8.  [***SEA-WS1***](urn:gd:lg:a:select-vm)로 전환하고 !!
    **Cindy@M365xXXXXXXX.onmicrosoft.com**!! 계정으로 로그인하고
    **password** 페이지에서 !! **P@55w.rd12345**!!를 입력합니다.

> **참고**: SEA-WS1은 Intune에 등록된 관리형 Windows 11 기기입니다.

9.  작업 표시줄에서 **Microsoft Edge**를 선택합니다. Microsoft Edge에
    [**Outlook.office.com**](urn:gd:lg:a:send-vm-keys)을 입력하고
    **Enter** 키를 누릅니다.

10. Cindy의 사서함에 액세스할 수 있는지 확인합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image27.png)
>
> **Note** 이는 **SEA-WS1**이 관리되는 장치이며 규정 준수로 표시되었기
> 때문입니다.

11. Microsoft Edge를 닫고 [***SEA-WS1***](urn:gd:lg:a:select-vm)에서
    로그아웃합니다.

작업 3: 조건부 액세스 정책 비활성화

1.  [***SEA-SVR1***](urn:gd:lg:a:select-vm)의 **Microsoft Intune admin
    center** !\!<https://intune.microsoft.com>!!에서 **Devices**를
    선택한 다음 **All devices**를 선택합니다.

> ![](./media/image28.png)
>
> SEA-WS1이 규정을 준수하므로 Cindy가 사서함에 액세스할 수 있었습니다.

2.  탐색 창에서 **Devices**를 선택한 다음 **Conditional access**를
    선택합니다.

> ![](./media/image29.png)

3.  **Conditional Access** 페이지에서 **Policies**를 선택한 다음
    **Conditional1**를 클릭합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image30.png)

4.  **Conditional1**  페이지 하단에서 **Off** 를 선택한 다음 **Save**를
    선택합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image31.png)

5.  Microsoft Edge를 닫습니다.

**결과**: 이 연습을 완료하면 장치 규정 준수 여부를 확인하기 위한 조건부
액세스 정책을 성공적으로 구성하게 됩니다.
