Lab01 - 在 Microsoft Entra ID 中管理身份

**總結**

在本實驗中，您將使用 Microsoft Entra
管理中心來創建和修改用戶、分配管理角色、創建和修改組，以及在 Microsoft
Entra ID 中管理許可證分配。

練習 1：在 Microsoft Entra ID 中創建用戶

**場景**

您需要在 Microsoft Entra ID
中為一些將于下周開始的新員工創建用戶帳戶。下表列出了新用戶：

[TABLE]

**注意：**對於位置，請使用您的本地區域或美國。

您還被告知，在接下來的幾個月內將再招聘幾名員工。您已經確定腳本編寫是添加大量新用戶的一種更有效的方法。您已決定創建一個
PowerShell 腳本，並在創建 Cody Godinez 的帳戶時對其進行測試。

任務 1：使用 Microsoft Entra 管理中心創建用戶

1.  在 [***SEA-SVR1***](urn:gd:lg:a:select-vm)上， 以
     [**Contoso\Administrator**](urn:gd:lg:a:send-vm-keys) 身份登錄，密碼為
    !\![**Pa55w.rd**](urn:gd:lg:a:send-vm-keys)!!。

> ![Screenshot](./media/image1.png)

2.  打開 **Microsoft Edge 瀏覽器**並導航到

> !\![**https://entra.microsoft.com/#view/Microsoft_AAD_UsersAndTenants/UserManagementMenuBlade/~/AllUsers/menuId/**](https://entra.microsoft.com/#view/Microsoft_AAD_UsersAndTenants/UserManagementMenuBlade/~/AllUsers/menuId/)!!

3.  在登錄提示符下，輸入 Lab 界面的 “主頁” 選項卡中的 **Office 365
    租戶憑據**。

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)

**注意 –** 如果提升為 MFA，請完成 MFA 登錄過程。

4.  在 **Microsoft Entra admin center** 中，展開 “**Identity**”
    ，然後在導航窗格中選擇 “**Users**” 。

> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)
>
> 記下已作為 Microsoft Entra ID 域成員存在的用戶。每個用戶都已啟用，如
> **Account enabled** 列所示。**On-premises synced enabled**
> （本地同步已啟用） 列對所有當前用戶顯示 **No**
> （否）。這表示每個用戶都是直接在 Microsoft Entra ID
> 中創建的，而不是從本地目錄服務同步的。
>
> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

5.  在 **Users | All users** 頁面上，選擇 **New user**
    （新建用戶），然後選擇 **Create new user** （創建新用戶）。

> ![](./media/image5.png)

6.  在 **New User** （新建用戶） 頁面上，確保選中 **Create user**
    （創建用戶），輸入以下內容：

    - 用戶主體名稱：!\![**ereeve**](urn:gd:lg:a:send-vm-keys)!!

    - 顯示名稱：!\![**Edmund Reeve**](urn:gd:lg:a:send-vm-keys)!!

    - 取消選中 **Auto-generate password**（自動生成密碼）。

    - 密碼 **–** !!**P@55w.rd1234**!!

> ![A screenshot of a computer Description automatically
> generated](./media/image6.png)

7.  在 **Properties** 選項卡上，提供以下信息，然後單擊 **Next
    Assignments**。

    - **職稱**，輸入!\![**HR Rep**](urn:gd:lg:a:send-vm-keys)!!

    - **部門，** 輸入!!**H[R](urn:gd:lg:a:send-vm-keys)**!!

    - **使用地點 - United States**

> ![](./media/image7.png)

8.  在 Assignments 選項卡上，單擊 **Review + create** 按鈕。

> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)

9.  驗證詳細信息，然後單擊 **Create** 按鈕。

> ![](./media/image9.png)
>
> ![A close-up of a computer screen Description automatically
> generated](./media/image10.png)

10. 同樣，使用以下詳細信息為 Miranda Snider 創建用戶帳戶。

    - 用戶主體名稱： !\![**msnider**](urn:gd:lg:a:send-vm-keys)!!

    - 顯示名稱：!! [**Miranda Snider**](urn:gd:lg:a:send-vm-keys)!!

    - 取消選中 **Auto-generate password**（自動生成密碼）。

    - 密碼 **–** !!**P@55w.rd1234**!!

    - 職稱 - !!**Helpdesk Manager**!!

    - 部門 **-** !!**Operations**!!

    - 使用地點 **- United States**

11. 選擇 **Allan Deyoung** 的用戶帳戶，然後單擊 **Edit properties**
    並使用以下詳細信息更新 Job 信息，然後單擊 **Save** 按鈕。

    - 職稱- !\![**IT Admin**](urn:gd:lg:a:send-vm-keys)!!

    -  部門 - !\![**IT**](urn:gd:lg:a:send-vm-keys)!!

> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)

12. 選擇 **Joni Sherman** 的用戶帳戶，然後單擊 **Edit properties**
    並使用以下詳細信息更新 Job 信息，然後單擊 **Save** 按鈕。

    - 職稱 - !!**ParaLegal**!!

    -  部門 - !!**Legal**!!

> ![A screenshot of a computer Description automatically
> generated](./media/image12.png)

13. 選擇 **Alex Wilber** 的用戶帳戶，然後單擊 **Edit properties**
    並使用以下詳細信息更新 Job 信息，然後單擊 **Save** 按鈕。

    - 職稱 - !!**Marketing Assistant**!!

    -  部門 – !\![**Marketing**](urn:gd:lg:a:send-vm-keys)!!

> ![](./media/image13.png)

任務 2：使用 PowerShell 創建用戶

1.  在 [***SEA-SVR1***](urn:gd:lg:a:select-vm) 的任務欄上，右鍵單擊
    **Start** 開始，然後選擇 **Windows PowerShell（Admin）。**

> ![](./media/image14.png)

2.  在 **Windows PowerShell** 窗口中，鍵入以下命令，然後按
    **Enter**。如果出現提示，請輸入!\![**Y**](urn:gd:lg:a:send-vm-keys)!!
    在 NuGet 和存儲庫消息中：

> !!**Install-Module MSOnline**!!
>
> ![](./media/image15.png)

3.  在 **Windows PowerShell** 窗口中，鍵入以下命令，然後按 **Enter**：

> !!**Connect-MsolService**!!
>
> ![A screenshot of a computer Description automatically
> generated](./media/image16.png)

4.  在 “**Sign in to your account**” 對話框中，使用 “主頁” 選項卡中的
    Office 365 租戶憑據登錄。

> **注意 –** 如果系統提示您更改 Tenant admin credentials
> 密碼，請確保提供更新的密碼。

5.  在 **Windows PowerShell** 窗口中，鍵入以下代碼以創建新用戶，然後按
    **Enter**。

> 注意 –
> 將以下命令粘貼到記事本中並替換租戶詳細信息，然後根據需要將命令複製並粘貼到
> Windows PowerShell 中，以確保租戶信息正確無誤
>
> !!**New-MsolUser -UserPrincipalName
> cgodinez@M365xXXXXXXXX.onmicrosoft.com -DisplayName "Cody Godinez"
> -FirstName "Cody" -LastName "Godinez" -Password ‘P@55w.rd1234’
> -ForceChangePassword $false -UsageLocation "US" -Title "Sales Rep"
> -Department "Sales"**!!
>
> ![A screenshot of a computer screen Description automatically
> generated](./media/image17.png)

6.  在 **Windows PowerShell** 窗口中，鍵入以下命令以重置 Alew
    Wilber、Allan Deyoung 和 Joni Sherman 的密碼

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

7.  在 **Windows PowerShell** 窗口中，鍵入以下命令，然後按 **Enter**：

> !!**Get-MsolUser**!!

8.  驗證是否顯示了租戶中的用戶列表。另請記下哪些用戶已分配許可證。尚未為
    **isLicensed** 值為 **False** 的任何用戶分配許可證。

> ![A screenshot of a computer Description automatically
> generated](./media/image19.png)

**結果：**完成本練習後，您將成功在 Microsoft Entra ID
中創建新的用戶帳戶。

練習 2：在 Microsoft Entra ID 中分配管理角色

**場景**

您需要查看和修改租戶的當前管理角色。

您已獲得一個用戶列表，其中應分配有管理角色，如下表所示。

[TABLE]

任務 1：查看和分配管理角色

1.  在 [***SEA-SVR1***](urn:gd:lg:a:select-vm)上，切換到 **Microsoft
    Edge**。

2.  在**Microsoft Entra admin center**的導航窗格中，展開**Roles &
    admins**。

3.  選擇 **Roles & admin** 並搜索 !!**Global administrator**!!
    ，然後單擊 Role **Global Administrator**。

> ![A screenshot of a computer Description automatically
> generated](./media/image20.png)

4.  單擊 **Add assignments**（添加分配）。

> ![A screenshot of a computer Description automatically
> generated](./media/image21.png)

5.  在 Add assignments （添加分配） 頁面上，選擇 **Allan
    Deyoung**，然後選擇 **Add** （添加）。

> ![A screenshot of a computer Description automatically
> generated](./media/image22.png)

6.  在頁面頂部的導航鏈接中，選擇 **Roles and
    administrators**（角色和管理員）。

> ![A screenshot of a computer Description automatically
> generated](./media/image23.png)

7.  在 **Roles and administrators** 頁面上，搜索並選擇 !!**User
    administrator**!!. 確保 **Assignments** （分配） 處於選中狀態。

> ![A screenshot of a chat Description automatically
> generated](./media/image24.png)
>
> 請注意，當前沒有分配給 User administrator 角色的用戶。

8.  單擊 **+ Add assignments**（添加分配）。

> ![A screenshot of a computer Description automatically
> generated](./media/image25.png)

9.  在 Add assignments （添加分配） 頁面上，選擇 **Edmund Reeve**
    ，然後選擇 **Add** （添加）。

> ![A screenshot of a computer Description automatically
> generated](./media/image26.png)

10. 單擊 **Roles and administrators** 鏈接，然後搜索並選擇 !!**Helpdesk
    administrator**!!。

> ![A screenshot of a computer Description automatically
> generated](./media/image27.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image28.png)
>
> 請注意，當前沒有分配給 Helpdesk 管理員角色的用戶。

11. 在 **Helpdesk administrator |Assignments** （分配） 頁面，選擇 **Add
    assignments**（添加分配）。

> ![A screenshot of a computer Description automatically
> generated](./media/image29.png)

12. 在 Add assignments （添加分配） 頁面上，選擇 **Miranda
    Snider**，然後選擇 **Add** （添加）。

> ![A screenshot of a computer Description automatically
> generated](./media/image30.png)

13. 在頁面頂部的導航鏈接中，選擇 **Roles and
    administrators**（角色和管理員）。

> ![A screenshot of a computer Description automatically
> generated](./media/image31.png)

**結果：**完成本練習後，您應該已成功為用戶分配管理角色。

練習 3：創建和管理組並驗證許可證分配。

**場景**

您需要將這三個新用戶添加到安全組並分配許可證，如下表所示。

[TABLE]

系統還要求您修改登錄頁面的公司品牌。

任務 1：使用 Microsoft Entra 管理中心創建組

1.  在 [***SEA-SVR1***](urn:gd:lg:a:select-vm)上，在 **Microsoft Entra
    admin center**
    的導航窗格中，展開“**Identity**”並選擇“**Groups**”，然後單擊 “**New
    group**”。

> ![A screenshot of a computer Description automatically
> generated](./media/image32.png)

2.  在 **New Group** （新建組） 頁面上，輸入以下內容：

    - 組類型：**Security**

    - 組名：!\![**Contoso_Managers**](urn:gd:lg:a:send-vm-keys)!!

    - 成員身份類型：**Assigned**

3.  在 Members 下，單擊 **No members selected**。

4.  在 Add members （添加成員） 頁面中，添加 **Edmund Reeve** 和
    **Miranda Snider**，然後單擊 **Select** （選擇）。

> ![A screenshot of a computer Description automatically
> generated](./media/image33.png)

5.  選擇**Create**。

任務 2：使用 PowerShell 創建組

1.  在 [***SEA-SVR1***](urn:gd:lg:a:select-vm)上，切換到 Windows
    PowerShell。

2.  在 **Windows PowerShell** 窗口中，鍵入以下代碼以創建新組，然後按
    **Enter**：

> !!**New-MsolGroup -DisplayName "Contoso_Sales" -Description "Contoso
> Sales team users"**!!
>
> ![A screenshot of a computer Description automatically
> generated](./media/image34.png)

3.  在 **Windows PowerShell** 窗口中，鍵入以下命令，然後按 **Enter**：

> !!**Get-MsolGroup**!!
>
> ![A screenshot of a computer screen Description automatically
> generated](./media/image35.png)

4.  驗證您是否獲取了租戶中的組列表，包括您剛剛創建的**Contoso_Sales**組。

> ![](./media/image36.png)

5.  在 **Windows PowerShell** 窗口中，鍵入以下代碼以將變量定義為
    Contoso_Sales 組，然後按 **Enter**：

> !!**$group = Get-MsolGroup | Where-Object {$\_.DisplayName -eq
> "Contoso_Sales"}**!!

6.  在 **Windows PowerShell**
    窗口中，鍵入以下代碼以將另一個變量定義為用戶，然後按 **Enter**：

> !!**$user = Get-MsolUser | Where-Object {$\_.DisplayName -eq "Cody
> Godinez"}**!!

7.  在 **Windows PowerShell** 窗口中，鍵入以下代碼以使用設置變量將 Cody
    添加到 Contoso_Sales，然後按 **Enter**：

> !!**Add-MsolGroupMember -GroupObjectId $group.ObjectId
> -GroupMemberType "User" -GroupMemberObjectId $user.ObjectId**!!

8.  在 **Windows PowerShell** 窗口中，鍵入以下代碼，然後按 **Enter**：

> !! **Get-MsolGroupMember -GroupObjectId $group.ObjectId**!!

9.  驗證您是否在命令輸出結果中看到 **Cody Godinez**。

> ![A screenshot of a computer program Description automatically
> generated](./media/image37.png)

10. 關閉 Windows PowerShell。

任務 3：查看許可證並修改公司品牌

1.  在 Microsoft Entra 管理中心的導航窗格中，展開 “**Identity**”
    ，然後展開 “**Billing**” 並選擇 “**Licenses**” 。

> https://admin.microsoft.com/Adminportal/Home?referrer=entra#/licenses
>
> ![](./media/image38.png)

2.  在 **Licenses** （許可證） 頁面的 Subscriptions （訂閱）
    下，檢查所有可用的許可證。

> ![](./media/image39.png)
>
> 注意 - 記下當前為**Enterprise Mobility + Security E5 and Office 365 E5
> (no Teams)** 分配和分配的許可證
>
> ![](./media/image40.png)

3.  在 Microsoft 365 管理中心中，在左側導航窗格中，選擇 “**Users**”
    ，然後選擇 “**Active users**” 。

> ![](./media/image41.png)

4.  在用戶列表中，選擇 **Cody Godinez**。

> ![A screenshot of a computer Description automatically
> generated](./media/image42.png)

5.  在 Cody Godinez 頁面上，選擇 **Licenses and apps**

> ![A screenshot of a computer Description automatically
> generated](./media/image43.png)
>
> 請注意，Cody 當前沒有任何許可證分配。

6.  在 “**Licenses and apps**” 頁上，選中 “**企業移動性 + 安全性 E5”**
    和**“Office 365 E5（無 Teams）**”旁邊的複選框，然後單擊“**Save
    changes**”。

> ![A screenshot of a login page Description automatically
> generated](./media/image44.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image45.png)

**注意：**重複步驟 4 到 8，將企業移動性 + 安全性 E5 和 Office 365 E5（無
Teams）許可證分配給 Joni Sherman、Alex Wilber 和 Allan
Deyoung，以防他們未分配許可證。

7.  在 Microsoft Entra 管理中心的導航窗格中，展開 **Identity** 並選擇
    **Groups**。

> ![](./media/image46.png)

8.  在 “**Groups | All groups**” 頁上，選擇 **Contoso_Managers**。

> ![A screenshot of a computer Description automatically
> generated](./media/image47.png)

9.  在 **Contoso_Managers** 頁上，選擇 **Licenses**。

> ![](./media/image48.png)
>
> **請注意，Contoso_Managers 組當前沒有任何許可證分配。**

10. . 導航到 Microsoft 365 管理中心，向下滾動到 “許可證” ，選擇
    “**Enterprise Mobility + Security E5**” 。

> ![A screenshot of a computer Description automatically
> generated](./media/image49.png)

11. 單擊 **Groups** 選項卡，然後單擊 **Assign licenses**。

> ![](./media/image50.png)

12. 從列表中選擇 Contoso_Mangers 然後單擊 **Assign**。

13. 在 Microsoft Entra 管理中心的導航窗格中，展開 “**Identity**”
    ，然後展開 “**Billing**” 並選擇 “**Licenses**” 。

> ![A screenshot of a computer Description automatically
> generated](./media/image51.png)![A screenshot of a computer
> Description automatically generated](./media/image52.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image53.png)

14. 在 **Licenses|Overview** （概述） 頁面的 **Manage** （管理）
    下，選擇 **All products** （所有產品）。

> ![A screenshot of a computer Description automatically
> generated](./media/image54.png)
>
> ![](./media/image53.png)

15. 重複相同的過程，並將 Office 365 E5（無
    Teams）許可證分配給Contoso_Managers團隊。

> 記下分配了 Office 365 E5（無 Teams）許可證的用戶。請注意 Assignment
> Paths 列，該列指示如何為每個用戶配置許可證分配。Edmund 和 Miranda
> 都從他們在 Contoso_Managers
> 組中的成員身份接收許可證分配。您可能需要多次選擇 **Refresh** （刷新）
> 以更新 Assignment path （分配路徑） 列。
>
> ![](./media/image55.png)

16. 關閉 Microsoft Edge。

**結果：**完成本練習後，您應該已成功創建和管理組，並分配了許可證。
