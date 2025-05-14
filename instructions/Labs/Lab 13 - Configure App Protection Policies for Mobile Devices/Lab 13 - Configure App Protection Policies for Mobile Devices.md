실습13: 모바일 기기에 대한 앱 보호 정책 구성

**요약**

이 실습에서는 모바일 기기의 앱 보호 정책을 구성합니다.

**시나리오**

Contoso의 모든 개발자는 최신 iOS/iPadOS 버전을 실행하는 iPhone과 iPad를
보유하고 있습니다. 보안 부서는 데이터 유출을 우려하여 회사 이메일의
데이터가 모바일 기기의 다른 앱으로 복사되는 것을 방지하고자 합니다. 보안
부서의 우려 사항을 해결하는 솔루션을 제공해야 합니다. 다음 사항을
확인해야 합니다:

- Outlook 데이터는 iTunes 또는 iCloud에 백업하는 것이 제한되어야 합니다.

&nbsp;

- 정책 관리 앱만 Outlook에서 데이터를 주고받을 수 있습니다.

&nbsp;

- 정책 관리 앱만 Outlook에서 잘라내기, 복사 또는 붙여넣기 작업을 수행할
  수 있습니다.

&nbsp;

- 사용자는 Outlook에 액세스하려면 회사 또는 학교 계정의 사용자 인증
  정보를 제공해야 합니다.

작업 1: iOS/iPadOS 기기용 앱 보호 정책 만들기

1.  On [***SEA-SVR1***](urn:gd:lg:a:select-vm), if necessary, sign in
    as [**Contoso\Administrator**](urn:gd:lg:a:send-vm-keys) with the
    password !\![**Pa55w.rd**](urn:gd:lg:a:send-vm-keys)!! 필요한 경우
    [***SEA-SVR1***](urn:gd:lg:a:select-vm)에서
    [**Contoso\Administrator**](urn:gd:lg:a:send-vm-keys)로 로그인하고
    비밀번호는 !! [**Pa55w.rd**](urn:gd:lg:a:send-vm-keys)!!입니다.

2.  작업 표시줄에서 **Microsoft Edge**를 선택하고 주소 표시줄에
    **Microsoft Intune admin center**!!
    **https://intune.microsoft.com**!!를 입력한 후 **Enter**키를
    누릅니다.

3.  홈 탭에서 Office 365 테넌트 관리자 자격 증명으로 로그인합니다.

4.  **Microsoft Intune admin center** 페이지에서 **Apps**를 선택합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image1.png)

5.  **Apps | Overview**  블레이드의 **Policy** 아래에서 **App protection
    policies**를 선택합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)

6.  세부 정보 창에서 **+Create policy** 를 선택한 다음 **iOS/iPadOS**를
    선택합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)

7.  **Basics** 탭에서 다음 옵션을 구성하고 **Next**를 선택합니다:

    - Name: !\![**Outlook – Developers**](urn:gd:lg:a:send-vm-keys)!!

    - Description: !\![**Policy to prevent cut/copy and paste from
      Outlook**](urn:gd:lg:a:send-vm-keys)!!

> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

8.  **Apps** 탭에서 + **Select public apps** 선택을 클릭합니다.

9.  **Select apps to target** 블레이드의 텍스트 상자에 !!
    **Outlook**!!을 입력하고 **Microsoft Outlook** 을 선택한 후
    **Select**버튼을 클릭하고 **Next**를 선택합니다.

> ![Screens screenshot of a computer Description automatically
> generated](./media/image5.png)

10. **Data protection**  탭에서 다음 옵션을 구성하고 **Next**를
    선택합니다:

    - Backup Org data to ITunes and iCloud backups: **Block**

    - Send Org data to other apps: **Policy managed apps**

    - Receive data from other apps: **Policy managed apps**

    - Restrict cut, copy, and paste between other apps: **Policy managed
      apps**

> 다른 모든 설정은 기본값으로 두세요
>
> ![](./media/image6.png)

11. **Access requirements**  탭에서 다음 옵션을 구성하고 **Next**를
    선택합니다:

    - PIN for access: **Not required**

    - Work or school account credentials for access: **Require**

> ![A screenshot of a computer Description automatically
> generated](./media/image7.png)

12. **Conditional launch** 탭에서 설정을 검토하고 **Next**를 선택합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)
>
> **참고**: 여기에서 액세스 보호 정책에 대한 로그인 보안 요구 사항을
> 설정할 수 있습니다. 설정을 선택하고 사용자가 회사 앱에 로그인하기 위해
> 충족해야 하는 값을 입력할 수 있습니다. 다양한 설정을 기록해 두되
> 아무것도 변경하지 마세요.

13. **Assignments** 탭에서 **Next**를 선택합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image9.png)

14. **Review + create** 탭에서 설정을 검토하고 **Create**를 선택합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image10.png)

15. **Apps | App protection policies** 블레이드의 세부 정보 창에서
    **Outlook – Developers가** 나열되어 있는지 확인합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)

16. Microsoft Edge를 닫습니다.

**결과**: 이 연습을 완료하면 모바일 기기에 대한 앱 보호 정책을
성공적으로 구성하게 됩니다.
