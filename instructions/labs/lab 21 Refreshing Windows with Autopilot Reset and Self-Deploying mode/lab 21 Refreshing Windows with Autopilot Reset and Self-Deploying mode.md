Lab 21: Autopilot ResetとSelf-Deployingモードを使用して Windowsの更新

**要約**

このラボでは、リモートでオートパイロットリセットを実行する方法を学びます。

**前提条件**

このラボの前に、次のラボを完了する必要があります:

- ラボ 01 - Microsoft Entra ID での ID の管理

- ラボ 02 - Azure AD Connect を使用した ID の同期

- ラボ 21 - Microsoft Deployment Toolkit を使用した Windows 11 の展開

- ラボ 20 - Autopilot を使用した Windows 11 の展開

**シナリオ**

SEA-WS4はWindows
Autopilotを使用して展開されています。Autopilotのリセットを含む別のプロビジョニングシナリオをテストする必要があります。Windows
Autopilotの自己展開モードで構成された新しい展開プロファイルを作成します。

タスク 1: Self-Deploying Windows Autopilot展開プロファイルを構成する

1.  [***SEA-SVR1***](urn:gd:lg:a:select-vm)に切り替える。

> ![](./media/image1.png)

2.  **Microsoft
    Edge**に新しいタブを開き、 [**https://intune.microsoft.com**](https://intune.microsoft.com)へ移動する。求めたら [**admin@M365xXXXXXXXX.onmicrosoft.com**](mailto:admin@M365xXXXXXXXX.onmicrosoft.com) とパスワードでサインインする。

3.  **Microsoft Intune admin center**に**Devices**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)

4.  **Device onboardingセクションにEnrollment**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)

5.  Windows登録ブレードで、詳細のペインに**Deployment
    Profiles**を選択する。

> ![](./media/image4.png)

6.  **Windows AutoPilot deployment profiles**ブレードで**Contoso Profile
    1**を選択してから**Properties**を選択する。

> ![](./media/image5.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image6.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image7.png)

7.  **Assignments**へスクロールダウンして**Edit**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)

8.  **IT Devices**の横に**Remove**を選択する。

> ![](./media/image9.png)

9.  **Review and save**を選択してから**Save**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image10.png)

10. **Contoso Profile 1|Properties**ページを閉じる。

11. **Windows AutoPilot deployment profiles**ブレードで**Create
    profileを**選択してから**Windows PC**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)

12. **Basics**タブで**Name**テキストボックスに[**Contoso profile
    2**](urn:gd:lg:a:send-vm-keys)を入力する。

13. **Convert all targeted devices to
    Autopilot**に対して**No**を選択してから**Next**を選択する。

> ![](./media/image12.png)

14. **Out-of-box experience (OOBE)** タブで**Deployment
    modeがSelf-Deploying**と設定されていることを確認する。

> ![](./media/image13.png)

15. 次のオプションが設定されていることを確認する：

    - Language (Region): **Operating system default**

    - Automatically configure keyboard: **Yes**

    - Apply device name template: **Yes**

    - Enter a name: [**Contoso-%RAND:2%**](urn:gd:lg:a:send-vm-keys)

> ![A screenshot of a computer Description automatically
> generated](./media/image14.png)

16. **Next**を選択する。

17. **Assignments**タブで**Included groups**の下に**Add
    groups**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image15.png)

18. **IT
    Devices**グループを選択して**、Select**をクリックする。**Next**を選択する。

> ![](./media/image16.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image17.png)

19. **Review +
    create**ブレードで情報を確認してから**Create**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image18.png)

タスク 2: Autopilotリセットを実行する

1.  **Microsoft Intune admin center**中に**Devices**を選択してから**All
    devices**を選択する。

2.  Autopilot PC (名前はDESKTOPで始まる)を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image19.png)

3.  メニューバーで三つのドットを選択してから **Autopilot
    Reset**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image20.png)

4.  メセッジプロンプトで**Yes**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image21.png)

5.  [***SEA-SVR2***](urn:gd:lg:a:select-vm)に切り替えて、**SEA-WS4ウィンドを最大化する。**

> **注:** SEA-WS4 は、前のラボからまだ実行されているはずです。
>
> **注**:デバイスを最新バージョンに更新し、\[再起動\]をクリックします。

6.  **SEA-WS4**を再起動する。

> ![A screenshot of a computer Description automatically
> generated](./media/image22.png)
>
> **注:**
> このプロセスには30分ほどかかる場合があり、途中で何度か再起動が発生します。このタスクが完了するまで、インストラクターは次のモジュールに進む場合があります。次回のラボセッションでは、必ずタスク3に戻って完了してください**。**

タスク 3: Autopilotの展開を確認

1.  サインインページで[**Cindy@M365x19242953.onmicrosoft.com**](mailto:Cindy@M365x19242953.onmicrosoft.com)を入力して、[**P@55w.rd1234**](mailto:P@55w.rd1234)パスワードを使用する。

2.  **Use Windows Hello with your accountでOK**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image23.png)

3.  **Verify your identity**ページにText verification methodを選択する。

4.  **Enter
    code**ページで携帯にテキストされたコードを入力して**Verify**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image24.png)

5.  **Setup up a PIN** ダイアログボックスでで**New PIN**と**Confirm
    PIN**フィールドに[**102938**](urn:gd:lg:a:send-vm-keys)を入力してから**OK**を選択する。.

> ![](./media/image25.png)

6.  **All set!ページでOK**を選択する。

7.  **Startを選択してからSettings**を選択する。

> ![](./media/image26.png)

8.  **Accounts**を選択してから**Access work or
    school**を選択する。デバイスがContosoのAzure
    ADへ接続していることを確認する。

> ![](./media/image27.png)

9.   **Connected to Contoso's Azure ADを選択してからInfo**を選択する。

> ![](./media/image28.png)

10. **Managed by
    Contoso**ページでスクロールダウンしてから**Sync**を選択する。

> ![](./media/image29.png)

11. **SEA-WS4**で**Settingsウィンドを閉じる。**

12. **SEA-WS4をシャットダウンしてから** **SEA-WS4ウィンドを閉じる。**

13. [***SEA-SVR2***](urn:gd:lg:a:select-vm)でHyper-V
    Managerをクロースする。

**結果: この演習を完了すると、セルフデプロイモードを使用して、Autopilot
Reset で Windows 11 デバイスをプロビジョニングできるようになります。**
