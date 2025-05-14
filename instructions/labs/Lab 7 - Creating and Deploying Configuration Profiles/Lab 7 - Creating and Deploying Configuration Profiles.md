**ラボ 7 - 構成プロファイルの作成と展開**

**要約**

このラボでは、Microsoft Intune を使用して、Windows 11
デバイスの構成プロファイルを作成して適用します。

**前提 条件**

このラボの前に、次のラボを完了する必要があります:

1.  ラボ \#1 - Microsoft Entra ID での ID の管理

2.  ラボ \#2 - Microsoft Entra Connect を使用した ID の同期

3.  ラボ \#5 - Microsoft Intune へのデバイス登録の管理

- ラボ \#6 - Microsoft Intune へのデバイスの登録

注:Microsoft Entra IDへのWindows
Helloサインイン認証を保護するために使用されるテキストメッセージを受信できる携帯電話も必要です。

**手順 1: 構成プロファイルを作成して適用する**

**シナリオ**

Contoso の開発部門のメンバーを管理するために、Microsoft Entra と
Microsoft Intune を使用する必要があります。Windows 11
デバイスでユーザーが効率的かつ安全に作業できるようにするソリューションを評価するよう依頼されました。Cindy
White
は、ソリューションのテストと評価、そしてフィードバックの提供を手伝ってくれると申し出てくれました。また、開発者の
Windows
デバイスに適用する必要がある初期要件もいくつか提示してくれました：

1.  \[設定\]の\[ゲーム\]セクションは表示されないようにする必要があります。

2.  \[設定\]の\[プライバシー\]セクションは、可能な限り制限する必要があります。

3.  **C:\DevProjects** フォルダーは、Windows Defender
    から除外する必要があります。

4.  devbuild.exeプロセスは、Windows Defender
    から除外する必要があります。

5.  Most used appsとRecently added apsは、\[スタート\]メニューに表示

**タスク 1: デバイスの設定を確認する**

1.  Cindy White
    の資格情報!!**Cindy@M365xXXXXXX.onmicrosoft.com**!!と、PIN !!**102938**!!又は!!**P@55w.rd1234**!!を使用して
    SEA-WS1 にサインインします。

![A screenshot of a computer Description automatically
generated](./media/image1.png)

2.  タスクバーで**Startを選択してからSettings**を選択する。

![A screenshot of a computer Description automatically
generated](./media/image2.png)

3.  **Settings**のナビゲーションリストで**、Gaming**の設定を表示できることを確認する。

![A screenshot of a computer Description automatically
generated](./media/image3.png)

4.  **Personalization設定を選択して**Personalizationページで**Start**を選択する。**Show
    recently added apps**と**Show most used apps**の設定は、メモする。

![](./media/image4.png)

![A screenshot of a computer Description automatically
generated](./media/image5.png)

5.  **Settings**アプリで**Privacy & security**を選択する。

6.  **Privacy & security**ページで **Security**, **Windows
    permissions**、と**App permissions**下のオプションのメモをとる。

![A screenshot of a computer Description automatically
generated](./media/image6.png)

7.  **Privacy & security**ページで**Windows
    Security**を選択してから**Open Windows Security**を選択する。

![](./media/image7.png)

![A screenshot of a computer security Description automatically
generated](./media/image8.png)

8.  **Windows Security**ページで**Virus & threat
    protection**を選択する。

9.  **Virus & threat protection**ページ**、Virus & threat**の下に**、
    protection settings**を選択して、**Manage settings**を選択する。

![A screenshot of a computer Description automatically
generated](./media/image9.png)

10. **Exclusions**にスクロールダウンして**、Add or remove
    exclusions**を選択する。User Account
    Controlダイアログボックスで**Yes**を選択する。

![A screenshot of a computer Description automatically
generated](./media/image10.png)

![A screenshot of a computer Description automatically
generated](./media/image11.png)

11. **Exclusions**ページで除外が設定されないことを確認する。 

12. **Windows Security**ウィンドを閉じる。

![A screenshot of a computer Description automatically
generated](./media/image12.png)

13. **Settings** ウィンドを閉じる。

**タスク 2: シナリオの要件に基づく構成プロファイルの作成**

1.  [*SEA-SVR1*](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)に切り替える。

2.  **Microsoft
    Intune**管理センターを開いた状態でタブに戻り**、ナビゲーション
    バーから** \[**Device**\] を選択します。

![A screenshot of a computer Description automatically
generated](./media/image13.png)

3.  **Devices |
    Overview**ページで以下の画像で示すよう、 **Windows**を選択する。

![A screenshot of a computer Description automatically
generated](./media/image14.png)

4.  **Windows | Windows devices**ページで**Configuration
    profiles**に移動してクリックする。

![A screenshot of a computer Description automatically
generated](./media/image15.png)

5.  **Windows | Configuration profilesページでPolicies**タブに**+
    Create**をクリックして**+ New Policy**を選択する。

![A screenshot of a computer Description automatically
generated](./media/image16.png)

6.  右側に表示する**Create a
    profile**ペインに、以下のオプションを選択してから**Create**を選択する：

- Platform: **Windows 10 and later**

- Profile type: **Templates**

- Template name: !!!!

![A screenshot of a profile Description automatically
generated](./media/image17.png)

7.  In
    the **Basics**ブレードに以下の詳細を入力して**、Next**を選択する。

- Name: !!Contoso Developer - standard!!

- Description: !!Basic restrictions and configuration for Contoso
  Developers.!!

![](./media/image18.png)

8.  **Configurations settings**ブレードで**Control Panel and
    Settings**を拡張する。

![A screenshot of a computer Description automatically
generated](./media/image19.png)

9.  **Gaming**と**Privacy**のオプションの横にある**Block**を選択する**。**

![A screenshot of a computer Description automatically
generated](./media/image20.png)

10. **Device restrictions**ブレードで**Start**を拡張する。

![A screenshot of a computer Description automatically
generated](./media/image21.png)

11. スクロールダウンして、**Most used apps**, **Recently added
    apps** と**Recently opened items in Jump
    Lists**の横にある**Block**を選択する**。**

![A screenshot of a computer Description automatically
generated](./media/image22.png)

12. **Device restrictions**ブレードで、スクロールダウンして**Microsoft
    Defender Antivirus**を拡張する。

![A screenshot of a computer Description automatically
generated](./media/image23.png)

13.  **Microsoft Defender
    Antivirus**の下に、スクロールダウンして**Microsoft Defender
    Antivirus Exclusions**を拡張する。

![](./media/image24.png)

14.  **Microsoft Defender Antivirus
    Exclusions**の下に、以下の詳細を入力して **Next**ボタンをクリックする。

- Files and folders box - !!**C:\DevProjects**!!

- Processes box - !!**DevBuild.exe**!!

![](./media/image25.png)

15. **Assignments**タブに**Next**ボタンをクリックする。

![A screenshot of a computer Description automatically
generated](./media/image26.png)

16. **Applicability Rules**タブに**Next**ボタンをクリックする。

![A screenshot of a computer Description automatically
generated](./media/image27.png)

17. **Review + create**タブに**Create**ボタンをクリックする**。**

![A screenshot of a computer Description automatically
generated](./media/image28.png)

18. これで、Configuration profileがリスト化するはずです。

![A screenshot of a computer Description automatically
generated](./media/image29.png)

**タスク 3: Contoso Developer デバイス グループを作成する**

1.  Microsoft Intune admin
    centerに、ナビゲーションウィンドウで、**Groups**を選択する。

![A screenshot of a computer Description automatically
generated](./media/image30.png)

2.  **Groups | All groupsブレードでNew group**を選択する。

![A screenshot of a computer Description automatically
generated](./media/image31.png)

3.  **New Groupブレードで**以下の情報を入力する。

- Group type: **Security**

- Group name: !!Contoso Developer devices!!

- Group description: !!All Windows devices in Contoso Developer
  department!!

- Membership type: **Assigned**

4.  **Members**の下に**No members selected**を選択する。

![](./media/image32.png)

5.  **Add
    members**ブレードで**Search**ボックスに!!Sea!!を入力する。**SEA-WS1**を選択してから**Select**を選択する。

![A screenshot of a computer Description automatically
generated](./media/image33.png)

6.  **New GroupブレードでCreate**を選択する。

![](./media/image34.png)

7.  **Groups | All groups**ブレードで**Contoso developer
    devices**グループが表示されていることを確認する**。**

![](./media/image35.png)

**タスク 4: Dynamic Azure AD デバイス グループを作成する**

1.  **Groups | All Groups**ブレードで詳細のペインに **New
    group**を選択する。

![A screenshot of a computer Description automatically
generated](./media/image36.png)

2.  **Group**ブレードで以下の値を提供する：

- Group type: **Security**

- Group name: !!Windows Devices!!

- Membership type: **Dynamic Device**

3.  **Dynamic Device Members**セクションの下に**Add dynamic
    query**を選択する。

![A screenshot of a computer Description automatically
generated](./media/image37.png)

4.  **Dynamic membership rules**ブレードで**Rule
    syntax**の中に**Edit**を選択する。

![A screenshot of a computer Description automatically
generated](./media/image38.png)

5.  In the **Edit rule
    syntaxテキストボックスに、次の単純なメンバーシップルールを追加し、OK**を選択する。

!!**(device.deviceOSType -contains "Windows")**!!

![A screenshot of a computer Description automatically
generated](./media/image39.png)

6.  **Dynamic membership rules**ブレードで**Save**を選択する。

![A screenshot of a computer Description automatically
generated](./media/image40.png)

7.  **New Group**ページで**Create**を選択する。

![A screenshot of a computer Description automatically
generated](./media/image41.png)

**タスク 5: Windows デバイスへに構成プロファイルの割り当て**

1.  **Microsoft Intune admin
    center**ページで**、**ナビゲーションバーから**Devicesを選択する。** 

![](./media/image42.png)

2.  **Devices |
    Overview**ページで以下の画像に示すよう**Windows**を選択する**。**

![](./media/image43.png)

3.  **Windows | Windows devicesページでConfiguration
    profiles**に移動して、クリックする。

![](./media/image44.png)

4.  **Devices | Configuration
    profiles**ブレードで、詳細のペインに**Contoso Developer –
    standard**プロファイルを選択する**。**

![A screenshot of a computer Description automatically
generated](./media/image45.png)

5.  **Contoso Developer –
    standardブレードで、Assignments**セクションにスクロールダウンして**Edit**を選択する。

![A screenshot of a computer Description automatically
generated](./media/image46.png)

6.  Assignmentsページで、**Included groups**の下に**Add
    groups**を選択する。

![A screenshot of a computer Description automatically
generated](./media/image47.png)

7.  **Select groups to
    include**ブレードで**、Search**ボックスの中に!!**Contoso Developer
    devices**!!を入力して選択してから、**Select**ボタンをクリックする。

![](./media/image48.png)

14. **Device restrictions**ブレードに戻り**、Review +
    save**を選択してから**Save**を選択する。

![A screenshot of a computer Description automatically
generated](./media/image49.png)

![](./media/image50.png)

**タスク 6: 構成プロファイルが適用されていることを確認します**

1.  [*SEA-WS1*](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)に切り替える。Cindy
    Whiteのアカウントを使用してログインする。

- Username - !!**Cindy@M365xXXXXXXX.onmicrosoft.com**!!

- Password – !!**P@55w.rd1234**!!

2.  タスクバーで**Start**を選択してから**Settings**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)

3.  **Settings**ウィンドに**Accounts**を選択する**。**アカウントページで**Access
    work or school**を選択する。

![A screenshot of a computer Description automatically
generated](./media/image51.png)

4.  **Connected to Contoso’s Azure
    AD**の横のドロップダウンをクリックして、**Info**ボタンを選択する。

![](./media/image52.png)

5.  In the **Managed by Contosoページにスクロールダウンしてから**Device
    sync statusの下に**Sync**を選択する。 同期が完了するまで待ちます。

6.  ![A screenshot of a computer Description automatically
    generated](./media/image53.png)

![A screenshot of a computer Description automatically
generated](./media/image54.png)

7.  **Settings**アプリを閉じる。

> **注:** プロファイルがWindows
> 11デバイスに適用されるまで、同期には最大15分かかる場合があります。デバイスをサインアウトする又は再起動すると、このプロセスが高速化されます。

1.  On [*SEA-WS1*](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)で、**Startをまた選択してからSettings**を選択する。ゲーム**設定が削除され**ていることを確認します。

![A screenshot of a computer Description automatically
generated](./media/image2.png)

![A screenshot of a computer Description automatically
generated](./media/image55.png)

1.  「**Privacy and security」を選択すると**
    、多くのプライバシー設定が非表示になっていることがわかります。

![](./media/image56.png)

8.  **Personalization**選択してから**Start**を選択する。**Show recently
    added apps** と **Show most used
    apps** は**Offと設定され、**グレー表示することを確認する。

![](./media/image57.png)

![A screenshot of a computer Description automatically
generated](./media/image58.png)

9.  **Settings**アプリで**Privacy and Security**を選択する。

10. On the **Privacy & Security**ページで**Windows
    Security**を選択してから**Open Windows Security**を選択する。

![](./media/image59.png)

![A screenshot of a computer security Description automatically
generated](./media/image60.png)

11. **Windows Security** ページで**Virus & threat
    protection**を選択する。

12. **Virus & threat protectionページで**under **Virus & threat
    protection settings**の下にある**Manage settings** を選択する。![A
    screenshot of a computer Description automatically
    generated](./media/image9.png)

13. **ExclusionsへスクロールダウンしてAdd or remove
    exclusionsを選択する。**User Account
    Controlメセッジで**Yesを選択する。**

![A screenshot of a computer Description automatically
generated](./media/image61.png)

![A screenshot of a computer Description automatically
generated](./media/image62.png)

14. **Exclusions**ページで**C:\DevProjects** and **DevBuild.exe**が表示されることを確認する。

![A screenshot of a computer Description automatically
generated](./media/image63.png)

15. **Windows
    Security**ページを閉じてから**Settings**アプリを閉じる**。**

**結果**: この手順を完了すると、Windows 11
デバイスの構成プロファイルが正常に作成され、割り当てられます.

**手順 2: 割り当てられた構成プロファイル・ポリシーを変更します。**

**シナリオ**

Contoso社のポリシーには、開発部門のメンバーがデバイスの設定でプライバシーオプションをブロックしてはならないという例外がありました。この変更は実装およびテストする必要があります。

**タスク 1: 割り当てられた構成プロファイルの設定を変更する**

1.  **SEA-SVR1**に切り替える**。**また**Microsoft Intune admin
    center**タブに戻る。ナビゲーションバーで**Devices**を選択する**。**

![](./media/image42.png)

2.  **Devices |
    Overview**ページで以下の画像で示すよう**Windows**を選択する。

![](./media/image43.png)

3.  **Windows | Windows devices**ページで**Configuration
    profiles**に移動してクリックする。

![](./media/image44.png)

4.  **Devices | Configuration
    profiles**ブレードで、詳細のペインに**Contoso Developer –
    standard**を選択する。

![](./media/image64.png)

5.  **Contoso Developer – standard**ブレードで、**Configuration
    settings**セクションへスクロールダウンしてから**Edit**を選択する。

![A screenshot of a computer Description automatically
generated](./media/image65.png)

6.  **Device restrictions**ページで**Control Panel and
    Settings**を拡張する。

![A screenshot of a computer Description automatically
generated](./media/image66.png)

7.  **Privacy**,の横に、**Not
    configured**が選択されていることを確認する**。**

![A screenshot of a computer Description automatically
generated](./media/image67.png)

8.  **Review + save**を選択して、**Save**を選択する。

![](./media/image68.png)

**タスク 2: Microsoft Intune管理センターからデバイス同期を強制する**

1.  [*SEA-SVR1*](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)で、**Microsoft
    Intune admin
    centerに、**ナビゲーションウィンドウで**Devices**を選択して**、All
    devices**と**SEA-WS1**を選択する。

![A screenshot of a computer Description automatically
generated](./media/image69.png)

2.  **SEA-WS1**ブレードで**Sync**を選択して、求めたら**Yes**を選択する。

![](./media/image70.png)

**注**: Intune
はデバイスを接続し、すべてのポリシーを同期します。これには最大5分かかる場合があります。

**タスク 3:
[*SEA-WS1*](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)上での変更を確認する**

1.  [*SEA-WS1*](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)に切り替えるタスクバーで**Start**を選択して**Settings**を選択する。

![A screenshot of a computer Description automatically
generated](./media/image2.png)

2.  **Settings**アプリに**Privacy &
    security**を選択して、全てのカスタマイズオプションが戻ったことを確認する。

![A screenshot of a computer Description automatically
generated](./media/image71.png)

3.  開いているすべてのウィンドウを閉じ、**SEA-WS1
    からサインアウトします**.

**結果:**
この手順を完了すると、構成プロファイルの変更と割り当て、変更の確認が正常に完了します。
