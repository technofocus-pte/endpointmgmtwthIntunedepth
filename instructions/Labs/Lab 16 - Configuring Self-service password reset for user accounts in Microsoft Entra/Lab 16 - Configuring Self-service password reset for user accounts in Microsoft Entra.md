실습 16 - Microsoft Entra에서 사용자 계정에 대한 셀프 서비스 암호 재설정
구성

**요약**

이 실습에서는 **Microsoft Entra ID** 사용자 계정에 대한 셀프 서비스 암호
재설정(SSPR)을 구성하고 유효성을 검사합니다.

**필수 조건**

이 실습을 시작하기 전에 다음 실습을 완료해야 합니다.:

- 실습 \#2 - Microsoft Entra Connect를 사용하여 ID 동기화

- 실습 \#5 - Microsoft Intune에 장치 등록 관리

**시나리오**

헬프 데스크에서 많은 지원 티켓이 암호 재설정과 관련되어 있다고
밝혔습니다. 사용자가 직접 암호를 재설정할 수 있는 솔루션을 제안해 달라는
요청을 받았습니다. AD DS에서 동기화된 계정의 경우, Microsoft Entra 및 AD
DS 암호가 모두 재설정되어야 합니다.

작업 1: 비밀번호 writeback 구성

1.  [***SEA-SVR1***](urn:gd:lg:a:select-vm)에 !!
    [**Contoso\Administrator**](urn:gd:lg:a:send-vm-keys)!! 계정으로
    로그인하고 비밀번호는 !!
    [**Pa55w.rd**](urn:gd:lg:a:send-vm-keys)!!로 설정합니다. **Server
    Manager**를 닫습니다.

2.  바탕 화면에서 **Azure AD Connect**를 두 번 클릭합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image1.png)

3.  **Welcome to Azure AD Connect** 페이지에서 **Configure**를
    선택합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)

4.  **Additional tasks** 페이지에서 **Customize synchronization
    options**을 선택한 후 **Next**를 선택합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)

5.  **Connect to Azure AD**  페이지에서 필요한 경우 사용자 이름 텍스트
    상자에 !! **admin@M365xXXXXXXX.onmicrosoft.com**!!을 입력하고
    **PASSWORD**를 입력한 후 **Next를** 선택합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

6.  On the **Connect to your directories** page, select **Next**.
    **Connect to your directories** 페이지에서 **Next를** 선택합니다.

7.  **Domain and OU filtering**  페이지에서 **Next**를 선택합니다.

8.  **Optional features** 페이지에서 **Password writeback**을 선택한 후
    **Next**를 선택합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image5.png)

9.  **Ready to configure** 페이지에서 **Configure**를 선택합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image6.png)
>
> ![A computer screen shot of a computer Description automatically
> generated](./media/image7.png)
>
> **참고**: 구성하는 데 몇 분 정도 걸릴 수 있습니다.

10. **Configuration complete** 페이지에서 **Exit**를 선택합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)

작업 2: 셀프 서비스 암호 재설정을 활성화

1.  타스크바에서 **Microsoft Edge**를 선택하고 **Microsoft Entra admin
    center** (**https://Entra.Microsoft.com**.)로 이동합니다.

2.  **Office 365 Tenant admin**자격 증명으로 로그인합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image9.png)
>
> **Microsoft Entra admin center가 열립니다.**

3.  **Microsoft Entra admin center**의 탐색 창에서 **Identity**를 확장한
    다음 **Users**를 선택합니다.

4.  **Users** 탐색 창에서 **Password reset를** 선택합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image10.png)

5.  **Password reset | Properties** 창에서 모든 사용자에게 셀프 서비스
    비밀번호 재설정 기능을 활성화하려면 **All** 를 선택합니다.
    **Save**를 선택합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)
>
> ![A screenshot of a computer screen Description automatically
> generated](./media/image12.png)

6.  **Password reset | Properties**  블레이드에서 **Authentication
    methods**을 선택합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image13.png)

7.  사용자가 사용할 수 있는 방법으로 **Mobile Phone** 및 **Email**이
    선택되어 있는지 확인한 후 **Security Questions**을 선택합니다.

8.  **Number of questions required to register**에서 **3**을 선택합니다.

9.  **Number of questions required to reset**에서 **3을** 선택합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image14.png)

10. **Select security questions** 섹션에서 **No security questions
    configured**을 선택한 후 **Predefined**을 선택합니다. 원하는 보안
    질문 세 개를 선택한 후 **OK**를 두 번 클릭합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image15.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image16.png)

11. **Save**를 선택합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image17.png)

12. **Require users to register when signing in**에서 **Yes**를
    선택하고, **Number of days before users are asked to re-confirm
    their authentication information**을 **90**으로 설정한 다음
    **Save**을 선택합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image18.png)

13. 탐색 창에서 **On-premises integration**을 선택합니다.

14. 온-프레미스 쓰기 저장 클라이언트가 실행 중인지 확인하고 **Enable
    password write back for synced users** " 확인란이 선택되어 있는지
    확인합니다. 필요한 경우 **Save**을 선택합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image19.png)

15. Microsoft Edge를 닫습니다.

작업 3: 셀프 서비스 비밀번호 재설정 확인

1.  [***SEA-WS3***](urn:gd:lg:a:select-vm)으로 전환합니다. 필요한 경우
    !! [**Admin**](urn:gd:lg:a:send-vm-keys)!! 계정으로 로그인하고
    비밀번호는 !! [**Pa55w.rd**](urn:gd:lg:a:send-vm-keys)!!입니다.

2.  타스크바에서 **Microsoft Edge**를 선택합니다. !!
    **https://mysignins.microsoft.com/**!!으로 이동합니다.

3.  **Pick an account**  페이지에서 **Use another account**을
    선택합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image20.png)

4.  **Sign in**  페이지에서 !! **Cindy@M365xXXXXXX.onmicrosoft.com**!!을
    입력하고 **Next**을 선택합니다.

5.  **Enter password** 페이지에서 !! **P@55w.rd1234**!!를 입력하고
    로그인을 선택합니다. Microsoft Edge에서 비밀번호를 저장하라는
    메시지가 표시되면 **Save**을 선택합니다.

> ![A screenshot of a computer error Description automatically
> generated](./media/image21.png)

6.  **More information required**메시지가 표시되면 **Next**을
    클릭합니다.

> ![A screenshot of a computer error Description automatically
> generated](./media/image22.png)

7.  세부 정보를 입력하고 **Next를** 클릭합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image23.png)

8.  6자리 코드를 입력하고 **Next**를 클릭합니다.

> ![](./media/image24.png)

9.  다시 Next를 클릭합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image25.png)

10. **Done**를 클릭합니다.

> ![](./media/image26.png)

11. **My Account** 페이지로 이동할 수 있어야 합니다.

> ![](./media/image27.png)

12. **Password**를 변경하려면
    **!!https://mysignins.microsoft.com/security-info!!**링크를
    방문합니다.

13. +XXXXXXXXXXXXXX 문자를 클릭하여 인증을 완료합니다.

> ![A screenshot of a computer error Description automatically
> generated](./media/image28.png)

14. 6자리 코드를 입력한 후 확인을 클릭합니다.

> ![A screenshot of a computer error Description automatically
> generated](./media/image29.png)

15. **Skip for now**를 클릭합니다.

> ![A screenshot of a computer error Description automatically
> generated](./media/image30.png)

16. 보안 정보 페이지에서 비밀번호 **Change를** 클릭합니다.

> ![A screenshot of a login page Description automatically
> generated](./media/image31.png)

17. **Change your password**  페이지에서 다음 정보를 입력한 후
    **Submit**을 선택합니다:

    - Create new password: **!!P@55w.rd12345!!**

    - Confirm new password: **!!P@55w.rd12345!!**

> ![A screenshot of a login box Description automatically
> generated](./media/image32.png)

18. **Done** 버튼을 클릭합니다.

> ![](./media/image33.png)

19. Microsoft Edge를 닫고 [***SEA-WS3***](urn:gd:lg:a:select-vm)에서
    로그아웃합니다.

작업 4: Azure AD Connect 동기화 실행

이 단계는 일반적으로 비밀번호 쓰기 저장에는 필요하지 않지만 랩 환경에서
내재된 문제를 해결하고 AD DS가 Microsoft Entra와 동기화되도록 하는 데
권장됩니다.

1.  [***SEA-SVR1***](urn:gd:lg:a:select-vm)로 전환하고 **Start**를
    마우스 오른쪽 버튼으로 클릭한 다음 **Windows PowerShell (Admin)**.을
    선택합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image34.png)

2.  **Windows PowerShell** 명령 프롬프트에서 다음 명령을 입력한 다음
    **Enter** 키를 누릅니다:

> **!!Start-ADSyncSyncCycle -PolicyType Delta!!**
>
> ![A screenshot of a computer Description automatically
> generated](./media/image35.png)

3.  Windows PowerShell을 닫고 약 3~4분 동안 기다립니다.

작업 5: 비밀번호 writeback확인

1.  [***SEA-CL1***](urn:gd:lg:a:select-vm)로 전환하고 필요한 경우
    로그아웃합니다. [***SEA-CL1***](urn:gd:lg:a:select-vm)에서 다른
    사용자를 선택한 후 !!Contoso\Cindy!! 계정으로 로그인하고 비밀번호는
    !! **P@55w.rd1234**!!입니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image36.png)

2.  사용자 이름 또는 비밀번호가 올바르지 않다는 메시지가 표시되는지
    확인하세요.

> ![A screenshot of a computer screen Description automatically
> generated](./media/image37.png)

3.  이제 !!**Contoso\Cindy!!** 계정으로 로그인하고, SSPR 기능을 사용하여
    설정한 !!**P@55w.rd12345!!**비밀번호를 사용하세요.

4.  이번에는 **new password**로 성공적으로 로그인될 것입니다.

이렇게 하면 내 로그인 포털에서 변경한 비밀번호가 로컬 Active Directory
domain service(AD DS) 계정에 다시 기록되었음을 확인할 수 있습니다.

![A screenshot of a computer error Description automatically
generated](./media/image38.png)

> 참고 – 로그인 중 위 메시지가 표시되면 인증은 성공했지만 그룹 멤버십
> 문제로 인해 해당 계정에 SEA-CL1 로그인 권한이 없음을 의미합니다.

**결과**: 이 연습을 완료하면 셀프 서비스 비밀번호 재설정을 성공적으로
구성하고 검증할 수 있습니다.
