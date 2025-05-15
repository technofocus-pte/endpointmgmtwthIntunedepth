實驗 02 - 使用 Microsoft Entra Connect 同步標識

**總結**

在本實驗中，您將配置從 Active Directory 域服務到 Microsoft Entra ID
的同步

**場景**

Contoso Corporation 目前將 AD DS 和 Microsoft Entra ID
中的用戶作為單獨的進程進行管理。這非常耗時，並且會導致信息不一致。您的任務是使用
Microsoft Entra Connect 同步工具連接兩個目錄來解決此問題。

## 任務 0：使用 PowerShell 腳本啟用 TLS 1.2 

1.  在 **SEA-SVR1** 上，使用密碼 **Pa55w.rd** 以
    **Contoso\Administrator** 身份登錄

2.  在開始菜單上，鍵入 [**PowerShell**](urn:gd:lg:a:send-vm-keys) ，右鍵單擊
    PowerShell，然後選擇 **run as administrator**。

![](./media/image1.png)

3.  在 PowerShell 上運行以下腳本。

**If** (-Not (Test-Path
'HKLM:\SOFTWARE\WOW6432Node\Microsoft\\NETFramework\v4.0.30319'))

{

New-Item 'HKLM:\SOFTWARE\WOW6432Node\Microsoft\\NETFramework\v4.0.30319'
-Force | Out-Null

}

New-ItemProperty -Path
'HKLM:\SOFTWARE\WOW6432Node\Microsoft\\NETFramework\v4.0.30319' -Name
'SystemDefaultTlsVersions' -Value '1' -PropertyType 'DWord' -Force |
Out-Null

New-ItemProperty -Path
'HKLM:\SOFTWARE\WOW6432Node\Microsoft\\NETFramework\v4.0.30319' -Name
'SchUseStrongCrypto' -Value '1' -PropertyType 'DWord' -Force | Out-Null

**If** (-Not (Test-Path
'HKLM:\SOFTWARE\Microsoft\\NETFramework\v4.0.30319'))

{

New-Item 'HKLM:\SOFTWARE\Microsoft\\NETFramework\v4.0.30319' -Force |
Out-Null

}

New-ItemProperty -Path
'HKLM:\SOFTWARE\Microsoft\\NETFramework\v4.0.30319' -Name
'SystemDefaultTlsVersions' -Value '1' -PropertyType 'DWord' -Force |
Out-Null

New-ItemProperty -Path
'HKLM:\SOFTWARE\Microsoft\\NETFramework\v4.0.30319' -Name
'SchUseStrongCrypto' -Value '1' -PropertyType 'DWord' -Force | Out-Null

**If** (-Not (Test-Path
'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS
1.2\Server'))

{

New-Item
'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS
1.2\Server' -Force | Out-Null

}

New-ItemProperty -Path
'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS
1.2\Server' -Name 'Enabled' -Value '1' -PropertyType 'DWord' -Force |
Out-Null

New-ItemProperty -Path
'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS
1.2\Server' -Name 'DisabledByDefault' -Value '0' -PropertyType 'DWord'
-Force | Out-Null

**If** (-Not (Test-Path
'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS
1.2\Client'))

{

New-Item
'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS
1.2\Client' -Force | Out-Null

}

New-ItemProperty -Path
'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS
1.2\Client' -Name 'Enabled' -Value '1' -PropertyType 'DWord' -Force |
Out-Null

New-ItemProperty -Path
'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS
1.2\Client' -Name 'DisabledByDefault' -Value '0' -PropertyType 'DWord'
-Force | Out-Null

寫-Host 'TLS 1.2 has been enabled. You must restart the Windows Server
for the changes to take affect.' -ForegroundColor Cyan

![](./media/image2.png)

4.  重新啟動 Windows Server VM。

![](./media/image3.png)

任務 1：使用 Microsoft Entra Connect 配置目錄同步

1.  在 [***SEA-SVR1***](urn:gd:lg:a:select-vm)上，
    如有必要，以[**Contoso\Administrator**](urn:gd:lg:a:send-vm-keys) 身份登錄，密碼為 !\![**Pa55w.rd**](urn:gd:lg:a:send-vm-keys)!!

2.  在任務欄上，選擇 Microsoft Edge。

3.  在地址欄中，輸入
    !\![**http://www.microsoft.com/en-us/download/details.aspx?id=47594**](urn:gd:lg:a:send-vm-keys)!!

4.  在 Microsoft Entra Connect 頁面上，選擇 “**Download**” 。

> Microsoft Entra Connect 會自動下載到 **SEA-SVR1** 上的 **Downloads**
> 文件夾。
>
> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

5.  單擊 **Open file** 以獲取下載的文件**AzureADConnect.msi**。

> ![A screenshot of a phone Description automatically
> generated](./media/image5.png)

6.  在 **Microsoft Azure Active Directory Connect** 嚮導的 “**Welcome to
    Azure AD Connect**”頁面上，選中 “**I agree to the license terms and
    privacy notice**” 複選框，然後選擇 “**Continue**” 。

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image6.png)

7.  在 **Express Settings** （快速設置） 頁面上，選擇 **Customize**
    （自定義）。

> ![](./media/image7.png)

8.  在 **Install required components** （安裝所需組件） 頁面上，選擇
    **Install** （安裝）。

> ![](./media/image8.png)

9.  在 **User sign-in** （用戶登錄） 頁面上，確保 **Password Hash
    Synchronization** （密碼哈希同步） 處於選中狀態，然後選擇 **Next**
    （下一步）。

> ![](./media/image9.png)

10. 在 “**Connect to Azure AD**” 頁面的 “**USERNAME**” 和 “**PASSWORD**”
    框中，輸入您的 **Office 365 租戶憑據**，然後選擇 “**Next**” 。

> ![](./media/image10.png)

11. 在 **Connect your directories** （連接目錄） 頁面上，確保
    **Contoso.com** 列在 **FOREST** 下，然後選擇 **Add Directory**
    （添加目錄）。

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image11.png)

12. 在 **AD forest account** 窗口中，選擇“ **Create New AD
    Account**”選項，然後在“**ENTERPRISE ADMIN
    USERNAME**”字段中鍵入[**Contoso\Administrator**](urn:gd:lg:a:send-vm-keys)，然後鍵入!\![**Pa55w.rd**](urn:gd:lg:a:send-vm-keys)!!
    在 **PASSWORD** 字段中。選擇 “**OK**”，然後選擇 “**Next**” 。

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image12.png)
>
> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image13.png)

13. 在 **Azure AD sign-in configuration** 頁上，確保在 **USER PRINCIPAL
    NAME** 下拉列表中，選擇了 **userPrincipalName** 值。

> ![](./media/image14.png)

14. 選擇 **Continue without matching all UPN suffixes to verified
    domains**，然後選擇 “**Next**” 。

15. 在 **Domain and OU filtering** （域和 OU 篩選） 頁面上，選擇 **Sync
    selected domains and OUs** （同步選定的域和 OU）。

16. 展開 **Contoso.com**，清除 **Contoso.com**
    旁邊的複選框，並確保僅選中以下複選框：**IT, Managers, Marketing,
    Research** 和 **Sales**。選擇 **Next**（下一步）。

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image15.png)

17. 在 **Unique identified your users** （唯一標識您的用戶）
    頁面上，選擇 **Next** （下一步）。

18. 在 **Filter users and devices** （篩選用戶和設備） 頁面上，選擇
    **Next** （下一步）。

19. 在 **Optional features** （可選功能）
    頁面上，查看可用選項，但不要進行任何更改。確保已選擇 **Password hash
    synchronization** （密碼哈希同步），然後選擇 **Next** （下一步）。

> ![](./media/image16.png)

20. 在 **Ready to configure** （準備配置） 頁面上，確保 **Start the
    synchronization process when configuration completes**
    處於選中狀態，然後選擇 **Install** （安裝）。

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image17.png)

21. 配置完成後，選擇 **Exit** （退出）。

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image18.png)
>
> **注意：**此時，開始從本地 Active Directory 域服務 （AD DS） 和
> Microsoft Entra ID 同步對象。您應該等待大約 3-4 分鐘，以便此過程完成。

22. 關閉所有打開的窗口。

任務 2：驗證 Microsoft Entra ID 中的同步

1.  在 **Microsoft Edge** 中打開一個新選項卡並導航到 Microsoft Entra
    管理中心用戶頁面 -
    !\![**https://entra.microsoft.com/#view/Microsoft_AAD_UsersAndTenants/UserManagementMenuBlade/~/AllUsers/menuId/**](https://entra.microsoft.com/#view/Microsoft_AAD_UsersAndTenants/UserManagementMenuBlade/~/AllUsers/menuId/)!!
    如果系統提示登錄，請使用 Lab 界面的“主頁”選項卡中的 Office 365
    租戶憑據。

> ![A screenshot of a computer Description automatically
> generated](./media/image19.png)

2.  驗證是否看到來自本地 AD DS 的用戶。確保這些用戶在 **On-premises sync
    enabled** （已啟用本地同步） 列中具有值 **Yes** （是）。

> ![](./media/image20.png)

3.  在 Navigation （導航） 窗格中，選擇 Expand **Groups**
    （展開組），然後選擇 **All groups** （所有組）。

> ![A screenshot of a computer Description automatically
> generated](./media/image21.png)

4.  驗證是否看到來自本地 AD DS （） 的組

> ![A screenshot of a computer Description automatically
> generated](./media/image22.png)

5.  選擇 **Managers** 組。

> ![A screenshot of a computer Description automatically
> generated](./media/image23.png)

6.  在 **Managers** group （經理組） 頁面上，選擇 **Members**
    （成員），然後確保您看到 users。

> ![A screenshot of a computer Description automatically
> generated](./media/image24.png)
>
> ![A screenshot of a group of people Description automatically
> generated](./media/image25.png)
>
> **請注意，您無法在此組中添加或刪除成員，因為它來自本地 AD DS。**

15. 關閉 Microsoft Edge。

**結果：**完成本練習後，您將成功配置 Microsoft Entra Connect，以將身份從
Active Directory 域服務同步到 Microsoft Entra ID
