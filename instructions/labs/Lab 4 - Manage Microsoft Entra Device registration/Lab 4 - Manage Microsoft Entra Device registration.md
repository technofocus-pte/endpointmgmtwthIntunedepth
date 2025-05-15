# 實驗 4 - 管理 Microsoft Entra 設備註冊。

**總結**

在本實驗中，我們將使用 Windows 設備執行 Microsoft Entra 註冊。

**練習 1：配置 Microsoft Entra 設備註冊**

**場景**

一些用戶要求使用其個人 iOS、Android 和 Windows 設備訪問 Contoso
雲資源。由於 Contoso 不擁有設備，因此您不希望讓用戶執行 Entra
加入以進行完整的設備管理。相反，你需要確保用戶能夠向 Microsoft Entra
註冊其設備，它仍然允許你根據需要將公司策略應用於應用程序，並且仍然允許用戶訪問
Contoso 資源。您將使用 Windows 11 設備測試 Microsoft Entra 設備註冊。

**任務 1：配置 Azure AD 設備註冊**

1.  在
    [*SEA-SVR1*](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)上，在
    Edge 瀏覽器中打開一個新選項卡並輸入以下 URL，
    !!**https://entra.microsoft.com**!!，然後按 **Enter** 按鈕。

2.  使用您的 O365 租戶 ID 登錄
    !!**admin@M365xXXXXXXXX.onmicrosoft.com**!! 並使用租戶管理員密碼。

> ![A screenshot of a computer Description automatically
> generated](./media/image1.png)
>
> ![A screenshot of a login box Description automatically
> generated](./media/image2.png)

3.  在 **Stay signed in?** 對話框中，選擇 **Yes** 按鈕。

> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)

4.  在 **Microsoft Entra 管理中心**窗口中，導航並單擊“**Identity**”。

![A screenshot of a computer Description automatically
generated](./media/image4.png)

5.  選擇“**Devices**”，然後選擇“**Device
    settings**”頁，在詳細信息窗格中，驗證“**Users may register their
    devices with Microsoft Entra**”是否設置為“**All** ”並灰顯。

> 在租戶中啟用 Microsoft Intune
> 時，此選項灰顯並默認設置為“**All**”。這可確保所有用戶都能夠向 Azure AD
> 註冊 Windows 10 或更高版本的個人、iOS、Android 和 macOS 設備。
>
> ![](./media/image5.png)

**任務 2：執行 Microsoft Entra 註冊**

1.  切換到[*SEA-WS1*](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10) 並以
    Admin 身份登錄，密碼為 !!**Pa55w.rd**!!。

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image6.png)

2.  在任務欄上，選擇“**Start**”，然後選擇“**Settings**”。

![A screenshot of a computer Description automatically
generated](./media/image7.png)

3.  在 **Settings** （設置） 窗口中，選擇 **Accounts** （帳戶）。

![A screenshot of a computer Description automatically
generated](./media/image8.png)

4.  在 “**Accounts**”頁上，選擇 “**Access work or school**”。

![A screenshot of a computer Description automatically
generated](./media/image9.png)

5.  在 “**Access work or school**” 頁面中，選擇 “**Connect**”。

![A screenshot of a computer Description automatically
generated](./media/image10.png)

6.  在 **Sign in** （登錄）
    頁面上，鍵入 !!**JoniS@M365xXXXXXXX.onmicrosoft.com**!!，然後選擇
    **Next**。

![](./media/image11.png)

7.  在 **Enter password** （輸入密碼） 頁面上，輸入租戶密碼：
    !\![**P@55w.rd1234**](mailto:P@55w.rd1234)!! ，然後選擇 **Sign in**

![A screenshot of a computer Description automatically
generated](./media/image12.png)

8.  在 **You're all set！**頁面上，選擇 “**Done**”。

![A screenshot of a computer Description automatically
generated](./media/image13.png)

9.  在 **Access work or school** （訪問工作或學校） 頁面上，驗證是否顯示
    Joni 的 **Work or school account**。

![A screenshot of a computer Description automatically
generated](./media/image14.png)

10. 關閉 **Settings** （設置） 頁面。

**任務 3：驗證 Microsoft Entra 註冊**

1.  在 [*SEA-WS1*](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)，上，右鍵單擊
    **Start button**，然後選擇 **Windows Terminal (Admin)**。

> ![A screenshot of a computer Description automatically
> generated](./media/image15.png)

2.  在 **User Account Control** （用戶帳戶控制） 對話框中，選擇 **Yes**
    （是）。

> ![A screenshot of a computer error Description automatically
> generated](./media/image16.png)

3.  在 PowerShell 控制台中，鍵入以下內容，然後按 **Enter**：

> !!**dsregcmd /status**!!

4.  在 **User State** （用戶狀態） 下的輸出中，驗證是否顯示
    **WorkplaceJoined ： YES** 。這表示用戶已在 Microsoft Entra
    中執行了設備註冊。

> ![A screenshot of a computer Description automatically
> generated](./media/image17.png)

5.  關閉 PowerShell，然後注銷 **SEA-WS1**。

6.  切換到 SEA-SVR1。轉到 **Microsoft Entra
    管理中心**窗口，導航並單擊“**Identity**”。

> ![A screenshot of a computer Description automatically
> generated](./media/image18.png)
>
> 7\. 在“**Identity**”部分下，選擇“**Devices**”，然後導航並單擊“**All
> devices**”，如下圖所示。
>
> ![A screenshot of a computer Description automatically
> generated](./media/image19.png)

8.  驗證 **Join Type** 是否列為 **Microsoft Entra registered**
    以及所有者是否為 **Joni Sherman**。

> ![](./media/image20.png)
>
> 請注意，設備已註冊 Microsoft Entra，而不是已加入 Microsoft Entra。註冊
> Entra 的設備通常是無法加入 Entra
> 的設備，或者是用戶個人擁有的設備。註冊設備將提供對基於雲的資源的訪問權限。

9.  關閉Microsoft Edge。

**任務 4：登錄到 Windows 並斷開與組織的連接**

1.  切換到 [*SEA-WS1*](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)。在任務欄上，選擇
    **Windows Start icon** 按鈕，然後選擇**Settings**。

![A screenshot of a computer Description automatically
generated](./media/image7.png)

2.  在 **Settings** （設置） 窗口中，選擇 **Accounts** （帳戶）。

> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)

3.  在 “**Accounts**”頁上，選擇 “**Access work or school**”。

> ![A screenshot of a computer Description automatically
> generated](./media/image9.png)

4.  在 “**Access work or school**”頁面中，單擊 **JJoniS@M3654xXXXXXXXX
    Work or school** 帳戶 “旁邊的下拉列表，如下圖所示。

> ![](./media/image21.png)

5.  單擊 **Disconnect** 按鈕。

> ![A screenshot of a computer Description automatically
> generated](./media/image22.png)

6.  點擊 **Yes** 按鈕確認刪除帳戶。

> ![A screenshot of a computer Description automatically
> generated](./media/image23.png)
>
> 請注意，無需重啟即可斷開已註冊 Microsoft Entra 的設備。

7.  注銷 **SEA-WS1**。

![A screenshot of a computer Description automatically
generated](./media/image24.png)

**結果：**完成本練習後，您將配置 Microsoft Entra 設備註冊。
