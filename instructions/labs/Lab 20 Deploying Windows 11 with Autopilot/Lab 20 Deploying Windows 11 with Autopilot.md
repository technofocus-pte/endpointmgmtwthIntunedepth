實驗 20：使用 Autopilot 部署 Windows 11

**總結**

在本實驗中，您將學習如何使用用戶驅動模式為 Windows 11 設備配置
Autopilot。

**先決條件**

在此實驗之前，必須完成以下實驗：

- 實驗 01 - 在 Microsoft Entra ID 中管理身份

- 實驗 02 - 使用 Azure AD Connect 同步身份

- 實驗 11 - 使用 Microsoft 部署工具包部署 Windows 11

**場景**

Contoso IT 計劃使用 Autopilot 推出新 Windows 11
設備的部署。這些設備默認安裝了 Windows 11。用戶應該能夠在 OOBE
期間使用其 Microsoft Entra ID
憑據登錄來連接設備、打開設備並回答最少的問題。該過程應自動註冊並加入
Entra ID 域。系統要求您使用 SEA-WS4 配置和測試體驗，您最近使用 Hyper-V
安裝和配置了 SEA-WS4。

任務 1：在 Microsoft Entra 管理中心創建組。

1.  切換並登錄 [***SEA-SVR1***](urn:gd:lg:a:select-vm) 作為!!  使用密碼 [**Pa55w.rd**](urn:gd:lg:a:send-vm-keys) 並關閉 **Server
    Manager**.**Contoso\Administrator**!! 用密碼 !!!!  並關閉 **Server
    Manager**。

2.  在任務欄上，選擇 **Microsoft Edge**。

3.  在 Microsoft Edge 的地址欄中，鍵入 !!﷟HYPERLINK
    "https://entra.microsoft.com"**ttps://entra.microsoft.com**!!,
    然後按 **Enter**如果出現提示，請使用您和
    password.[**admin@M365xXXXXXXXX.onmicrosoft.com**](mailto:admin@M365xXXXXXXXX.onmicrosoft.com)!!
     和密碼。

![](./media/image1.png)

4.  在導航窗格中，選擇 **Identity** （身份）。

5.  在 **Identity** （身份） 下，選擇 **Groups** （組）。

> ![](./media/image2.png)

6.  在 “**Groups | All groups**” 邊欄選項卡中，選擇 “**New group**” 。

> ![](./media/image3.png)

7.  在 **New Group** （新建組） 邊欄選項卡的 **Group type** （組類型）
    列表中，選擇 **Security** （安全性）。

8.  在 **Group name** （組名稱） 框中，鍵入 !!﷟HYPERLINK
    "http://urn:gd:lg:a:send-vm-keys"**IT Devices**!!.

9.  在 **Group description** （組描述） 框中，鍵入 !!﷟HYPERLINK
    "http://urn:gd:lg:a:send-vm-keys"**IT Department Devices**!!.

10. 在 “**Membership type**” 列表中，選擇 “**Dynamic Device**” 。

11. 選擇 **Add dynamic query**（添加動態查詢）。

> ![](./media/image4.png)

12. 在 **Dynamic membership rules** 邊欄選項卡上，選擇 **Rule syntax**
    框上方的 **Edit**。

> ![](./media/image5.png)

13. 在 Edit rule syntax （編輯規則語法）
    文本框中，添加以下簡單成員身份規則，然後選擇 **OK** （確定）。

14. !!(device.devicePhysicalIDs -any (\_ -contains "\[ZTDId\]"))!!

> ![](./media/image6.png)

15. 選擇 **Save** 以關閉 **Dynamic membership rules**，然後選擇
    **Create** 以創建組。

> ![A screenshot of a computer Description automatically
> generated](./media/image7.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)
>
> ![](./media/image9.png)

任務 2：生成特定於設備的逗號分隔值 （CSV） 文件

1.  切換到 [***SEA-SVR2***](urn:gd:lg:a:select-vm) 並以 [**Contoso\Administrator**](urn:gd:lg:a:send-vm-keys) 身份登錄，密碼為
    !!﷟HYPERLINK "http://urn:gd:lg:a:send-vm-keys"**Pa55w.rd**!!.

> ![A screenshot of a computer Description automatically
> generated](./media/image10.png)

2.  在任務欄中選擇 **Hyper-V Manager**。

> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)

3.  在虛擬機下，右鍵單擊 **SEA-WS4** 並選擇 **Connect**。

> ![](./media/image12.png)

4.  在 **SEA-WS4** 窗口中，選擇 **Start**
    開始。當計算機啟動時，將窗口最大化。

> ![A screenshot of a computer Description automatically
> generated](./media/image13.png)

5.  以 [**Administrator**](urn:gd:lg:a:send-vm-keys) 身份登錄
    **SEA-WS4**，密碼為 !!﷟HYPERLINK
    "http://urn:gd:lg:a:send-vm-keys"**Pa55w.rd**!!.

> ![A screenshot of a computer Description automatically
> generated](./media/image14.png)

6.  右鍵單擊 “**Start**”，選擇 “**Windows Terminal (Admin)**” ，然後在
    “**User Account Control**” 提示符處選擇 “**Yes**” 。

> ![](./media/image15.png)
>
> ![A screenshot of a computer error Description automatically
> generated](./media/image16.png)

7.  在 Windows PowerShell 命令行提示符下，鍵入以下 cmdlet，然後按
    **Enter**：

> !! Install-Script -Name Get-WindowsAutoPilotInfo!!

![A screenshot of a computer Description automatically
generated](./media/image17.png)

8.  您將收到 3
    個提示。每次鍵入 [**Y**](urn:gd:lg:a:send-vm-keys)，然後按
    **Enter**。

> ![](./media/image18.png)

9.  在 Windows PowerShell 命令行提示符下，鍵入以下 cmdlet，然後按
    **Enter**：

> !!**Set**-ExecutionPolicy *RemoteSigned*!!

10. 出現提示時，鍵入 [**Y**](urn:gd:lg:a:send-vm-keys)，然後按 Enter。

11. 在 Windows PowerShell 命令行提示符下，鍵入以下 cmdlet，然後按
    **Enter**：

> !!Get-WindowsAutoPilotInfo.ps1 -OutputFile C:\Computer.csv!!
>
> ![](./media/image19.png)

12. 在 Windows PowerShell 命令行提示符下，鍵入以下命令，按
    **Enter**，然後查看文件內容：

13. **type** !!C:\Computer.csv!!

> ![](./media/image20.png)

14. 在 Windows PowerShell 命令行提示符下，鍵入以下命令，然後按
    **Enter**。這會將文件複製到 **SEA-SVR2**：

15. copy !!c:\computer.csv \\sea-svr2\labfiles!!

> ![A screenshot of a computer screen Description automatically
> generated](./media/image21.png)

16. 關閉 Windows PowerShell 命令提示符。

任務 3：使用 Windows Autopilot 部署配置文件

1.  切換到 [***SEA-SVR1***](urn:gd:lg:a:select-vm)。

> ![](./media/image22.png)

2.  在 **Microsoft Edge** 中，打開一個新選項卡並導航到 !!﷟HYPERLINK
    "https://intune.microsoft.com"**https://intune.microsoft.com**!!
    如果出現提示，請登錄並password.[**admin@M365xXXXXXXX.onmicrosoft.com**](mailto:admin@M365xXXXXXXX.onmicrosoft.com)!!
    和密碼。

3.  在 **Microsoft Intune 管理中心**，選擇 “**Devices**” 。

4.  在 **Device enrollment** （設備註冊） 部分中，選擇 **Enroll
    devices** （註冊設備）。

5.  在詳細信息窗格中，向下滾動到 **Windows Autopilot Deployment
    Program**，然後選擇 **Devices**。

> ![A screenshot of a computer Description automatically
> generated](./media/image23.png)

6.  在菜單欄上的 **Windows Autopilot devices** 邊欄選項卡中，選擇
    “**Import**” ，選擇 **folder icon**，然後瀏覽到 !!﷟HYPERLINK
    "http://urn:gd:lg:a:send-vm-keys"**\\SEA-SVR2\Labfiles**!!,
    選擇**Computer.csv**，選擇 **Open**，然後選擇 “**Import**” 。

> ![](./media/image24.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image25.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image26.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image27.png)
>
> **注意：** 導入過程最多可能需要 15 分鐘，但通常需要大約 5 分鐘。
>
> **重要提示：**該過程完成後，設備可能不會顯示。如果是這種情況，請選擇
> **Sync** （同步） 按鈕，等待幾分鐘，然後選擇 **Refresh** （刷新）。

7.  選擇 “**X**” 以關閉 “**Windows Autopilot devices**” 邊欄選項卡。

> ![](./media/image28.png)

8.  在 Windows enrollment （Windows 註冊）
    邊欄選項卡上的詳細信息窗格中，選擇 **Deployment
    Profiles**（部署配置文件）。

> ![](./media/image29.png)

9.  在 “**Windows AutoPilot deployment profiles**” 邊欄選項卡上，選擇
    “**Create profile**” ，然後選擇 “**Windows PC**” 。

> ![](./media/image30.png)

10. 在 **Basics** 選項卡的 **Name** 文本框中，鍵入 !!﷟HYPERLINK
    "http://urn:gd:lg:a:send-vm-keys"**Contoso profile1**!!.

11. 對於 “**Convert all targeted devices to Autopilot**” ，選擇
    “**No**”，然後選擇 “**Next**” 。

> ![A screenshot of a computer Description automatically
> generated](./media/image31.png)

12. 在 “**Out-of-box experience（OOBE）**” 選項卡上，確保將
    “**Deployment mode**” 設置為 “**User-Driven**” 。

13. 確保將 **Join to Microsoft Entra ID as** 設置為 **Microsoft Entra
    Joined**。

14. 確保設置了以下選項：

    - Microsoft 軟件許可條款：**Hide**

    - 隱私設置：**Hide**

    - 隱藏更改帳戶選項：**Hide**

    - 用戶帳戶類型：**Administrator**。

    - 允許預配置部署：**No**

    - 語言 （區域） ：**Operating system default**

    - 自動配置鍵盤：**Yes**

    - 應用設備名稱模板： **No**

15. 選擇 **Next**。

> ![](./media/image32.png)

16. 在 **Assignments** （分配） 選項卡上的 **Included groups**
    （包含的組） 下，選擇 **Add groups** （添加組）。

17. 選擇 **IT Devices** 組，然後單擊 **Select**。選擇
    **Next**（下一步）。

> ![](./media/image33.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image34.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image35.png)

18. 在 “**Review + create**” 邊欄選項卡上，查看信息，然後選擇
    “**Create**” 。

> ![A screenshot of a computer Description automatically
> generated](./media/image36.png)
>
> ![](./media/image37.png)

任務 4：重置電腦

1.  切換到 [***SEA-SVR2***](urn:gd:lg:a:select-vm)。 **SEA-WS4**
    計算機仍應最大化。

> ![](./media/image38.png)

2.  在 **SEA-WS4** 上，選擇 **Start** 開始，鍵入 !!﷟HYPERLINK
    "http://urn:gd:lg:a:send-vm-keys"**reset**!! ，然後選擇 **Reset this
    PC**。

> ![](./media/image39.png)

3.  在 “**Reset this PC**” 部分中，選擇 “**Reset PC**” 。

> ![A screenshot of a computer Description automatically
> generated](./media/image40.png)

4.  選擇 **Remove everything** （刪除所有內容），然後選擇 **Local
    reinstall**（本地重新安裝）。

> ![A blue screen with white text Description automatically
> generated](./media/image41.png)
>
> ![A blue screen with white text Description automatically
> generated](./media/image42.png)

5.  選擇 **Next** ，然後選擇 **Reset**。

> ![A screenshot of a computer Description automatically
> generated](./media/image43.png)
>
> ![A blue screen with white text Description automatically
> generated](./media/image44.png)
>
> **注意：**通常，新部署物理設備不需要此任務。設備的 Autopilot
> 信息由製造商提供，也可以在 OOBE
> 之前從設備獲取。在本實驗中，我們必須啟動重置以模擬新設備 OOBE。
>
> **注意：** 此過程可能需要 45-60
> 分鐘，並且在此過程中會重新啟動幾次。在此任務完成時，您的教師可以繼續學習下一個模塊。請務必在下一次實驗期間返回完成任務
> 5。

任務 5：驗證 Autopilot 部署

1.  在 **Contoso Corp. 登錄頁面上**，輸入 !!﷟HYPERLINK
    "mailto:Cindy@M365x19242953.onmicrosoft.com"**Cindy@M365x19242953.onmicrosoft.com**!!
    ，然後選擇 **Next**。

2.  在 Password 頁面，輸入 !!﷟HYPERLINK
    "mailto:P@55w.rd1234"**P@55w.rd1234**!!，然後選擇 **Sign in**
    （登錄）。

3.  在 “**Use Windows Hello with your account**” 中，選擇 “**OK**” 。

> ![A screenshot of a computer Description automatically
> generated](./media/image45.png)

4.  在 **Verify your identity** （驗證您的身份） 頁面上，選擇 Text
    verification method （文本驗證方法）。

> ![A screenshot of a computer Description automatically
> generated](./media/image46.png)

5.  在 **Enter code** （輸入代碼）
    頁面上，輸入已發送到您的移動設備的代碼，然後選擇 **Verify**
    （驗證）。

> ![A screenshot of a computer Description automatically
> generated](./media/image47.png)

6.  在 **Setup up a PIN** 對話框的 **New PIN** 和 **Confirm PIN**
    字段中，輸入 [**102938**](urn:gd:lg:a:send-vm-keys)，然後選擇
    **OK**。

> ![A screenshot of a computer Description automatically
> generated](./media/image48.png)

7.  在 **All set！**頁面上，選擇 **OK**。

8.  選擇 **Start** （開始），然後選擇 **Settings** （設置）。

> ![A screenshot of a computer Description automatically
> generated](./media/image49.png)

9.  選擇 “**Accounts**”，然後選擇 “**Access work or school**”
    。驗證設備是否已連接到 Contoso 的 Azure AD。

> ![A screenshot of a computer Description automatically
> generated](./media/image50.png)

10. 選擇 “**Connected to Contoso's Azure AD**”，然後選擇 “**Info**” 。

> ![A screenshot of a computer Description automatically
> generated](./media/image51.png)

11. 在 **Managed by Contoso** （由 Contoso 管理）
    頁面上，向下滾動，然後選擇 **Sync** （同步）。

> ![A screenshot of a computer Description automatically
> generated](./media/image52.png)
>
> ![](./media/image53.png)

12. 在 **SEA-WS4** 上，關閉 **Settings** 窗口。

13. 切換到 [***SEA-SVR1***](urn:gd:lg:a:select-vm)。

14. 在 Microsoft Entra 管理中心，選擇 “**Identity**”，選擇 “**Devices**”
    ，然後選擇 “**All devices**” 。

> ![](./media/image54.png)
>
> 請注意，新設備顯示的名稱以 “**DESKTOP-**” 開頭。另請注意，加入類型是
> **Microsoft Entra ID joined**，Cindy White 作為所有者加入。

15. 選擇 Autopilot 設備。查看頂部菜單欄中的管理選項。

> 請注意，您可以 **Retire、Wipe、Sync** 和 **Restart** 設備。

16. 選擇菜單欄末尾的省略號，並注意其他管理功能。

> ![A screenshot of a computer Description automatically
> generated](./media/image55.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image56.png)
>
> 其他功能包括 Fresh Start、Autopilot Reset、Quick scan、Full scan 等。

17. 關閉Microsoft Edge。

**結果：**完成本練習後，您將使用用戶驅動模式為 Windows 11 設備配置了
Autopilot。
