ラボ 20: Autopilot を使用した Windows 11 の展開

**要約**

このラボでは、ユーザー主導モードを使用して、Autopilot で Windows 11
デバイスを提供する方法を学びます。

**前提条件**

- このラボの前に、次のラボを完了する必要があります。

- ラボ 01 - Microsoft Entra ID での ID の管理

- ラボ 02 - Azure AD Connect を使用した ID の同期

- ラボ 11 - Microsoft Deployment Toolkit を使用した Windows 11 の展開

**シナリオ**

Contoso IT は、Autopilot を使用して新しい Windows 11
デバイスのデプロイを展開することを計画しています。デバイスには、Windows
11 がデフォルトでインストールされています。ユーザーは、OOBE
中にデバイスを接続し、電源を入れ、Microsoft Entra ID
資格情報を使用してサインインすることで、最小限の質問に答えることができる必要があります。このプロセスは、Entra
ID ドメインに自動的に登録され、参加する必要があります。最近 Hyper-V
を使用してインストールおよび構成した SEA-WS4
を使用してエクスペリエンスを構成およびテストするように求められました.

タスク 1: Microsoft Entra Adminセンターでグループを作成する

1.  [***SEA-SVR1***](urn:gd:lg:a:select-vm)に切り替えて、
    !!としてサインインし、パスワード [**Pa55w.rd**](urn:gd:lg:a:send-vm-keys) を使用して、 **Server
    Manager**.**Contoso\Administrator**!! を !!!! を使用して**Server
    Manager**を閉じる。

2.  タスクバーで**Microsoft Edge**を使用する。

3.  Microsoft Edgeにアドレスバーに!!﷟HYPERLINK
    "https://entra.microsoft.com"**ttps://entra.microsoft.com**!!を入力して**Enter**を押す。求めたらパスワード.[**admin@M365xXXXXXXXX.onmicrosoft.com**](mailto:admin@M365xXXXXXXXX.onmicrosoft.com)!!
     を使用してサインインする。

![](./media/image1.png)

4.  ナビゲーションウィンドウで**Identity**を選択する**。**

5.  **Identity** の下に**Groups**を選択する。

> ![](./media/image2.png)

6.  **Groups | All groups**ブレードで**、New group**を選択する

> ![](./media/image3.png)

7.  **New GroupブレードにGroup typeリストにSecurity**を選択する。

8.  **Group nameボックスに**!!﷟HYPERLINK
    "http://urn:gd:lg:a:send-vm-keys"**IT Devices**!!.を入力する。

9.  **Group descriptionボックスに** !!﷟HYPERLINK
    "http://urn:gd:lg:a:send-vm-keys"**IT Department
    Devices**!!を入力する。

10. **Membership typeリストにDynamic Device**を選択する。

11. **Add dynamic query**を選択する。

> ![](./media/image4.png)

12. **Dynamic membership rulesブレードで** **Rule
    syntaxボックスの上にあるEdit**を選択する。

> ![](./media/image5.png)

13. In the
    Editルール構文テキストボックスに次のシンプルなメンバーシップルールを追加してから**OK**を選択する。

14. !!(device.devicePhysicalIDs -any (\_ -contains "\[ZTDId\]"))!!

> ![](./media/image6.png)

15. **Save**を選択して**Dynamic membership
    rules**を閉じてから**Createを**選択してグループを作成する**。** 

> ![A screenshot of a computer Description automatically
> generated](./media/image7.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)
>
> ![](./media/image9.png)

タスク 2: デバイス固有のcomma-separated value (CSV) ファイルを生成する。

1.  [***SEA-SVR2***](urn:gd:lg:a:select-vm) に切り替えて、[**Contoso\Administrator**](urn:gd:lg:a:send-vm-keys) にサインインし、パスワード
    of !!﷟HYPERLINK
    "http://urn:gd:lg:a:send-vm-keys"**Pa55w.rd**!!を使用する。

> ![A screenshot of a computer Description automatically
> generated](./media/image10.png)

2.  タスクバーで**Hyper-V Manager**を選択する。.

> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)

3.  Virtual
    Machinesに、**SEA-WS4**を右クリックし**、Connect**を選択する。

> ![](./media/image12.png)

4.  **SEA-WS4**ウィンドで**Start**を選択する。コンピューターが起動されたらウィンドを最大化する。

> ![A screenshot of a computer Description automatically
> generated](./media/image13.png)

5.  **SEA-WS4** に [**Administrator**](urn:gd:lg:a:send-vm-keys) としてサインインし、!!﷟HYPERLINK
    "http://urn:gd:lg:a:send-vm-keys"**Pa55w.rd**!!パスワードを使用する。

> ![A screenshot of a computer Description automatically
> generated](./media/image14.png)

6.  **Start**を右クリックし、**Windows Terminal
    (Admin)**を選択してから **User Account
    Control**プロンプト**Yes** を選択する。

> ![](./media/image15.png)
>
> ![A screenshot of a computer error Description automatically
> generated](./media/image16.png)

7.  Windows PowerShell コマンド ライン
    プロンプトで、次のコマンドレットを入力し、**Enter** キーを押します：

> !! Install-Script -Name Get-WindowsAutoPilotInfo!!

![A screenshot of a computer Description automatically
generated](./media/image17.png)

1.  3 つのプロンプトが表示されます。毎回、「Y」と入力し、**Enter
    キーを押します**。

> ![](./media/image18.png)

8.  Windows PowerShell コマンド ライン
    プロンプトで、次のコマンドレットを入力し、**Enter** キーを押します：

> !!**Set**-ExecutionPolicy *RemoteSigned*!!

9.  プロンプトされたら、[**Y**](urn:gd:lg:a:send-vm-keys)を入力してEnterキーを押します。

10. At the Windows
    PowerShellコマントラインプロンプトで次のcmdletを入力して**Enter**キーを押します。

> !!Get-WindowsAutoPilotInfo.ps1 -OutputFile C:\Computer.csv!!
>
> ![](./media/image19.png)

1.  Windows PowerShell コマンド ライン
    プロンプトで、次のコマンドを入力して **Enter**
    キーを押し、ファイルの内容を確認します。

&nbsp;

11. !!C:\Computer.csv!!をタイプする

> ![](./media/image20.png)

1.  Windows PowerShell コマンド ライン
    プロンプトで、次のコマンドを入力し、**Enter**
    キーを押します。これにより、ファイルが **SEA-SVR2
    にコピーされます**。

&nbsp;

12. !!c:\computer.csv
    [\\sea-svr2\labfiles](file:///\\sea-svr2\labfiles)!!をコピーする。

> ![A screenshot of a computer screen Description automatically
> generated](./media/image21.png)

13. Windows PowerShellコマンドプロンプトを閉じる。

タスク 3: Windows Autopilot 展開プロファイルの操作

1.  [***SEA-SVR1***](urn:gd:lg:a:select-vm)に切り替える。

> ![](./media/image22.png)

2.  **Microsoft Edge**で、新しいタブを開き、 !!﷟HYPERLINK
    "https://intune.microsoft.com"**https://intune.microsoft.com**!!に移動する。プロンプトされたら.[**admin@M365xXXXXXXX.onmicrosoft.com**](mailto:admin@M365xXXXXXXX.onmicrosoft.com)!!
    を使用してサインインする。

3.  **Microsoft Intune admin center**で**Devices**を選択する**。**

4.  **Device enrollment**セクションで**Enroll devices**を選択する。

5.  ディテールペインに**Windows Autopilot Deployment
    Program**へスクロールダウンして、**Devices**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image23.png)

6.  In the **Windows Autopilot
    devicesブレードにメニューバーでImport**を選択して、**folder
    icon**を選択し、 !!﷟HYPERLINK
    "http://urn:gd:lg:a:send-vm-keys"**\\SEA-SVR2\Labfiles**!!を観覧して**Computer.csv**を選択し、**Open**を選択してから**Import**を選択する。

> ![](./media/image24.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image25.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image26.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image27.png)
>
> **注**: インポート プロセスには最大 15
> 分かかる場合がありますが、通常は約 5 分かかります。
>
> **重要**:
> 処理が完了すると、デバイスが表示されないことがあります。この場合は、**Sync**
> ボタンを選択し、数分待ってから、**Refresh を選択します**。

7.  **Windows Autopilot
    devices**ブレードをクロースするにはXを選択する**。**

> ![](./media/image28.png)

8.  Windows 登録ブレードの詳細ウィンドウで、\[**Deploy profiles\]
    を選択します**。

> ![](./media/image29.png)

9.  **Windows AutoPilot deployment profilesブレードで** **Create
    profileを選択してからWindows PC**を選択する。

> ![](./media/image30.png)

10. In the **Basicsタブで、Nameテキストボックスに** !!﷟HYPERLINK
    "http://urn:gd:lg:a:send-vm-keys"**Contoso profile1**!!を入力する。

11. **Convert all targeted devices to
    Autopilot** で**No**を選択してから**Next**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image31.png)

12. **Out-of-box experience (OOBE)タブで、Deployment
    modeはUser-Driven**と設定されていることを確認する。

13. **Join to Microsoft Entra ID はMicrosoft Entra
    Joined**と設定すること

14. 次のオプションが設定されることを確認する：

    - Microsoft Software License Terms: **Hide**

    - Privacy Settings: **Hide**

    - Hide change account options: **Hide**

    - User account type: **Administrator**.

    - Allow pre-provisioned deployment: **No**

    - Language (Region): **Operating system default**

    - Automatically configure keyboard: **Yes**

    - Apply device name template: **No**

15. **Next**を選択する。

> ![](./media/image32.png)

16. **AssignmentsタブでIncluded groupsの下にAdd groups**を選択する。

17. **IT
    Devicesグループを選択して、Select**を選択し、**Next**を選択する。

> ![](./media/image33.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image34.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image35.png)

18. **Review +
    create**ブレードで情報を確認してから **Create**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image36.png)
>
> ![](./media/image37.png)

タスク 4: PCをリセットする

1.  [***SEA-SVR2***](urn:gd:lg:a:select-vm)に切り替える。**SEA-WS4コンピューターはまだ最大化するはずです。**

> ![](./media/image38.png)

2.  **SEA-WS4**で**Start**を選択して、 !!﷟HYPERLINK
    "http://urn:gd:lg:a:send-vm-keys"**reset**!!を入力してから** Reset
    this PC**を選択する。

> ![](./media/image39.png)

3.  **Reset this PC**セクションに**Reset PC**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image40.png)

4.   **Remove everything**を選択してから**Local reinstall**を選択する。

> ![A blue screen with white text Description automatically
> generated](./media/image41.png)
>
> ![A blue screen with white text Description automatically
> generated](./media/image42.png)

5.  **Nextを選択してからReset**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image43.png)
>
> ![A blue screen with white text Description automatically
> generated](./media/image44.png)
>
> **注:**
> 通常、このタスクは物理デバイスの新規導入には必要ありません。デバイスのオートパイロット情報は、製造元から提供されるか、OOBE
> 前にデバイスから取得できます。このラボでは、新しいデバイスの OOBE
> をシミュレートするためにリセットを開始する必要があります。
>
> **注:** このプロセスには 45～60
> 分かかる場合があり、プロセス中に数回再起動されます。このタスクが完了するまで、インストラクターは次のモジュールに進む場合があります。次回のラボセッションでは、必ずタスク
> 5 に戻って完了してください。

タスク 5: Autopilotのデプロイを確認

1.  **Contoso Corp. サインインページで**enter !!﷟HYPERLINK
    "mailto:Cindy@M365x19242953.onmicrosoft.com"**Cindy@M365x19242953.onmicrosoft.com**!!を入力してから**Next**を選択する。

2.  パスワードページで!!﷟HYPERLINK
    "mailto:P@55w.rd1234"**P@55w.rd1234**!! を入力して**Sign
    in**を選択する。

3.  **Use Windows Hello with your account**で**OK**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image45.png)

4.  **Verify your identityページで**Text検証方法を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image46.png)

5.  **Enter
    code**ページで、携帯デバイスにテキストで送信されたコードを入力して**Verify**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image47.png)

6.  **Setup up a PINダイアログボックスでNew PINとConfirm
    PINフィールドに[102938](urn:gd:lg:a:send-vm-keys)**を入力して,
    **OK**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image48.png)

7.  **All set!**ページで**OK**を選択する。

8.  **Start**を選択し**、Settings**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image49.png)

9.  **Accounts**を選択して**Access work or
    school**を選択する。デバイスが ContosoのAzure AD
    と接続されていることを確認する。

> ![A screenshot of a computer Description automatically
> generated](./media/image50.png)

10. **Connected to Contoso's Azure AD**を選択して**、Info**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image51.png)

11. **Managed by
    Contoso**ページでスクロールダウンし**、** **Sync**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image52.png)
>
> ![](./media/image53.png)

12. **SEA-WS4**で**Settings**ウィンドを閉じる

13. [***SEA-SVR1***](urn:gd:lg:a:select-vm)に切り替える。

14. Microsoft
    Entraアドミンセンターに**Identity**を選択して、**Devices**を選択し、 **All
    devices**を選択する。

> ![](./media/image54.png)
>
> 新しいデバイスの名前が「**DESKTOP-**」で始まることをご確認する。また、Join
> Typeが**Microsoft Entra ID joined**で、所有者がCindy
> Whiteであることにも注意する

1.  Autopilotデバイスを選択する。上部のメニューバーに沿って管理オプションを確認します。

> デバイスを**Retire, Wipe,
> Sync,** と **Restart**できることに注意する**。**

15. メニューバーの最後にある三つのドットを選択して、追加の管理機能に注意する。

> ![A screenshot of a computer Description automatically
> generated](./media/image55.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image56.png)
>
> 追加のケーパビリティにはFresh Start, Autopilot Reset, Quick scan, Full
> scan, などが含めています。

16. Microsoft Edgeをクロースする。

**結果:**
この手順を完了すると、ユーザー主導モードを使用して、**Autopilot** で
**Windows 11** デバイスを提供することになります。
