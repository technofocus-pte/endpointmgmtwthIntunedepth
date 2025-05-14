ラボ 18 - Microsoft Intune を使用したエンドポイント セキュリティの構成

**要約**

このラボでは、Microsoft Intune で管理対象デバイス用に Microsoft Defender
を構成するポリシーを作成します。

**前提 条件**

このラボの前に、次のラボを完了する必要があります:

- ラボ \#5 - Microsoft Intune へのデバイス登録の管理

- ラボ \#6 - Microsoft Intune へのデバイスの登録

- ラボ \#7 - 構成プロファイルの作成と展開

**シナリオ**

Contoso Developers GroupでMicrosoft
Defenderが正しく構成されていることを確認するよう求められています:

- • 改ざん防止を防止します。

- • Windows セキュリティ
  アプリで、アカウント保護、アプリとブラウザーの制御、デバイス
  セキュリティ、デバイスのパフォーマンスと正常性、ファミリー
  オプションの領域を非表示にします。

- • 会社名と電話番号を追加する必要があります。

- • リアルタイム保護、修復、スキャン設定も構成する必要があります。

設定は、登録済みデバイス SEA-WS1 と未登録デバイス SEA-CL1
でテストすることによって検証されます。

タスク 1: Windows Security Experience in IntuneでWindows Security
Experienceを構成する。

1.  [***SEA-SVR1***](urn:gd:lg:a:select-vm)に切り替えて、 !!**[Contoso\Administrator](urn:gd:lg:a:send-vm-keys)!!** としてサインインし、 !!**[Pa55w.rd](urn:gd:lg:a:send-vm-keys)!!**パスワードを使用する**。**

2.  タスクバーで**Microsoft Edge**を選択する。

3.  Microsoft
    Edgeでアドレスバーに!!**https://Intune.microsoft.com!!** を入力して、**Enter**を押す。

4.  Office 365 Tenant Adminとしてサインインする。

> ![A screenshot of a computer Description automatically
> generated](./media/image1.png)

5.  ナビゲーションウィンドウで**Endpoint
    security**を選択してから**Antivirus**を選択する。

> ![](./media/image2.png)

6.  **Endpoint security |Antivirus**ペインで**+ Create
    Policy**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)

7.  **Create a profile**ペインで**、Platform**に対して**Windows 10,
    Windows 11, and Windows Server**を選択する。

8.  **Profile**リストに**Windows Security
    experience**を選択する。その後**Create**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

9.  Basicsタブで**Nameフィールドに** !!**[Windows Security
    Settings](urn:gd:lg:a:send-vm-keys)!!**を入力して、**Next**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image5.png)

10. **Defender**の下に以下の構成を設定する：

    - TamperProtection (Device): **On**

> ![A screenshot of a computer Description automatically
> generated](./media/image6.png)

11. **Windows Defender Security Center**の下に以下の設定を構成する：

    - Disable Account Protection UI: **Enable**

    - Disable App Browser UI: **Enable**

    - Disable Device Security UI: **Enable**

    - Disable Family UI: **Enable**

    - Disable Health UI: **Enable**

> ![A screenshot of a computer Description automatically
> generated](./media/image7.png)

12. **Enable Customized Toastsの横にEnable**を選択する。

13. **Company nameフィールドにConfigured**を選択してから !!**[Contoso
    IT](urn:gd:lg:a:send-vm-keys)!!を入力する。**

14. **Phone**に対して**Configuredを選択してから** !!**[555-1234](urn:gd:lg:a:send-vm-keys)!!** を入力し、**Next**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)

15. **Scope tags**ページで**Next**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image9.png)

16. **Assignments**タブで**Included groups**の下に**Add
    groups**を選択する**。Contoso Developer
    Devices**グループを選択して**Select**をクリックし**、Next**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image10.png)

17. **Review + create**タブで情報を確認してから**Save**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)

タスク 2: IntuneでMicrosoft Defender Antivirusポリシーを構成する。

1.  **Endpoint security |Antivirus**ペインで**Create
    Policy**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image12.png)

2.  **Create a profileペインでPlatform**に対して**Windows 10, Windows
    11, and Windows Server**を選択する。

3.  **Profile** リストに、**Microsoft Defender
    Antivirus**を選択してから**Create**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image13.png)

4.  **Basics**タブで**Name**フィールドに!!**[Microsoft Defender
    Antivirus
    Settings](urn:gd:lg:a:send-vm-keys)!!**を入力してから**Next**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image14.png)

5.  **Configuration settings**タブで、以下の設定を構成する**：**

    - Allow Intrusion Prevention System: **Allowed**

    - Allow scanning of all downloaded files and
      attachments: **Allowed**

    - Allow Realtime Monitoring: **Allowed**

> ![](./media/image15.png)

- Check For Signatures Before Running Scan: **Enabled**

- Days to Retain Cleaned Malware: !!**[60](urn:gd:lg:a:send-vm-keys)!!**

> ![A screenshot of a computer Description automatically
> generated](./media/image16.png)

- Schedule Quick Scan
  Time: !!**[60](urn:gd:lg:a:send-vm-keys)!!** (represents 1:00AM)

> ![A screenshot of a computer Description automatically
> generated](./media/image17.png)

- Submit samples consent: **Send safe samples automatically**

> ![A screenshot of a computer Description automatically
> generated](./media/image18.png)

6.  **Configuration settings**タブで**Next**を選択する。

7.  **Scope tags**ページで**Next**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image19.png)

8.  **Assignments**タブで**Included groups**の下に**Add
    groups**を選択する。

9.  **Contoso Developer
    Devices**グループを選択を選択してから**Select**を選択し**、Next**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image20.png)

10. **Review + create**タブで情報を確認してから**Save**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image21.png)

タスク 3: 管理対象デバイスを同期する

1.  **Microsoft Intune admin center**内に**Devices**を選択してから**All
    devices**を選択する。

2.  **Devices | All
    devices**ペインに**SEA-WS1**を選択してから**SEA-WS1**ブレードで、ツールバーで**Sync**を選択してから**Yes**を選択する。

> ![](./media/image22.png)
>
> 同期が完了するまで 3 分から 4 分待ちます.

3.  Microsoft Edge.を閉じる。

タスク 4: 構成の確認

1.  [***SEA-CL1***](urn:gd:lg:a:select-vm)に切り替える。必要に応じて、!!**[Contoso\Administrator](urn:gd:lg:a:send-vm-keys)!!** としてサインインし、 !!**[Pa55w.rd](urn:gd:lg:a:send-vm-keys)!!**のパスワードを使用する。

2.   [***SEA-CL1***](urn:gd:lg:a:select-vm)で**Start**を選択して、!!**[Windows
    Security](urn:gd:lg:a:send-vm-keys)!!**を入力し、Windows
    Securityアイコンの下に**Open**を選択する。

> ![](./media/image23.png)
>
> すべてのセキュリティ・オプションが表示されています。これは、**SEA-CL1**
> が **Intune** に登録されていないためです。
>
> ![A screenshot of a computer security system Description automatically
> generated](./media/image24.png)

3.  **Windows
    Securityを閉じ、[*SEA-CL1*](urn:gd:lg:a:select-vm)**からサインアウトする。

4.   [***SEA-WS1***](urn:gd:lg:a:select-vm)に切り替えて、**!!Cindy@M365x27131290.onmicrosoft.com!!**
    としてサインインし、**!!P@55w.rd12345!!** パスワードを使用する。

5.  **Start**を選択して、!!**[Windows
    Security](urn:gd:lg:a:send-vm-keys)!!**　を入力し、Windows
    Securityアイコンの下に**Open**を選択する。

> ![](./media/image25.png)
>
> Intuneポリシーで設定されている制限領域がすべて表示されていないことに注意する。**SEA-WS1**はIntuneに登録されており、セキュリティ設定が適用されています。
>
> ![A screenshot of a computer Description automatically
> generated](./media/image26.png)

6.  **Windows
    Security**をクロースして、[***SEA-WS1***](urn:gd:lg:a:select-vm)からサインアウトする。

**結果: この手順を完了すると、Intune で管理対象デバイス用に Microsoft
Defender を構成するポリシーが正常に作成され、適用されます**.
