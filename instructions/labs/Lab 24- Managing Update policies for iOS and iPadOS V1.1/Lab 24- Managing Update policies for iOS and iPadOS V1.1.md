實踐實驗室 26：管理 iOS 和 iPadOS 的更新策略

**總結**

在本實驗中，您將配置用於管理 iOS 和 iPadOS作系統更新的更新策略。

**場景**

Contoso 的所有開發人員都擁有運行最新 iOS/iPadOS 版本的 iPhone 和
iPad。您已通過 Apple
的自動設備註冊註冊了這些設備，並且需要為設備作系統配置更新策略。您需要確保以下幾點：

- 要安裝的版本：最新更新。

- 僅允許在星期三淩晨 12 點到星期四淩晨 12 點之間進行自動更新。

任務 1：為 iOS/iPadOS 設備創建更新策略

1.  如有必要，在 [***SEA-SVR1***](urn:gd:lg:a:select-vm) 上，
    使用密碼[**Pa55w.rd**](urn:gd:lg:a:send-vm-keys)
    以[**Contoso\Administrator**](urn:gd:lg:a:send-vm-keys) 身份登錄並關閉
    **Server Manager**。

2.  在任務欄上，選擇 **Microsoft Edge**。

3.  在 Microsoft Edge
    中，在地址欄中鍵入 [**https://intune.microsoft.com**](https://intune.microsoft.com) ，然後按
    **Enter**。

4.  使用密碼以 [**admin@M365x19242953.onmicrosoft.com**](urn:gd:lg:a:send-vm-keys) 身份登錄。

5.  在 **Microsoft Intune 管理中心**頁面上，選擇 “**Devices**” 。

6.  在 **Devices|By platform** 邊欄選項卡，在 “Policy” 下，選擇
    “**iOS/iPadOS**” 。

> ![](./media/image1.png)

7.  選擇 **Update Policies for iOS/iPadOS**

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)

8.  在詳細信息窗格中，選擇 **Create profile** （創建配置文件）。

9.  在 **Basics** 選項卡上，配置以下選項，然後選擇 **Next**：

    - 名字： !\![**iOS/iPadOS update
      policy**](urn:gd:lg:a:send-vm-keys)!!

    - 描述： !\![**Policy to manage system updates for iOS and
      iPadOS**](urn:gd:lg:a:send-vm-keys)!!

> ![](./media/image3.png)

10. 在 **Update policy settings** （更新策略設置）
    選項卡上，配置以下選項，然後選擇 **Next** （下一步）：

    - 選擇要安裝的版本： **Latest update**

    - 計劃類型： **Update during scheduled time**

    - 時區： **UTC:00**

    - 時間窗口：

    - 開課日期：**Wednesday**

      - 開始時間： **12 AM**

      - 結束日期： **Thursday**

      - 結束時間： **12 AM**

> ![](./media/image4.png)

11. 在 **Assignments** （分配） 選項卡上，選擇 **Next** （下一步）。

> ![A screenshot of a computer Description automatically
> generated](./media/image5.png)

12. 在 “**Review + create**” 選項卡上，查看設置，然後選擇 “**Create**”
    。

13. 在 “**Devices | Update policies for iOS/iPadOS**”
    邊欄選項卡的詳細信息窗格中，驗證是否列出了 **iOS/iPadOS update
    policy**。

> ![A screenshot of a computer Description automatically
> generated](./media/image6.png)

14. 關閉Microsoft Edge。

**結果：**完成本練習後，您將成功配置了 iOS 和 iPadOS 的更新策略。
