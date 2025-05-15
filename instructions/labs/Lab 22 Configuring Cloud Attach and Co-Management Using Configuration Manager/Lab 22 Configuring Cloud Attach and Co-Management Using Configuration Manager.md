實驗 22：使用 Configuration Manager 配置 Cloud Attach 和共同管理

**總結**

在本實驗中，您將啟用 Cloud Attach 並使用 Microsoft Endpoint
Configuration Manager 和 Microsoft Intune 配置共同管理。

**先決條件**

在此實驗之前，必須完成以下實驗：

- 實驗 01 - 在 Microsoft Entra ID 中管理身份

- 實驗 02 - 使用 Azure AD Connect 同步身份

- 實驗 03 - 配置和管理 Microsoft Entra ID 加入

- 實驗 05 - 管理設備註冊到 Intune

**場景**

Contoso 同時具有 Microsoft Endpoint Configuration Manager 實現和
Microsoft Intune。您需要配置這兩項服務之間的集成，並為託管的 Windows
設備啟用共同管理。您將啟用 Cloud Attach，配置共同管理，然後使用 SEA-CL1
驗證設置。

任務 1：準備環境

1.  切換到[***SEA-SVR1***](urn:gd:lg:a:select-vm) 並以 [**Contoso\Administrator**](urn:gd:lg:a:send-vm-keys) 身份登錄，密碼為 !\![**Pa55w.rd**](urn:gd:lg:a:send-vm-keys)!!。

2.  從服務器管理器中，選擇 “**Tools**” ，然後選擇 “**Active Directory
    Users and Computers**” 。

> ![](./media/image1.png)

3.  在導航窗格中，選擇 **Seattle Clients**。

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)

4.  右鍵單擊 **SEA-CL1**，然後選擇 **Move**。

> ![A computer screen shot of a computer Description automatically
> generated](./media/image3.png)

5.  在 “**Move**” 對話框中，選擇 “**Entra clients**”，然後選擇 “**OK**”
    。

> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

6.  關閉 **Active Directory Users and Computers**。

7.  在任務欄上，右鍵單擊 **Start** 並開始並選擇 **Windows Powershell
    （Admin）。**

> ![A screenshot of a computer Description automatically
> generated](./media/image5.png)

8.  在 **Windows PowerShell** 窗口中，鍵入以下命令，然後按 **Enter**：

> !!**Start**-ADSyncSyncCycle -PolicyType **Initial**!!
>
> ![A screenshot of a computer screen Description automatically
> generated](./media/image6.png)

9.  關閉 PowerShell 窗口。

10. 切換到 [***SEA-CL1***](urn:gd:lg:a:select-vm)。

11. 在任務欄上，右鍵單擊 “**Start**” ，選擇 “**Shut down or sign
    out**”，然後選擇 “**Restart**” 。

> ![](./media/image7.png)
>
> **注意：**重新啟動將在 SEA-CL1 上觸發混合 Azure AD 聯接。

12. [***SEA-CL1***](urn:gd:lg:a:select-vm) 重啟後，使用密碼
    [**Pa55w.rd**](urn:gd:lg:a:send-vm-keys) 以
    [**Contoso\Administrator**](urn:gd:lg:a:send-vm-keys) 身份登錄。

13. 在任務欄上，右鍵單擊 **Start** 並開始並選擇 **Windows Terminal
    (Admin)**。

> ![](./media/image8.png)

14. 在 **Windows PowerShell** 窗口中，鍵入以下命令，然後按 **Enter**：

> !!dsregcmd /**status**!!

15. 在 **Device State**（設備狀態）下的輸出中，驗證是否顯示
    **AzureAdJoined ： YES** 和 **DomainJoined ： YES**。

> ![](./media/image9.png)
>
> **注意：**如果設備尚未加入 Azure AD，請等待 Azure AD Connect
> 同步完成並再次重新啟動 SEA-CL1。

16. 關閉 [***SEA-CL1***](urn:gd:lg:a:select-vm) 上的所有窗口。

任務 2：創建設備集合

1.  切換到 [***SEA-CFG1***](urn:gd:lg:a:select-vm)，使用密碼
    [**Pa55w.rd**](urn:gd:lg:a:send-vm-keys) 以
    [**Contoso\Administrator**](urn:gd:lg:a:send-vm-keys) 身份登錄。

2.  在任務欄上，選擇 **Configuration Manager Console**。此時將打開
    Microsoft Endpoint Configuration Manager 控制台。

> ![A screenshot of a computer Description automatically
> generated](./media/image10.png)

3.  在 **Assets and Compliance** 工作區中，選擇 **Device Collections**。

4.  右鍵單擊 **Device Collections** （設備集合），然後選擇 **Create
    Device Collection** （創建設備集合）。此時將打開 Create Device
    Collection Wizard。

> ![](./media/image11.png)

5.  在 **General** （常規） 頁面上，配置以下內容，然後選擇 **Next**
    （下一步）：

    - 名字： !\![**Co-managed Devices**](urn:gd:lg:a:send-vm-keys)!!

    - 限制收集： **All Desktop and Server Clients**

> ![](./media/image12.png)
>
> ![](./media/image13.png)
>
> ![](./media/image14.png)

6.  在 “**Membership Rules**” 頁上，選擇 “**Next**” 。

> ![A screenshot of a computer Description automatically
> generated](./media/image15.png)

7.  在 Configuration Manager 警告處，選擇 “**OK**”
    。您將在後續步驟中添加直接成員。

> ![A screenshot of a computer error Description automatically
> generated](./media/image16.png)

8.  在 **Summary** （摘要） 頁面上，選擇 **Next** （下一步），然後在
    **Completion** （完成） 頁面上，選擇 **Close** （關閉）。

> ![A screenshot of a computer Description automatically
> generated](./media/image17.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image18.png)

任務 3：將設備分配給現有集合

1.  在 **Assets and Compliance** （資產和合規性） 工作區中，選擇
    **Devices** （設備）。

> 記下列出的設備。任何帶有綠色圓圈和白色對勾標記的設備當前都處於活動狀態。

2.  在詳細信息窗格中，選擇 **SEA-CL1**。

3.  右鍵單擊 **SEA-CL1**，指向 “**Add Selected Items**” ，然後選擇
    “**Add Selected Items to Existing Device Collection**” 。

> ![](./media/image19.png)

4.  在 **Select Collection** 對話框中，選擇 **Co-managed
    Devices**，然後選擇 **OK**。

> ![](./media/image20.png)

5.  若要驗證，請在 “**Assets and Compliance**” 工作區中，選擇 “**Device
    Collections**” ，然後雙擊 “**Co-managed Devices**” 。

> ![](./media/image21.png)
>
> ![](./media/image22.png)
>
> **SEA-CL1** 應列為此集合的成員。

任務 4：雲附加 Endpoint Configuration Manager

1.  在 Microsoft Endpoint Configuration Manager 控制台中，選擇
    “**Administration**” 工作區。

> ![](./media/image23.png)

2.  在 **Administration** 工作區中，展開 **Cloud Services**，然後選擇
    **Cloud Attach**。

> ![A screenshot of a computer Description automatically
> generated](./media/image24.png)

3.  在功能區中，選擇 **Configure Cloud Attach**。此時將打開 **Cloud
    Attach Configuration Wizard** 。

> ![](./media/image25.png)
>
> ![](./media/image26.png)

4.  在 **Cloud Attach Configuration Wizard** 的 **Cloud attach**
    頁面上，選擇 **Sign In** （登錄）。

5.  登錄身份 [**admin@M365x19242953.onmicrosoft.com**](urn:gd:lg:a:send-vm-keys) 密碼為 [**9whL~;H8ke=D1^95%D**](urn:gd:lg:a:send-vm-keys).

6.  在 **Cloud attach** （雲附加） 頁面上，選擇 **Customize settings**
    （自定義設置），然後選擇 **Next** （下一步）。

> ![](./media/image27.png)

7.  在 **Create AAD Application** （創建 AAD 應用程序） 警告中，選擇
    **Yes** （是）。

> ![A screenshot of a computer Description automatically
> generated](./media/image28.png)

8.  在 **Configure upload** （配置上傳） 頁面上，接受默認值並選擇
    **Next** （下一步）。

> ![A screenshot of a computer Description automatically
> generated](./media/image29.png)

9.  在 “**Enablement**” 頁上的 “**Automatic enrollment in Intune**”
    旁邊，選擇 “**Pilot**” 。

10. 在 “**Enablement**” 頁上的 “**Intune Auto Enrollment**” 旁邊，選擇
    “**Browse**” 。

> ![](./media/image30.png)

11. 在 **Select Collection** （選擇集合） 對話框中，選擇 **Co-managed
    Devices** （共同管理的設備），然後選擇 **OK** （確定）。 選擇
    **Next** （下一步）。

> ![A screenshot of a computer Description automatically
> generated](./media/image31.png)

12. 在 **Summary** （摘要） 頁面上，選擇 **Next** （下一步），然後在
    **Completion** （完成） 頁面上，選擇 **Close** （關閉）。

> ![A screenshot of a computer Description automatically
> generated](./media/image32.png)

任務 5：配置工作負載

1.  在 Microsoft Endpoint Configuration Manager 控制台中，選擇
    “**Administration**” 工作區。

2.  在 **Administration** 工作區中，展開 **Cloud Services** ，然後選擇
    **Cloud Attach**。

3.  在詳細信息窗格中，選擇 **CoMgmtSettingsProd**，然後從功能區中選擇
    **Properties**。

> ![A screenshot of a computer Description automatically
> generated](./media/image33.png)
>
>  **CoMgmtSettingsProd Properties** （屬性） 框打開。

4.  選擇 **Workloads** （工作負載）。在 “**Workloads**”
    頁上，將滑塊拖動到 “為以下工作負載 **Pilot Intune**” ：

    - **Compliance policies**

    - **Client apps**

    - **Windows Update policies**

> ![](./media/image34.png)

5.  選擇 **Staging page**。在 “**Staging**” 頁面上，選擇 “**Compliance
    policies**” 、 “**Client Apps**” 和 “**Windows Update Policies**”
    旁邊的 “**Browse**” ，然後為每個工作負載選擇 “**Co-managed
    Devices**” 集合。

6.  選擇 **OK** 關閉 **CoMgmtSettingsProd Properties** 框。

> ![](./media/image35.png)

任務 6：驗證 SEA-CL1 是否為共同管理

1.  切換到 [***SEA-SVR1***](urn:gd:lg:a:select-vm)。

2.  在任務欄上，選擇 **Microsoft Edge**，在地址欄中鍵入
    [**https://entra.microsoft.com**](https://entra.microsoft.com)，然後按
    **Enter**。

3.  以用戶
     [**admin@M365x19242953.onmicrosoft.com**](urn:gd:lg:a:send-vm-keys)身份登錄，然後使用密碼。

4.  如果 **Stay signed in?** 提示符，請選擇 **No**。

> 此時將打開 Microsoft Entra 管理中心。

5.  在 Microsoft Entra 管理中心的導航窗格中，選擇 “**Identity**” 。

> ![](./media/image36.png)

6.  在 **Devices|All devices** 頁面，驗證是否列出了 **SEA-CL1** 以及
    “**聯接類型**” 是否為 “**Microsoft Entr hybrid Join**” 。

> ![](./media/image37.png)

7.  在 Microsoft Edge 中打開另一個選項卡並在地址欄中鍵入
     [**https://intune.microsoft.com**](https://intune.microsoft.com) ，然後按
    **Enter**。

8.  在導航窗格中，選擇 **Devices** （設備），然後選擇 **All devices**
    （所有設備）。

9.  驗證 SEA-CL1 是否列出，並將 “**Managed by**” 設置設置為
    “**Co-managed**” 。

> ![](./media/image38.png)
>
> 可能需要一些時間才能顯示。根據需要刷新詳細信息窗格。機器可能會出現在不同的名稱下，單擊設備以確認它顯示
> **SEA-CL1**。

10. 選擇 **SEA-CL1**
    ，然後在詳細信息窗格中向下滾動以顯示與共同管理狀態相關的信息。

11. 關閉Microsoft Edge。

**結果：**完成本練習後，您將成功啟用雲附加並使用 Microsoft Endpoint
Configuration Manager 和 Microsoft Intune 配置共同管理。
