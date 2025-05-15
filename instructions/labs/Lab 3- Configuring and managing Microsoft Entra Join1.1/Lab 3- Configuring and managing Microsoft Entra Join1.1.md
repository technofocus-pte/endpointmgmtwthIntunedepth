實驗 03：配置和管理 Microsoft Entra ID Join

**總結**

在本實驗中，您將配置 Microsoft Entra ID 加入設置，並為 Windows
設備執行標準和 Microsoft Entra 混合加入方案。

**先決條件**

在此實驗之前，必須完成以下實驗：

- 實驗 \#2：使用 Microsoft Entra Connect 同步標識

**注意：**您還需要一部可以接收短信的移動電話，該短信用於保護 Windows
Hello 登錄對 Entra ID 的身份驗證。

**練習 1：配置 Microsoft Entra Join**

**場景**

您需要配置 Entra ID 設備設置，以確保允許所有用戶將設備加入 Entra
ID。您還需要確保用戶最多只能加入 20 台設備，並且 Allan Deyoung
已添加為所有已加入 Microsoft Entra 的設備的本地管理員。最後，您將通過讓
Joni Sherman 將 SEA-WS1 加入租戶來驗證 Microsoft Entra Join
是否按預期工作。

## 任務 0：使用 PowerShell 腳本啟用 TLS 1.2。

1.  在 SEA-WS1 上，使用密碼 Pa55w.rd 以 Contoso\Administrator 身份登錄

2.  在開始菜單上，鍵入 [**PowerShell**](urn:gd:lg:a:send-vm-keys) ，右鍵單擊
    PowerShell，然後選擇以管理員身份運行。

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

## 任務 1：配置 Microsoft Entra ID 加入設備設置

1.  切換到 **SEA-SVR1**。在 **Microsoft Edge** 瀏覽器地址欄中，鍵入以下
    URL：!\![**https://entra.microsoft.com**](https://entra.microsoft.com)!!，然後按
    Enter 按鈕。

2.  使用您的 O365 租戶 ID
    登錄：!!**admin@M365xXXXXXXXX.onmicrosoft.com**!!
    ,並使用租戶管理員密碼。

![A screenshot of a computer Description automatically
generated](./media/image4.png)

![A screenshot of a login box Description automatically
generated](./media/image5.png)

3.  在 **Stay signed in?** 對話框中，選擇 **Yes** 按鈕。

![A screenshot of a computer Description automatically
generated](./media/image6.png)

4.  在 **Microsoft Entra admin center**
    窗口中，導航並單擊“**Identity**”。

![A screenshot of a computer Description automatically
generated](./media/image7.png)

5.  在“**Identity**”部分下，選擇“**Devices**”，然後導航並單擊“**All
    devices**”，如下圖所示。

![A screenshot of a computer Description automatically
generated](./media/image8.png)

請注意，由於您尚未加入任何設備，因此未找到任何設備。

![](./media/image9.png)

6.  在 **Devices**|“所有設備”頁上，選擇 “**Device settings**”。

![A screenshot of a computer Description automatically
generated](./media/image10.png)

7.  在 **Devices | Device settings** 頁面的詳細信息窗格中的 “**Users may
    join devices to Entra**” 下，驗證是否已選擇 “**All**”。

這表示允許所有 Entra 用戶將 Windows 10 或更高版本的設備加入 Microsoft
Entra。請注意，此設置不適用於已加入 Entra 混合的設備，或使用 Windows
Autopilot 自部署模式加入的設備。

8.  在 “**Require Multi-factor Authentication to register or join
    devices with Entra**” 部分中，驗證該設置是否設置為 “**No**”。

![A screenshot of a computer Description automatically
generated](./media/image11.png)

9.  在 **Maximum number of devices per user** （每個用戶的最大設備數）
    部分中，選擇 **20 （Recommended）**。

10. 單擊 “**Manage Additional local administrators on all Microsoft
    Entra Joined devices**”鏈接。此時將打開 **Device Administrators
    頁面**。

![A screenshot of a computer Description automatically
generated](./media/image12.png)

11. 在 **Device Administrators |Assignments** （分配） 頁面，選擇 **Add
    assignments**（添加分配）。

![A screenshot of a computer Description automatically
generated](./media/image13.png)

12. 在 Search （搜索） 框中，輸入 !!**Allan Deyoung**!!，選擇 **Allan
    Deyoung** 用戶對象，然後選擇 **Add**。

![A screenshot of a computer Description automatically
generated](./media/image14.png)

13. Allan Deyoung 現在將被添加為所有已加入 Microsoft Entra
    的設備上的設備管理員。

![A screenshot of a computer screen Description automatically
generated](./media/image15.png)

14. 點擊 **Devices | Device settings Azure** 門戶搜索欄下的鏈接可返回到
    “**Device Settings**” 頁。

![A screenshot of a computer Description automatically
generated](./media/image16.png)

15. 在 **Device settings** （設備設置） 頁面上，選擇 **Save** （保存）。

![A screenshot of a computer Description automatically
generated](./media/image17.png)

**任務 2：執行 Microsoft Entra ID 聯接**

1.  切換到[SEA-WS1](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10) 並以
    **Admin** 身份登錄，密碼為 !!**Pa55w.rd**!!。

![](./media/image18.png)

2.  在任務欄上，選擇 **Windows Start button**
    圖標，然後選擇“**Settings**”。

![](./media/image19.png)

3.  在 **Settings** （設置） 窗口中，選擇 **Accounts** （帳戶）。

![A screenshot of a computer Description automatically
generated](./media/image20.png)

4.  在 “**Accounts**”頁上，選擇 “**Access work or school**”。

![A screenshot of a computer Description automatically
generated](./media/image21.png)

5.  在 “**Access work or school**” 頁面中，選擇 “**Connect**”。

![A screenshot of a computer Description automatically
generated](./media/image22.png)

6.  在 **Microsoft account** 窗口中，選擇 **Join this device to
    Microsoft Entra ID**。

![A screenshot of a computer screen Description automatically
generated](./media/image23.png)

7.  在 **Sign in** （登錄） 頁面上，鍵入 
    !!JoniS@M365xXXXXXXX.onmicrosoft.com!!  ，然後選擇 **Next**。

![Graphical user interface, application, Teams Description automatically
generated](./media/image24.png)

8.  在 **Enter password** （輸入密碼） 頁面上，輸入租戶密碼：
    !\![**P@55w.rd1234**](mailto:P@55w.rd1234)!!，然後選擇 **Sign in**
    （登錄）。

![Graphical user interface, application Description automatically
generated](./media/image25.png)

9.  在 **Make sure this is your organization** （確保這是您的組織）
    對話框中，選擇 **Join** （加入）。

![A screenshot of a computer error Description automatically
generated](./media/image26.png)

10. 在 **You're all set！**頁面上，選擇 “**Done**”。

![A screenshot of a computer Description automatically
generated](./media/image27.png)

11. 在 “**Access work or school**”頁上，驗證是否顯示“**Connected to
    Contoso's Azure AD**”。

![A screenshot of a computer Description automatically
generated](./media/image28.png)

12. 關閉 **Settings** （設置） 頁面。

**任務 3：驗證 Microsoft Entra Join**

1.  在 [SEA-WS1](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)上，右鍵單擊
    **Windows Start button** 圖標，然後選擇 **Windows Terminal
    (Admin)**，如下圖所示。

![](./media/image29.png)

2.  在 **User Account Control** （用戶帳戶控制） 對話框中，選擇 **Yes**
    （是）。

![](./media/image30.png)

3.  在 PowerShell 控制台中，鍵入以下命令，然後按 **Enter** 按鈕：

!!**dsregcmd /status**!!

4.  在輸出中，在 **Device State**（設備狀態）下，驗證是否顯示
    **AzureAdJoined ： YES**。

這表示設備已加入 Microsoft Entra。

![](./media/image31.png)

5.  關閉 PowerShell。

6.  再次右鍵單擊 **Windows Start button** 圖標，然後選擇“**Computer
    Management**”。

![A screenshot of a computer Description automatically
generated](./media/image32.png)

7.  在 **Computer Management** （計算機管理） 窗口中，展開 **Local Users
    and Groups**（本地用戶和組），然後選擇 **Groups**（組）。

![](./media/image33.png)

![A screenshot of a computer Description automatically
generated](./media/image34.png)

8.  雙擊 **Administrators** 組。

![A screenshot of a computer Description automatically
generated](./media/image35.png)

請注意，Joni Sherman 已添加為 SEA-WS1
上的本地管理員。另請注意兩個安全主體，由其安全標識符 （SID）
表示。這兩個 SID 表示 Entra 全域管理員角色和 Microsoft Entra Joined
設備管理員角色。

![](./media/image36.png)

9.  關閉所有打開的窗口並注銷 SEA-WS1，方法是單擊 **Windows Start button
    icon \> Admin \> Sign out**。

![](./media/image37.png)

10. 切換到 **SEA-SVR1** 並使用憑據 **Contoso\Administrator** 和密碼登錄
    !!**Pa55w.rd**!!

![A screenshot of a computer Description automatically
generated](./media/image38.png)

11. 在 **Microsoft Entra admin center**，導航並單擊“**Identity**”。

12. 導航並選擇 **Devices**（設備），然後單擊 **All
    devices**（所有設備）。

13. 在 **Devices | All devices** 頁面上，請注意 **SEA-WS1** 已列出。

![](./media/image39.png)

14. 驗證 **Join Type** 是否列為 **Microsoft Entra
    Joined**，以及所有者是否為 **Joni Sherman**。

![](./media/image40.png)

15. 另請注意，MDM 列顯示 **None**。這表示此設備尚未由 Microsoft Intune
    管理。

![A screenshot of a computer Description automatically
generated](./media/image41.png)

**任務 4：以 Microsoft Entra 用戶身份登錄到 Windows**

1.  切換到 **SEA-WS1** 並單擊 **Other user**。

![](./media/image42.png)

2.  **登錄**身份 !!**JoniS@M365xXXXXXXX.onmicrosoft.com**!!
     使用租戶密碼： !!**P@55w.rd1234**!!

**注意：等待配置文件創建完成。**

![](./media/image43.png)

**注意 –** 如果系統提示您使用 **Windows
Hello**，請相應地完成登錄過程，然後在 **Set up a PIN** 頁面的 **New
PIN** 和 **Confirm PIN** 框中，鍵入 !!**102938**!!，然後選擇 **OK**。

![](./media/image44.png)

**任務 5：從 Entra 中刪除 Windows 設備**

1.  在 [SEA-WS1](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)上，如果出現提示，請使用
    Joni Sherman 登錄，如果輸入 PIN 的選項可用，則輸入 PIN：
    !!**102938**!! 或輸入密碼為 !!**P@55w.rd1234**!!

![A screenshot of a computer Description automatically
generated](./media/image45.png)

2.  在 **Settings** （設置） 窗口中，選擇 **Accounts** （帳戶）。

![A screenshot of a computer Description automatically
generated](./media/image46.png)

3.  在左側導航窗格中，導航並單擊 **Account**（賬戶）。在
    “**Accounts**”頁上，選擇 “**Access work or school**”。

![A screenshot of a computer Description automatically
generated](./media/image47.png)

4.  在 “**Access work or school**”頁中，選擇“**Connected to Contoso's
    Azure AD**”旁邊的下拉列表，如下圖所示。單擊
    **Disconnect**（斷開連接），然後選擇 **Yes**（是）。

![](./media/image48.png)

![A screenshot of a computer Description automatically
generated](./media/image49.png)

![A screenshot of a computer Description automatically
generated](./media/image50.png)

5.  在 **Disconnect from the organization** （斷開與組織的連接）
    頁面上，選擇 **Disconnect** （斷開連接）。

![A blue box with white text Description automatically
generated](./media/image51.png)

6.  在 **Windows Security** 對話框的 **電子郵件地址**
    框中，輸入 !!Admin!! 管理！！，然後在 **Password**
    框中，鍵入 !!Pa55w.rd!!。選擇 **OK**。

![Graphical user interface Description automatically
generated](./media/image52.png)

7.  在 **Restart your PC** 對話框中，選擇 **Restart now**
    （立即重啟）。**SEA-WS1** 重新啟動。

![A blue box with white text Description automatically
generated](./media/image53.png)

**結果：**完成本練習後，您將配置 Microsoft Entra 設備設置，將設備加入
Entra，並從 Entra 中刪除設備。

**練習 2：配置 Microsoft Entra 混合聯接**

**場景**

某些 Contoso Windows 設備當前已加入本地 Active Directory
域服務。要使這些設備能夠無縫訪問雲服務，您計劃啟用 Microsoft Entra
混合加入。您將通過重新配置 Azure AD Connect 並在 SEA-CL2
上測試該過程來測試 Microsoft Entra 混合聯接。

**任務 1：準備環境**

1.  切換到[SEA-SVR1](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)。

![A picture containing text Description automatically
generated](./media/image54.png)

2.  選擇 **Windows Start 圖標** 按鈕，展開 **Windows Administrative
    Tools**，然後選擇 **Active Directory Users and Computers**。

![](./media/image55.png)

3.  在 **Active Directory Users and Computers** 中，右鍵單擊
    **Contoso.com**，指向 **New** 建，然後選擇 **Organizational Unit**。

![](./media/image56.png)

4.  在 **New-Object - Organizational Unit** 對話框中，鍵入 !!**Entra
    clients**!!，然後選擇 **OK**。

![A screenshot of a computer Description automatically
generated](./media/image57.png)

5.  在導航窗格中，選擇 **Seattle Clients**。右鍵單擊
    **SEA-CL2**，然後選擇 **Move**。

![](./media/image58.png)

6.  在 “**Move**”對話框中，選擇 “**Entra clients**”，然後選擇 “**OK**”。

![A screenshot of a computer Description automatically
generated](./media/image59.png)

7.  關閉 **Active Directory Users and Computers**。

![A screenshot of a computer Description automatically
generated](./media/image60.png)

**任務 2：重新配置 Entra Connect**

1.  在 [SEA-SVR1](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)上，
    雙擊桌面上的 Azure AD Connect

![A black rectangle with blue lines Description automatically
generated](./media/image61.png)

2.  在 **Microsoft Azure Active Directory Connect** 窗口中，選擇
    **Configure**。

![](./media/image62.png)

3.  在 **Additional tasks** （其他任務） 頁面上，選擇 **Customize
    synchronization options** （自定義同步選項），然後選擇 **Next**
    （下一步）。

![A screenshot of a computer Description automatically
generated](./media/image63.png)

4.  在 “**Connect to Entra**” 頁面的 “**USERNAME**” 和 “**PASSWORD**”
    框中，輸入您的 **Office 365 租戶憑據**，然後選擇 “**Next**” 。

![A screenshot of a computer Description automatically
generated](./media/image64.png)

5.  在 **Connect your directories** （連接目錄） 頁面上，單擊 Next
    （下一步） 按鈕。

![A screenshot of a computer Description automatically
generated](./media/image65.png)

6.  在 **Domain and OU filtering** （域和 OU 篩選） 頁面上，確保 **Sync
    selected domains and Ous** （同步所選域和 OU） 處於選中狀態。

7.  Expand **Contoso.com**, select **Entra clients,** and then click
    on **Next**.

![A screenshot of a computer Description automatically
generated](./media/image66.png)

8.  在 **Optional features** （可選功能） 頁面上，確保 **Password hash
    synchronization** （密碼哈希同步） 處於選中狀態，然後選擇 **Next**
    （下一步）。

9.  在 **Ready to configure** 頁面上，確保選中 **Start the
    synchronization process when configuration completes**，然後選擇
    **Configure**（配置）。

![A screenshot of a computer Description automatically
generated](./media/image67.png)

10. 配置完成後，選擇 **Exit** （退出）。

![](./media/image68.png)

注意：等待大約 5 分鐘以完成同步。

**任務 3：使用 Azure AD Connect 配置 Microsoft Entra 混合加入**

1.  在 [SEA-SVR1](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)
    VM **桌面**上，雙擊 **Azure AD Connect**。

![Text Description automatically generated with medium
confidence](./media/image69.png)

2.  在 **Microsoft Azure Active Directory Connect** 窗口中，選擇
    **Configure**。

![](./media/image70.png)

3.  在 **Additional tasks** （其他任務） 頁面上，選擇 **Configure device
    options** （配置設備選項），然後選擇 **Next** （下一步）。

![](./media/image71.png)

4.  在 **Overview** （概述） 頁面上，選擇 **Next** （下一步）。

![A screenshot of a computer Description automatically
generated](./media/image72.png)

5.  在 “**Connect to Entra**”頁上，在 “**PASSWORD**”框中輸入
    管理員租戶密碼，然後選擇 “**Next**”。

![](./media/image73.png)

6.  在 **Device options** （設備選項） 頁面上，選擇 **Configure Hybrid
    Azure AD Join**（配置混合 Azure AD 聯接），然後選擇
    **Next**（下一步）。

![A screenshot of a computer Description automatically
generated](./media/image74.png)

7.  在 “**Device operating systems**”頁上，選擇“**Windows 10 or later
    domain-joined devices**”，然後選擇“**Next**”。

![A screenshot of a computer Description automatically
generated](./media/image75.png)

8.  在 **SCP configuration** （SCP 配置） 頁面上，選中 **Contoso.com**
    旁邊的複選框。從 **Authentication Service** 下拉列表中選擇 **Azure
    Active Directory**，然後選擇 **Add**。

![](./media/image76.png)

9.  在 **Enterprise Admin Credentials** （企業管理員憑據）
    窗口中，輸入 **Contoso\Administrator** 作為 **Username** 和
    !!**Pa55w.rd**!! 作為 **Password**。選擇 “**OK** ”，然後選擇
    “**Next**”。

![A screenshot of a computer security Description automatically
generated](./media/image77.png)

![](./media/image78.png)

10. 在 **Ready to configure** （準備配置） 頁面中，選擇 **Configure**
    （配置） 以運行配置。

![A screenshot of a computer Description automatically
generated](./media/image79.png)

11. 配置完成後，選擇 **Exit** （退出）。

![A screenshot of a computer Description automatically
generated](./media/image80.png)

12. 在任務欄上，右鍵單擊 **Windows Start button 圖標**，然後選擇
    **Windows Powershell (Admin)**。

![A screenshot of a computer Description automatically
generated](./media/image81.png)

13. 在 **Windows PowerShell** 窗口中，鍵入以下命令，然後按 **Enter**：

!!**Start-ADSyncSyncCycle -PolicyType Initial**!!

![A screenshot of a computer Description automatically
generated](./media/image82.png)

14. 關閉 PowerShell 窗口。

注意：等待大約 5 分鐘以完成同步。

**任務 4：驗證 Entra 註冊**

1.  切換到
     [SEA-CL2](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)。

2.  在登錄頁面上，選擇 **Power** 按鈕，然後選擇 **Restart**。

![Graphical user interface, application Description automatically
generated](./media/image83.png)

***請注意：**
重新啟動將觸發 [SEA-CL2](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)上的混合
Microsoft Entra Join。*

3.  After **SEA-CL2** has restarted, 以
    **Contoso\Administrator** 身份登錄，密碼為 !!**Pa55w.rd**!!

![Graphical user interface, application Description automatically
generated](./media/image84.png)

4.  在任務欄上，右鍵單擊 **Windows Start icon button** 並選擇 **Windows
    Terminal (Admin)**。

![A screenshot of a computer Description automatically
generated](./media/image81.png)

5.  在 **Windows PowerShell** 窗口中，鍵入以下命令，然後按 **Enter**：

!!**dsregcmd /status**!!

6.  在 **Device State**（設備狀態）下的輸出中，驗證這一點。 

- **AzureAdJoined : YES** 

- **DomainJoined :** 顯示 **YES。**

![](./media/image85.png)

***請注意： 如果設備尚未加入 Entra，請等待 Entra Connect
同步完成並再次重新啟動 SEA-CL2。狀態可能需要 5-10 分鐘才能更新。***

此外，您可以登錄 **SEA-SVR1** 並在 **Windows PowerShell**
窗口中鍵入以下命令以加快同步速度。

!!**Start-ADSyncSyncCycle -PolicyType Initial**!!

7.  關閉 [SEA-CL2](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10) 上的所有窗口並注銷。

8.  切換到 [SEA-SVR1](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10) 並移至
    **Microsoft Entra admin center** 窗口，導航並單擊**Identity**。

![A screenshot of a computer Description automatically
generated](./media/image7.png)

9.  在“**Identity**”部分下，選擇“**Devices**”，然後導航並單擊“**All
    devices**”，如下圖所示。

![A screenshot of a computer Description automatically
generated](./media/image8.png)

10. 驗證 **SEA-CL2** 是否已將 **Microsoft Entra hybrid joined**
    聯接作為行 **Join type** 的值。點擊 **Refresh** 按鈕，如果 SEA-CL2
    未列出。

![A screenshot of a computer Description automatically
generated](./media/image86.png)

11. 關閉 [SEA-SVR1](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)上的所有窗口。

**結果：**完成本練習後，您將成功配置和驗證 Microsoft Entra 混合聯接。
