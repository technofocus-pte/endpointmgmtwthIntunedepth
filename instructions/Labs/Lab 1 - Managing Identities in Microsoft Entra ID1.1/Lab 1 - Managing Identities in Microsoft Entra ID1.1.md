실습01 - Microsoft Entra ID에서 ID 관리

**요약**

이 랩에서는 Microsoft Entra 관리 센터를 사용하여 Microsoft Entra ID에서
사용자를 만들고 수정하고, 관리 역할을 할당하고, 그룹을 만들고 수정하고,
라이선스 할당을 관리합니다.

연습 1: Microsoft Entra ID에서 사용자 만들기

시나리오

다음 주에 근무를 시작하는 신입 직원을 위해 Microsoft Entra ID에 사용자
계정을 생성해야 합니다. 새 사용자는 다음 표에 나와 있습니다:

[TABLE]

**참고:** 위치 입력 시 해당 지역이나 미국을 입력합니다

또한 향후 몇 달 동안 직원을 몇 명 더 채용할 것이라는 소식을 들었습니다.
스크립팅이 많은 신규 사용자를 추가하는 데 훨씬 더 효율적인 방법이라고
판단했습니다. PowerShell 스크립트를 만들어 Cody Godinez의 계정을 생성할
때 테스트해 보기로 했습니다.

작업 1: Microsoft Entra 관리 센터를 사용하여 사용자 만들기

1.  [***SEA-SVR1***].에서
    [**Contoso\Administrator**]로 로그인하고
    비밀번호는 !! [**Pa55w.rd**]!!입니다.

> ![Screenshot](./media/image1.png)

2.  **Microsoft Edge 브라우저**를 열고 다음으로 이동합니다. 

> !\![**https://entra.microsoft.com/#view/Microsoft_AAD_UsersAndTenants/UserManagementMenuBlade/~/AllUsers/menuId/**](https://entra.microsoft.com/#view/Microsoft_AAD_UsersAndTenants/UserManagementMenuBlade/~/AllUsers/menuId/)!!

3.  로그인 프롬프트에서 랩 인터페이스의 홈 탭에서 **Office 365 테넌트
    자격 증명**을 입력합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)

참고 – MFA로 승격된 경우 MFA 로그인 절차를 완료합니다.

4.  **Microsoft Entra 관리 센터**에서 **ID**를 확장하고 탐색 창에서
    **Users**를 선택합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)
>
> Microsoft Entra ID 도메인에 이미 구성원으로 존재하는 사용자를 기록해
> 두십시오. 각 사용자는 **Account enabled**열에 표시된 대로 활성화되어
> 있습니다. **On-premises synced** **enabled** 사용 열은 모든 현재
> 사용자에 대해 **No**로 표시됩니다. 이는 각 사용자가 Microsoft Entra
> ID에서 직접 생성되었으며 온-프레미스 디렉터리 서비스에서 동기화되지
> 않았음을 나타냅니다.
>
> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

5.  **Users | All users**  페이지에서 **New user** 를 선택한 다음
    **Create new user**를 선택합니다.

> ![](./media/image5.png)

6.  **New User** 페이지에서 **Create user** 가 선택되었는지 확인하고
    다음을 입력합니다:

    - User principal name: !\![**ereeve**]!!

    - Display Name: !\![**Edmund Reeve**]!!

    - Uncheck **Auto-generate password.**

    - Password **–** !!**P@55w.rd1234**!!

> ![A screenshot of a computer Description automatically
> generated](./media/image6.png)

7.  **Properties** 탭에서 아래 정보를 입력한 후 **Next Assignments**를
    클릭합니다.

    - **Job title**, enter !\![**HR Rep**]!!

    - **Department**, enter  !!**H[R]**!!

    - **Usage location - United States**

> ![](./media/image7.png)

8.  Assignments 탭에서 **Review + create**버튼을 클릭합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)

9.  세부 정보를 확인한 후 **Create** 버튼을 클릭합니다.

> ![](./media/image9.png)
>
> ![A close-up of a computer screen Description automatically
> generated](./media/image10.png)

10. 마찬가지로 아래 세부 정보를 사용하여 Miranda Snider의 사용자 계정을
    생성합니다.

    - User principal name:  !\![**msnider**]!!

    - Display Name: !! [**Miranda Snider**]!!

    - Uncheck **Auto-generate password.**

    - Password **–** !!**P@55w.rd1234**!!

    - Job title - !!**Helpdesk Manager**!!

    - Department **-** !!**Operations**!!

    - Usage location **- United States**

11. **Allan Deyoung**의 사용자 계정을 선택하고 **Edit propertiesf**를
    클릭한 다음 아래 세부 정보로 작업 정보를 업데이트한 다음 **Save**
    버튼을 클릭합니다.

    - Job title- !\![**IT Admin**]!!

    -  Department - !\![**IT**]!!

> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)

12. **Joni Sherman**의 사용자 계정을 선택하고 **Edit properties**을
    클릭한 다음 아래 세부 정보로 작업 정보를 업데이트한 다음
    **Save**버튼을 클릭합니다.

    - Job title- !!**ParaLegal**!!

    -  Department - !!**Legal**!!

> ![A screenshot of a computer Description automatically
> generated](./media/image12.png)

13. **Alex Wilber**의 사용자 계정을 선택하고 **Edit properties**를
    클릭한 다음 아래 세부 정보로 작업 정보를 업데이트한 다음 **Save**
    버튼을 클릭합니다.

    - Job title - !!**Marketing Assistant**!!

    -  Department – !\![**Marketing**]!!

> ![](./media/image13.png)

작업 2: PowerShell을 사용하여 사용자 만들기

1.  [***SEA-SVR1***].의 작업 표시줄에서
    **Start**을 마우스 오른쪽 버튼으로 클릭한 다음 **Windows PowerShell
    (Admin)**을 선택합니다.

> ![](./media/image14.png)

2.  **Windows PowerShell**  창에 다음 명령을 입력하고 **Enter**키를
    누릅니다. 메시지가 표시되면 NuGet 및 저장소 메시지에 **!!Y!!**를
    입력합니다:

> !!**Install-Module MSOnline**!!
>
> ![](./media/image15.png)

3.  **Windows PowerShell** 창에서 다음 명령을 입력한 다음 **Enter** 키를
    누릅니다.

> !!**Connect-MsolService**!!
>
> ![A screenshot of a computer Description automatically
> generated](./media/image16.png)

4.  **Sign in to your account** 대화 상자에서 홈 탭의 Office 365 테넌트
    자격 증명을 사용하여 로그인합니다.

> **참고 –** 테넌트 관리자 자격 증명 비밀번호를 변경하라는 메시지가
> 표시된 경우 업데이트된 비밀번호를 제공해야 합니다.

5.  **Windows PowerShell** 창에서 다음 코드를 입력하여 새 사용자를 만든
    다음 **Enter** 키를 누릅니다.

> 참고 – 아래 명령을 메모장에 붙여넣고 테넌트 세부 정보를 대체한 다음
> 필요한 경우 테넌트 정보가 올바른지 확인하기 위해 명령을 복사하여
> Windows PowerShell에 붙여넣습니다.
>
> !!**New-MsolUser -UserPrincipalName
> cgodinez@M365xXXXXXXXX.onmicrosoft.com -DisplayName "Cody Godinez"
> -FirstName "Cody" -LastName "Godinez" -Password ‘P@55w.rd1234’
> -ForceChangePassword $false -UsageLocation "US" -Title "Sales Rep"
> -Department "Sales"**!!
>
> ![A screenshot of a computer screen Description automatically
> generated](./media/image17.png)

6.  **Windows PowerShell** 창에서 다음 명령을 입력하여 Alew Wilber,
    Allan Deyoung 및 Joni Sherman의 암호를 재설정합니다.

> !!**Get-MsolUser | Where-Object DisplayName -EQ "Alex Wilber" |
> Set-MsolUserPassword -NewPassword P@55w.rd1234 -ForceChangePassword
> $false**!!
>
> !!**Get-MsolUser | Where-Object DisplayName -EQ “Allan Deyoung” |
> Set-MsolUserPassword -NewPassword P@55w.rd1234 -ForceChangePassword
> $false**!!
>
> !!**Get-MsolUser | Where-Object DisplayName -EQ "Joni Sherman" |
> Set-MsolUserPassword -NewPassword P@55w.rd1234 -ForceChangePassword
> $false**!!
>
> ![A computer screen shot of a program Description automatically
> generated](./media/image18.png)

7.  **Windows PowerShell** 창에서 다음 명령을 입력한 다음 **Enter**키를
    누릅니다:

> !!**Get-MsolUser**!!

8.  테넌트의 사용자 목록이 표시되는지 확인하세요. 또한 라이선스가 할당된
    사용자도 확인하세요. **isLicensed**값이 **False**인 사용자는
    라이선스가 할당되지 않은 것입니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image19.png)

**결과:** 이 연습을 완료하면 Microsoft Entra ID에서 새로운 사용자 계정을
성공적으로 만들 수 있습니다.

연습 2: Microsoft Entra ID에서 관리 역할 할당

**시나리오**

테넌트의 현재 관리 역할을 검토하고 수정해야 합니다.

다음 표에 표시된 대로 관리 역할을 할당해야 하는 사용자 목록이
제공되었습니다.

[TABLE]

작업 1: 관리 역할 검토 및 할당

1.  [***SEA-SVR1***].에서 **Microsoft Edge**로
    전환하세요.

2.  **Microsoft Entra admin center**의 탐색 창에서 **Roles & admins**를
    확장합니다.

3.  **Roles & admin**를 선택하고 !!**Global administrator**!!를 검색한
    후 역할 **Global Administrator**를 클릭합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image20.png)

4.  **Add assignments**.를 클릭합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image21.png)

5.  할당 추가 페이지에서 **Allan Deyoung**을 선택한 다음 **Add**를
    선택합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image22.png)

6.  페이지 상단의 탐색 링크에서 **Roles and administrators**를
    선택합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image23.png)

7.  **Roles and administrators**  페이지에서 !!**User
    administrator**!!를 검색하여 선택합니다. **Assignments**가 선택되어
    있는지 확인하세요.

> ![A screenshot of a chat Description automatically
> generated](./media/image24.png)
>
> 현재 사용자 관리자 역할에 할당된 사용자가 없는지 확인합니다.

8.  + **Add assignments**를 클릭합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image25.png)

9.  할당 추가 페이지에서 **Edmund Reeve**를 선택한 다음 **Add**를
    선택합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image26.png)

10. **Roles and administrators** 링크를 클릭한 다음 !!**Helpdesk
    administrator**!!를 검색하여 선택합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image27.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image28.png)
>
> 현재 헬프데스크 관리자 역할에 할당된 사용자가 없습니다.

11. **Helpdesk administrator | Assignments**  페이지에서 **Add
    assignments**.를 선택합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image29.png)

12. 할당 추가 페이지에서 **Miranda Snider** 를 선택한 다음 **Add**를
    선택합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image30.png)

13. 페이지 상단의 탐색 링크에서 **Roles and administrators**를
    선택합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image31.png)

**결과**: 이 연습을 완료하면 사용자에게 관리 역할을 성공적으로 할당할 수
있어야 합니다.

연습 3: 그룹 생성 및 관리, 라이선스 할당 검증

**시나리오**

다음 표에 표시된 대로 보안 그룹에 세 명의 새 사용자를 추가하고
라이선스를 할당해야 합니다.

[TABLE]

또한 로그인 페이지의 회사 브랜딩을 수정해 달라는 요청을 받았습니다.

작업 1: Microsoft Entra 관리 센터를 사용하여 그룹 만들기

1.  [***SEA-SVR1***].의 **Microsoft Entra admin
    center** 내 탐색 창에서 **Identity**를 확장하고 **Groups**을 선택한
    다음 **New group**을 클릭합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image32.png)

2.  **New Group** 페이지에서 다음을 입력합니다.:

    - Group type: **Security**

    - Group name: !\![**Contoso_Managers**]!!

    - Membership type: **Assigned**

3.  **No members selected**을 클릭합니다.

4.  멤버 추가 페이지에서 **Edmund Reeve**, **Miranda Snider**를 추가한
    다음 **Select**를 클릭합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image33.png)

5.  **Create를 선택합니다.**

작업 2: PowerShell을 사용하여 그룹 만들기

1.  [***SEA-SVR1***].에서 Windows PowerShell로
    전환합니다.

2.  **Windows PowerShell** 창에서 다음 코드를 입력하여 새 그룹을 만든
    다음 **Enter**키를 누릅니다.

> !!**New-MsolGroup -DisplayName "Contoso_Sales" -Description "Contoso
> Sales team users"**!!
>
> ![A screenshot of a computer Description automatically
> generated](./media/image34.png)

3.  **Windows PowerShell** 창에서 다음 코드를 입력하여 새 그룹을 만든
    다음 **Enter** 키를 누릅니다.

> !!**Get-MsolGroup**!!
>
> ![A screenshot of a computer screen Description automatically
> generated](./media/image35.png)

4.  방금 만든 **Contoso_Sales**그룹을 포함하여 테넌트의 그룹 목록을
    가져왔는지 확인합니다.

> ![](./media/image36.png)

5.  **Windows PowerShell** 창에서 다음 코드를 입력하여 변수를
    Contoso_Sales 그룹으로 정의한 다음 **Enter**:키를 누릅니다.

> !!**$group = Get-MsolGroup | Where-Object {$\_.DisplayName -eq
> "Contoso_Sales"}**!!

6.  **Windows PowerShell** 창에서 다음 코드를 입력하여 다른 변수를
    사용자로 정의한 다음 **Enter**키를 누릅니다.

> !!**$user = Get-MsolUser | Where-Object {$\_.DisplayName -eq "Cody
> Godinez"}**!!

7.  **Windows PowerShell** 창에서 다음 코드를 입력하여 설정된 변수를
    사용하여 Cody를 Contoso_Sales에 추가한 다음 **Enter**:키를 누릅니다.

> !!**Add-MsolGroupMember -GroupObjectId $group.ObjectId
> -GroupMemberType "User" -GroupMemberObjectId $user.ObjectId**!!

8.  **Windows PowerShell** 창에서 다음 코드를 입력한 다음 **Enter** 키를
    누릅니다.

> !! **Get-MsolGroupMember -GroupObjectId $group.ObjectId**!!

9.  Verify that you see **Cody Godinez** in the command output result.
    명령 출력 결과에 **Cody Godinez** 가 표시되는지 확인합니다.

> ![A screenshot of a computer program Description automatically
> generated](./media/image37.png)

10. Windows PowerShell을 닫습니다.

작업 3: 라이선스 검토 및 회사 브랜딩 수정

1.  Microsoft Entra 관리 센터의 탐색 창에서 **Identity**를 확장한 다음
    **Billing**를 확장하고 **Licenses**를 선택합니다.

> https://admin.microsoft.com/Adminportal/Home?referrer=entra#/licenses
>
> ![](./media/image38.png)

2.  **Licenses** 페이지의 구독에서 사용 가능한 모든 라이선스를
    확인합니다.

> ![](./media/image39.png)
>
> 참고 - Enterprise Mobility + Security E5 및 Office 365 E5(Teams
> 제외)에 대해 현재 사용 가능하고 할당된 라이선스를 기록해 두십시오.
>
> ![](./media/image40.png)

3.  Microsoft 365 관리 센터의 왼쪽 탐색 창에서 **Users** 를 선택한 다음
    **Active users**를 선택합니다.

> ![](./media/image41.png)

4.  사용자 목록에서 **Cody Godinez**를 선택합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image42.png)

5.  Cody Godinez 페이지에서 **Licenses and apps**을 선택합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image43.png)
>
> Cody에게는 현재 라이센스 할당이 없습니다.

6.  **Licenses and apps** 페이지에서 **Enterprise Mobility + Security
    E5** 및 **Office 365 E5 (no Teams)**  옆에 있는 확인란을 선택하고
    변경 내용 저장을 클릭합니다.

> ![A screenshot of a login page Description automatically
> generated](./media/image44.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image45.png)

**참고:** Joni Sherman, Alex Wilber, Allan Deyoung에게 라이선스가
할당되지 않은 경우, Enterprise Mobility + Security E5 및 Office 365
E5(No Teams) 라이선스를 할당하려면 4~8단계를 반복합니다.

7.  Microsoft Entra 관리 센터의 탐색 창에서 **Identity**를 확장하고
    **Groups**를 선택합니다.

> ![](./media/image46.png)

8.  **Groups | All groups** 페이지에서 **Contoso_Managers**를
    선택합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image47.png)

9.  **Contoso_Managers** 페이지에서 **Licenses**를 선택합니다.

> ![](./media/image48.png)
>
> **Contoso_Managers 그룹에는 현재 라이선스 할당이 없습니다.**

10. Microsoft 365 관리 센터로 이동하여 라이선스까지 아래로 스크롤하여
    **Enterprise Mobility + Security E5**를 선택합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image49.png)

11. **Groups** 탭을 클릭하고 **Assign licenses**를 클릭합니다.

> ![](./media/image50.png)

12. 목록에서 Contoso_Mangers를 선택하고 **Assign**을 클릭합니다.

13. Microsoft Entra 관리 센터의 탐색 창에서 **ID**를 확장한 다음
    **Billing**를 확장하고 **Licenses**를 선택합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image51.png)![A screenshot of a computer
> Description automatically generated](./media/image52.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image53.png)

14. **Licenses|Overview**  페이지의 **Manage**에서 **All products**를
    선택합니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image54.png)
>
> ![](./media/image53.png)

15. 동일한 프로세스를 반복하고 Contoso_Managers 팀에 Office 365 E5(Teams
    없음) 라이선스를 할당합니다.

Office 365 E5(Teams 없음) 라이선스가 할당된 사용자를 확인하세요. 각
사용자에 대한 라이선스 할당 구성 방식을 나타내는 '할당 경로' 열에
주목하세요. Edmund와 Miranda는 모두 Contoso_Managers 그룹의 멤버십을
통해 라이선스 할당을 받습니다. '할당 경로' 열을 업데이트하려면
**Refresh**를 여러 번 선택해야 할 수 있습니다.

> ![](./media/image55.png)

16. Microsoft Edge를 닫습니다.

**결과:** 이 연습을 완료하면 그룹을 성공적으로 만들고 관리하고
라이선스를 할당할 수 있어야 합니다.
