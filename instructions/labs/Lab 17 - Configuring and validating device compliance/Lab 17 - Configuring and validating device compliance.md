Lab17 - 配置和驗證設備合規性

**總結**

在本實驗中，您將通過配置用於確定託管設備狀態的合規性策略和關聯的條件訪問規則來驗證設備合規性。

**先決條件**

在此實驗之前，必須完成以下實驗：

- 實驗 \#1 - 在 Microsoft Entra ID 中管理身份

- 實驗 \#2 - 使用 Microsoft Entra Connect 同步標識

- 實驗 \#5 - 管理設備註冊到 Microsoft Intune

- 實驗 \#6 - 將設備註冊到 Microsoft Intune

- 實驗 \#7 - 創建和部署配置文件

練習 1：配置合規性策略。

**場景**

Contoso 希望確保在 Microsoft Intune 中註冊的 Windows
設備滿足最低配置規範。以下是必需的規格：

- 最低 Windows作系統版本：10.0.19041.329

- 需要 Microsoft Defender 反惡意軟件。

如果設備滿足這些要求，它將被標記為合規。如果設備不滿足這些要求，則應將設備標記為不合規。

任務 1：創建並分配合規性策略

1.  登錄 [***SEA-SVR1***](urn:gd:lg:a:select-vm) 為 !!**[Contoso\Administrator](urn:gd:lg:a:send-vm-keys)!!** 用密碼
    !!**[Pa55w.rd](urn:gd:lg:a:send-vm-keys)!!** 

2.  在任務欄上，選擇 **Microsoft Edge**。在 Microsoft Edge
    中，鍵入 !!**https://Intune.microsoft.com!!** ，然後按 **Enter**。

3.  使用 **Office 365 租戶管理員憑據**登錄。

> ![A screenshot of a computer Description automatically
> generated](./media/image1.png)

4.  從導航窗格中，選擇 **Devices**（設備），然後選擇 Manage
    devices（管理設備）下的 **Compliance**（合規性）。

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)

5.  在 “**Compliance | Policies**” 邊欄選項卡中，在詳細信息窗格中選擇
    “**+ Create Policy**” 。

> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)

6.  在 **Create a policy** （創建策略） 邊欄選項卡上，提供以下值並選擇
    **Create** （創建）：

    - 平臺： **Windows 10 and later**

> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

7.  在 **Basics** 選項卡上，提供以下值，然後選擇 **Next**：

    - 名字： !!**[Compliance1](urn:gd:lg:a:send-vm-keys)!!**

> ![](./media/image5.png)

8.  在 **Compliance settings** （合規性設置） 選項卡上，展開 **Device
    Health** （設備運行狀況） 並查看可用設置。

> ![A screenshot of a computer Description automatically
> generated](./media/image6.png)

9.  在 **Compliance settings** （合規性設置） 選項卡上，展開 **Device
    Properties** （設備屬性）。在 **Minimum OS version**
    字段中，鍵入 !!**[10.0.19041.329](urn:gd:lg:a:send-vm-keys)!!**

> ![A screenshot of a computer Description automatically
> generated](./media/image7.png)

10. 在 **Compliance settings** （合規性設置） 選項卡上，展開 **System
    Security** （系統安全）。將 **Microsoft Defender Antimalware**
    設置設置為 “**Require**” ，然後選擇 “**Next**” 。

> ![](./media/image8.png)

11. 在 **Actions for noncompliance** （針對不符合性的作）
    選項卡上，請注意 **Mark device noncompliant** default setting
    （將設備不符合性標記為不符合性） 的作是 **immediately** （立即）。

> ![A screenshot of a computer Description automatically
> generated](./media/image9.png)
>
> 查看如何配置設備標記為不合規的天數，以及配置其他作。

12. 選擇 **Next**（下一步）。在 **Assignments** （分配） 選項卡上，選擇
    **Add groups** （添加組）。選擇 **Windows Devices**，選擇
    **Select**，然後選擇**Next**。

> ![A screenshot of a computer Description automatically
> generated](./media/image10.png)
>
> **注意：Windows Devices** 組是在創建和部署配置文件 - 實驗室中創建的。

13. 選擇 **Create**。

> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)

14. 在導航菜單中，選擇 “**Devices**” ，然後在 “設備” 導航窗格中，選擇
    “**Compliance**” 。

> ![A screenshot of a computer Description automatically
> generated](./media/image12.png)

15. 在 **Compliance** （合規性） 頁面上，選擇 **Compliance settings**
    （合規性設置）。

> ![A screenshot of a computer Description automatically
> generated](./media/image13.png)

16. 在 **Compliance policy settings** （合規性策略設置） 頁面上，在
    **Mark devices with no compliance policy assigned as**
    （將未分配合規策略的設備標記為） 旁邊，選擇 **Not Compliant**
    （不合規），然後選擇 **Save** （保存）。

> ![A screenshot of a computer Description automatically
> generated](./media/image14.png)
>
> 此設置將確保任何未分配合規性策略的設備都將設置為 **Not compliant**
> （不合規）。

**結果：**完成本練習後，您將成功配置合規性策略。

練習 2：創建條件訪問策略以強制實施合規性。

**場景**

當用戶使用標記為不符合的設備時，他們應該無法訪問其電子郵件。系統要求你配置強制實施此規則的條件訪問策略，並驗證它是否按預期運行。

任務 1：創建條件訪問策略

1.  在 [***SEA-SVR1***](urn:gd:lg:a:select-vm)上， 在 **Microsoft Intune
    管理中心**中選擇 “**Devices**”，然後選擇 “**Conditional access**”。

> ![A screenshot of a computer Description automatically
> generated](./media/image15.png)

2.  單擊 **Policies**，然後選擇 **+ New policy**，

> ![A screenshot of a computer Description automatically
> generated](./media/image16.png)

3.  在 **New** blade 的 **Name**
    文本框中，鍵入 !\![**Conditional1!! **](urn:gd:lg:a:send-vm-keys)
    ，然後選擇 **0 users or workload identities selected**（0
    個用戶或已選擇的工作負載身份）。

> ![A screenshot of a computer Description automatically
> generated](./media/image17.png)

4.  在 **Users and groups** 邊欄選項卡上，選擇 **All users** 單選按鈕。

> ![A screenshot of a computer screen Description automatically
> generated](./media/image18.png)

5.  在 “**New**” 邊欄選項卡上，選擇 “**No target resources selected**”
    ，選擇 “**Select apps**” 單選按鈕，然後選擇 !!**Office 365 Exchange
    Online!!**，然後單擊 “**Select**” 。

> ![A screenshot of a computer Description automatically
> generated](./media/image19.png)

6.  在 “**New**” 邊欄選項卡的 “**Conditions**” 部分中，選擇 “**0
    conditions selected**” 。

> ![A screenshot of a computer Description automatically
> generated](./media/image20.png)

7.  在條件列表中，在 **Device platforms** （設備平臺） 下，選擇 **Not
    configured** （未配置）。在 **Configure** 部分中，選擇 **Yes**，選擇
    **Select device platforms** 單選按鈕，選中 **Windows**
    複選框，然後選擇 **Done**。

> ![A screenshot of a computer Description automatically
> generated](./media/image21.png)

8.  在 **Access controls** 下的 **New** blade 的 **Grant** 部分中，選擇
    **0 controls selected**。

9.  選中 **Require device to be marked as compliant** 複選框，然後選擇
    **Select**。

> ![A screenshot of a computer Description automatically
> generated](./media/image22.png)

10. 在 “**New**” 邊欄選項 **On**，為 “**Enable policy**”
    選項選擇，然後選擇 “**Create**” 。

> ![A screenshot of a computer Description automatically
> generated](./media/image23.png)

11. 關閉 Microsoft Edge。

任務 2：驗證條件訪問策略是否正常工作

1.  切換到 [***SEA-WS3***](urn:gd:lg:a:select-vm) 並以 !!**[Admin](urn:gd:lg:a:send-vm-keys)!!** 使用密碼 !!**[Pa55w.rd](urn:gd:lg:a:send-vm-keys)!!**。

2.  在 [***SEA-WS3***](urn:gd:lg:a:select-vm) 的任務欄上，選擇
    **Microsoft Edge**。在 Microsoft Edge
    中，鍵入 [**outlook.office.com**](urn:gd:lg:a:send-vm-keys) ，然後按
    Enter。

3.  在 選取帳戶
    對話框中，選擇 !!**Cindy@M365xXXXXXXX.onmicrosoft.com!!**

4.  在 **Enter password** （輸入密碼）
    頁面上，輸入 !!**P@55w.rd12345!!** ，然後選擇 **Sign in**
    （登錄）。如果出現 Microsoft Edge Save password 提示，請選擇
    **Update**。

> ![A screenshot of a computer error Description automatically
> generated](./media/image24.png)

5.  確認您收到消息 **"** **Sign in with your work account"**。

> ![A screenshot of a computer Description automatically
> generated](./media/image25.png)

6.  選擇 **More details**。您應該會看到有關您被阻止的原因的更多信息。

> ![A screenshot of a computer error Description automatically
> generated](./media/image26.png)
>
> **注意：**這是因為 SEA-WS3 未加入 Microsoft Entra ID，也不由 Microsoft
> Intune 管理，因此未標記為合規。

7.  **關閉**瀏覽器窗口**。**

8.  切換到 [***SEA-WS1***](urn:gd:lg:a:select-vm)，並以
    !!**Cindy@M365xXXXXXXX.onmicrosoft.com!!**
    使用**密碼**頁面，輸入 !!**P@55w.rd12345!!** 

> **注意：**SEA-WS1 是在 Intune 中註冊的託管 Windows 11 設備。

9.  在任務欄上，選擇 **Microsoft Edge**。在 Microsoft Edge
    中，鍵入 [**Outlook.office.com**](urn:gd:lg:a:send-vm-keys) ，然後按
    **Enter**。

10. 驗證您是否可以訪問 Cindy 的郵箱。

> ![A screenshot of a computer Description automatically
> generated](./media/image27.png)
>
> **注意：**這是因為 **SEA-WS1** 是託管設備並標記為合規。

11. 關閉 Microsoft Edge 並注銷 [***SEA-WS1***](urn:gd:lg:a:select-vm)。

任務 3：禁用條件訪問策略

1.  在 [***SEA-SVR1***](urn:gd:lg:a:select-vm)上， 在 **Microsoft Intune
    管理中心** !\!<https://intune.microsoft.com>!! 選擇 “**Devices**”
    ，然後選擇 “**All devices**” 。

> ![](./media/image28.png)
>
> 請注意，**SEA-WS1** 是合規的，這就是允許 Cindy 訪問其郵箱的原因。

2.  從導航窗格中，選擇 **Devices**（設備），然後選擇 **Conditional
    access**（條件訪問）。

> ![](./media/image29.png)

3.  在 “**Conditional Access**” 頁上，選擇 “**Policies**”，然後單擊
    “**Conditional1**” 。

> ![A screenshot of a computer Description automatically
> generated](./media/image30.png)

4.  在 **Conditional1** 頁面底部的頁面上，選擇 **Off**，然後選擇
    **Save**。

> ![A screenshot of a computer Description automatically
> generated](./media/image31.png)

5.  關閉Microsoft Edge。

**結果：**完成本練習後，您將成功配置條件訪問策略以確定設備合規性。
