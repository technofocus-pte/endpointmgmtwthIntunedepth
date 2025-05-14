# ラボ 4 - Microsoft Entra デバイスの登録を管理します。

**要約**

このラボでは、Windows デバイスを使用して Microsoft Entra
の登録を実行します。

**手順 1: Configuring Microsoft Entra device registration**

**シナリオ**

複数のユーザーから、個人のiOS、Android、Windowsデバイスを使用してContosoのクラウドリソースにアクセスしたいという要望がありました。Contosoはこれらのデバイスを所有していないため、ユーザーにデバイス管理の完全な実行を要求したくありません。代わりに、ユーザーがMicrosoft
Entraにデバイスを登録できるようにする必要があります。これにより、必要に応じてアプリに会社のポリシーを適用し、ユーザーがContosoのリソースにアクセスできるようになります。Windows
11デバイスを使用して、Microsoft Entraデバイスの登録をテストします。

**タスク 1: Azure AD デバイス登録を構成する**

1.  On the
    [*SEA-SVR1*](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)でEdgeブラウザに新しいタブを開き、次のURLを入力し
    て、!!**https://entra.microsoft.com**!! **Enter**ボタンを押す**。**

2.  O365テナントID
    でサインインし、!!**admin@M365xXXXXXXXX.onmicrosoft.com**!!
    テナントAdminパスワードを使用する。

> ![A screenshot of a computer Description automatically
> generated](./media/image1.png)
>
> ![A screenshot of a login box Description automatically
> generated](./media/image2.png)

3.  **Stay signed in?**ダイアログボックスで**Yes**ボタンを選択する**。**

> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)

4.  **Microsoft Entra admin
    centerウィンドにIdentity**に移動してクリックする。

![A screenshot of a computer Description automatically
generated](./media/image4.png)

5.  **Device**を選択してから**Device
    settings** ページに、詳細のペインで**Users may register their
    devices with Microsoft
    Entra**は**All**として設定しているし、グレー表示されることを確認する**。** 

> テナントでMicrosoft
> Intuneが有効になっている場合、このオプションはデフォルトでグレー表示され、「**All**」に設定されています。これにより、すべてのユーザーがWindows
> 10以降の個人用デバイス、iOS、Android、macOSデバイスをAzure
> ADに登録できるようになります。
>
> ![](./media/image5.png)

**タスク 2: Microsoft Entra 登録を実行する**

1.  [*SEA-WS1*](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)に切り替えて、 **Admin**としてサインインし**、**パスワードを !!**Pa55w.rd**!!使用する。

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image6.png)

2.  タスクバーで**Startを選択してからSettings**を選択する。

![A screenshot of a computer Description automatically
generated](./media/image7.png)

3.  **Settings**ウィンドに**Accounts**を選択する。

![A screenshot of a computer Description automatically
generated](./media/image8.png)

4.  **Accounts**ページに**Access work or school**を選択する。

![A screenshot of a computer Description automatically
generated](./media/image9.png)

5.  **Access work or school**ページで**Connect**を選択する。

![A screenshot of a computer Description automatically
generated](./media/image10.png)

6.  **Sign
    in**ページで[!!**JoniS@M365xXXXXXXX.onmicrosoft.com**](mailto:!!JoniS@M365xXXXXXXX.onmicrosoft.com)!!を入力して**Next**を選択する。

![](./media/image11.png)

7.  On the **Enter password**ページでテナントパスワード:
    !\![**P@55w.rd1234**](mailto:P@55w.rd1234)!! Aを入力して**Sign
    in**を選択する。

![A screenshot of a computer Description automatically
generated](./media/image12.png)

8.  **You're all set!**ページで**Done**を選択する。

![A screenshot of a computer Description automatically
generated](./media/image13.png)

9.  **Access work or school**ページでJoniの**Work or school
    account**が表示していることを確認する。

![A screenshot of a computer Description automatically
generated](./media/image14.png)

10. **Settingsページを閉じる。**

**タスク 3: Microsoft Entra 登録の検証**

1.  [*SEA-WS1*](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)で、**Start
    button**を右クリックし、**Windows Terminal (Admin)**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image15.png)

2.  **User Account ControlダイアログボックスでYes**を選択する。

> ![A screenshot of a computer error Description automatically
> generated](./media/image16.png)

3.  PowerShellコンソールに以下を入力してから**Enter**を押す：

> !!**dsregcmd /status**!!

4.  アウトプットに**User Stateの下に** verify that **WorkplaceJoined :
    YESが表示することを確認する。**これは、ユーザーがMicrosoft Entra
    にデバイスの登録を実行したことを示しています。

> ![A screenshot of a computer Description automatically
> generated](./media/image17.png)

5.  PowerShellを閉じて**SEA-WS1**からサインアウトする。

6.  SEA-SVR1に切り替える。**Microsoft Entra admin
    center**ウィンドに移動し、**Identity**に移動してからクリックする。

> ![A screenshot of a computer Description automatically
> generated](./media/image18.png)
>
> 7\.
> **Identity**セクションの下に**Devices**を選択して以下の画像で示したように**All
> devices**に移動してクリックする**。**
>
> ![A screenshot of a computer Description automatically
> generated](./media/image19.png)

8.  **Join Type**は **Microsoft Entra
    registered**として登録されていて**、**所有者は**Joni
    Sherman**であることを確認する。

> ![](./media/image20.png)
>
> デバイスはMicrosoft Entraに登録されており、Microsoft Entra
> joinしているわけではないことに注意する。Entraに登録されているデバイスは、通常、Entraにjoinできないデバイス、またはユーザーが個人所有するデバイスです。デバイスを登録すると、クラウドベースのリソースにアクセスできるようになります。

9.  Microsoft Edgeを閉じる。

**タスク 4: Windows にサインインして組織から切断する**

1.  [*SEA-WS1*](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)に切り替える。タスクバーで**Windows
    Start icon**ボタンを選択してから**Settings**を選択する。

![A screenshot of a computer Description automatically
generated](./media/image7.png)

2.  **Settings**ウィンドに**Accounts**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)

3.  **Accounts**ページで**Access work or school**を選択します。

> ![A screenshot of a computer Description automatically
> generated](./media/image9.png)

4.  **Access work or
    schoolページに** 、以下画像に示したよう、**JoniS@M3654xXXXXXXXX** **Work
    or school**アカウントの横にあるドロップダウンをクリックする。

> ![](./media/image21.png)

5.  **Disconnect**ボタンをクリックする**。**

> ![A screenshot of a computer Description automatically
> generated](./media/image22.png)

6.  「Yes**」**ボタンをクリックして、アカウントの削除を確認します。

> ![A screenshot of a computer Description automatically
> generated](./media/image23.png)
>
> 注：Microsoft Entra
> 登録済みデバイスを切断するために再起動する必要はありません。

7.  **SEA-WS1**からサインアウトする。

![A screenshot of a computer Description automatically
generated](./media/image24.png)

**結果**: この手順を完了すると、Microsoft Entra
デバイスの登録が構成されます。
