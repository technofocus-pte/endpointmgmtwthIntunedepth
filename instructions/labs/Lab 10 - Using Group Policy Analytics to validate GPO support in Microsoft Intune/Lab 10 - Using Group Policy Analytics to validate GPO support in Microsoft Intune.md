**實驗 10 - 使用組策略分析驗證 Microsoft Intune 中的 GPO 支持**

**總結**

在本實驗中，您將使用組策略分析導入 Active Directory 組策略對象 （GPO）
並確定支持等效 Microsoft Intune MDM 策略的設置。

**場景**

Contoso 傳統上使用 Active Directory GPO
在整個域中部署計算機和用戶策略設置。您計劃將所有受支持的 GPO 設置移動到
Microsoft Intune 配置文件。您有一個名為 **Windows Client Policy** 的
GPO。您需要使用組策略分析來驗證 Windows 客戶端策略 GPO
中的設置，並確定哪些設置可以成功遷移到 Intune。

**任務 1：將 Windows 客戶端策略 GPO 導出到 XML 文件**

1.  使用提供的憑據搜索欄登錄  ，鍵入 !!**Server
    Manager**!!，然後選擇它。

> ![](./media/image1.png)

2.  在 **Server Manager - Dashboard** 中，選擇 **Tools** ，然後選擇
    **Group Policy Management**。

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)

3.  在組策略管理控制台中，依次展開
    **Forest:Contoso.com**、**Domains**、**Contoso.com**，然後選擇
    **Group Policy Objects**。

> 驗證是否列出了多個組策略對象。

4.  在詳細信息窗格中，選擇 **Windows Client Policy** GPO。

> ![](./media/image3.png)

5.  右鍵單擊 **Windows Client Policy**，然後選擇 **Save Report**。

> ![](./media/image4.png)

6.  在 “保存 GPO 報告” 對話框中，選擇 “**Documents**”，將 “**Save as
    type**” 更改為 “**XML file**”，然後選擇 “**Save**”。

> ![](./media/image5.png)

7.  關閉組策略管理控制台。

8.  關閉 Server Manager。

**任務 2：使用組策略分析分析 Windows 客戶端 GPO**

1.  打開 Microsoft Edge，鍵入
    !!**https://intune.microsoft.com**!!，然後按 **Enter**。

2.  如果出現提示，請使用 Office 365 租戶憑據登錄。

3.  在 **Microsoft Intune 管理中心**，導航並選擇“**Devices**”。

> ![](./media/image6.png)

4.  導航到 **Manage devices** 部分，然後選擇 **Group Policy
    analytics**。

> ![](./media/image7.png)

5.  在 **Devices | Group Policy analytics**
    邊欄選項卡中，選擇“**Import**”。

> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)

6.  在 **GPO file upload** 選項卡上，單擊旁邊的文件夾 **Select a file**
    搜索欄 如下圖所示。

> ![A screenshot of a computer Description automatically
> generated](./media/image9.png)

7.  在 **Open** 框中，選擇 **Documents**，然後選擇 **Windows Client
    Policy.xml**。然後，點擊 **Open** 按鈕。

> ![A screenshot of a computer Description automatically
> generated](./media/image10.png)

8.  點擊 **Next** 按鈕。

> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)

9.  在 **Scope tags** 中，單擊 **Next** 按鈕。

> ![A screenshot of a computer Description automatically
> generated](./media/image12.png)

10. 在 **Review + create** 選項卡中，單擊 **Create** 按鈕。

> ![A screenshot of a computer Description automatically
> generated](./media/image13.png)

11. Windows 客戶端策略 GPO 會立即導入和分析。關閉 **Import GPO files**
    （導入 GPO 文件） 頁面。

12. 在 **Devices | Group Policy analytics** 邊欄選項卡中，查看
    “**Windows Client Policy**” 旁邊的信息。

> 請注意，89% 的設置都支持 MDM。
>
> ![A screenshot of a computer Description automatically
> generated](./media/image14.png)

13. 在 MDM Support （MDM 支持） 下，選擇 **89%**。

> 請注意每個受支持設置的每個**設置名稱、MDM 支持、CSP 名稱**和 **CSP
> 映射**。記下哪些設置沒有等效的 CSP 映射。
>
> ![A screenshot of a computer Description automatically
> generated](./media/image15.png)

14. 關閉 **Windows Client Policy** 窗口。

**任務 3：查看組策略分析摘要報告**

1.  在 **Microsoft Intune 管理中心**導航菜單中，選擇 “**Reports**”。

> ![](./media/image16.png)

2.  在 **Reports** （報告） 頁面的 **Device management** （設備管理）
    部分中，選擇 **Group Policy analytics** （組策略分析）。

> ![](./media/image17.png)

3.  在詳細信息窗格中的 **Summary** （摘要） 下，選擇 **Refresh**
    （刷新）。您可能需要刷新幾次

> 刷新和構建摘要報告可能需要 5-10 分鐘。

4.  查看 **Group policy migration readiness** 信息。

> ![A screenshot of a computer Description automatically
> generated](./media/image18.png)
>
> 應該有許多策略可供遷移，並且有許多策略不受支持。

5.  選擇 **Reports** （報告） 選項卡，然後選擇 **Group policy migration
    readiness** （組策略遷移就緒情況）。

> ![A screenshot of a group policy migration Description automatically
> generated](./media/image19.png)

6.  選擇 **Generate report**（生成報告）。

> ![A screenshot of a computer Description automatically
> generated](./media/image20.png)

7.  組策略遷移就緒情況報告提供與每個設置相關的信息，以及支持的配置文件類型。

> ![A screenshot of a computer Description automatically
> generated](./media/image21.png)

8.  關閉 **Group policy migration readiness** （組策略遷移就緒） 窗口。

**結果：**完成本練習後，您將成功導出 GPO 並使用組策略分析來驗證 Intune
中的等效策略設置。
