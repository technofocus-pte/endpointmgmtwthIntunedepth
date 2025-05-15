**實驗 11 - 在 Intune 中監視設備和用戶活動**

**總結**

在本實驗中，您將監控用戶登錄活動、審核日誌和設備活動。

**先決條件**

在此實驗之前，必須完成以下實驗：

- 實驗 \#1 - 在 Microsoft Entra ID 中管理身份

- 實驗 \#2 - 使用 Microsoft Entra Connect 同步標識

- 實驗 \#5 - 管理設備註冊到 Microsoft Intune

- 實驗 \#6 - 將設備註冊到 Microsoft Intune

- 實驗 \#7 - 創建和部署配置文件

**注意：**您還需要一部可以接收短信的移動電話，該短信用於保護 Windows
Hello 登錄身份驗證對 Microsoft Entra ID 的安全。

**場景**

您需要查看 Cindy White
登錄活動以及審核日誌提供的一般信息。您還需要驗證硬件
在 [*SEA-WS1*](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10) 上，
並確認分配給此設備的配置文件已成功應用。

**任務 1：監視用戶活動**

1.  切換到
    *[SEA-SVR1](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)*
    並在需要時使用提供的憑據登錄。

2.  在 **Microsoft Entra 管理中心**頁面上，導航並選擇
    “**Users**”，然後單擊 “**All users**”。

> ![](./media/image1.png)

3.  在 **Users** （用戶） 頁面中，導航並選擇 **Allan Deyoung**。

> ![](./media/image2.png)

4.  在 **Allan Deyoung** User 頁面中，導航並單擊 **Sign-in logs**。

> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)

5.  在 **Allan Deyoung | Sign-in logs** 頁面中，單擊 **User sign-ins
    （interactive）** （用戶登錄（交互式）） 選項卡下的第一個條目。

> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

6.  選擇每個主頁，包括 **Basic
    info**（基本信息）、**Location**（位置）、**Device
    info**（設備信息）、**Authentication Details**（身份驗證詳細信息）和
    **Conditional
    Access**（條件訪問）。向下滾動並檢查每個頁面上的信息。仔細查看每個頁面中提供的信息後，關閉該窗格。

> ![](./media/image5.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image6.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image7.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image9.png)

7.  在 Users （用戶） 導航窗格中，選擇 **Audit logs** （審核日誌）。

8.  在詳細信息窗格中，將顯示有關用戶管理更改的審核信息。通過選擇各種條目來檢查信息。

> ![A screenshot of a computer Description automatically
> generated](./media/image10.png)
>
> ![](./media/image11.png)

**任務 2：監控設備活動**

1.  切換到 **Microsoft Intune 管理中心**窗口，導航並單擊“**Devices**”。

![](./media/image12.png)

2.  在 Devices （設備） 導航窗格中，選擇 **Overview** （概述）。

> ![A screenshot of a computer Description automatically
> generated](./media/image13.png)

3.  向下滾動並查看以下內容：

- 配置策略分配失敗

- 不合規的設備。

- 每個 Windows 更新通道的部署狀態。

> ![](./media/image14.png)

4.  向下滾動到 **Manage devices** 部分，然後單擊
    **Configuration**。查看配置詳細信息。

> ![](./media/image15.png)

5.  向上滾動並選擇 **All devices**（所有設備）。在 “**Devices | All
    devices** ”
    頁面中，將顯示有關設備的信息，例如設備名稱、管理者、所有權、合規性、作系統和作系統版本。點擊
    **SEA-WS1**。

> ![](./media/image16.png)

6.  在 SEA-WS1 導航窗格中，選擇 “**Hardware**” 並檢查硬件清單。

> ![A screenshot of a computer Description automatically
> generated](./media/image17.png)

7.  在 SEA-WS1 導航窗格中，選擇 **Discovered apps** （發現的應用程序）
    並檢查應用程序清單。

> ![A screenshot of a computer Description automatically
> generated](./media/image18.png)

8.  在 SEA-WS1 導航窗格中，選擇 **Device configuration**
    並在詳細信息窗格中記下分配給設備的 設備配置文件。**State** 列應顯示
    **Succeeded**，這意味著配置文件已成功應用於設備。

> ![](./media/image19.png)

9.  在 **SEA-WS1 | Device configuration** 頁面，單擊 **Contoso Developer
    – standard**。

> ![](./media/image20.png)

10. 在 “**Contoso Developer – standard**”
    邊欄選項卡上，記下在配置文件中配置的每個設置。

> **State** 應在所有旁邊顯示 **Succeeded**。
>
> ![](./media/image21.png)

**結果：**完成本練習後，您將成功監控用戶登錄活動、審核日誌和設備活動。
