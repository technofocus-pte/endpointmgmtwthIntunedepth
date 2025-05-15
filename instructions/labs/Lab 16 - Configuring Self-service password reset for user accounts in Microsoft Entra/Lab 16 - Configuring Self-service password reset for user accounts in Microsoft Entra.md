實驗 16 - 在 Microsoft Entra 中為用戶帳戶配置自助密碼重置

**總結**

在本實驗中，你將為 **Microsoft Entra ID**
中的用戶帳戶配置和驗證自助密碼重置 （SSPR）。

**先決條件**

在此實驗之前，必須完成以下實驗：

- 實驗 \#2 - 使用 Microsoft Entra Connect 同步標識

- 實驗 \#5 - 管理設備註冊到 Microsoft Intune

**場景**

Help Desk
表示，大量支持票證與密碼重置有關。系統要求您為用戶提出一個解決方案來重置自己的密碼。對於從
AD DS 同步的帳戶，該過程應重置其 Microsoft Entra 和 AD DS 密碼。

任務 1：配置密碼寫回

1.  登錄 [***SEA-SVR1***](urn:gd:lg:a:select-vm) 為 !!**[Contoso\Administrator](urn:gd:lg:a:send-vm-keys)!!** 用密碼
    !!**[Pa55w.rd](urn:gd:lg:a:send-vm-keys)!!** 並關閉 **Server
    Manager**。

2.  在桌面上，雙擊 **Azure AD Connect**。

> ![A screenshot of a computer Description automatically
> generated](./media/image1.png)

3.  在 “**Welcome to Azure AD Connect**” 頁上，選擇 “**Configure**” 。

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)

4.  在 **Additional tasks** （其他任務） 頁面上，選擇 **Customize
    synchronization options** （自定義同步選項），然後選擇 **Next**
    （下一步）。

> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)

5.  在 **Connect to Azure AD** （連接到 Azure AD）
    頁面上，如果需要，鍵入 !!**admin@M365xXXXXXXX.onmicrosoft.com!!** 在
    **USERNAME** （用戶名） 文本框中，鍵入 **PASSWORD**，然後選擇
    **Next** （下一步）。

> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

6.  在 **Connect to your directories** （連接到您的目錄） 頁面上，選擇
    **Next** （下一步）。

7.  在 **Domain and OU filtering** （域和 OU 篩選） 頁面上，選擇
    **Next** （下一步）。

8.  在 **Optional features** （可選功能） 頁面上，選擇 **Password
    writeback**（密碼寫回），然後選擇 **Next**（下一步）。

> ![A screenshot of a computer Description automatically
> generated](./media/image5.png)

9.  在 “**Ready to configure**” 頁面上，選擇 “**Configure**” 。

> ![A screenshot of a computer Description automatically
> generated](./media/image6.png)
>
> ![A computer screen shot of a computer Description automatically
> generated](./media/image7.png)
>
> **注意：**配置可能需要幾分鐘時間。

10. 在 **Configuration complete** （配置完成） 頁面上，選擇 **Exit**
    （退出）。

> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)

任務 2：啟用自助式密碼重置。

1.  在任務欄上，選擇 **Microsoft Edge**，導航到 **Microsoft Entra
    管理中心** **https://Entra.Microsoft.com**.

2.  使用 **Office 365 租戶管理員**憑據登錄。

> ![A screenshot of a computer Description automatically
> generated](./media/image9.png)
>
> 此時將打開 **Microsoft Entra 管理中心**。

3.  在 **Microsoft Entra 管理中心**的導航窗格中，展開 “**Identity**”
    ，然後選擇 “**Users**” 。

4.  在 **Users** （用戶） 導航窗格中，選擇 **Password reset**
    （密碼重置）。

> ![A screenshot of a computer Description automatically
> generated](./media/image10.png)

5.  在 **Password reset | Properties** 窗口中，選擇 “**All**”
    以啟用對所有用戶的自助密碼重置。選擇 **Save** （保存）。

> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)
>
> ![A screenshot of a computer screen Description automatically
> generated](./media/image12.png)

6.  在 **Password reset | Properties** 邊欄選項卡中，選擇
    “**Authentication methods**” 。

> ![A screenshot of a computer Description automatically
> generated](./media/image13.png)

7.  對於用戶可用的方法，請確保選擇 **Mobile Phone** （移動電話） 和
    **Email** （電子郵件），然後選擇 **Security
    Questions**（安全問題）。

8.  對於 **Number of questions required to register**
    （註冊所需的問題數），選擇 **3**。

9.  對於 **Number of questions required to
    reset**（重置所需的問題數），選擇 **3**。

> ![A screenshot of a computer Description automatically
> generated](./media/image14.png)

10. 在 **Select security questions** 部分中，選擇 **No security
    questions configured**，然後選擇
    **Predefined**。選擇您選擇的三個問題，然後選擇 **OK** （確定）
    兩次。

> ![A screenshot of a computer Description automatically
> generated](./media/image15.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image16.png)

11. 選擇 **Save** （保存）。

> ![A screenshot of a computer Description automatically
> generated](./media/image17.png)

12. 選擇 “**Registration**” ，為 “**Require users to register when
    signing in**” 和 “**Number of days before users are asked to
    re-confirm their authentication information**” 選擇 “**Yes**”
    ，將值設置為 **90**，然後選擇 “**Save**” 。

> ![A screenshot of a computer Description automatically
> generated](./media/image18.png)

13. 在導航窗格中，選擇 **On-premises integration**（本地集成）。

14. 驗證您的本地寫回客戶端是否正在運行，並確保選中 **Enable password
    write back for synced users** （為同步用戶啟用密碼回寫）
    複選框。如果需要，請選擇 **Save** （保存）。

> ![A screenshot of a computer Description automatically
> generated](./media/image19.png)

15. 關閉 Microsoft Edge。

任務 3：驗證自助式密碼重置

1.  切換到 [***SEA-WS3***](urn:gd:lg:a:select-vm)。 如有必要，請以
    !!**[Admin](urn:gd:lg:a:send-vm-keys)!!** 使用密碼 !!**[Pa55w.rd](urn:gd:lg:a:send-vm-keys)!!**

2.  在任務欄上，選擇 **Microsoft
    Edge**。瀏覽至 !!**https://mysignins.microsoft.com/!!**

3.  在 **Pick an account** （選擇賬戶） 頁面上，選擇 **Use another
    account** （使用其他賬戶）。

> ![A screenshot of a computer Description automatically
> generated](./media/image20.png)

4.  在 **Sign in** （登錄）
    頁面上，輸入 !!**Cindy@M365xXXXXXX.onmicrosoft.com!!** ，然後選擇
    **Next**。

5.  在 **Enter password** （輸入密碼）
    頁面上，輸入 **!!P@55w.rd1234!!**，然後選擇 **Sign in**
    （登錄）。如果 Microsoft Edge 提示保存密碼，請選擇 **Save**
    （保存）。

> ![A screenshot of a computer error Description automatically
> generated](./media/image21.png)

6.  系統將提示您 **More information required** （需要更多信息），單擊
    **Next** （下一步）

> ![A screenshot of a computer error Description automatically
> generated](./media/image22.png)

7.  提供詳細信息，然後單擊 **Next**。

> ![A screenshot of a computer Description automatically
> generated](./media/image23.png)

8.  輸入 6 位代碼，然後單擊 **Next**

> ![](./media/image24.png)

9.  再次單擊 Next（下一步）。

> ![A screenshot of a computer Description automatically
> generated](./media/image25.png)

10. 點擊 **Done**。

> ![](./media/image26.png)

11. 您應該能夠訪問 **My Account** 頁面

> ![](./media/image27.png)

12. 要更改 Password，請訪問鏈接 -
    **!!https://mysignins.microsoft.com/security-info!!**

13. 通過單擊文本 +XXXXXXXXXXXXXX 完成驗證

> ![A screenshot of a computer error Description automatically
> generated](./media/image28.png)

14. 提供 6 位數代碼，然後單擊 Verify （驗證）。

> ![A screenshot of a computer error Description automatically
> generated](./media/image29.png)

15. 單擊 **Skip for now。**

> ![A screenshot of a computer error Description automatically
> generated](./media/image30.png)

16. 在 **Security info** （安全信息） 頁面上，單擊 **Change** （更改）
    作為密碼。

> ![A screenshot of a login page Description automatically
> generated](./media/image31.png)

17. 在 **Change your password** （更改密碼）
    頁面上，輸入以下信息，然後選擇 **Submit** （提交）：

    - 創建新密碼： **!!P@55w.rd12345!!**

    - 確認新密碼： **!!P@55w.rd12345!!**

> ![A screenshot of a login box Description automatically
> generated](./media/image32.png)

18. 點擊 Done 按鈕。

> ![](./media/image33.png)

19. 關閉 Microsoft Edge 並注銷 [***SEA-WS3***](urn:gd:lg:a:select-vm)。

任務 4：運行 Azure AD Connect Sync

請注意，此步驟通常對於密碼寫回不是必需的，但建議執行此步驟以解決實驗室環境中固有的問題，並確保
AD DS 與 Microsoft Entra 同步。

1.  切換到 [***SEA-SVR1***](urn:gd:lg:a:select-vm) 並右鍵單擊 **Start**
    開始 然後選擇 **Windows PowerShell （Admin）。**

> ![A screenshot of a computer Description automatically
> generated](./media/image34.png)

2.  在 **Windows PowerShell** 命令提示符下，鍵入以下命令，然後按
    **Enter**：

> **!!Start-ADSyncSyncCycle -PolicyType Delta!!**
>
> ![A screenshot of a computer Description automatically
> generated](./media/image35.png)

3.  關閉 Windows PowerShell，然後等待大約 3-4 分鐘。

任務 5：驗證密碼寫回

1.  切換到 [***SEA-CL1***](urn:gd:lg:a:select-vm) 並在必要時注銷。在 [***SEA-CL1***](urn:gd:lg:a:select-vm)上，
    選擇 **Other
    user**（其他用戶），然後嘗試以 !!**Contoso\Cindy!!** 使用密碼 !!**P@55w.rd1234!!**

> ![A screenshot of a computer Description automatically
> generated](./media/image36.png)

2.  確保您收到用戶名或密碼不正確的消息。

> ![A screenshot of a computer screen Description automatically
> generated](./media/image37.png)

3.  現在以 !!**Contoso\Cindy!!** 使用密碼 !!**P@55w.rd12345!!** 使用
    SSPR 功能設置的密碼。

4.  這次，您應該使用 **new password** 成功登錄。

這將確認您在 “我的登錄”門戶中更改的密碼已寫回到本地 Active Directory
域服務 （AD DS） 帳戶。

![A screenshot of a computer error Description automatically
generated](./media/image38.png)

> 注意 –
> 如果您在登錄期間收到上述消息，則確認***身份驗證成功***，但由於組成員資格問題，帳戶無權登錄
> SEA-CL1。

**結果：**完成本練習後，您將成功配置並驗證自助式密碼重置。
