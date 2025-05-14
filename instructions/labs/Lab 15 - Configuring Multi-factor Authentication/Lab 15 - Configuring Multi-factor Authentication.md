ラボ 15 - 多要素認証の構成

**要約**

このラボでは、ユーザーごとの多要素認証 (MFA) を構成し、条件付きアクセス
ポリシーを使用して MFA を適用します.

手順 1: ユーザーごとの多要素認証を構成します。

**シナリオ**

ユーザーサインオンイベントのセキュリティを強化するには、多要素認証(MFA)を設定してテストする必要があります。最初にユーザーごとの
MFA をテストすることにしました。Alex Wilber
は、設定の検証に同意しました.

タスク 1: MFA を有効にする前にサインインを検証する

1.  [**SEA-WS3**](urn:gd:lg:a:select-vm)に切り替えて  !\![**Admin**](urn:gd:lg:a:send-vm-keys)!!
    としてサインインし、!\![**Pa55w.rd**](urn:gd:lg:a:send-vm-keys)!!パスワードを使用する。

2.  タスクバーで**Microsoft
    Edge**を選択する。アドレスバーに!\![**outlook.office.com**](urn:gd:lg:a:send-vm-keys)!!
    を入力してEnterを押します。

3.  **Sign**
    [**inページに**!!**AlexW@M365xXXXXXXX.onmicrosoft.com**](mailto:inページに!!AlexW@M365xXXXXXXX.onmicrosoft.com)!!を入力して**Next**を選択する。

4.   **Enter passwordページで**!!**P@55w.rd1234**!! を入力して**Sign
    in**を選択する。Edgeの Save passwordプロンプトで**Save**を選択する。

> **Outlook on the Web** が開きます。**Outlook on the
> Web**にサインインするために必要なのはパスワードのみであることに注意する。

5.  右上隅で**Account manager for Alex Wilberを選択して**、**Sign
    out**を選択する。

> ![](./media/image1.png)

6.  Microsoft Edgeを閉じる

タスク 2: ユーザーの MFA を有効にする

1.  [**SEA-SVR1**](urn:gd:lg:a:select-vm)に切り替える。[**SEA-SVR1**](urn:gd:lg:a:select-vm)で、必要に応じて、[**Contoso\Administrator**](urn:gd:lg:a:send-vm-keys)としてサインインし、!!
    [**Pa55w.rd**](urn:gd:lg:a:send-vm-keys)!!
    パスワードを使用して、**Server Manager**を閉じる。

2.  タスクバーで**Microsoft Edge**を選択して、**Microsoft Entra admin
    center** !!**https://Entra.Microsoft.com**!!に移動する。

3.  **Office 365 Tenant admin**の資格情報を使用してサインインする**。**

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)
>
> **Microsoft Entra admin centerが開きます。**

4.  **Microsoft Entra admin
    centerに、**ナビゲーションウィンドウに**Identity**を拡張してから**Users**を選択する。

5.  **All usersを選択して、結果ペインの上にPer-user
    MFA**を選択する。**Per-user MFA** 
    オプションを表示するためには最初に三つのドットを選択する必要です。

> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)

6.  multi-factor authenticationページで**service settings**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

7.  **Verification optionsセクションにスクロールダウンする。**

> ユーザー検証用に構成できるさまざまな方法に注意する。

8.  **Remember multi-factor authentication on trusted
    deviceセクションに** **Allow users to remember multi-factor
    authentication on devices they
    trust**横のチェックボックスをオンにする。

9.  **Number of days users can trust devices
    forの横に30を入力してからsave**を選択する。求めたら**close**を選択する。

> ![](./media/image5.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image6.png)

10. ページの上で、**multi-factor
    authentication**の下に**users**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image7.png)

11. ユーザリストに、**Alex Wilber**の横のチェックボックスをオンにする。

12. Alex Wilberページに、**Enable**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)

13. **About enabling multi-factor auth**メセッジで**enable multi-factor
    auth**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image9.png)

14. **Updates successful**メセッジで**、close**を選択する。Alex Wilberの
    **Multi-Factor Auth Status** は今**Enabled**であることを注意する。

> ![A screenshot of a computer Description automatically
> generated](./media/image10.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)

15. Microsoft Edgeを閉じる

タスク 3: MFA の登録と検証

1.  [**SEA-WS3**](urn:gd:lg:a:select-vm)に切り替える。タスクバーで**Microsoft
    Edge**を選択する。

2.  アドレスバーに !\![**outlook.office.com**](urn:gd:lg:a:send-vm-keys)!!
     を入力してEnterを押します。

3.  **Pick an
    account**ページで!\![**AlexW@M365xXXXXXXX.onmicrosoft.com**](mailto:AlexW@M365xXXXXXXX.onmicrosoft.com)!!を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image12.png)

4.  **Enter password**ページで!!**P@55w.rd1234**!! を入力して**Sign
    in**を選択する。

5.  **More information requiredページでNextを選択する。**Keep your
    account secureページが開きます。

> ![A screenshot of a computer Description automatically
> generated](./media/image13.png)
>
> 通常は、Microsoft Authenticator
> アプリを使用して多要素認証を管理します。ただし、このラボ
> シナリオでは、テキスト メッセージを使用します。

6.  **Keep your account secure**ページで**I want to set up a different
    method**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image14.png)

7.  **Choose a different
    method**ダイアログボックスで**Phone**を選択してから**Confirm**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image15.png)

8.  **Phone**ページでテキストメセッジを受け入れるための携帯番号を入力し、**Next**を選択する。

> ![A screenshot of a computer screen Description automatically
> generated](./media/image16.png)

1.  確認コードをテキスト メッセージとして受信したら、\[**Phone**\]
    ページに示されている場所にコードを入力し 、\[**Next**\]
    を選択します。

> ![](./media/image17.png)

9.  SMS確認メッセージで**Next**を選択してから**Done**を選択する。

> ![A screenshot of a computer screen Description automatically
> generated](./media/image18.png)
>
> ![](./media/image19.png)

10. Stay signed inメッセージで**No**を選択する。

> ![A screenshot of a computer error Description automatically
> generated](./media/image20.png)
>
> Outlook on the Web が開き、Alex Wilber の受信トレイが表示されます。

11.  右上隅で、**Account manager for Alex Wilber**を選択してから**Sign
    out**を選択する。

> ![](./media/image21.png)
>
> **注**: ユーザーは、MFA
> を初めて使用するときにのみ登録する必要があります。その後のサインインでは、登録時に入力した電話番号にテキストで送信された検証コードのみを提供する必要があります.

12. アドレスバーに!\![**outlook.office.com**](urn:gd:lg:a:send-vm-keys)!!を入力してEnterをクリックする。

13. **Pick an
    accountページで**!!**AlexW@M365xXXXXXXXX.onmicrosoft.com**!!を選択する

14. **Enter
    passwordページで**  [!!**P@55w.rd1234**](mailto:!!P@55w.rd1234)!!を入力して**Sign
    in**選択する

> ![A screenshot of a computer error Description automatically
> generated](./media/image22.png)
>
> **Verify your
> identityプロンプトが開きます。携帯番号の最後の**下2桁がふくまれていることに注意する。

15. **Verify your
    identity**プロンプトでテキストの電話番号を選択する**。** 

16. **Enter
    code**ページで携帯番号まで送信された コードを入力して**Verify**を選択する。

> ![A screenshot of a computer error message Description automatically
> generated](./media/image23.png)
>
> チェック ボックスをオンにすると、30
> 日間は再度確認を求められないことに注意する。

1.  **Microsoft
    Authenticator**アプリは、より多くのセキュリティとスムーズなエクスペリエンスを確保するため、それを構成するように求められますが、今のところ**はスキップをクリックする。**

> ![A screenshot of a computer error Description automatically
> generated](./media/image24.png)

17. Stay signed inメッセージで**No**を選択する。 Outlook on the Web
    が開き、Alex Wilber の受信トレイが表示されます。

> ![A screenshot of a computer error Description automatically
> generated](./media/image25.png)

18. 右上隅で**Account manager for Alex Wilber**を選択して**、Sign
    out**を選択する。

> ![A computer screen shot of a computer screen Description
> automatically generated](./media/image26.png)

19. Microsoft Edgeを閉じる。

タスク 3: ユーザーごとの MFA を削除する

1.  [**SEA-SVR1**](urn:gd:lg:a:select-vm)に切り替える。.
    [**SEA-SVR1**](urn:gd:lg:a:select-vm)で、必要に応じて、[**Contoso\Administrator**](urn:gd:lg:a:send-vm-keys)としてサインインし、!\![**Pa55w.rd**](urn:gd:lg:a:send-vm-keys)!!
    パスワードを使用して、**Server Manager**を閉じる。

2.  タスクバーページで**Microsoft Edge**を選択して**、Microsoft Entra
    admin center** !!**https://Entra.Microsoft.com**!!へ移動する。

3.  **Office 365 Tenant admin**資格情報でサインインする**。**

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)
>
> **Microsoft Entra admin centerが開きます。**

4.  **Microsoft Entra admin
    center**のナビゲーションウィンドウに、**Identity**を拡張してから**Users**を選択する。

5.  **All users**を選択してから結果ペインの上で**Per-user
    MFA**を選択する**。** **Per-user
    MFA**オプションを表示するために最初に三つのドットを選択する必要です**。**

> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)

6.  ページの上に、**multi-factor authenticationの下でusers**を選択する

7.  ユーザのリストに、**Alex
    Wilber**の横にあるチェックボックスをオンにする。

>  **Alex Wilber の** Multi-Factor Auth Status が **Enforced**
> に設定されました (以前は Enabled
> に設定されていました)。これは、Alexが登録し、MFAを使用しているためです。
>
> ![A screenshot of a computer Description automatically
> generated](./media/image27.png)

8.  Alex Wilberページで**Manage user settings**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image28.png)

9.  Manage user
    settingsボックスで、三つの全てのオプションの横のボックスを選択して、**save**を選択し**、close**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image29.png)
>
> これらのオプションは、Alexに保存されているすべてのMFA設定を削除します。
>
> ![A white rectangular frame with black border Description
> automatically generated](./media/image30.png)

10. ユーザリストに、**Alex Wilber**の横のチェックボックスをオンにする。

11. Alex Wilberページに**Disable**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image31.png)

12. **Disable multi-factor
    authentication**メッセージで**yes**を選択する。

> ![](./media/image32.png)

13. **Updates successful**メッセージで**close**を選択する

> ![A white screen with black text Description automatically
> generated](./media/image33.png)
>
> これで、Alex Wilberの**Multi-Factor Auth
> Status** は**Disabled**であることに注意する。
>
> ![A screenshot of a computer Description automatically
> generated](./media/image34.png)

14. Microsoft Edgeを閉じる。

**結果**:
この手順を完了すると、ユーザーごとの多要素認証が正常に構成されます。

手順 2: 条件付きアクセスを使用して多要素認証を構成する

**Scenario**

ユーザーのサインオンイベントのセキュリティを強化するには、多要素認証（MFA）を設定してテストする必要があります。条件付きアクセスポリシーを使用することで、MFA要件をより柔軟に満たせると判断しました。Alex
Wilberが設定の検証に同意します。

タスク 1: MFA で条件付きアクセスを有効にする前にサインインを検証する

1.  [**SEA-WS3**](urn:gd:lg:a:select-vm)に切り替えて、!\![**Admin**](urn:gd:lg:a:send-vm-keys)!!
    としてサインインし、!\![**Pa55w.rd**](urn:gd:lg:a:send-vm-keys)!!を使用する。

2.  タスクバーで**Microsoft
    Edgeを選択する。**アドレスバーで!\![**outlook.office.com**](urn:gd:lg:a:send-vm-keys)!!
    を選択して、Enterを押します。

3.  **Sign in**ページで!!**AlexW@M365xXXXXXXX.onmicrosoft.com**!!
    を入力して**Next**を選択する。

4.  **Enter password**ページで!!**P@55w.rd1234**!! を入力して**Sign
    in**を選択する。Edgeの Save passwordプロンプトで**Save**を選択する。

> Outlook on the Web が開きます。Outlook on the
> Webにサインインするために必要なのはパスワードのみであることに注意する。

5.  右上隅で**Account manager for Alex Wilber**を選択してから**Sign
    out**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image1.png)

6.  Microsoft Edgeを閉じる

タスク 2: MFA を使用した条件付きアクセスの構成

1.  [**SEA-SVR1**](urn:gd:lg:a:select-vm)に切り替える。[**SEA-SVR1**](urn:gd:lg:a:select-vm)で、必要に応じて、[**Contoso\Administrator**](urn:gd:lg:a:send-vm-keys)としてサインインし、!\![**Pa55w.rd**](urn:gd:lg:a:send-vm-keys)!!を使用して、**Server
    Manager**を閉じる。

2.  タスクバーで**Microsoft Edge**を選択して**Microsoft Entra admin
    center** !!**https://Entra.Microsoft.com**!!へ移動する。

3.  **Office 365 Tenant adminの資格情報でサインインする。**

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)
>
> **Microsoft Entra admin centerが開きます。**

4.  **Microsoft Entra admin
    center**に、ナビゲーションウィンドウで**Identity**を拡張してから**Protection**、とそして**Conditional
    Access**を拡張する。

> ![A screenshot of a computer Description automatically
> generated](./media/image35.png)

5.  **Conditional Access**ページで**Policies**を選択してから**+ New
    policy**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image36.png)

6.  **New Conditional access
    policy**ページで**、Name**ボックスに !\![**Contoso MFA
    Policy**](urn:gd:lg:a:send-vm-keys)!!を入力する。

7.  **Assignmentsの下に**, **0 users or workload identities
    selected**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image37.png)

8.  Users and groupsペインに**Select users and
    groupsの横にあるオプションを選択して** **Users and
    groups**の横のチェックボックスをオンにする。

9.  **SelectページでAlex Wilberを選択してSelect**をクリックする。

> ![A screenshot of a computer Description automatically
> generated](./media/image38.png)
>
> 通常はグループを指定しますが、この手順では Alex Wilber
> の設定をテストするだけです。

10. Target resourcesの下に**No target resources
    selected**を選択して**、Select apps**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image39.png)

11. **SelectページOffice
    365** aの横にあるチェックボックスをオンにして**Select**をクリックする。

> ![A screenshot of a computer Description automatically
> generated](./media/image40.png)

12.  **Access controlsのGrantのセクションに0 controls
    selected**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image41.png)

13. **GrantページでGrant access**を選択して、**Require multi-factor
    authentication**の横のチェックボックスをオンにしてから**Select**を選択数する。

> ![A screenshot of a computer Description automatically
> generated](./media/image42.png)

14. **Enable policyの下にOn**を選択する。

15. **Create**を選択して、Contoso MFA Policyを作成する。ポリシーが
    \[State\] が \[On\] でリストされていることに注意する。

> ![A screenshot of a computer Description automatically
> generated](./media/image43.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image44.png)

16. **Microsoft Entra admin centerにUsers**を選択する。User listに**Alex
    Wilber**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image45.png)

17. Alex Wilberページで**Authentication methods**を選択する。

> ![](./media/image46.png)
>
> 電話番号は Alex に既に設定されていることに注意してください

18. Microsoft Edgeを閉じる。

タスク 3: 条件付きアクセス MFA の検証

1.  [**SEA-WS3**](urn:gd:lg:a:select-vm)に切り替える。タスクバーで**Microsoft
    Edge**を選択する。

2.  アドレスバーで!\![**outlook.office.com**](urn:gd:lg:a:send-vm-keys)!!
    を入力してEnterを押します。

3.  **Pick an
    accountページで**!!**AlexW@M365xXXXXXXX.onmicrosoft.com**!!を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image12.png)

4.  **Enter**
    [**passwordページで**!!**P@55w.rd1234**](mailto:passwordページで!!P@55w.rd1234)!!を入力して、**Sign
    in**を入力する。

5.  **Verify your identity**プロンプトでテキストの電話番号を選択する。

> ![A screenshot of a computer error Description automatically
> generated](./media/image22.png)

6.  **Enter
    code**ページで携帯番号に送信されたコードを入力し**、Verify**を選択する。

> ![A screenshot of a computer error message Description automatically
> generated](./media/image23.png)
>
> チェック ボックスをオンにすると、30
> 日間再度確認を求められないことに注意してください.

1.  Stay signed inメッセージで**No**を選択する。 Outlook on the Web
    が開き、Alex Wilber の受信トレイが表示されます。

> ![A screenshot of a computer error Description automatically
> generated](./media/image25.png)

7.  右上隅で**Account manager for Alex Wilberを選択すしてSign
    out**を選択する。

> ![A computer screen shot of a computer screen Description
> automatically generated](./media/image26.png)

8.  Microsoft Edgeを閉じる

タスク 4: 条件付きアクセス MFA を削除する

1.  [**SEA-SVR1**](urn:gd:lg:a:select-vm)に切り替える。[**SEA-SVR1**](urn:gd:lg:a:select-vm)で、必要に応じて、[**Contoso\Administrator**](urn:gd:lg:a:send-vm-keys) wとしてサインインし!\![**Pa55w.rd**](urn:gd:lg:a:send-vm-keys)!!
    を使用して、 **Server Manager**を閉じる。

2.  On the タスクバーで**Microsoft Edge**を選択して**Microsoft Entra
    admin center**  !!**https://Entra.Microsoft.com**!!に移動する。

3.  **Office 365 Tenant admin資格情報でサインインする。**

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)
>
> **Microsoft Entra admin centerが開きます。**

4.  In the **Microsoft Entra admin
    center**に、ナビゲーションウィンドウで**Identity**を拡張して、そして**Protection**とそれから
    **Conditional Accessを拡張する。**

> ![A screenshot of a computer Description automatically
> generated](./media/image35.png)

5.  On the **Conditional AccessページでPoliciesを選択してからContoso MFA
    Policy**を選択する。

6.  **Contoso MFA PolicyページでDeleteを選択してDelete**をクリックする。

> ![A screenshot of a computer Description automatically
> generated](./media/image47.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image48.png)

7.  Deleteの確認でDeleteボタンをクリックする。

> ![A screenshot of a computer error Description automatically
> generated](./media/image49.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image50.png)

8.  Microsoft Edgeを閉じる。

**結果**: この手順を完了すると、条件付きアクセス
ポリシーを使用して多要素認証が正常に構成されます。
