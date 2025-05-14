**실습 6 - Microsoft Intune에 장치 등록**

**요약**

이 랩에서는 Windows 클라이언트를 Entra ID에 가입시키고 장치가 Microsoft
Intune에 자동으로 등록되었는지 확인합니다.

**필수 조건**

이 실습을 시작하기 전에 다음 실습을 완료해야 합니다:

- 실습 \#1- Microsoft Entra ID에서 ID 관리

- 실습 \#2- Microsoft Entra Connect를 사용하여 ID 동기화

- 실습 \#5- Microsoft Intune에 장치 등록 관리

**참고**: Entra ID에 대한 Windows Hello 로그인 인증을 보호하는 데
사용되는 문자 메시지를 수신할 수 있는 휴대폰이 필요할 수도 있습니다.

**시나리오**

Cindy White에게 적절한 라이선스를 할당했으며 이제 Windows 장치를 Entra
ID에 가입하고 Microsoft Intune에 자동으로 등록하는 프로세스를
테스트합니다.

**작업 1: Windows 장치를 Microsoft Intune에 자동으로 등록**

1.  [*SEA-WS1*](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)로
    전환하고 !!**Pa55w.rd**!! 비밀번호를 사용하여 **Admin**로
    로그인하세요.

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image1.png)

2.  타스크바에서 **Start** 를 선택한 다음 **Settings**를 선택합니다.

![A screenshot of a computer Description automatically
generated](./media/image2.png)

3.  **Settings** 창에서 **Accounts**을 선택합니다.

![A screenshot of a computer Description automatically
generated](./media/image3.png)

4.  계정 페이지에서 **Access work or school**를 선택합니다.

![A screenshot of a computer Description automatically
generated](./media/image4.png)

5.  **Access work or school**  페이지에서 **Connect**.를 선택합니다.

![A screenshot of a computer Description automatically
generated](./media/image5.png)

6.  **Microsoft account** 창에서 **Join this device to Microsoft Entra
    ID**를 선택합니다.

![](./media/image6.png)

7.  **Sign in**  페이지에서
    !\![**Cindy@M365x51282399.onmicrosoft.com**](mailto:Cindy@M365x51282399.onmicrosoft.com)!!
    을 입력하고 **Next**를 선택합니다.

![](./media/image7.png)

8.  **Enter password**  페이지에서 비밀번호
    !\![**P@55w.rd1234**](mailto:!!P@55w.rd1234)!!를 입력한 다음 **Sign
    in**을 선택합니다.

![A screenshot of a computer Description automatically
generated](./media/image8.png)

9.  **Make sure this is your organization** 대화 상자가 나타나는지
    확인한 후 **Join**를 선택합니다.

![](./media/image9.png)

10. **You're all set!**' 페이지에서 정보를 읽은 다음 **Done**.를
    선택합니다.

![A screenshot of a computer Description automatically
generated](./media/image10.png)

11. **Access work or school** 섹션에서 **Connected to Contoso's Azure
    AD가** 표시되는지 확인합니다.

12. **Connected to Contoso's Azure AD** 에 연결을 선택한 다음 **Info**를
    선택합니다.

![A screenshot of a computer Description automatically
generated](./media/image11.png)

13. Contoso에서 관리하는 영역에 대한 정보를 확인하고 아래로 스크롤하여
    **Sync**를 선택하세요. 이렇게 하면 장치가 Intune과 강제로
    동기화됩니다.

![A screenshot of a computer Description automatically
generated](./media/image12.png)

14. **Settings**  창을 닫습니다.

**작업 2: Microsoft Entra 및 Intune에 대한 장치 등록 확인**

1.  **SEA-WS1**  ​​작업 표시줄에서 **Start**를 선택하고
    !!**certlm.msc**!!를 입력한 후 **Enter**를 누릅니다.

![A screenshot of a computer Description automatically
generated](./media/image13.png)

2.  사용자 계정 컨트롤 대화 상자에서 **Yes** 버튼을 선택합니다.

![](./media/image14.png)

3.  **Certificates**콘솔의 탐색 창에서 **Personal**을 확장하고
    **Certificates**노드를 선택합니다. 세부 정보 창에 다음 인증서가
    나열되어 있는지 확인합니다:

- Microsoft Intune MDM Device CA

- MS-Organization-Access

- MS-Organization-P2P-Access \[2024\]

이는 해당 장치가 Microsoft Entra 및 Intune에 등록되었음을 나타냅니다.

![](./media/image15.png)

4.  Certificates 창을 닫습니다.

5.  **Start** 버튼을 마우스 오른쪽 버튼으로 클릭한 다음 **Windows
    Terminal (Admin)**을 선택합니다.

![A screenshot of a computer Description automatically
generated](./media/image16.png)

6.  **User Account Control** 대화 상자에서 **Yes** 버튼을 클릭합니다.

![A screenshot of a computer error Description automatically
generated](./media/image17.png)

7.  PowerShell 콘솔에 다음을 입력하고 **Enter**를 누릅니다.

!!**dsregcmd /status**!!

8.  출력의 **Device State**아래에 **AzureAdJoined** : **YES**가
    표시되는지 확인하세요. 이는 장치가 Azure AD에 가입되었음을
    나타냅니다.

![A screenshot of a computer Description automatically
generated](./media/image18.png)

9.  Tenant Details 아래의 출력에서 ​​다음 세 가지 항목이 있는지
    확인합니다:

- mdmUrl:https://enrollment.manage.microsoft.com/enrollmentserver/discovery.svc

- mdmTouUrl:https://portal.manage.microsoft.com/TermsofUse.aspxmdm

- ComplianceUrl:https://portal.manage.microsoft.com/?portalAction=Compliance

![](./media/image19.png)

*참고: 이 항목은 해당 장치가 Intune에 등록되었음을 나타냅니다.*

**작업 3: Microsoft Entra ID 사용자로 로그인**

1.  로컬 관리자 계정으로 로그인했으므로 **SEA-WS1**에서 로그아웃합니다.

2.  !\![**P@55w.rd1234**](mailto:P@55w.rd1234)!! 로그인 화면에서 다른
    사용자를 선택하고 !!**Cindy@M365xXXXXXXX.onmicrosoft.com**!!  으로
    로그인하고 비밀번호는
    !\![**P@55w.rd1234**](mailto:P@55w.rd1234)!!입니다:

![](./media/image20.png)

3.  프로필이 생성될 때까지 기다립니다.

![A screenshot of a computer Description automatically
generated](./media/image21.png)

**참고 – Windows Hello를 묻는 메시지가 표시되면 로그인 과정을 적절히
완료하고 Set up a PIN  페이지의 New PIN  및 Confirm PIN 상자에
!!102938!!을 입력한 다음 OK를 선택합니다**

![A screenshot of a computer Description automatically
generated](./media/image22.png)

4.  **SEA-WS1**에서 로그아웃합니다.

**작업 4: Microsoft Intune 콘솔에서 장치 등록 확인**

1.  [*SEA-SVR1*](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)로
    전환하고 제공된 자격 증명을 사용하여 로그인합니다.

2.  Microsoft Edge 브라우저에서 주소창에
    !!**https://intune.microsoft.com**!!을 입력하고 **Enter**키를
    누릅니다. Office 365 테넌트 관리자 계정으로 로그인합니다.

3.  탐색 창에서 **Devices**를 선택합니다.

![A screenshot of a computer Description automatically
generated](./media/image23.png)

4.  **Devices | Overview** 페이지에서 **Windows**를 찾아 클릭합니다.

![](./media/image24.png)

5.  **Windows devices**를 찾아 클릭합니다. **SEA-WS1** 이 목록에 있는지
    확인합니다.

Note that for SEA-WS1, the **Managed by** column displays **Intune** and
the **Ownership** column displays **Corporate**.

![A screenshot of a computer Description automatically
generated](./media/image25.png)

**참고**: 이 보기에는 Intune에 등록된 장치가 나열됩니다. Microsoft
Entra와 Microsoft Intune 간의 자동 등록을 구성했기 때문에 Microsoft
Entra에 연결되거나 등록된 모든 장치는 Microsoft Intune에 자동으로
등록됩니다. 등록 설정 전에 연결된 장치는 Entra에만 연결되거나 등록되고
Intune에는 등록되지 않습니다.

6.  새 탭을 열고 **Microsoft Entra admin center**로 이동합니다
    !!**https://entra.microsoft.com**!!. **Devices**를 클릭한 다음 **All
    devices**를 선택합니다.

![A screenshot of a computer Description automatically
generated](./media/image26.png)

7.  **SEA-WS1**을 참고합니다. **Join Type** 열에는 Microsoft Entra가
    조인되었고 **MDM**열에는 Microsoft Intune이 표시되어 있습니다.

![A screenshot of a computer Description automatically
generated](./media/image27.png)

**결과**: 이 연습을 완료하면 Windows 클라이언트를 Microsoft Entra ID에
성공적으로 가입시키고 장치가 Microsoft Intune에 자동으로 등록되었는지
확인할 수 있습니다.
