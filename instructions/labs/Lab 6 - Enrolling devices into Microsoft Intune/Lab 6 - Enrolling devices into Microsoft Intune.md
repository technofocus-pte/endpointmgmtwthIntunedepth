**ラボ 6 - Microsoft Intune へのデバイスの登録**

**要約**

このラボでは、Windows クライアントを Entra ID にjoinさせ、デバイスが
Microsoft Intune に自動的に登録されたことを確認します.

**前提 条件**

このラボの前に、次のラボを完了する必要があります。

1.  ラボ \#1 - Microsoft Entra ID での ID の管理

2.  ラボ \#2 - Microsoft Entra Connect を使用した ID の同期

3.  ラボ \#5 - Microsoft Intune へのデバイス登録の管理

注: Entra ID への Windows Hello
サインイン認証を保護するために使用されるテキスト
メッセージを受信できる携帯電話も必要になる場合があります。

**シナリオ**

Cindy White に適切なライセンスを割り当てたので、次に Windows デバイスを
Entra ID に参加joinさせ、Microsoft Intune
に自動的に登録するプロセスをテストします.

**タスク 1: Windows デバイスを Microsoft Intune に自動的に登録する**

1.  [*SEA-WS1*](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)に切り替え、**Adminとしてサインインするために**パスワード!!**Pa55w.rd**!!を使用する。

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image1.png)

2.  タスクバーで**Start**を選択してから**Settings**を選択する。

![A screenshot of a computer Description automatically
generated](./media/image2.png)

3.  **Settings**ウィンドに**Accounts**を選択する**。**

![A screenshot of a computer Description automatically
generated](./media/image3.png)

4.  Accountsページで**Access work or school**を選択する。

![A screenshot of a computer Description automatically
generated](./media/image4.png)

5.  **Access work or school**ページで**Connect**を選択する。

![A screenshot of a computer Description automatically
generated](./media/image5.png)

6.  **Microsoft account**ウィンドに**Join this device to Microsoft Entra
    ID**を選択する。

![](./media/image6.png)

7.  **Sign
    in**ページで、type !\![**Cindy@M365x51282399.onmicrosoft.com**](mailto:Cindy@M365x51282399.onmicrosoft.com)!!を入力して**Next**を選択する。

![](./media/image7.png)

8.  **Enter
    password**ページでパスワード!\![**P@55w.rd1234**](mailto:!!P@55w.rd1234)!!
    を入力してから**Sign in**を選択する。

![A screenshot of a computer Description automatically
generated](./media/image8.png)

9.  **Make sure this is your
    organization**ダイアログボックスが表示してから**Join**を選択する。

![](./media/image9.png)

10. **You're all set!**ページで情報を読んでから**、Done**を選択する。

![A screenshot of a computer Description automatically
generated](./media/image10.png)

11. **Access work or school**セクションの中に**Connected to Contoso's
    Azure AD**が表示することを確認する。

12. **Connected to Contoso's Azure AD**を選択して**、Info**を選択する。

![A screenshot of a computer Description automatically
generated](./media/image11.png)

13. Contoso
    が管理する領域に関する情報をメモし、下にスクロールして「**Sync**」を選択します。これにより、デバイスが
    Intune と強制的に同期されます。

![A screenshot of a computer Description automatically
generated](./media/image12.png)

14. **Settings**ウィンドを閉じる**。**

**タスク 2: Microsoft Entra と Intune へのデバイス登録の検証**

1.  **SEA-WS1** タスクバーで**Start**を選択して、!!**certlm.msc**!!を入力し、**Enter**を押します。

![A screenshot of a computer Description automatically
generated](./media/image13.png)

2.  User Account Controlダイアログボックスで**Yes**ボタンを選択する。

![](./media/image14.png)

3.  **Certificates**コンソールに**、**ナビゲーションウィンドウで**Personal**を拡張して、**Certificate**ノードを選択する**。**以下の証明書が詳細ペインにリストされていることを確認する：

- Microsoft Intune MDM Device CA

- MS-Organization-Access

- MS-Organization-P2P-Access \[2024\]

これは、デバイスがMicrosoft Entra and Intuneに登録されていることを示す。

![](./media/image15.png)

4.  証明書ウィンドを閉じる。

5.  **Start**ボタンを右クリックし**、Windows Terminal
    (Admin)**を選択する。

![A screenshot of a computer Description automatically
generated](./media/image16.png)

6.  **User Account
    Control**ダイアログボックスで**Yes**ボタンをクリックする**。**![A
    screenshot of a computer error Description automatically
    generated](./media/image17.png)

7.  PowerShellコンソールに以下を入力して**Enter**を選択する：

!!**dsregcmd /status**!!

8.  アウトプットに、**Device State**の下に**AzureAdJoined :
    YES**が表示されることを確認する**。** これは、デバイスがAzure AD
    joinedであることを示しています。

![A screenshot of a computer Description automatically
generated](./media/image18.png)

9.  アウトプットに、**Tenant
    Details**の下に、次の三つのエントリが存在することを確認する：

- mdmUrl:https://enrollment.manage.microsoft.com/enrollmentserver/discovery.svc

- mdmTouUrl:https://portal.manage.microsoft.com/TermsofUse.aspxmdm

- ComplianceUrl:https://portal.manage.microsoft.com/?portalAction=Compliance

![](./media/image19.png)

*注:
これらのエントリは、デバイスがIntuneに登録されていることを示します。*

**タスク 3: Microsoft Entra ID ユーザーとしてサインインする**

1.  ローカル管理者アカウントでログインしているので、SEA-WS1からサインアウトします。

2.  サインイン画面でOther
    userを選択して!!**Cindy@M365xXXXXXXX.onmicrosoft.com**!!
    としてサインインするために!\![**P@55w.rd1234**](mailto:P@55w.rd1234)!!パスワードを使用する。

![](./media/image20.png)

1.  プロファイルが作成されるのを待ちます

![A screenshot of a computer Description automatically
generated](./media/image21.png)

**注 –** Windows Hello の入力を求められた場合は、それに応じてサインイン
プロセスを完了し、\[**Set up a PIN**\] ページの \[**New PIN\]**
ボックスと **\[Confirm PIN**\] ボックスに「!!**102938**!!
次に、\[**OK\]** を選択します.

![A screenshot of a computer Description automatically
generated](./media/image22.png)

3.  **SEA-WS1**からサインアウトする。

**タスク 4: Microsoft Intune コンソールでのデバイス登録の確認**

1.  Switch
    to [*SEA-SVR1*](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)に切り替え、提供される資格情報をを使用してログインする

2.  In Microsoft
    Edgeブラウザにアドレスバーに!!**https://intune.microsoft.com**!!を入力し、**Enter**を押します**。**Office
    365 Tenant管理者アカウントを使用してサインインする。

3.  ナビゲーションウィンドウに**Devices**を選択する。

![A screenshot of a computer Description automatically
generated](./media/image23.png)

4.  **Devices | Overview**ページで、移動して**Windows**をクリックする。

![](./media/image24.png)

5.  **Windows
    devices**に移動して、クリックする**。SEA-WS1**がリストされることを確認する。

SEA-WS1 の場合、\[**Managed\] 列には** \[**Intune\]
と**表示され**、\[Ownership**\] 列には **\[Corporate\]**
と表示されます。

![A screenshot of a computer Description automatically
generated](./media/image25.png)

**注:** このビューには、Intune
に登録されているデバイスが一覧表示されます。Microsoft Entra と Microsoft
Intune の自動登録を設定したことを注意する。そのため、Microsoft Entra
にjoinまたは登録されているデバイスは、Microsoft Intune
にも自動的に登録されます。登録設定前にjoinしていたデバイスは、Entra
に参加または登録されているだけで、Intune には登録されていません。

6.  Open a new tab and navigate to 新しいタブを開き、**Microsoft Entra
    admin center**へ移動するする
    !!**https://entra.microsoft.com**!!.。**Devices**クリックして**、All
    devices**を選択する。

![A screenshot of a computer Description automatically
generated](./media/image26.png)

1.  SEA-WS1に注意する。**\[Join type**\] 列には \[**Microsoft Entra
    joined**\] と表示され、\[**MDM**\] 列には \[**Microsoft Intune**\]
    と表示されます。

![A screenshot of a computer Description automatically
generated](./media/image27.png)

**結果**: この演習を完了すると、Windows クライアントが Microsoft Entra
ID に正常にjoinし、デバイスが Microsoft Intune
に自動的に登録されたことを確認できます。
