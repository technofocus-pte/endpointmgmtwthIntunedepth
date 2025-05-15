Lab13：為移動設備配置應用程序保護策略

**總結**

在本實驗中，您將為移動設備配置應用程序保護策略。

**場景**

Contoso 的所有開發人員都擁有運行最新 iOS/iPadOS 版本的 iPhone 和
iPad。安全部門擔心數據洩露，並希望防止將公司電子郵件中的數據複製到移動設備上的其他應用程序。您必須提供解決安全部門問題的解決方案。您需要確保以下幾點：

- 必須限制 Outlook 數據備份到 iTunes 或 iCloud。

- 只有策略託管的應用程序才能從 Outlook 發送和接收數據。

- 只有策略託管的應用程序才能使用 Outlook 進行剪切、複製或粘貼。

- 用戶必須提供其工作或學校帳戶憑據才能訪問 Outlook。

任務 1：為 iOS/iPadOS 設備創建應用保護策略

1.  在 [***SEA-SVR1***](urn:gd:lg:a:select-vm)上，
    如有必要，使用密碼以 [**Contoso\Administrator**](urn:gd:lg:a:send-vm-keys) 身份登錄 !\![**Pa55w.rd**](urn:gd:lg:a:send-vm-keys)!!

2.  在任務欄上，選擇 **Microsoft Edge** 並導航到 **Microsoft Intune
    管理中心** !!**https://intune.microsoft.com**!!  ，然後按
    **Enter**。

3.  使用 Office 365 租戶管理員憑據從“主頁”選項卡登錄。

4.  在 **Microsoft Intune 管理中心**頁面上，選擇 “**Apps**” 。

> ![A screenshot of a computer Description automatically
> generated](./media/image1.png)

5.  在 **Apps | Overview** 邊欄選項卡的 “**Policy**” 下，選擇 “**App
    protection policies**” 。

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)

6.  在詳細信息窗格中，選擇 “**+ Create policy** “，然後選擇
    “**iOS/iPadOS**” 。

> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)

7.  在 **Basics** 選項卡上，配置以下選項，然後選擇 **Next**：

    - 名字： !\![**Outlook – Developers**](urn:gd:lg:a:send-vm-keys)!!

    - 描述： !\![**Policy to prevent cut/copy and paste from
      Outlook**](urn:gd:lg:a:send-vm-keys)!!

> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

8.  在 **Apps** （應用程序） 選項卡上，單擊 **+ Select public apps**
    （選擇公共應用程序）。

9.  在 **Select apps to target** 邊欄選項卡的文本框中，鍵入
    !!**Outlook**!! 選擇 **Microsoft Outlook**，然後單擊 “**Select**”
    按鈕，然後選擇 “**Next**” 。

> ![Screens screenshot of a computer Description automatically
> generated](./media/image5.png)

10. 在 **Data protection** （數據保護） 選項卡上，配置以下選項，然後選擇
    **Next** （下一步）：

    - 將組織數據備份到 iTunes 和 iCloud 備份： **Block**

    - 將組織數據發送到其他應用： **Policy managed apps**

    - 從其他應用接收數據： **Policy managed apps**

    - 限制其他應用之間的剪切、複製和粘貼： **Policy managed apps**

> 將所有其他設置保留為默認值
>
> ![](./media/image6.png)

11. 在 **Access requirements** （訪問要求）
    選項卡上，配置以下選項，然後選擇 **Next**：

    - 訪問 PIN： **Not required**

    - 用於訪問的工作或學校帳戶憑據： **Require**

> ![A screenshot of a computer Description automatically
> generated](./media/image7.png)

12. 在 **Conditional launch** （條件啟動） 選項卡上，查看設置。選擇
    **Next**（下一步）。

> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)
>
> **注意：**您可以在此處設置訪問保護策略的登錄安全要求。您可以選擇一個設置，並輸入用戶登錄公司應用程序必須滿足的值。記下各種設置，但不要更改任何內容。

13. 在 **Assignments** （分配） 選項卡上，選擇 **Next** （下一步）。

> ![A screenshot of a computer Description automatically
> generated](./media/image9.png)

14. 在 “**Review + create**” 選項卡上，查看設置，然後選擇 “**Create**”。

> ![A screenshot of a computer Description automatically
> generated](./media/image10.png)

15. 在 “**Apps | App protection policies**”
    邊欄選項卡上的詳細信息窗格中，驗證是否列出了 “**Outlook -
    Developers**” 。

> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)

16. 關閉Microsoft Edge。

**結果：**完成本練習後，您將成功為移動設備配置應用程序保護策略。
