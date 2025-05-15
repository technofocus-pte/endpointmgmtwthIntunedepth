**實驗 8 - 使用配置配置文件配置 Kiosk 模式**

**總結**

在本實驗中，我們將使用 Microsoft Intune 創建並應用配置文件，以在 Windows
11 設備上運行單應用展臺模式。

**先決條件**

在此實驗之前，必須完成以下實驗：

- 實驗 05 - 管理設備註冊到 Microsoft Intune

注意：您還需要一部可以接收短信的移動電話，該短信用於保護 Windows Hello
登錄對 Entra ID 的身份驗證。

**練習 1：創建並應用配置文件**

**場景**

系統要求您將 **SEA-WS2** 配置為 Windows 11 展臺，以允許 Contoso
訪問者瀏覽 Internet。您需要確保 Kiosk 的配置如下：

- 單個應用程序、全屏展臺。

- 自動登錄。

- 提供對 Microsoft Edge 瀏覽器的訪問，該瀏覽器將在公共瀏覽 （InPrivate）
  模式下進行配置。應為 **http://bing.com** 配置主頁。

**任務 1：將 SEA-WS2 註冊到 Microsoft Intune**

1.  以 **Admin**
    身份登錄 [*SEA-WS2*](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)，密碼為!!**Pa55w.rd**!!。

2.  在任務欄上，選擇“**Start**”，然後選擇“**Settings**”。

![](./media/image1.png)

3.  在 **Settings** （設置） 窗口中，選擇 **Accounts** （帳戶）。

![A screenshot of a computer Description automatically
generated](./media/image2.png)

4.  在 “帳戶 ”頁上，選擇 “**Access work or school**”。

![A screenshot of a computer Description automatically
generated](./media/image3.png)

5.  在 “**Access work or school** ” 頁面中，選擇 “**Connect**”。

![A screenshot of a computer Description automatically
generated](./media/image4.png)

6.  在 **Microsoft 帳戶**窗口中，選擇**Join this device to Microsoft
    Entra ID**。

![A screenshot of a computer screen Description automatically
generated](./media/image5.png)

7.  在 **Sign in** （登錄）
    頁面上，鍵入 !!**AllanD@M365xXXXXXX.onmicrosoft.com**!! ，然後選擇
    **Next**。

![](./media/image6.png)

8.  在 **Enter password** （輸入密碼） 頁面上，輸入租戶密碼：
    !!**P@55w.rd1234**!! ，然後選擇 **Sign in （**登錄）。

![A screenshot of a computer Description automatically
generated](./media/image7.png)

9.  在 **Make sure this is your organization** （確保這是您的組織）
    對話框中，選擇 **Join** （加入）。

![A screenshot of a computer error Description automatically
generated](./media/image8.png)

10. 在 **You're all set！**頁面上，閱讀信息，然後選擇 **Done**。

![A screenshot of a computer screen Description automatically
generated](./media/image9.png)

11. 在 “**Access work or school**”部分中，驗證是否顯示 “**Connected to
    Contoso's Azure AD**”。

![A screenshot of a computer Description automatically
generated](./media/image10.png)

12. 選擇“**Connected to Contoso's Azure AD**”，然後選擇 “**Info**”。

![A screenshot of a computer Description automatically
generated](./media/image11.png)

13. 向下滾動，然後選擇 **Sync** （同步）。這將強制設備與 Intune 同步。

![A screenshot of a computer Description automatically
generated](./media/image12.png)

14. 關閉 **Settings** （設置） 窗口。

**任務 2：創建 Contoso 展臺設備組**

1.  在 [*SEA-SVR1*](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)
    上， 切換到 **Microsoft Entra 管理中心**選項卡。導航並選擇
    **Groups**，然後單擊 **All groups**。

![](./media/image13.png)

2.  在 “**Groups | All groups**” 頁上，選擇 “**New group**”。

![A screenshot of a computer Description automatically
generated](./media/image14.png)

3.  在 **New Group** （新建組） 邊欄選項卡上，輸入以下信息：

- 組類型： **Security**

- 組名： !! Contoso Kiosk Devices!!

- 組介紹： !!All Windows devices configured as a Kiosk!!

- 成員身份類型： **Assigned**

4.  在 **Members** （成員） 下，選擇 **No members selected**
    （未選擇成員）。

![](./media/image15.png)

5.  在“**Add members**”邊欄選項卡上的“**Search**”框中，鍵入 **Sea**.
    選擇 **SEA-WS2**，然後選擇 **Select**。

![](./media/image16.png)

6.  在 **New Group** 邊欄選項卡上，選擇 **Create**。

![A screenshot of a computer Description automatically
generated](./media/image17.png)

7.  在 “**Groups | All groups**” 邊欄選項卡刷新頁面，並驗證是否顯示
    “**Contoso Kiosk Devices**” 組。

![](./media/image18.png)

**任務 3：根據方案要求創建配置文件**

1.  返回到 Microsoft Intune 管理中心，從導航欄中選擇“**Devices** ”。

![A screenshot of a computer Description automatically
generated](./media/image19.png)

2.  在 **Devices | Overview** 頁中，選擇 “**Windows**”，如下圖所示。

![A screenshot of a computer Description automatically
generated](./media/image20.png)

3.  在 **Windows | Windows devices** 頁面上，導航並單擊 **Configuration
    profiles**。

![A screenshot of a computer Description automatically
generated](./media/image21.png)

4.  在 **Windows | Configuration profiles** 頁面的 **Policies**
    選項卡中，單擊 **+ Create** 並選擇 **+ New Policy**。

![A screenshot of a computer Description automatically
generated](./media/image22.png)

5.  在 **Create a profile** （創建配置文件）
    邊欄選項卡中，選擇以下選項，然後選擇 **Create** （創建）：

- 平臺： **Windows 10 and later**

- 配置文件類型： **Templates**

- 模板名稱： !!**Kiosk**!!

![A screenshot of a computer Description automatically
generated](./media/image23.png)

6.  在“**Basics**”邊欄選項卡中，輸入以下信息，然後選擇“**Next**”：

- 名字： !!Contoso Kiosk Policy!!

- 描述： !!Basic settings for Contoso Kiosk Devices.!!

![A screenshot of a computer Description automatically
generated](./media/image24.png)

7.  在“**Configuration settings**”邊欄選項卡上，在“**Select a kiosk
    mode**”旁邊，選擇“**Single app, full-screen kiosk**”。

其他選項根據所選模式顯示。

8.  在“**Configuration
    settings**”邊欄選項卡上，選擇以下選項，然後選擇“**Next**”：

- 用戶登錄類型： **Auto logon (Windows 10, version 1803 and later, or
  Windows 11)**

- 應用程序類型： **Add Microsoft Edge browser**

- Edge Kiosk 網址： !! **http://bing.com**!!

- Microsoft Edge 展臺模式類型： **Public Browsing (InPrivate)**

- 空閑時間後刷新瀏覽器： **5**

- 指定 App Restarts 的維護時段： **Not configured**

> ![A screenshot of a computer Description automatically
> generated](./media/image25.png)

9.  在 **Assignments** 邊欄選項卡上的 **Included groups** 下，選擇 **Add
    groups**。

![A screenshot of a computer Description automatically
generated](./media/image26.png)

10. 在 **Select groups to include** （選擇要包含的組）
    窗口中，選擇 !!**Contoso Kiosk Devices**!!，然後單擊 **Select**。

![A screenshot of a computer Description automatically
generated](./media/image27.png)

11. 在 **Assignment** 選項卡中，單擊 **Next** 按鈕。

![A screenshot of a computer Description automatically
generated](./media/image28.png)

12. 在 **Applicability Rules** 選項卡中，單擊 **Next** 按鈕。

![A screenshot of a computer Description automatically
generated](./media/image29.png)

13. 在 **Review + create** 選項卡中，單擊 **Create** 按鈕。

![A screenshot of a computer Description automatically
generated](./media/image30.png)

14. 將列出 Configuration profile （配置文件）。

![A screenshot of a computer Description automatically
generated](./media/image31.png)

**任務 4：驗證是否已應用配置文件**

1.  以 **Admin**
    身份登錄 [*SEA-WS2*](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10) 密碼為!!**Pa55w.rd**!!。

2.  在任務欄上，選擇“**Start**”，然後選擇“**Settings**”。

![A screenshot of a computer Description automatically
generated](./media/image1.png)

3.  在 **Settings** （設置） 窗口中，選擇 **Accounts** （帳戶）。

![A screenshot of a computer Description automatically
generated](./media/image2.png)

4.  在 “帳戶 ”頁上，選擇 “**Access work or school**”。

![A screenshot of a computer Description automatically
generated](./media/image3.png)

5.  選擇“**Connected to Contoso's Azure AD**”，然後選擇“**Info**”。

![A screenshot of a computer Description automatically
generated](./media/image11.png)

6.  向下滾動，然後選擇 **Sync** （同步）。這將強制設備與 Intune 同步。

![A screenshot of a computer Description automatically
generated](./media/image12.png)

7.  關閉 **Settings** （設置） 窗口。

> ![](./media/image32.png)

5.  重新啟動 **SEA-WS2**。

請注意，**SEA-WS2** 會自動登錄並創建配置文件。登錄完成後，將顯示配置了
InPrivate 瀏覽的 Microsoft Edge。如果 SEA-WS2 未自動登錄，請重複步驟 1-7
以確保策略已在設備上刷新。

![](./media/image33.png)

**結果：**完成本練習後，您將成功創建並分配配置文件，以將 Windows 11
設備配置為單應用展臺。
