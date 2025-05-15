Lab12 - 使用 Microsoft Intune 部署雲應用

**總結**

在本實驗室中，你將使用 Intune 和公司門戶網站創建和部署基於雲的應用。

**先決條件**

在此實驗之前，必須完成以下實驗：

- 實驗 \#1 - 在 Microsoft Entra ID 中管理身份

- 實驗 \#2 - 使用 Microsoft Entra Connect 同步標識

- 實驗 \#5 - 管理設備註冊到 Microsoft Intune

- 實驗 \#6 - 將設備註冊到 Microsoft Intune

- 實驗 \#7 - 創建和部署配置文件

**注意：**您還需要一部可以接收短信的移動電話，該短信用於保護 Windows
Hello 登錄身份驗證對 Microsoft Entra ID 的安全。

練習1: 將 Microsoft Store 應用添加到 Microsoft Intune

**場景**

使用 Microsoft Intune 管理 Contoso Corporation
的桌面和應用程序。研究部門經常連接到各種服務器來執行任務，並要求研究成員根據需要安裝
Microsoft 遠程桌面應用程序。Microsoft 遠程桌面可從 Microsoft Store
獲得，但你決定將應用添加到
Intune，以便用戶可以從公司門戶網站訪問它。名為 Aaron Nicholls 的
Research 成員已同意在您將應用程序發佈到門戶後測試安裝過程。

任務 1：將 Microsoft 遠程桌面添加到 Microsoft Intune

1.  在 [***SEA-SVR1***](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17)
    上，如有必要，使用密碼以 [**Contoso\Administrator**](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17) 身份登錄 !\![**Pa55w.rd**](urn:gd:lg:a:select-vm)!!
     並關閉 **Server Manager**。

2.  在任務欄上，選擇 **Microsoft Edge**。

3.  在 Microsoft Edge 中，鍵入!!
    [**https://Intune.microsoft.com**](urn:gd:lg:a:select-vm) !!
    ，然後按 **Enter**。

4.  使用 Home （主頁） 選項卡中的 Office 365 Tenant 憑據登錄。

5.  在 **Microsoft Intune 管理中心**頁面上，選擇 “**Apps**” 。

> ![A screenshot of a computer Description automatically
> generated](./media/image1.png)

6.  在 **Apps** （應用程序） 頁面的導航窗格中，選擇 **All apps**
    （所有應用程序）。

7.  在詳細信息窗格中，選擇 **+Add**。

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)

8.  在 **Select app type** 頁面上，單擊下拉菜單，然後選擇 **Microsoft
    store app （new）。**

> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)
>
> 閱讀有關 Microsoft Store 應用程序的信息，然後單擊
> **Select**。此時將打開 **Add App** （添加應用程序） 頁面。

9.  在 **App information** （應用程序信息） 頁面上，單擊 **Search the
    Microsoft Store app （new）** （搜索 Microsoft Store
    應用程序（新）） 鏈接。

> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

10. 在 **Search the Microsoft Store app （new）** 選項卡上，搜索並選擇
    !\![**Microsoft Remote
    Desktop**](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17)!!
    然後點擊 Select 按鈕。

> ![A screenshot of a computer Description automatically
> generated](./media/image5.png)

11. 返回 Add App 選項卡，輸入以下信息，然後選擇 **Next**：

    - 類別： **Business**

    - 在公司門戶中將此應用顯示為特色應用： **Yes**

> ![A screenshot of a computer Description automatically
> generated](./media/image6.png)

12. 在 **Assignments** （分配） 選項卡上，單擊 **+ Add group**
    （添加組）

> ![A screenshot of a computer Description automatically
> generated](./media/image7.png)

13. 在 **Select groups** （選擇組） 頁面上，選擇 **Research,
    Sales** 組，然後單擊 **Select** （選擇）。

> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)

14. 點擊 **Next** 按鈕。

> ![A screenshot of a computer Description automatically
> generated](./media/image9.png)

15. 在 Review + create 選項卡上，單擊 **Create** 按鈕。

> ![](./media/image10.png)

16. 此時將打開 Microsoft 遠程桌面頁面。

> 記下 Properties （屬性）、Device install status （設備安裝狀態） 和
> User install status （用戶安裝狀態） 節點。
>
> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)

任務 2：從 Microsoft Intune 控制台強制同步策略

1.  在 **Microsoft Intune 管理中心**，選擇 “**Devices**” ，然後選擇
    “**All devices**” 。

2.  在詳細信息窗格中，選擇 **SEA-WS1**。

> ![A screenshot of a computer Description automatically
> generated](./media/image12.png)

3.  在 **SEA-WS1**
    邊欄選項卡上，選擇“**Sync**”，並在出現提示時選擇“**Yes**”。

> ![A screenshot of a computer Description automatically
> generated](./media/image13.png)
>
> Microsoft Intune 將聯繫設備並同步所有策略。這可能需要長達 5
> 分鐘的時間。

任務 3：從公司門戶網站安裝應用

1.  使用她的憑據以 **Cindy White** 的身份登錄  
    !!**Cindy@M365xXXXXXX.onmicrosoft.com**!! 使用密碼
    !!**P@55w.rd1234**!! 或使用 PIN 碼 !!**102938**!!

2.  在任務欄上，選擇 **Microsoft Edge**。

3.  如有必要，在 **Welcome to Microsoft Edge** 頁面上，選擇 **Confirm
    and continue**。關閉 Welcome （歡迎） 頁面。

4.  在地址欄中瀏覽到 !\![**https://portal.manage.microsoft.com**](urn:gd:lg:a:send-vm-keys)!!

5.  登錄身份 !!**Cindy@M365xXXXXXX.onmicrosoft.com**!!

> ![](./media/image14.png)

6.  在 Contoso Web 門戶上，選擇 “**Devices**” 。

> ![A screenshot of a computer Description automatically
> generated](./media/image15.png)

7.  在 Devices （設備） 頁面上，選擇 **Tap here to tell us which device
    you're using or add a new device**。

> ![](./media/image16.png)

8.  在 “**Which device are you using**” 對話框中，選擇旁邊的選項
    **SEA-WS1**，然後單擊 “**Select**” 按鈕。

> ![A screenshot of a computer Description automatically
> generated](./media/image17.png)
>
> 請注意，消息現在更改為 Apps will be installed onto：**SEA-WS1**
>
> ![](./media/image18.png)

9.  在左上角，選擇導航按鈕，然後選擇**Downloads & updates**。

> ![A screenshot of a computer Description automatically
> generated](./media/image19.png)

10. 從列出的結果中，檢查狀態，**Microsoft Remote Desktop**
    應用程序應顯示為 已 **Installed**。

> 注意 - 應用程序可能需要 10 到 20 分鐘才能顯示。
>
> ![A screenshot of a computer Description automatically
> generated](./media/image20.png)

11. 單擊 **Start Menu** 並驗證 “**Remote Desktop**” 是否顯示在 “開始”
    菜單上。

> ![A screenshot of a computer Description automatically
> generated](./media/image21.png)

**結果：**完成本練習後，您將成功從 Microsoft Intune 添加和安裝 Microsoft
Store 應用程序。

練習 2：從 Microsoft Intune 配置和部署 Microsoft 365 應用

**場景**

Contoso 研究部門的所有用戶都需要 Microsoft 365 應用版。系統要求您將 64
位版本的 Microsoft Excel、Outlook、PowerPoint 和 Word 部署到其 Windows
設備。您還需要確保為 Current Channel （當前頻道） 配置它們以進行更新。

任務 1：驗證 SEA-WS1 上已安裝的應用程序

1.  在 [***SEA-WS1***](urn:gd:lg:a:send-vm-keys) 的任務欄上，選擇
    “**Start**”，然後選擇“**Settings**”應用程序。

> ![A screenshot of a computer Description automatically
> generated](./media/image22.png)

2.  在 **Settings** 應用程序中，選擇 **Apps**，然後選擇 **Apps &
    features**。

> ![A screenshot of a computer Description automatically
> generated](./media/image23.png)
>
> 驗證 **Microsoft 365 Apps for enterprise - en-us** 未列出。
>
> ![A screenshot of a computer Description automatically
> generated](./media/image24.png)

3.  關閉所有打開的窗口。

任務 2：將 Microsoft 365 應用添加到 Microsoft Intune

1.  切換到 [***SEA-SVR1***](urn:gd:lg:a:send-vm-keys)， 然後在
    **Microsoft Intune 管理中心**中選擇“**Apps**”。

2.  在 “**Apps | Overview**” 邊欄選項卡中，選擇 “**All Apps**”
    。在詳細信息窗格中，選擇 **+Add**。

> ![A screenshot of a computer Description automatically
> generated](./media/image25.png)

3.  在 “**Select app type**” 邊欄選項卡中的 “**Microsoft 365 應用版**”
    下，選擇 “**Windows 10 and later** ”，然後單擊 “**Select**” 。

> ![A screenshot of a computer Description automatically
> generated](./media/image26.png)

4.  在 “**Add Microsoft 365 Apps**” 邊欄選項卡上，配置以下選項，然後選擇
    “**Next**” ：

    - 套房名稱： !\![**Microsoft 365 Apps
      (Research)**](urn:gd:lg:a:select-vm)!!

    - 套房描述： !\![**Microsoft 365 Apps for the Research department at
      Contoso**](urn:gd:lg:a:select-vm) !! (選擇 **Edit Description**
      （編輯描述） 以輸入此信息。)

> ![A screenshot of a computer Description automatically
> generated](./media/image27.png)

5.  在 **Configure app suite** 選項卡上，展開 **Select Office apps**
    下拉列表，選擇以下 Office 應用：

    - Excel

    - Outlook

    - PowerPoint

    - Word

> ![A screenshot of a computer Description automatically
> generated](./media/image28.png)

6.  在 **Configure app suite** （配置應用程序套件）
    選項卡上，配置以下選項，然後選擇 **Next** （下一步）：

    - 體系結構： **64-bit**

    - 默認文件格式： **Office Open XML Format**

    - Update channel： **Current Channel**

    - 代表用戶接受 Microsoft 軟件許可條款： **Yes**

> ![A screenshot of a computer Description automatically
> generated](./media/image29.png)

7.  在 **Assignments** 選項卡上的 **Required** 部分中，選擇 **Add
    group**。

> ![A screenshot of a computer Description automatically
> generated](./media/image30.png)

8.  在 **Select groups** （選擇組） 邊欄選項卡上，選擇 **Research**
    （研究），然後選擇 **Select** （選擇）。

> ![A screenshot of a group Description automatically
> generated](./media/image31.png)

9.  選擇 **Next**。

> ![A screenshot of a computer Description automatically
> generated](./media/image32.png)

10. 在 **Review + Create** （查看 + 創建） 選項卡上，選擇 **Create**
    （創建）。

> ![A screenshot of a computer Description automatically
> generated](./media/image33.png)

11. 在 **Microsoft 365 應用版 （研究）** 頁上，選擇 “**Properties**” 。

> ![A screenshot of a computer Description automatically
> generated](./media/image34.png)

12. 在詳細信息窗格中，驗證 **Research** 是否列在 **Assignments** 部分的
    **Required** 下。

> ![A screenshot of a computer Description automatically
> generated](./media/image35.png)

任務 3：從 Microsoft Intune 控制台強制同步策略

1.  在 **Microsoft Intune 管理中心**，選擇 “**Devices**” ，然後選擇
    “**All devices**” 。

2.  在詳細信息窗格中，選擇 **SEA-WS1**。

> ![A screenshot of a computer Description automatically
> generated](./media/image36.png)

3.  在 **SEA-WS1**
    邊欄選項卡上，選擇“**Sync**”，並在出現提示時選擇“**Yes**”。

> ![A screenshot of a computer Description automatically
> generated](./media/image37.png)
>
> Microsoft Intune 將聯繫設備並同步所有策略。這可能需要長達 5
> 分鐘的時間。

任務 4：驗證是否已安裝 Microsoft 365 應用

1.  如果您已以 **Cindy White**
    身份登錄 [*SEA-WS1*](urn:gd:lg:a:send-vm-keys?rc=10)。

> **注意 –** 您可能需要等待大約 10-15 分鐘才能在設備上安裝 Microsoft 365
> 套件。

2.  使用她的憑據以 **Cindy White** 的身份注銷並重新登錄  
    !!**Cindy@M365xXXXXXX.onmicrosoft.com**!! 使用密碼
    !!**P@55w.rd1234**!!

3.  在 [***SEA-WS1***](urn:gd:lg:a:send-vm-keys)
    的任務欄上，選擇“**Start**”，然後選擇“**Settings**”應用程序。

> ![A screenshot of a computer Description automatically
> generated](./media/image38.png)

4.  在 **Settings** 應用程序中，選擇 **Apps** ，然後在 **Apps &
    features** 頁面上。

> ![A screenshot of a computer Description automatically
> generated](./media/image23.png)

5.  尋找 !!**Microsoft 365**!! 並驗證是否列出了 **Microsoft 365 Apps for
    enterprise - en-us**。

> ![A screenshot of a computer Description automatically
> generated](./media/image39.png)

6.  關閉 **Settings** 應用程序，然後選擇 **Start** 開始 按鈕。

7.  在 “**Recommended**” 部分中，您應該能夠看到從 Microsoft Intune 中的
    Microsoft 365 Apps 中選擇的新安裝的應用程序。

> ![A screenshot of a computer Description automatically
> generated](./media/image40.png)

任務 5：在 Microsoft Intune 中監視應用安裝狀態

1.  切換到 [***SEA-SVR1***](urn:gd:lg:a:select-vm)， 然後在 **Microsoft
    Intune 管理中心**中選擇“**Apps**”。

> ![](./media/image41.png)

2.  在 **Apps | Overview** 邊欄選項卡中，選擇 “**Monitor**”，然後選擇
    “**App install status**” 。

> ![A screenshot of a computer Description automatically
> generated](./media/image42.png)

3.  在詳細信息窗格中，選擇 **Microsoft 365 Apps (Research)**。

> ![A screenshot of a computer Description automatically
> generated](./media/image43.png)

4.  在詳細信息窗格中的 **Device status** （設備狀態） 和 **User status**
    （用戶狀態） 下，驗證 **1** 是否顯示在 Installed （已安裝） 下。

> ![A screenshot of a computer Description automatically
> generated](./media/image44.png)
>
> **注意：**這表示該應用程序安裝在一台設備上，並且為一位用戶安裝。請注意，信息可能需要一些時間才能顯示，並且可能會顯示為
> **Install Pending** （待安裝）。
>
> **注意 –** 您可以開始**實驗室13**，然後在 **30-45** 分鐘後回來查看。

![A screenshot of a computer Description automatically
generated](./media/image45.png)

5.  選擇 **Device install status**（設備安裝狀態）。

> 在詳細信息窗格中，您可以看到安裝了應用程序的設備，以及用戶的名稱。**Device
> Name** 列應列出 **SEA-WS1**，**Status** 列應顯示已
> **Installed**。這意味著該應用程序安裝在 **SEA-WS1** 上。
>
> ![A screenshot of a computer Description automatically
> generated](./media/image46.png)

6.  在 **Microsoft Intune 管理中心**，選擇 “**Devices**” 。

7.  在 **Devices | Overview** 邊欄選項卡，選擇 “**All devices**”
    ，然後在詳細信息窗格中選擇 “**SEA-WS1**” 。

> ![A screenshot of a computer Description automatically
> generated](./media/image47.png)

8.  在 **SEA-WS1** 邊欄選項卡上，選擇 “**Managed Apps**” 。

9.  在 **SEA-WS1 | Managed Apps** 邊欄選項卡的 “詳細信息窗格” 中，選擇
    “**Microsoft 365 Apps (Research)**” 。

> ![A screenshot of a computer Description automatically
> generated](./media/image48.png)
>
> 在 **Microsoft 365 Apps (Research) - Installation details**
> 窗口中，你可以查看應用程序的整個生命週期，即 -
> 創建、分配、安裝時間和狀態以及設備上次簽入（與 Microsoft Intune
> 同步）的時間。.
>
> ![A screenshot of a computer Description automatically
> generated](./media/image49.png)

10. 關閉所有打開的窗口。

**結果：**完成本練習後，您將成功從 Microsoft Intune 配置和部署 Microsoft
365 應用版。
