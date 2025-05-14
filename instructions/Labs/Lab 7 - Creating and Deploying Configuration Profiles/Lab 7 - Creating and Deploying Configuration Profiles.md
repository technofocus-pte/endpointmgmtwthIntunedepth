**실습 7 - 구성 프로필 생성 및 배포**

**요약**

이 실습에서는 Microsoft Intune을 사용하여 Windows 11 장치에 대한 구성
프로필을 만들고 적용합니다.

**필수 조건**

이 실습을 시작하기 전에 다음 실습을 완료해야 합니다:

- 실습 \#1 - Microsoft Entra ID에서 ID 관리

- 실습 \#2 - Microsoft Entra Connect를 사용하여 ID 동기화

- 실습 \#5 - Microsoft Intune에 장치 등록 관리

- 실습 \#6 - Microsoft Intune에 장치 등록

참고: Microsoft Entra ID에 대한 Windows Hello 로그인 인증을 보호하는 데
사용되는 문자 메시지를 수신할 수 있는 휴대폰도 필요합니다.

**연습 1: 구성 프로필 생성 및 적용**

**시나리오**

Contoso의 개발자 부서 구성원을 관리하려면 Microsoft Entra와 Microsoft
Intune을 사용해야 합니다. Windows 11 기기에서 사용자가 효과적이고
안전하게 작업할 수 있도록 지원하는 솔루션을 평가해 달라는 요청을
받았습니다. Cindy White는 솔루션 테스트 및 평가와 피드백 제공을 지원해
주었습니다. 또한 개발자의 Windows 기기에 포함하고 적용해야 하는 몇 가지
초기 요구 사항을 제시했습니다:

- 설정의 게임 섹션이 표시되지 않아야 합니다.

- 설정의 개인 정보 보호 섹션은 최대한 제한되어야 합니다.

- **C:\DevProjects** 폴더는 Windows Defender에서 제외되어야 합니다.

- devbuild.exe 프로세스는 Windows Defender에서 제외되어야 합니다.

- 가장 많이 사용된 앱과 최근에 추가된 앱은 시작 메뉴에 표시되지 않아야
  합니다.

**작업 1: 장치 설정 확인**

1.  **Cindy White**라는 계정으로
    [*SEA-WS1*](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)에
    로그인합니다. 계정 정보는 !!
    **Cindy@M365xXXXXXX.onmicrosoft.com**!!이고 PIN은 !! **102938**!!,
    비밀번호는 !! **P@55w.rd1234**!!입니다.

![A screenshot of a computer Description automatically
generated](./media/image1.png)

2.  작업 표시줄에서 **Start**를 선택한 다음 **Settings**를 선택합니다.

![A screenshot of a computer Description automatically
generated](./media/image2.png)

3.  **Settings** 탐색 목록에서 **Gaming** 설정이 보이는지 확인합니다.

![A screenshot of a computer Description automatically
generated](./media/image3.png)

4.  **Personalization**설정을 선택한 다음, 개인 설정 페이지에서
    **Start를** 선택합니다. **Show recently added apps**  및 " **Show
    most used apps**설정을 기록해 둡니다.

![](./media/image4.png)

![A screenshot of a computer Description automatically
generated](./media/image5.png)

5.  **Settings**앱에서 ' **Privacy & security**을 선택합니다.

6.  **Privacy & security**페이지에서 **Security**, **Windows
    permissions**, **App permissions**아래의 옵션을 확인합니다.

![A screenshot of a computer Description automatically
generated](./media/image6.png)

7.  **Privacy & security** 페이지에서 **Windows Security** 를 선택한
    다음 **Open Windows Security**를 선택합니다.

![](./media/image7.png)

![A screenshot of a computer security Description automatically
generated](./media/image8.png)

8.  **Windows Security** 페이지에서 **Virus & threat protection**를
    선택합니다.

9.  **Virus & threat protection** 페이지의 **Virus & threat protection
    settings**에서 **Manage settings**를 선택합니다.

![A screenshot of a computer Description automatically
generated](./media/image9.png)

10. **Exclusions**까지 아래로 스크롤하여 **Add or remove exclusions**를
    선택합니다. User Account Control대화 상자에서 **Yes**를 선택합니다.

![A screenshot of a computer Description automatically
generated](./media/image10.png)

![A screenshot of a computer Description automatically
generated](./media/image11.png)

11. **Exclusions** 페이지에서 제외가 구성되어 있지 않은지 확인하세요.

12. **Windows Security**  창을 닫습니다.

![A screenshot of a computer Description automatically
generated](./media/image12.png)

13. **Settings**창을 닫습니다.

**작업 2: 시나리오 요구 사항에 따라 구성 프로필 만들기**

1.  [*SEA-SVR1*](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)로
    전환합니다.

2.  **Microsoft Intune admin center**가 열린 탭으로 돌아가 탐색 모음에서
    **Devices**를 선택합니다.

![A screenshot of a computer Description automatically
generated](./media/image13.png)

3.  **Devices | Overview** 페이지에서 아래 이미지와 같이 **Windows**를
    선택합니다.

![A screenshot of a computer Description automatically
generated](./media/image14.png)

4.  **Windows | Windows devices**페이지에서 **Configuration profiles**을
    찾아 클릭합니다.

![A screenshot of a computer Description automatically
generated](./media/image15.png)

5.  **Windows | Configuration profiles**페이지의 **Policies** 탭에서 +
    **Create**를 클릭하고 + **New Policy를** 선택합니다.

![A screenshot of a computer Description automatically
generated](./media/image16.png)

6.  오른쪽에 나타나는 **Create a profile** 창에서 다음 옵션을 선택한
    다음 **Create**를 선택합니다:

- Platform: **Windows 10 and later**

- Profile type: **Templates**

- Template name: !!!!

![A screenshot of a profile Description automatically
generated](./media/image17.png)

7.  **Basics**블레이드에서 다음 정보를 입력한 후 **Next를** 선택합니다:

- Name: !!Contoso Developer - standard!!

- Description: !!Basic restrictions and configuration for Contoso
  Developers.!!

![](./media/image18.png)

8.  **Configurations settings**  블레이드에서 **Control Panel and
    Settings**을 확장합니다.

![A screenshot of a computer Description automatically
generated](./media/image19.png)

9.  **Gaming**  및 **Privacy** 옵션 옆에 있는 **Block**를 선택합니다.

![A screenshot of a computer Description automatically
generated](./media/image20.png)

10. **Device restrictions**  블레이드에서 **Start**를 확장합니다.

![A screenshot of a computer Description automatically
generated](./media/image21.png)

11. 아래로 스크롤하여 **Most used apps**, **Recently added apps**,
    **Recently opened items in Jump Lists** 옆에 있는 **Block**를
    선택합니다.

![A screenshot of a computer Description automatically
generated](./media/image22.png)

12. **Device restrictions**블레이드에서 아래로 스크롤하여 **Microsoft
    Defender Antivirus**를 확장합니다.

![A screenshot of a computer Description automatically
generated](./media/image23.png)

13. **Microsoft Defender Antivirus**에서 아래로 스크롤하여 **Microsoft
    Defender Antivirus Exclusions**를 확장합니다.

![](./media/image24.png)

14. **Microsoft Defender Antivirus Exclusions**  항목에서 아래 세부
    정보를 입력하고 **Next** 버튼을 클릭합니다:

- Files and folders box - !!**C:\DevProjects**!!

- Processes box - !!**DevBuild.exe**!!

![](./media/image25.png)

15. **Assignments** 탭에서 **Next**버튼을 클릭합니다.

![A screenshot of a computer Description automatically
generated](./media/image26.png)

16. **Applicability Rules**탭에서 **Next** 버튼을 클릭합니다.

![A screenshot of a computer Description automatically
generated](./media/image27.png)

17. **Review + create** 탭에서 **Create** 버튼을 클릭합니다.

![A screenshot of a computer Description automatically
generated](./media/image28.png)

18. 구성 프로필이 이제 나열되어야 합니다.

![A screenshot of a computer Description automatically
generated](./media/image29.png)

**작업 3: Contoso Developer 장치 그룹 만들기**

1.  Microsoft Intune admin center의 탐색 창에서 **Groups**을 선택합니다.

![A screenshot of a computer Description automatically
generated](./media/image30.png)

2.  **Groups | All groups**  블레이드에서 **New group**을 선택합니다.

![A screenshot of a computer Description automatically
generated](./media/image31.png)

3.  **New Group** 블레이드에서 다음 정보를 입력합니다.

- Group type: **Security**

- Group name: !!Contoso Developer devices!!

- Group description: !!All Windows devices in Contoso Developer
  department!!

- Membership type: **Assigned**

4.  **Members**에서 **No members selected**을 선택합니다.

![](./media/image32.png)

5.  **Add members** 블레이드에서 **Search** 상자에 !! Sea!!를
    입력합니다. **SEA-WS1** 을 선택한 후 **Select를** 클릭합니다.

![A screenshot of a computer Description automatically
generated](./media/image33.png)

6.  **New Group** 블레이드에서 **Create**를 선택합니다.

![](./media/image34.png)

7.  **Groups | All groups**  블레이드에서 **Contoso developer
    devices**그룹이 표시되는지 확인합니다.

![](./media/image35.png)

**작업 4: 동적 Azure AD 장치 그룹 만들기**

1.  **Groups | All Groups** 블레이드의 세부 정보 창에서 **New group**을
    선택합니다.

![A screenshot of a computer Description automatically
generated](./media/image36.png)

2.  **Group**블레이드에서 다음 값을 입력합니다:

- Group type: **Security**

- Group name: !!Windows Devices!!

- Membership type: **Dynamic Device**

3.  **Dynamic Device Members**  섹션에서 **Add dynamic query**를
    선택합니다.

![A screenshot of a computer Description automatically
generated](./media/image37.png)

4.  **Dynamic membership rules**  블레이드의 **Rule syntax** 섹션에서
    **Edit**를 선택합니다.

![A screenshot of a computer Description automatically
generated](./media/image38.png)

5.  **Edit rule syntax** 텍스트 상자에 다음과 같은 간단한 멤버십 규칙을
    추가하고 **OK를** 선택합니다.

!!**(device.deviceOSType -contains "Windows")**!!

![A screenshot of a computer Description automatically
generated](./media/image39.png)

6.  **Dynamic membership rules** 블레이드에서 **Save**를 선택합니다.

![A screenshot of a computer Description automatically
generated](./media/image40.png)

7.  **New Group**페이지에서 **Create**를 선택합니다.

![A screenshot of a computer Description automatically
generated](./media/image41.png)

**작업 5: Windows 장치에 구성 프로필 할당**

1.  **Microsoft Intune admin center** 페이지의 탐색 모음에서
    **Devices**를 선택합니다.

![](./media/image42.png)

2.  **Devices | Overview** 페이지에서 아래 이미지와 같이 **Windows**를
    선택합니다.

![](./media/image43.png)

3.  **Windows | Windows devices**페이지에서 **Configuration profiles**를
    찾아 클릭합니다.

![](./media/image44.png)

4.  **Devices | Configuration profiles**  블레이드의 세부 정보 창에서
    **Contoso Developer – standard** 프로필을 선택합니다.

![A screenshot of a computer Description automatically
generated](./media/image45.png)

5.  **Contoso Developer – standard** 블레이드에서
    **Assignments**섹션까지 아래로 스크롤하여 **Edit**을 선택합니다.

![A screenshot of a computer Description automatically
generated](./media/image46.png)

6.  할당 페이지의 **Included groups** 에서 **Add groups를** 선택합니다.

![A screenshot of a computer Description automatically
generated](./media/image47.png)

7.  **Select groups to include** 블레이드에서 **Search** 상자에 !!
    **Contoso Developer devices**!!를 입력하고 선택한 다음 **Select**
    버튼을 클릭합니다.

![](./media/image48.png)

14. **Device restrictions** 블레이드로 돌아가서 **Review + save**를
    선택한 다음 **Save**를 선택합니다.

![A screenshot of a computer Description automatically
generated](./media/image49.png)

![](./media/image50.png)

**작업 6: 구성 프로필이 적용되었는지 확인**

1.  [*SEA-WS1*](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)로
    전환합니다. Cindy White의 계정으로 로그인합니다.

- Username - !!**Cindy@M365xXXXXXXX.onmicrosoft.com**!!

- Password – !!**P@55w.rd1234**!!

2.  작업 표시줄에서 **Start**를 선택한 다음 **Settings**를 선택합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)

3.  **Settings** 창에서 '계정'을 선택합니다. **Accounts**페이지에서
    **Access work or school**을 선택합니다.

![A screenshot of a computer Description automatically
generated](./media/image51.png)

4.  **Connected to Contoso’s Azure AD** 옆에 있는 드롭다운을 클릭하고
    **Info** 버튼을 선택합니다.

![](./media/image52.png)

5.  **Managed by Contoso**  페이지에서 아래로 스크롤하여 "장치 동기화
    상태" 아래에서 **Sync**를 선택합니다. 동기화가 완료될 때까지
    기다립니다.

6.  ![A screenshot of a computer Description automatically
    generated](./media/image53.png)

![A screenshot of a computer Description automatically
generated](./media/image54.png)

7.  **Settings** 앱을 닫습니다.

> **참고**: 프로필이 Windows 11 기기에 적용되기까지 동기화 진행률은 최대
> 15분까지 걸릴 수 있습니다. 기기를 로그아웃하거나 다시 시작하면 동기화
> 속도를 높일 수 있습니다.

8.  [*SEA-WS1*](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)에서
    **Start**를 다시 선택한 다음 **Settings**를 선택합니다.
    **Gaming** 설정이 제거되었는지 확인합니다.

![A screenshot of a computer Description automatically
generated](./media/image2.png)

![A screenshot of a computer Description automatically
generated](./media/image55.png)

9.  **Privacy & security** 를 선택하면 많은 개인정보 보호 설정이 숨겨져
    있는 것을 확인할 수 있습니다.

![](./media/image56.png)

10. **Personalization** 설정을 선택한 다음 **Start**를 선택합니다.
    **Show recently added apps**및 **Show most used apps**  표시가
    **Off**으로 설정되어 있고 회색으로 표시되어 있는지 확인합니다.

![](./media/image57.png)

![A screenshot of a computer Description automatically
generated](./media/image58.png)

11. **Settings** 앱에서 **Privacy and Security**을 선택합니다.

12. **Privacy & Security** 페이지에서 **Windows Security** 를 선택한
    다음 **Open Windows Security**를 선택합니다.

![](./media/image59.png)

![A screenshot of a computer security Description automatically
generated](./media/image60.png)

13. **Windows Security** 페이지에서 **Virus & threat protection**를
    선택합니다.

14. **Virus & threat protection**페이지에서 **Virus & threat protection
    settings** 아래의 **Manage settings** 를 선택합니다.

![A screenshot of a computer Description automatically
generated](./media/image9.png)

15. **Exclusions**까지 아래로 스크롤하여 **Add or remove exclusions**를
    선택합니다. 사용자 계정 컨트롤 메시지가 나타나면 **Yes** 를
    선택합니다.

![A screenshot of a computer Description automatically
generated](./media/image61.png)

![A screenshot of a computer Description automatically
generated](./media/image62.png)

16. **Exclusions** 페이지에서 **C:\DevProjects** 및 **DevBuild.exe**가
    표시되는지 확인합니다.

![A screenshot of a computer Description automatically
generated](./media/image63.png)

17. **Windows Security**  페이지를 닫은 다음 **Settings** 앱을 닫습니다.

**결과**: 이 연습을 완료하면 Windows 11 장치에 대한 구성 프로필을
성공적으로 만들고 할당하게 됩니다.

**연습 2: 할당된 구성 프로필 정책 수정**

**시나리오**

Contoso 정책에는 개발자 부서 구성원의 장치 설정에서 개인 정보 보호
옵션을 차단해서는 안 된다는 예외가 있습니다. 이 변경 사항은 구현 및
테스트되어야 합니다.

**작업 1: 할당된 구성 프로필의 설정 변경**

1.  **SEA-SVR1**로 전환합니다. **Microsoft Intune admin center** 탭으로
    돌아가 탐색 모음에서 **Devices**를 선택합니다.

![](./media/image42.png)

2.  **Devices | Overview** 페이지에서 아래 이미지와 같이 **Windows**를
    선택합니다.

![](./media/image43.png)

3.  **Windows | Windows devices** 페이지에서 **Configuration
    profiles**을 찾아 클릭합니다.

![](./media/image44.png)

4.  **Devices | Configuration profiles**  블레이드의 세부 정보 창에서
    **Contoso Developer - standard**를 선택합니다.

![](./media/image64.png)

5.  **Contoso Developer - standard** 블레이드에서 **Configuration
    settings** 섹션까지 아래로 스크롤한 다음 **Edit**를 선택합니다.

![A screenshot of a computer Description automatically
generated](./media/image65.png)

6.  **Device restrictions**  페이지에서 **Control Panel and Settings을**
    확장합니다.

![A screenshot of a computer Description automatically
generated](./media/image66.png)

7.  **Privacy**옆에서 **Not configured**이 선택되어 있는지 확인합니다.

![A screenshot of a computer Description automatically
generated](./media/image67.png)

8.  **Review + save**를 선택한 다음 **Save**를 선택합니다.

![](./media/image68.png)

**작업 2: Microsoft Intune 관리 센터에서 장치 동기화 강제 실행**

1.  [*SEA-SVR1*](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)의
    **Microsoft Intune admin center**에서 탐색 창의 **Devices**를 선택한
    다음, **All devices**와 **SEA-WS1**을 차례로 선택합니다.

![A screenshot of a computer Description automatically
generated](./media/image69.png)

2.  **SEA-WS1**  ​​블레이드에서 **Sync** 를 선택하고 메시지가 표시되면
    **Yes**를 선택합니다.

![](./media/image70.png)

**참고**: Intune이 기기를 연결하고 모든 정책을 동기화합니다. 이 작업에는
최대 5분이 소요될 수 있습니다.

**작업 3:
[*SEA-WS1*](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)에서
변경 사항 확인**

1.  [*SEA-WS1*](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)로
    전환하세요. 작업 표시줄에서 **Start**를 선택한 다음 **Settings**를
    선택합니다.

![A screenshot of a computer Description automatically
generated](./media/image2.png)

2.  **Settings**앱에서 **Privacy & security** 을 선택하고 모든 사용자
    지정 옵션이 다시 표시되었는지 확인합니다.

![A screenshot of a computer Description automatically
generated](./media/image71.png)

3.  열려 있는 모든 창을 닫고 **SEA-WS1**에서 로그아웃합니다.

**결과:** 이 연습을 완료하면 구성 프로필을 수정하고 할당하고, 구성
프로필을 수정하고, 변경 사항을 확인하는 데 성공하게 됩니다.
