**ラボ 11 - Intune でデバイスとユーザーのアクティビティを監視する**

**要約**

このラボでは、ユーザーのサインイン アクティビティ、監査ログ、デバイス
アクティビティを監視します。

**前提 条件**

このラボの前に、以下のラボを完了する必要があります。

1.  ラボ \#1 - Microsoft Entra ID での ID の管理

2.  ラボ \#2 - Microsoft Entra Connect を使用した ID の同期

3.  ラボ \#5 - Microsoft Intune へのデバイス登録の管理

4.  ラボ \#6 - Microsoft Intune へのデバイスの登録

5.  ラボ \#7 - 構成プロファイルの作成と展開

**注**:Microsoft Entra IDへのWindows
Helloサインイン認証を保護するために使用されるテキストメッセージを受信できる携帯電話も必要です。

**シナリオ**

Cindy White のサインイン
アクティビティと、監査ログによって提供される一般情報を確認する必要があります。また、[*SEA-WS1*](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)
のハードウェアを確認し、このデバイスに割り当てられた設定プロファイルが正常に適用されていることを確認する必要があります。

**タスク 1: ユーザーアクティビティの監視**

1.  [*SEA-SVR1*](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)に切り替えて、必要に応じて提供された資格情報でログインする

2.  **Microsoft Entra admin
    center**ページで**Users**へ移動し、選択してから**All
    users**をクリックする。

> ![](./media/image1.png)

3.  **UsersページでAllan Deyoung**へ移動し、選択する。

> ![](./media/image2.png)

4.  In the **Allan Deyoungユーザーページで、Sign-in
    logs**へ移動し、クリックする。

> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)

5.  In **Allan Deyoung | Sign-in logsページにUser sign-ins
    (interactive)タブの最初のエントリをクリックする。**

> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

1.  **Basic info**, **Location**, **Device info**, **Authentication
    Details**, and **Conditional
    Access**など各メインページを選択する**。**下にスクロールして、各ページの情報を調べます。各ページに記載されている情報を慎重に確認した後、ウィンドウを閉じます。

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

6.  ユーザーのナビゲーションウィンドウに**Audit logs**を選択する。

7.  詳細ペインには、ユーザーに対する管理上の変更に関する監査情報が表示されます。各エントリを選択して情報を確認してください。

> ![A screenshot of a computer Description automatically
> generated](./media/image10.png)
>
> ![](./media/image11.png)

**タスク 2: デバイスのアクティビティを監視する**

1.  **Microsoft Intune admin
    centerウィンドに切り替えて、Devices**へ移動してクリックする。

![](./media/image12.png)

2.  デバイスのナビゲーションウィンドに**Overview**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image13.png)

3.  下にスクロールして以下を確認する：

- Configuration policy assignment failures

- Noncompliant devices.

- Deployment status per Windows update ring.

> ![](./media/image14.png)

4.  **Manage
    devices**セクションにスクロールダウンして**Configuration**にクリックする。Configurationの詳細を確認する。

> ![](./media/image15.png)

5.  上にスクロールして**All devices**を選択する。**Devices | All
    devices** ページにDevice name, Managed by, Ownership, Compliance,
    OS, and OS
    versionのようデバイスの情報が表示されています。**SEA-WS1**をクリックする。

> ![](./media/image16.png)

6.  SEA-WS1ナビゲーションペインに、**Hardware**を選択してハードウェアのインベントリを検査する**。** 

> ![A screenshot of a computer Description automatically
> generated](./media/image17.png)

7.  SEA-WS1ペインに **Discovered
    apps**を選択して、アプリのインベントリを検査する。

> ![A screenshot of a computer Description automatically
> generated](./media/image18.png)

8.  SEA-WS1のナビゲーションペインで「**Device
    configuration**」を選択し、詳細ペインでデバイスに割り当てられたDevice
    configurationプロファイルを確認します。「**State**」列に「**Succeeded**」​​と表示されている場合は、プロファイルがデバイスに正常に適用されたことを示してします。

> ![](./media/image19.png)

9.  **SEA-WS1 | Device configurationページにContoso Developer –
    standard**をクリックする。

> ![](./media/image20.png)

10. **Contoso Developer –
    standardブレードでプロファイルに構成した核設定を確認する。**

**Stateではそれらすべての横にSucceededを表示されるはずです。**

> ![](./media/image21.png)

**結果:**
この手順を完了すると、ユーザーのサインインアクティビティ、監査ログ、デバイスアクティビティを正常に監視できるようになりました。
