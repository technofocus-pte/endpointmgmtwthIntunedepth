**ラボ 5 - Microsoft Intune へのデバイス登録の管理**

**要約**

このラボでは、ライセンスの確認と割り当て、Windows
の自動登録の構成、登録制限の構成などを行い、Microsoft Intune
を使用したデバイス管理の準備をします。.

**前提 条件**

このラボの前に、次のラボを完了する必要があります。

- ラボ \#1 - Microsoft Entra ID でのアイデンティティーの管理

- ラボ \#2 - Microsoft Entra Connect を使用したアイデンティティーの同期

**注:** Entra ID への Windows Hello
サインイン認証を保護するために使用されるテキスト
メッセージを受信できる携帯電話も必要になります**。**

**シナリオ**

Microsoft Intune
を使用したデバイス管理を準備する必要があります。まず、ユーザーにデバイス管理用の適切なライセンスが割り当てられていることを確認する必要があります。検証テストとして、Aaron
Nicholls に必要なライセンスを割り当てます。また、Microsoft Entra ID
に参加または登録されているすべての Windows デバイスが Intune
に自動的に登録されるようにする必要があります。さらに、Sales
グループのメンバーが個人の Android デバイスと iOS デバイスを Intune
に登録できないように制限し、登録デバイスの制限を 10
台に増やすように指示されています。最後に、Allan Deyoung
をデバイス登録管理者として構成し、1,000
台のデバイスを登録できるようにする必要があります。

**Task 1: デバイス管理のライセンスを確認して割り当てる**

1.  [*SEA-SVR1*](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)で、**Microsoft
    365 admin center**ウィンドに移動する**。**

![](./media/image1.png)

2.  **Billing**に移動して選択し、**Licenses**をクリックする。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image2.png)

3.  **Licenses**ページ にテナントで利用可能なライセンスに注意する。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image3.png)

1.  Select and click on **Enterprise Mobility + Security
    E5**を選択してクリックする。全てのユーザーがこのライセンスをアサインされたことを注意する。この場所からライセンスを割り当てたり削除したりできます。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image4.png)

![](./media/image5.png)

4.  ユーザーを選択すると、そのユーザーに割り当てられているライセンスが表示されます。Enterprise
    Mobility + Security
    E5ライセンスに含まれるサービスに注意してください。Microsoft
    Intuneはこのライセンスでサポートされているサービスの1つです。

![](./media/image6.png)

5.  In the **Microsoft 365 admin center ナビゲーションウィンドウでActive
    users**を選択する。

![](./media/image7.png)

6.  !!**Cindy White**!!を検索して、選択する。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image8.png)

7.  **Cindy White userページでLicenses and apps**をクリックする。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image9.png)

8.  Under **SettingsのUsage locationフィールドにUnited
    Statesを選択して、** and click on the check box for **Enterprise
    Mobility + Security E5 and Office 365 E5 (no
    teams)のチェックボックスをオンにしてSave changes**をクリックする。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image10.png)

***注意:
ユーザーにライセンスを割り当てる前に、ユーザーに使用場所を設定する必要があります。***

![](./media/image11.png)

**タスク 2: PowerShellを使用するユーザーのパスワードの設定**

1.  In
    [***SEA-SVR1***](urn:gd:lg:a:select-vm)に右クリックしから**Windows
    PowerShell (Admin)**をせんたくする。

![](./media/image12.png)

2.  **User Account Control**ダイアログボックスで**Yes**を選択する。

![](./media/image13.png)

3.  In the **Windows
    PowerShellウィザードに、次のコマンドを入力して、Enter**をクリックする。

!!**Connect-MsolService**!!

![A computer screen with white text Description automatically
generated](./media/image14.png)

4.  In the **Sign in to your
    accountダイアログボックスでホームタブから**Office 365
    Tenant資格情報を使用してサインインする。

**注 –
テナント管理者の資格情報のパスワードを変更するように求められた場合は、更新されたパスワードを指定します**

![A screenshot of a computer Description automatically
generated](./media/image15.png)

![A screenshot of a computer screen Description automatically
generated](./media/image16.png)

5.  **Windows
    PowerShell** ウィンドタイプに、以下のコマンドを入力して**Cindy
    Whiteのパスワードをリセットする。**

!!**Get-MsolUser | Where-Object DisplayName -EQ "Cindy White" |
Set-MsolUserPassword -NewPassword P@55w.rd1234 -ForceChangePassword
$false**!!

![A computer screen shot of a program Description automatically
generated](./media/image17.png)

**タスク 3: Microsoft Intune への Windows 自動登録を有効にする**

1.  In **SEA-SVR1**に **Microsoft
    Edge**に新しいタブを開き、アドレスバーに!!**https://Endpoint.microsoft.com**!!を入力して**Enterを押す。**サインインを求めたら**Office
    365 Tenant Admin**の資格情報を提供する。

2.  Microsoft Intune admin centerに**Devices**を選択する。

![A screenshot of a computer Description automatically
generated](./media/image18.png)

3.  **Enrollment**へ移動しクリックする**。Windows**タブが選択されていて**、Enrollment
    options**セクションへ移動し、**Automatic
    Enrollment**をクリックする。

![](./media/image19.png)

4.  **MDM user
    scope**列で**All**ラジオボタンを選択し**、Save**を選択する。

![](./media/image20.png)

5.  以下画像に示すよう**Devices | Enrollment**リンクをクリックする**。**

![](./media/image21.png)

**注**: この手順を実行すると、Windows デバイスとの Azure AD
joinを実行するすべてのユーザーに対して、Intune
への自動登録が有効になります。

**タスク 4: 登録制限の設定**

1.  **Devices
    onboarding**セクションへ移動して**Enrollment**をクリックする。それから、以下画像に示すよう**Android**タブをクリックする。

![](./media/image22.png)

2.  **Enrollment options**セクションにスクロールダウンして**、Device
    platform restriction**をクリックする。

![](./media/image23.png)

3.  **Android restrictions**タブを選択してから+**Create
    restriction**を選択する。

![](./media/image24.png)

![](./media/image25.png)

4.  **Create restriction**ページで**Name**ボックスに!!**Android Personal
    Device Restriction**!!を入力して**Next**を選択する。

![](./media/image26.png)

5.  On the Platform設定ページで**Personally
    owned**の下に以下のデバイスタイプに対して**Block**を選択して**、Next**ボタンをクリックする**。**

    - Android Enterprise (work profile)

    - Android device administrator

![](./media/image27.png)

6.  **Scope tags**ページで**Next**を選択する。

![A screenshot of a computer Description automatically
generated](./media/image28.png)

7.  **Assignments**ページで**Included groups**の下に**Add
    groups**を選択する。

![A screenshot of a computer Description automatically
generated](./media/image29.png)

8.  **Select groups to include**ペインの**Search bar**に、 type and
    select
    **Sales**を入力して選択し、**Select**ボタンをクリックする**。**

![A screenshot of a computer Description automatically
generated](./media/image30.png)

9.  **Assignments**タブに**Next**ボタンをクリックする。

![A screenshot of a computer Description automatically
generated](./media/image31.png)

10. **Review + create**ページで**Create**を選択する。

![A screenshot of a computer Description automatically
generated](./media/image32.png)

注： Android Personal Device Restrictionは優先度 1 を割り当てられた![A
screenshot of a computer Description automatically
generated](./media/image33.png)

11. **Devices | Enrollment**ページで**Windows**タブに**Enrollment
    options**セクションへ移動して**Device limit
    restriction**をクリックする。

注: 「All
users」には、デフォルトのデバイス制限が設定されています。このデフォルトの制限では、ユーザーあたりのデバイス登録台数が5台に制限されています。

12. **Enrollment device limit restrictions**で+ **Create
    restriction**を選択する。

![A screenshot of a computer Description automatically
generated](./media/image34.png)![A screenshot of a computer Description
automatically generated](./media/image35.png)

13. On the Create restrictionページで**Name**ボックスに !!**Sales Device
    Enrollment Limit**!!を入力する。**Next**を選択する。

![A screenshot of a computer Description automatically
generated](./media/image36.png)

14. **Device limit**ページで**10**を選択してから**Next**を選択する。

![A screenshot of a computer Description automatically
generated](./media/image37.png)

15. **Scope tags**ページで**Next**を選択する。

![A screenshot of a computer Description automatically
generated](./media/image38.png)

16. **Assignments**ページで**Included groups**の下に**Add
    groups**を選択する。

![A screenshot of a computer Description automatically
generated](./media/image39.png)

17. **Select groups to
    include**ページの検索ボックスに**Sales**を入力して選択し**、Select**ボタンをクリックする**。**

![](./media/image40.png)

18. **Next**ボタンをクリックする。

![A screenshot of a computer Description automatically
generated](./media/image41.png)

19. **Review + create**ページで**Create**を選択する。

![A screenshot of a computer Description automatically
generated](./media/image42.png)

20. ページをリロードします。Sales Device Enrollment
    Limitがデバイス数10に設定され、優先度1が割り当てられていることに注意する。

![A screenshot of a computer Description automatically
generated](./media/image43.png)

**タスク 5: デバイス登録マネージャーを構成する**

1.  **Microsoft Intune admin center**に**Devices**を選択する。

![](./media/image44.png)

2.  **Device
    onboarding**セクションへ移動して**Enrollment**をクリックしてから**Device
    enrolment managers**タブにクリックする**。**

![](./media/image45.png)

3.  **Enroll devices**ペインで**Device enrollment managers**を選択する。

注：デフォルトでデバイス登録マネージャーは構成されていない。

4.  **Enroll devices|Device enrollment
    managers**ページで**Add**を選択する。

![A screenshot of a computer Description automatically
generated](./media/image46.png)

5.  \[**Add user**\] ページの \[User name\] に、Allan DeYoung のメール
    アドレス !!AllanD@M365xXXXXXXX.onmicrosoft.com!! を入力し (XXXXXX
    をテナント名に置き換えます)、\[**Add**\] を選択します。

![A screenshot of a computer Description automatically
generated](./media/image47.png)

**Allan は最大 1000 台のデバイスを登録できるようになりました。**

6.  Microsoft Intune admin
    centerのナビゲーションペインに**Home**を選択する。

![A screenshot of a computer Description automatically
generated](./media/image48.png)

7.  Microsoft Edgeを閉じる。

**結果**: この手順を完了すると、ライセンスの確認と割り当て、Windows
の自動登録の構成、登録制限の有効化と割り当て、デバイス登録マネージャーの構成が正常に完了します。
