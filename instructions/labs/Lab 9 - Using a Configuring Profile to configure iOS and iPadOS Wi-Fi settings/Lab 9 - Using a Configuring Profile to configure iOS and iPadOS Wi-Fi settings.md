**實驗 9 - 使用配置配置文件配置 iOS 和 iPadOS Wi-Fi 設置。**

**總結**

在本實驗中，我們將使用 Microsoft Intune 創建並應用配置文件，以運行為 iOS
和 iPadOS 設備配置 Wi-Fi 設置。

**練習 1：創建配置文件。**

**場景**

系統要求您創建一個配置描述文件，用於為已註冊的 iOS 和 iPadOS
設備自動配置 Wi-Fi 設置。您需要確保 Wi-Fi 設置配置如下：

- 網絡名稱： **Contoso Wi-Fi**

- SSID： **MainOffice**

- 自動連接： **Enable**

- 安全類型： **WPA/WPA2-Personal**

- 預共享密鑰： **ContosoWiFi123**

- 分配給： **A new security group named iOS_iPadOS Devices**

**任務 1：創建 iOS_iPadOS 設備組**

1.  切換到 [*SEA-SVR1*](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)。在
    **Microsoft Entra 管理中心**窗口中，導航並選擇 “**Groups**
    ”，然後單擊 “**All groups**”。

> ![A screenshot of a computer Description automatically
> generated](./media/image1.png)

2.  在 “**Groups | All groups**” 邊欄選項卡中，選擇“**New group**”。

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)

3.  在 “**New Group**”
    邊欄選項卡上，輸入以下信息，然後單擊“**Create**”按鈕，如下圖所示：

    - 組類型： **Security**

    - 組名： !!**iOS_iPadOS Devices**!!

    - 組介紹： !!**All iOS and iPadOS devices**!!

    - 成員身份類型： **Assigned**

> ![A screenshot of a group Description automatically
> generated](./media/image3.png)

4.  在“**Groups | All groups**”邊欄選項卡，刷新頁面並驗證是否顯示
    “**iOS_iPadOS Devices** ”組。

> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

**任務 2：根據方案要求創建配置文件**

1.  切換到 **Microsoft Intune
    管理中心**選項卡，從導航欄中選擇“**Devices**”。

> ![A screenshot of a computer Description automatically
> generated](./media/image5.png)

2.  在 **Devices | Overview** 頁中，選擇 “**iOS/iPadOS**”，如下圖所示。

> ![A screenshot of a computer Description automatically
> generated](./media/image6.png)

3.  在 **iOS/iPadOS** 頁面上，導航並單擊 **Configuration
    profiles**（配置文件）。

4.  在 **iOS/iPadOS | Configuration profiles** 頁面的 **Policies**
    選項卡中，單擊 **+ Create** 並選擇 **+ New Policy**。

> ![](./media/image7.png)

5.  在 **Create a profile** （創建配置文件）
    邊欄選項卡中，選擇以下選項，然後選擇 **Create** （創建）：

    - 平臺： **iOS/iPadOS**

    - 配置文件類型： **Templates**

    - 模板名稱： **Wi-Fi**

> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)

6.  在“**Basics**”邊欄選項卡中，輸入以下信息，然後選擇“**Next**”：

    - 名字： !!**iOS/iPadOS Wi-Fi Policy**!!

    - 描述： !!**Wi-Fi settings for iOS/iPadOS Devices**!!

> ![A screenshot of a computer Description automatically
> generated](./media/image9.png)

7.  在 “**Configuration settings**” 邊欄選項卡上，選擇 “**Wi-Fi type**”
    旁邊的 “**Basic**”。

> 其他選項根據所選類型顯示。

8.  在 “**Configuration settings**” 邊欄選項卡上，選擇以下選項，然後選擇
    “**Next**”：

    - 網絡名稱： !!**Contoso Wi-Fi**!!

    - SSID： !! **MainOffice**!!

    - 自動連接： **Enable**

    - 安全類型： **WPA/WPA2-Personal**

    - 預共享密鑰： !!**ContosoWiFi123**!!

> ![A screenshot of a computer Description automatically
> generated](./media/image10.png)

9.  在 **Assignments** 邊欄選項卡上的 **Included groups** 下，選擇 **Add
    groups**。

> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)

10. 在 **Select groups to include** （選擇要包含的組） 窗口中，選擇
    **iOS_iPadOS Devices**（設備），然後單擊 **Select**（選擇）。

> ![](./media/image12.png)

11. 在 **Assignments** 選項卡中，單擊 **Next** 按鈕。

> ![A screenshot of a computer Description automatically
> generated](./media/image13.png)

12. 在 **Review + create** 選項卡中，單擊 **Create** 按鈕。

> ![A screenshot of a computer Description automatically
> generated](./media/image14.png)

13. 驗證是否列出了 **iOS/iPadOS Wi-Fi Policy**。

> ![A screenshot of a computer Description automatically
> generated](./media/image15.png)
>
> **結果：**完成本練習後，您將成功創建並分配配置文件，以便為 iOS 和
> iPadOS 設備配置 Wi-Fi 設置。
