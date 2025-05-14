ラボ12 - Microsoft Intune を使用したクラウド アプリのデプロイ

**要約**

このラボでは、Intune とポータル サイト Web
サイトを使用してクラウドベースのアプリを作成およびデプロイします。

**前提 条件**

このラボの前に、次のラボを完了する必要があります:

- ラボ \#1 - Microsoft Entra ID での ID の管理

- ラボ \#2 - Microsoft Entra Connect を使用した ID の同期

- ラボ \#5 - Microsoft Intune へのデバイス登録の管理

- ラボ \#6 - Microsoft Intune へのデバイスの登録

- ラボ \#7 - 構成プロファイルの作成と展開

**注**:Microsoft Entra IDへのWindows
Helloサインイン認証を保護するために使用されるテキストメッセージを受信できる携帯電話も必要です.

手順 1: Microsoft IntuneにMicrosoft Store Appを追加する

**シナリオ**

Contoso Corporation のデスクトップとアプリを管理するために、Microsoft
Intune
を使用しています。研究部門では、タスクを実行するためにさまざまなサーバーに頻繁に接続するため、研究部門のメンバーが必要に応じて
Microsoft リモート デスクトップ
アプリをインストールできるようにしてほしいと依頼されています。Microsoft
リモート デスクトップは Microsoft Store
から入手できますが、ユーザーがCompany Portal
ウェブサイトからアクセスできるように、Intune
にアプリを追加することにしました。研究部門のメンバーである Aaron
Nicholls は、アプリをポータルに公開した後、インストール
プロセスをテストすることに同意しました

タスク 1: Microsoft IntuneにMicrosoft Remote Desktopを追加する

1.  必要に応じて[***SEA-SVR1***](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17)で[**Contoso\Administrator**](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17)としてサインインし、!\![**Pa55w.rd**](urn:gd:lg:a:select-vm)!!を使用して、**Server
    Manager**を閉じる。

2.  タスクバーで**Microsoft Edge**を選択する。

3.  Microsoft Edgeに、アドレスバーで、!!
    [**https://Intune.microsoft.com**](urn:gd:lg:a:select-vm) !!を入力して、**Enter**を押します。

4.  ホームタブからOffice 365 Tenant資格情報を使用してサインインする。

5.  **Microsoft Intune admin centerページでApps**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image1.png)

6.  On the **AppsページでナビゲーションペインにAll apps**を選択する。

7.  詳細のペインに**+Add**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)

8.  **Select app
    typeページでドロップダウンメニューをクリックして、Microsoft store
    app (new)**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)
>
> Microsoft store
> appに関しての情報を読んでから**Select**を選択する。**Add
> Appページが開きます。**

9.  **App information**ページで**Search the** **Microsoft Store app
    (new)** リンクをクリックする

> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

10. **Search the** **Microsoft Store app (new)**タブで!\![**Microsoft
    Remote
    Desktop**](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17)!!を検索して選択してからSelectボタンをクリックする。

> ![A screenshot of a computer Description automatically
> generated](./media/image5.png)

11. Add Appタブに戻り、以下の情報を入力して、**Next**を選択する。

    - Category: **Business**

    - Show this as a featured app in the Company Portal: **Yes**

> ![A screenshot of a computer Description automatically
> generated](./media/image6.png)

12. **Assignments**タブで**+ Add group**をクリックする**。**

> ![A screenshot of a computer Description automatically
> generated](./media/image7.png)

13. **Select groups**ページで**Research,
    Sales** グループを選択してから**Select**をクリックする。

> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)

14. **Next**ボタンをクリックする。

> ![A screenshot of a computer Description automatically
> generated](./media/image9.png)

15. Review + createタブで**Create**ボタンをクリックする。

> ![](./media/image10.png)

16. Microsoft Remote Desktopページが開きます。

> Properties, Device install status, and User install status
> nodesに注意する。
>
> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)

タスク 2: Microsoft Intuneコンソールからポリシーの同期を強制する。

1.  **Microsoft Intune admin centerに、Devicesを選択し、All
    devices**を選択する。

2.  詳細ペインに**SEA-WS1**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image12.png)

3.  **SEA-WS1**ブレードで**Sync**を選択し**、**求めたら**Yes**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image13.png)
>
> Microsoft
> Intuneがデバイスに接続して全てのポリシーを同期します。これには最大5分かかります。
> will contact the device and synchronize all policies. This may take up
> to 5 minutes.

タスク 3 Company Portal Websiteからアプリをインストール

1.  に、**Cindy
    Whiteとして資格情報**!!**Cindy@M365xXXXXXX.onmicrosoft.com**!!
    を使用してサインするために!!**P@55w.rd1234**!!またはPIN !!**102938**!!を使用する。

2.  タスクバーで**Microsoft Edge**を選択する。

3.  必要に応じて、**Welcome to Microsoft EdgeページにConfirm and
    continueを選択して**Welcomeページを閉じる。

4.  In the address bar browse
    toアドレスバーに !\![**https://portal.manage.microsoft.com**](urn:gd:lg:a:send-vm-keys)!!を参照

5.  する。

6.  !!**Cindy@M365xXXXXXX.onmicrosoft.com**!!としてサインインする。

> ![](./media/image14.png)

7.  Contosoウェブポータルで**Devices**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image15.png)

8.  デバイスページで**Tap here to tell us which device you're using or
    add a new device**を選択する。

> ![](./media/image16.png)

9.  **Which device are you
    using**ダイアログボックスで 、**SEA-WS1**の横にあるオプションを選択して**、Select**
    buttonをクリックする。

> ![A screenshot of a computer Description automatically
> generated](./media/image17.png)
>
> メセッジがApps will be installed onto: **SEA-WS1**に変わります。
>
> ![](./media/image18.png)

10. 左上の隅でナビゲーションボタンを選択してから**Downloads &
    updates**を選択する**。**

> ![A screenshot of a computer Description automatically
> generated](./media/image19.png)

11. リストされた結果の中状態をチェックし、**Microsoft Remote
    DesktopアプリがInstalled**として表示されるはずです。

> 注 - アプリが表示されるまでに最大 10 分から 20
> 分かかる場合があります。
>
> ![A screenshot of a computer Description automatically
> generated](./media/image20.png)

12. **Start** **Menuをクリックして、Remote Desktop** がStart
    menuの上に表示されていることを確認する。

> ![A screenshot of a computer Description automatically
> generated](./media/image21.png)

**結果**: この手順を完了すると、Microsoft Intune から Microsoft Store
アプリが正常に追加およびインストールされます.

手順 2: Microsoft IntuneからMicrosoft 365 Appsの構成とデプロイ

**シナリオ**

Contoso社の研究部門の全ユーザーにはMicrosoft
365アプリが必要です。Microsoft
Excel、Outlook、PowerPoint、Wordの64ビット版をWindowsデバイスに展開するよう依頼されています。また、更新のために最新チャネルが設定されていることを確認する必要があります。

タスク 1:　インストるされたアプリをSEA-WS1上に確認する。

1.  [***SEA-WS1***](urn:gd:lg:a:send-vm-keys)で、タスクバーで**Start**を選択して**Settings**アプリを選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image22.png)

2.  **Settings**アプリに**Apps**を選択してから**Apps &
    features**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image23.png)
>
> **Microsoft 365 Apps for enterprise -
> en-us**がリストされていないことを確認する。
>
> ![A screenshot of a computer Description automatically
> generated](./media/image24.png)

3.  全てのウィンドを閉じる。

タスク 2: Microsoft IntuneにMicrosoft 365アプリを追加

1.  [***SEA-SVR1***](urn:gd:lg:a:send-vm-keys)に切り替えて、**Microsoft
    Intune admin centerでApps**を選択する。

2.  **Apps | Overview**ブレードに**All
    Apps**を選択する。詳細ペインに**+Add**を追加する。

> ![A screenshot of a computer Description automatically
> generated](./media/image25.png)

3.  **Select app type**ブレードに**Microsoft 365 Apps**の下に**Windows
    10 and later**を選択してから**Select**をクリックする。

> ![A screenshot of a computer Description automatically
> generated](./media/image26.png)

4.  **Add Microsoft 365
    Apps**ブレードで次のオプションを構成して**Next**を選択する。

    - Suite Name: !\![**Microsoft 365 Apps
      (Research)**](urn:gd:lg:a:select-vm)!!

    - Suite Description: !\![**Microsoft 365 Apps for the Research
      department at Contoso**](urn:gd:lg:a:select-vm) !! (Select **Edit
      Description** to enter this information.)

> ![A screenshot of a computer Description automatically
> generated](./media/image27.png)

5.  **Configure app suite**タブで**Select Office
    apps**のドロップダウンを拡張してから次のOffice appsを選択する：

    - Excel

    - Outlook

    - PowerPoint

    - Word

> ![A screenshot of a computer Description automatically
> generated](./media/image28.png)

6.  **Configure app
    suite**タブで次のオプションを構成して**Next**を選択する:

    - Architecture: **64-bit**

    - Default file format: **Office Open XML Format**

    - Update channel: **Current Channel**

    - Accept the Microsoft Software License Terms on behalf of
      users: **Yes**

> ![A screenshot of a computer Description automatically
> generated](./media/image29.png)

7.  **Assignments**タブで**Required**のセクション内に**Add
    group**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image30.png)

8.  **Select
    groups**ブレードで**Research**を選択してから**Select**を選択する。

> ![A screenshot of a group Description automatically
> generated](./media/image31.png)

9.  **Next**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image32.png)

10. **Review + Create**タブで**Create**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image33.png)

11. **Microsoft 365 Apps (Research)**ページで**Properties**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image34.png)

12. 詳細のペインに**Assignments**セクション内に、**Required
    の下でResearch**がリストされていることを確認する**。**

> ![A screenshot of a computer Description automatically
> generated](./media/image35.png)

タスク 3: Microsoft Intuneコンソールからポリシーの同期を強制する

1.  **Microsoft Intune admin center**に**Devicesを選択して**から**All
    devices**を選択する。

2.  詳細ペインに**SEA-WS1**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image36.png)

3.  **SEA-WS1**ブレードで**Sync**を選択して**、**求めたら **Yes**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image37.png)
>
> Microsoft
> Intuneがデバイスに接続し、全てのポリシーを同期します。この処理は約5分かかる可能性があります。

タスク 4: Microsoft 365 appsがインストるされていることを確認する。

1.  既に[*SEA-WS1*](urn:gd:lg:a:send-vm-keys?rc=10)に**Cindy
    White**としてサインインされている場合

> **注** – Microsoft 365 Suite がデバイスにインストールされるまで、約 10
> 分から 15 分待つ必要がある場合があります.

2.  からサインアウトしてまた**Cindy
    White**として資格情報!!**Cindy@M365xXXXXXX.onmicrosoft.com**!!とパスワード!!**P@55w.rd1234**!!を使用してまたサインインする。

3.  [***SEA-WS1***](urn:gd:lg:a:send-vm-keys)で、タスクバーで**Startを選択してからSettingsアプリを選択する。**

> ![A screenshot of a computer Description automatically
> generated](./media/image38.png)

4.  **Settings**アプリに**Apps**を選択して**、Apps &
    features**ページを選択する**。**

> ![A screenshot of a computer Description automatically
> generated](./media/image23.png)

5.  !!**Microsoft 365**!! を検索して、**Microsoft 365 Apps for
    enterprise - en-us** がリストされていることを確認する。

> ![A screenshot of a computer Description automatically
> generated](./media/image39.png)

6.  **Settings**アプリを閉じて**、Start**ボタンそ選択する**。**

7.  **Recommended**セクションでは、Microsoft Intune の Microsoft 365
    アプリから選択された新しくインストールされたアプリが表示されるはずです。

> ![A screenshot of a computer Description automatically
> generated](./media/image40.png)

タスク 5: Microsoft Intune内にアプリのインストール状況の監視

1.  [***SEA-SVR1***](urn:gd:lg:a:select-vm)に切り替えて**Microsoft
    Intune admin center**に**Apps**を選択する。

> ![](./media/image41.png)

2.  **Apps | Overview**ブレードで **Monitor**を選択してから**App install
    status**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image42.png)

3.  詳細のペインに**Microsoft 365 Apps (Research)**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image43.png)

4.  詳細のペインに、**Device statusとUser
    status**の下にインストールで**1**が表示されていることを確認する。

> ![A screenshot of a computer Description automatically
> generated](./media/image44.png)
>
> **注:**
> これは、アプリが1台のデバイスに1人のユーザー向けにインストールされていることを示します。情報が表示されるまで時間がかかる場合があり、「**Install
> pending**」と表示されることがあります**。**
>
> **注意** – Lab 13を開始でき、30‐45分後またチェックできます。

![A screenshot of a computer Description automatically
generated](./media/image45.png)

5.   **Device install status**を選択する。

> 詳細ウィンドに、アプリがインストールされるデバイスと、ユーザ名も表示できます。**Device
> Name**  列には**SEA-WS1**  が表示され、**Status列に** **Installed**
> が表示されるはずです。この意味は、アプリが**SEA-WS1でインストールされたことです。**
>
> ![A screenshot of a computer Description automatically
> generated](./media/image46.png)

6.  In the **Microsoft Intune admin centerに、Devices**を選択する。

7.  **Devices | Overview**ブレードで **All
    devices**を選択して、詳細ペインに**SEA-WS1**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image47.png)

8.  **SEA-WS1**ブレードで**Managed Apps**を選択する。

9.  **SEA-WS1 | Managed Apps**ブレードで、詳細ウィンドに**Microsoft 365
    Apps (Research)**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image48.png)
>
> **Microsoft 365 Apps (Research) - Installation
> detailsウィンドにアプリケーションのライフサイクル全体を確認できます‐つまり、作成、割り当て、インストールの時間とステータス、およびデバイスが最後にチェックインした時刻(Microsoft
> Intuneと同期)を確認できます** 
>
> ![A screenshot of a computer Description automatically
> generated](./media/image49.png)

10. 開いているすべてのウィンドウを閉じる。

**結果**: この手順を完了すると、Microsoft IntuneからMicrosoft 365
Appsが正常に構成およびデプロイされます.
