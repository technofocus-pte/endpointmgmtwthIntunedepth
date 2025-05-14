# 실습 4 - Microsoft Entra 장치 등록 관리

**요약**

이 랩에서는 Windows 장치를 사용하여 Microsoft Entra 등록을 수행합니다.

**연습 1: Microsoft Entra 장치 등록 구성**

**시나리오**

여러 사용자가 개인 iOS, Android 및 Windows 기기를 사용하여 Contoso
클라우드 리소스에 액세스하도록 요청했습니다. Contoso는 기기를 소유하지
않으므로, 사용자가 전체 기기 관리를 위해 Entra에 가입하도록 요구하지
않아야 합니다. 대신, 사용자가 Microsoft Entra에 기기를 등록할 수 있도록
해야 합니다. 이렇게 하면 필요에 따라 앱에 회사 정책을 적용하고 사용자가
Contoso 리소스에 액세스할 수 있습니다. Windows 11 기기를 사용하여
Microsoft Entra 기기 등록을 테스트해 보겠습니다.

**작업 1: Azure AD 장치 등록 구성**

1.  [*SEA-SVR1*](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)에서
    Edge 브라우저의 새 탭을 열고 다음 URL을 입력합니다. !!
    **https://entra.microsoft.com**!!, 그런 다음 **Enter** 버튼을
    누릅니다.

2.  O365 테넌트 ID !!**admin@M365xXXXXXXXX.onmicrosoft.com**!!로
    로그인하고 테넌트 관리자 비밀번호를 사용합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image1.png)
>
> ![A screenshot of a login box Description automatically
> generated](./media/image2.png)

3.  **Stay signed in?** 대화 상자에서 **Yes** 버튼을 선택합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)

4.  **Microsoft Entra admin center** 창에서 **Identity**를 찾아
    클릭합니다.

![A screenshot of a computer Description automatically
generated](./media/image4.png)

5.  **Devices**를 선택한 다음 **Device settings**  페이지의 세부 정보
    창에서 **Users may register their devices with Microsoft Entra**이
    **All** 으로 설정되어 있고 회색으로 표시되어 있는지 확인합니다.

> 테넌트에서 Microsoft Intune이 활성화된 경우 이 옵션은 기본적으로
> 회색으로 표시되고 All으로 설정됩니다. 이를 통해 모든 사용자가 Windows
> 10 이상 개인용, iOS, Android 및 macOS 기기를 Azure AD에 등록할 수
> 있습니다..
>
> ![](./media/image5.png)

**작업 2: Microsoft Entra 등록 수행**

1.  [*SEA-WS1*](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)로
    전환하고 !! **Pa55w.rd**!! 비밀번호를 사용하여 관리자로
    로그인합니다.

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image6.png)

2.  타스크바에서 **Start를** 선택한 다음 **Settings**를 선택합니다.

![A screenshot of a computer Description automatically
generated](./media/image7.png)

3.  **Settings** 창에서 **Accounts**를 선택합니다.

![A screenshot of a computer Description automatically
generated](./media/image8.png)

4.  **Accounts**페이지에서 **Access work or school**선택합니다.

![A screenshot of a computer Description automatically
generated](./media/image9.png)

5.  **Connect** 페이지에서 **Connect**를 선택합니다.

![A screenshot of a computer Description automatically
generated](./media/image10.png)

6.  **Sign in**  페이지에서 !!**JoniS@M365xXXXXXXX.onmicrosoft.com**!!
     을 입력하고 **Next를** 선택합니다.

![](./media/image11.png)

7.  **Enter password** 페이지에서 테넌트 비밀번호 !!
    [**P@55w.rd1234**](mailto:P@55w.rd1234)!!를 입력한 다음 **Sign
    in**을 선택합니다.

![A screenshot of a computer Description automatically
generated](./media/image12.png)

8.  **You're all set!** 페이지에서 **Done**를 선택합니다.

![A screenshot of a computer Description automatically
generated](./media/image13.png)

9.  **Access work or school** 페이지에서 Joni의 **Work or school
    account**가 표시되는지 확인합니다.

![A screenshot of a computer Description automatically
generated](./media/image14.png)

10. **Settings** 페이지를 닫습니다.

**작업 3: Microsoft Entra 등록 확인**

1.  [*SEA-WS1*](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)에서
    **Start button**을 마우스 오른쪽 버튼으로 클릭한 다음 **Windows
    Terminal (Admin)**을 선택합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image15.png)

2.  **User Account Control** 대화 상자에서 **Yes**를 선택합니다.

> ![A screenshot of a computer error Description automatically
> generated](./media/image16.png)

3.  PowerShell 콘솔에 다음을 입력하고 **Enter**를 누릅니다:

> !!**dsregcmd /status**!!

4.  **User State**아래의 출력에서 ​​ **WorkplaceJoined : YES** 가
    표시되는지 확인하세요. 이는 사용자가 Microsoft Entra에서 장치를
    등록했음을 나타냅니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image17.png)

5.  PowerShell을 닫고 **SEA-WS1**에서 로그아웃합니다.

6.  SEA-SVR1로 전환하세요. **Microsoft Entra admin center**창으로
    이동하여 **Identity**를 클릭합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image18.png)
>
> 7\. **Identity**섹션에서 **Devices**를 선택한 다음 아래 이미지에
> 표시된 대로 **All devices**를 찾아 클릭합니다.
>
> ![A screenshot of a computer Description automatically
> generated](./media/image19.png)

8.  **Join Type**가**Microsoft Entra registered** 으로 나열되어 있고
    소유자가 **Joni Sherman**인지 확인합니다.

> ![](./media/image20.png)
>
> 해당 기기는 Microsoft Entra에 등록된 기기, Microsoft Entra에 가입된
> 기기가 아닙니다. Entra에 등록된 개체는 일반적으로 Entra에 가입할 수
> 있는 사용자가 등록된 개체입니다. 기기를 등록하면 클라우드 기반
> 리소스에 액세스할 수 있습니다.

9.  Microsoft Edge 닫습니다.

**작업 4: Windows에 로그인하고 조직과의 연결을 끊기**

1.  [*SEA-WS1*](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)로
    전환하세요. 작업 표시줄에서 **Windows Start icon**버튼을 선택한 다음
    **Settings를** 선택합니다.

![A screenshot of a computer Description automatically
generated](./media/image7.png)

2.  **Settings**창에서 **Accounts**를 선택합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)

3.  **Accounts**페이지에서 **Access work or school**를 선택합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image9.png)

4.  **Access work or school** 페이지에서 아래 이미지에 표시된 대로
    **JoniS@M3654xXXXXXXXX** **Work or school**계정 옆에 있는 드롭다운을
    클릭합니다.

> ![](./media/image21.png)

5.  **Disconnect** 버튼을 클릭합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image22.png)

6.  계정 삭제를 확인하려면 **Yes** 버튼을 클릭합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image23.png)
>
> Microsoft Entra에 등록된 장치의 연결을 끊을 때는 다시 시작할 필요가
> 없습니다.

7.  **SEA-WS1**에서 로그아웃합니다.

![A screenshot of a computer Description automatically
generated](./media/image24.png)

**결과**: 이 연습을 완료하면 Microsoft Entra 장치 등록이 구성됩니다.
