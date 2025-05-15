# 實驗 25：使用 Endpoint Analytics 監控設備性能和用戶體驗

**總結**

在此實驗室中，您將啟用 Endpoint analytics
來監控設備性能以及用戶體驗分數和見解。

**先決條件**

在此實驗之前，必須完成以下實驗：

- 實驗 05 - 管理設備註冊到 Intune

- 實驗 06 - 將設備註冊到 Intune

- 實驗 07 - 創建和部署配置文件

**場景**

系統要求您監控啟動性能、應用程序可靠性和用戶體驗，以及用戶重啟設備的頻率。要獲取此信息，您需要啟用
Endpoint analytics。

### 任務 1：啟用 Endpoint 分析

1.  在 [**SEA-SVR1**](urn:gd:lg:a:select-vm)上，如有必要，使用密碼以 [**Contoso\Administrator**](urn:gd:lg:a:send-vm-keys) 身份登錄 !\![**Pa55w.rd**](urn:gd:lg:a:send-vm-keys)!! 並關閉
    **Server Manager**。

2.  在任務欄上，選擇 **Microsoft Edge**。

3.  在 Microsoft Edge 中，鍵入
    !\![**https://intune.microsoft.com**](https://intune.microsoft.com)!!，然後按
    **Enter**。

4.  使用密碼以 [**admin@M365x19242953.onmicrosoft.com**](urn:gd:lg:a:send-vm-keys) 身份登錄。

5.  在 **Microsoft Intune 管理中心**頁面上，選擇 “**Reports**” 。

6.  在 “**Reports**” 邊欄選項卡上的 “**Analytics**” 下，選擇 “**Endpoint
    analytics**”。

> ![](./media/image1.png)

7.  在 **Endpoint analytics** （終端節點分析） 頁面上，確保 **Collect
    device data from** （收集設備數據來源） 設置為 **All cloud-managed
    devices**（所有雲託管設備），然後選擇 **Start**（啟動）。

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)
>
> 記下 Overview （概述） 頁面頂部的消息。分數和見解最多可能需要 24
> 小時才能顯示在頁面上。
>
> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)

8.  切換到 [**SEA-WS1**](urn:gd:lg:a:select-vm) 並重新啟動設備。

9.  以 **Cindy White** 身份登錄，密碼為
    ： [**102938**](urn:gd:lg:a:send-vm-keys)。

10. 切換到[**SEA-SVR1**](urn:gd:lg:a:select-vm)。

11. 在 **Microsoft Intune 管理中心**頁面上，選擇 “**Devices**”
    ，然後選擇 “**All devices**” 。

12. 選擇 **SEA-WS1**。

> ![](./media/image4.png)

13. 在 **SEA-WS1** 頁面上，選擇 **Sync** 同步，然後選擇 **Yes**。

> ![A screenshot of a computer Description automatically
> generated](./media/image5.png)

14. 在 **SEA-WS1** 頁面的 “**Monitor**” 下，選擇 “**User experience**”
    。 ![A screenshot of a computer Description automatically
    generated](./media/image6.png)

15. 查看 **Endpoint analytics** （終端節點分析）、**Startup
    performance** （啟動性能） 和 **Application reliability**
    （應用程序可靠性） 選項卡。

> ![A screenshot of a computer Description automatically
> generated](./media/image7.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image9.png)
>
> 由於時間延遲，可能不會報告任何信息，但請閱讀每個選項卡上可見內容的詳細信息。

16. 在 **Microsoft Intune 管理中心**頁面上，選擇 “**Reports**” 。

17. 在 “**Reports**” 邊欄選項卡上的 “**Analytics**” 下，選擇 “**Endpoint
    analytics**” 。

> ![](./media/image10.png)
>
> 請注意，Endpoint Analytics
> 中提供了相同類型的信息，但此信息基於所有已註冊的設備。
>
> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)

18. 瀏覽 Endpoint analytics （終端節點分析） 頁面中提供的 Reports
    （報告）。

19. 關閉 Microsoft Edge。

**結果：**完成本練習後，您將成功啟用 Endpoint Analytics
來監控設備性能以及用戶體驗分數和見解。
