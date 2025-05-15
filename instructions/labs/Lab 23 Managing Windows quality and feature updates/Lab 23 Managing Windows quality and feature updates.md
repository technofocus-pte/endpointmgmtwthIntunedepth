實驗 23：管理 Windows 質量和功能更新

**總結**

在本實驗中，你將使用 Intune 配置 Windows 質量和功能更新設置。

**先決條件**

在此實驗之前，必須完成以下實驗：

- 實驗 01 - 管理設備註冊到 Intune

- 實驗 06 - 將設備註冊到 Intune

- 實驗 07 - 創建和部署配置文件

**注意：**您還需要一部可以接收短信的移動電話，該短信用於保護 Azure AD 的
Windows Hello 登錄身份驗證。

**場景**

系統要求你將更新通道配置為僅影響屬 Contoso
開發人員設備組成員的設備。此組必須滿足以下要求：

- 質量更新延遲期（天）：**15**

- 功能更新延遲期（天）： **45**

- 暫停 Windows 更新的選項：**Disable**

- 檢查 Windows 更新的選項：**Enable**

- 傳遞優化：下載模式：**HTTP only, no peering (0)**

任務 1：驗證單個設備的當前更新設置

1.  切換到 [***SEA-WS1***](urn:gd:lg:a:select-vm)，以 **Cindy White**
    的身份登錄，PIN [**102938**](urn:gd:lg:a:select-vm)。

2.  選擇 **Start** 開始，然後選擇 **Settings** 圖標。

> ![](./media/image1.png)

3.  在 “**Settings**” 中，選擇 “**Windows Update**” 。

> 請注意，您可以選擇將更新暫停特定時間。

4.  在 **Windows Update** 頁面上，選擇 **Advanced
    options**（高級選項）。

> ![](./media/image2.png)

5.  在 **Advanced options** （高級選項） 頁面上，選擇 **Delivery
    Optimization** （傳遞優化）。

> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)

6.  在 “**Delivery Optimization**” 頁上，驗證 “**Allow downloads from
    other PCs**” 選項是否已啟用。

7.  選擇 **Devices on internet and my local network**（Internet
    上的設備和我的本地網絡）。

> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

8.  在 “**Settings**” 中，選擇 “**Windows Update**” 。

> ![A screenshot of a computer Description automatically
> generated](./media/image5.png)

9.  選擇 **Advanced options** （高級選項），然後選擇 **Configure update
    policies** （配置的更新策略）。

> ![A screenshot of a computer Description automatically
> generated](./media/image6.png)
>
> 請注意，設備上未設置任何更新策略。
>
> ![A screenshot of a computer Description automatically
> generated](./media/image7.png)

10. 在導航窗格中，選擇 **Windows Update**。

任務 2：查看應用的設置

1.  在 **Windows Update** 頁面上，選擇 **Update history**
    （更新歷史記錄）。

> ![A screenshot of a computer update Description automatically
> generated](./media/image8.png)

2.  查看列出的更新，然後選擇 **Uninstall updates** （卸載更新）。

> ![A screenshot of a computer update Description automatically
> generated](./media/image9.png)

3.  查看 **Installed Updates** 中列出的更新。關閉已安裝的更新。

> ![A screenshot of a computer Description automatically
> generated](./media/image10.png)

4.  關閉 Settings 應用程序。

任務 3：使用 Intune 配置更新設置

1.  切換到 [***SEA-SVR1***](urn:gd:lg:a:send-vm-keys) 並使用密碼
    [**Pa55w.rd**](urn:gd:lg:a:send-vm-keys) 以
    [**Contoso\Administrator**](urn:gd:lg:a:send-vm-keys) 身份登錄。

2.  在任務欄上，選擇 **Microsoft Edge**。

3.  在 Microsoft Edge
    中，在地址欄中鍵入 [**https://intune.microsoft.com**](urn:gd:lg:a:send-vm-keys)，然後按
    Enter。

4.  使用密碼以 [**admin@M365x19242953.onmicrosoft.com**](urn:gd:lg:a:send-vm-keys) 身份登錄。

5.  在導航窗格中，選擇 “**Devices**” ，然後選擇 “**Windows 10 and later
    Updates**” 。

> ![](./media/image11.png)

6.  在 **Devices | Update rings for Windows 10 and later**
    邊欄選項卡選擇 “**Create profile**”。

> ![](./media/image12.png)

7.  在 “**Basics**” 邊欄選項卡中，輸入以下信息，然後選擇 “**Next**” ：

    - 名字： !\![**Contoso Updates -
      standard**](urn:gd:lg:a:send-vm-keys)!!

    - 描述： !\![**Standard Windows updates
      configuration**](urn:gd:lg:a:select-vm)!!

> ![](./media/image13.png)

8.  在 **Update ring settings** 邊欄選項卡中，輸入以下信息，然後選擇
    **Next**：

    - 質量更新延遲期（天）：[**15**](https://urn:gd:lg:a:send-vm-keys/)

    - 功能更新延遲期（天）：[**45**](https://urn:gd:lg:a:send-vm-keys/)

    - 暫停 Windows 更新的選項：**Disable**

    - 檢查 Windows 更新的選項：**Enable**

> ![](./media/image14.png)

9.  在 “**Assignments**” 邊欄選項卡上的 “**Included groups**” 下，選擇
    “**Add groups**” 。

10. 在 “**Select groups to include**” 邊欄選項卡上的 “**Search**”
    框中，選擇 “**Contoso Developer devices**”，然後選擇 “**Select**” 。

> ![A screenshot of a computer Description automatically
> generated](./media/image15.png)
>
> ![](./media/image16.png)

11. 選擇 “**Next**”，然後在 “**Review + create**” 邊欄選項卡上選擇
    “**Create**” 。

12. 從導航欄中，選擇 **Configuration profiles**。

13. 在 **Devices | Configuration** （配置）
    邊欄選項卡的詳細信息窗格中，選擇 **Create policy**（創建策略）。

> ![](./media/image17.png)

14. 在 **Create a profile** （創建配置文件）
    邊欄選項卡中，選擇以下選項，然後選擇 **Create** （創建）：

    - 平臺：**Windows 10 and later**

    - 配置文件類型：**Templates**

    - 模板名稱：**Delivery Optimization**

> ![](./media/image18.png)

15. 在 “**Basics**” 邊欄選項卡中，輸入以下信息，然後選擇 “**Next**” ：

    - 名字： !\![**Contoso Developer - Delivery
      optimization**](urn:gd:lg:a:send-vm-keys)!!

    - 描述： !\![**Delivery optimization for
      Developer**](urn:gd:lg:a:send-vm-keys)!!

> ![](./media/image19.png)

16. 在 “**Configuration settings**” 邊欄選項卡中，輸入以下信息，然後選擇
    “**Next**” ：

    - 下載模式： **HTTP only, no peering (0)**

> ![A screenshot of a computer Description automatically
> generated](./media/image20.png)

17. 在 “**Assignments**” 邊欄選項卡上的 “**Included groups**” 下，選擇
    “**Add groups**” 。

18. 在 “**Select groups to include**” 邊欄選項卡上，選擇 “**Contoso
    Developer devices**” ，然後選擇 “**Select**” 。

> ![A screenshot of a computer Description automatically
> generated](./media/image21.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image22.png)

19. 選擇 “**Next**” 兩次，然後在 “**Review + create**” 邊欄選項卡上選擇
    “**Create**” 。

> ![Screenshot](./media/image23.png)

任務 4：驗證設備的更新設置是否集中管理

1.  切換到 [***SEA-WS1***](https://intune.microsoft.com)。

2.  選擇 **Start** 開始，然後選擇 **Settings** 圖標。

> ![](./media/image24.png)

3.  在 “**Settings**” 應用中，選擇 “**Accounts**” ，然後選擇 “**Access
    work or school**” 。

> ![A screenshot of a computer Description automatically
> generated](./media/image25.png)

4.  在 “**Access work or school**” 部分中，選擇 “**Connected to
    Contoso's Azure AD**” 鏈接，然後選擇 “**Info**” 。

> ![A screenshot of a computer Description automatically
> generated](./media/image26.png)

5.  在 “**Areas Managed by Contoso**” 對話框中，選擇 “**Sync**”
    。等待同步完成。

> ![A screenshot of a computer Description automatically
> generated](./media/image27.png)

6.  在 “**Settings**” 應用中，選擇 “**Windows Update**” 。

> 請注意，您無法暫停更新。

7.  選擇 **Advanced options**（高級選項）。

> ![](./media/image28.png)

8.  選擇 **Delivery Optimization** （傳遞優化）。

> ![A screenshot of a computer Description automatically
> generated](./media/image29.png)
>
> 請注意， “**Allow downloads from other PCs**” 不可用。

9.  在 “**Settings**” 應用中，選擇 “**Windows Update**” ，選擇
    “**Advanced options**” ，然後選擇 “**Configured update policies**”
    。

> ![](./media/image30.png)
>
> 記下設備上設置的所有策略。

10. 關閉所有打開的應用程序和窗口。

> **注意：**練習環境配置為阻止應用 Windows
> 更新，以避免在練習期間出現延遲和意外影響。
