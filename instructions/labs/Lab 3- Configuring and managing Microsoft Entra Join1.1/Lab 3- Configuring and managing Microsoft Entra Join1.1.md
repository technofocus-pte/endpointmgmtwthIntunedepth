ラボ 03: Microsoft Entra ID Join の構成と管理

**要約**

このラボでは、Microsoft Entra ID Join 設定を構成し、Windows
デバイスの標準および Microsoft Entra hybrid joinシナリオを実行します。

**前提 条件**

このラボの前に、次のラボを完了する必要があります:

- ラボ \#2: Microsoft Entra Connect を使用したアイデンティティの同期

**注**: Entra ID への Windows Hello
サインイン認証を保護するために使用されるテキスト
メッセージを受信できる携帯電話も必要になります**。**

**手順 1: Configuring Microsoft Entra Join**

**シナリオ**

Entra IDデバイスの設定を構成し、すべてのユーザーがデバイスをEntra IDに
join
できるようにする必要があります。また、ユーザーが参加できるデバイスが最大20台に制限されていること、およびAllan
DeyoungがすべてのMicrosoft
Entra参加済みデバイスにローカル管理者として追加されていることを確認する必要があります。最後に、Joni
ShermanをSEA-WS1のテナントに join させることで、Microsoft Entra
Joinが期待どおりに機能することを確認します。

## タスク 0: PowerShell スクリプトを使用して TLS 1.2 を有効にします。

1.  SEA-WS1で、Contoso\AdministratorとしてサインインするためにPa55w.rdパスワードを使用する。

2.  スタートメニューで「PowerShell[」と入力し**、**](urn:gd:lg:a:send-vm-keys)
    PowerShellを右クリックして、 \[**Run as administrator**\]
    を選択します。

![](./media/image1.png)

3.  PowerShell で次のスクリプトを実行します。

**If** (-Not (Test-Path
'HKLM:\SOFTWARE\WOW6432Node\Microsoft\\NETFramework\v4.0.30319'))

{

New-Item 'HKLM:\SOFTWARE\WOW6432Node\Microsoft\\NETFramework\v4.0.30319'
-Force | Out-Null

}

New-ItemProperty -Path
'HKLM:\SOFTWARE\WOW6432Node\Microsoft\\NETFramework\v4.0.30319' -Name
'SystemDefaultTlsVersions' -Value '1' -PropertyType 'DWord' -Force |
Out-Null

New-ItemProperty -Path
'HKLM:\SOFTWARE\WOW6432Node\Microsoft\\NETFramework\v4.0.30319' -Name
'SchUseStrongCrypto' -Value '1' -PropertyType 'DWord' -Force | Out-Null

**If** (-Not (Test-Path
'HKLM:\SOFTWARE\Microsoft\\NETFramework\v4.0.30319'))

{

New-Item 'HKLM:\SOFTWARE\Microsoft\\NETFramework\v4.0.30319' -Force |
Out-Null

}

New-ItemProperty -Path
'HKLM:\SOFTWARE\Microsoft\\NETFramework\v4.0.30319' -Name
'SystemDefaultTlsVersions' -Value '1' -PropertyType 'DWord' -Force |
Out-Null

New-ItemProperty -Path
'HKLM:\SOFTWARE\Microsoft\\NETFramework\v4.0.30319' -Name
'SchUseStrongCrypto' -Value '1' -PropertyType 'DWord' -Force | Out-Null

**If** (-Not (Test-Path
'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS
1.2\Server'))

{

New-Item
'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS
1.2\Server' -Force | Out-Null

}

New-ItemProperty -Path
'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS
1.2\Server' -Name 'Enabled' -Value '1' -PropertyType 'DWord' -Force |
Out-Null

New-ItemProperty -Path
'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS
1.2\Server' -Name 'DisabledByDefault' -Value '0' -PropertyType 'DWord'
-Force | Out-Null

**If** (-Not (Test-Path
'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS
1.2\Client'))

{

New-Item
'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS
1.2\Client' -Force | Out-Null

}

New-ItemProperty -Path
'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS
1.2\Client' -Name 'Enabled' -Value '1' -PropertyType 'DWord' -Force |
Out-Null

New-ItemProperty -Path
'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS
1.2\Client' -Name 'DisabledByDefault' -Value '0' -PropertyType 'DWord'
-Force | Out-Null

Write-Host 'TLS 1.2 has been enabled. You must restart the Windows
Server for the changes to take affect.' -ForegroundColor Cyan

![](./media/image2.png)

4.  Windows Server VMを再起動する。

![](./media/image3.png)

## タスク 1: Microsoft Entra ID joinデバイス設定を構成する

1.  **SEA-SVR1に切り替える。Microsoft
    Edgeブラウズアドレスバーに次おURLを入力して**URL:
    !\![**https://entra.microsoft.com**](https://entra.microsoft.com)!!
    **Enter**ボタンを押す。

2.  O365 tenant ID:
    !!**admin@M365xXXXXXXXX.onmicrosoft.com**!!でサイン人してテナントAdminパスワードを使用する。

![A screenshot of a computer Description automatically
generated](./media/image4.png)

![A screenshot of a login box Description automatically
generated](./media/image5.png)

3.  **Stay signed in?　**ダイアログボックスで**Yes**ボタンを選択する。

![A screenshot of a computer Description automatically
generated](./media/image6.png)

4.  **Microsoft Entra admin
    centerウィンドにIdentity**に移動し、クリックする。

![A screenshot of a computer Description automatically
generated](./media/image7.png)

5.  **IdentityセクションにDevices**を選択してから以下画像に示すよう**All
    devices**へ移動してクリックする**。**

![A screenshot of a computer Description automatically
generated](./media/image8.png)

まだどのデバイスにもjoinしていないため、デバイスが見つからないことに注意する。

![](./media/image9.png)

6.  **Devices** | All devicesページで**Device settings**を選択する。

![A screenshot of a computer Description automatically
generated](./media/image10.png)

7.  **Devices | Device settings**ページでdetailsのペインに**Users may
    join devices to
    Entra**で**All**が選択していることを確認　する**。　**

これは、すべてのEntraユーザーがWindows 10以降のデバイスをMicrosoft
Entraにjoinさせることを許可していることを示します。この設定は、Entraハイブリッドjoinデバイス、またはWindows
Autopilotセルフ展開モードを使用してjoinしたデバイスには適用されないことに注意してください。

8.  **Require Multi-factor Authentication to register or join devices
    with Entra**セクションで設定は**No**であることを確認する**。**

![A screenshot of a computer Description automatically
generated](./media/image11.png)

9.  In the **Maximum number of devices per
    userセクションで20**を選択する **(推奨)**.

10. **Manage** **Additional local administrators on all Microsoft Entra
    Joined devices**リンクをクリックする**。Device Administrators
    page**が開きます**。**

![A screenshot of a computer Description automatically
generated](./media/image12.png)

11. **Device Administrators | Assignments**ページで**Add
    assignments**を選択する。

![A screenshot of a computer Description automatically
generated](./media/image13.png)

12. 検索ボックスに!!**Allan Deyoung**!!を入力して**Allan
    Deyoung**ユーザーオブジェクトを選択してから**Add**を選択する。

![A screenshot of a computer Description automatically
generated](./media/image14.png)

13. Allan Deyoungは、すべてのMicrosoft Entra Joined
    devicesのデバイス管理者として追加されます。

![A screenshot of a computer screen Description automatically
generated](./media/image15.png)

14. 検索バーのしたに**Devices | Device
    settings**リンクをクリックして**Device Settings**ページに戻ります。

![A screenshot of a computer Description automatically
generated](./media/image16.png)

15. **Device settingsペンでSave**を選択する。

![A screenshot of a computer Description automatically
generated](./media/image17.png)

**タスク 2: Microsoft Entra ID Join**を実行

1.  [SEA-WS1](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)に切り替えて、**Admin**としてサインインするには !!**Pa55w.rd**!!を使用する。

![](./media/image18.png)

2.  タスクバーで**Windows
    Start buttonアイコンを選択してSettings**を選択する。

![](./media/image19.png)

3.  **SettingsウィンドにAccounts**を選択する。

![A screenshot of a computer Description automatically
generated](./media/image20.png)

4.  **Accounts**ページに**Access work or school**を選択する。

![A screenshot of a computer Description automatically
generated](./media/image21.png)

5.  **Access work or schoolページ**に**Connect**を選択する。

![A screenshot of a computer Description automatically
generated](./media/image22.png)

6.  **Microsoft accountウィンドにJoin this device to Microsoft Entra
    ID**を選択する。

![A screenshot of a computer screen Description automatically
generated](./media/image23.png)

7.  **Sign in**ページで!!JoniS@M365xXXXXXXX.onmicrosoft.com!!
    を入力して**Next**を選択する。

![Graphical user interface, application, Teams Description automatically
generated](./media/image24.png)

8.  On the **Enter
    password**ページでテナントパスワード!\![**P@55w.rd1234**](mailto:P@55w.rd1234)!!を入力して**Sign
    in**を選択する。

![Graphical user interface, application Description automatically
generated](./media/image25.png)

9.  **Make sure this is your
    organizationダイアログボックスでJoin**を選択する。

![A screenshot of a computer error Description automatically
generated](./media/image26.png)

10. **You're all set!** ページで**Done**を選択する。

![A screenshot of a computer Description automatically
generated](./media/image27.png)

11. On the **Access work or school**ページで**Connected to Contoso's
    Azure AD**が表示されていることを確認する。

![A screenshot of a computer Description automatically
generated](./media/image28.png)

12. **Settings**ページを閉じる**。**

**タスク 3: Microsoft Entra Join の検証**

1.  On [SEA-WS1](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)で**Windows**
    **Start buttonを右クリックし、**以下の画像で示すよう **Windows
    Terminal (Admin)** を選択する。

![](./media/image29.png)

2.  **User Account Control**ダイアログボックスで**Yes**を選択する。

![](./media/image30.png)

3.  PowerShellコンソールに次のコマンドを入力して**Enter**ボタンを押す**：**

!!**dsregcmd /status**!!

4.  アウトプットに**Device Stateの下にAzureAdJoined :
    YES**が表示していることを確認する。

これは、デバイスがMicrosoft Entra Joinedであることを示します。

![](./media/image31.png)

5.  PowerShellを閉じる。

6.  Right-click again on また**Windows**
    **Start** **button**アイコンを右クリックし**、Computer
    Management**を選択する。

![A screenshot of a computer Description automatically
generated](./media/image32.png)

7.  **Computer Management**ウィンドに**Local Users and
    Groups**を拡張して**Groups**を選択する。

![](./media/image33.png)

![A screenshot of a computer Description automatically
generated](./media/image34.png)

8.  **Administrators**のグループをダブルクリックする**。**

![A screenshot of a computer Description automatically
generated](./media/image35.png)

SEA-WS1 に Joni Sherman
がローカル管理者として追加されていることに注意してください。また、security
identifiers (SID) で表される 2 つのセキュリティ
プリンシパルにも注目してください。これらの 2 つの SID は、Entra
グローバル管理者ロールと Microsoft Entra
参加デバイス管理者ロールを表しています。

![](./media/image36.png)

9.  開いているすべてのウィンドウを閉じ、Windows Start button icon\>
    Admin \> Signout をクリックして **SEA-WS1**
    からサインアウトします**。**

![](./media/image37.png)

10. **SEA-SVR1** に切り替えて、資格情報
    **Contoso\Administrator**とパスワード !! **Pa55w.rd**!!
    を使用してログインします。

![A screenshot of a computer Description automatically
generated](./media/image38.png)

11. **Microsoft Entra admin
    center**に**Identity**に移動してクリックする。

12. **Devices**に移動して選択し、**All devices**をクリックする。

13. **Devices | All
    devicesページにSEA-WS1**がリストされることを確認する**。**

![](./media/image39.png)

14. **Join TypeはMicrosoft Entra
    Joinedとしてリストされ、**所有者は**Joni
    Sherman**であることを確認する。

![](./media/image40.png)

15. また、\[MDM\] 列に **\[None\]**
    と表示されていることにも注意する。これは、このデバイスがまだ
    Microsoft Intune によって管理されていないことを示しています.

![A screenshot of a computer Description automatically
generated](./media/image41.png)

**タスク 4: Microsoft Entra UserとしてWindowsにサインインする**

1.  **SEA-WS1**に切り替え**Other user**をクリックする。

![](./media/image42.png)

2.  [!!**JoniS@M365xXXXXXXX.onmicrosoft.com**](mailto:!!JoniS@M365xXXXXXXX.onmicrosoft.com)!!とサインインし、[テナントパスワード!!**P@55w.rd1234**](mailto:テナントパスワード!!P@55w.rd1234)!!を使用する。

**注: プロファイルが作成されるのを待ちます。**

![](./media/image43.png)

**注 –** Windows Hello の入力を求められた場合は、それに応じてサインイン
プロセスを完了し、\[**Set up a PIN**\] ページの \[**New PIN**\]
ボックスと \[**Confirm PIN**\] ボックスに「!\!102938!! 次に、\[OK\]
を選択します.

![](./media/image44.png)

**タスク 5: EntraからWindowsデバイスを削除する**

1.  [SEA-WS1](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)では、プロンプトが表示されたらJoni
    Shermanでログインし、ピンを入力するオプションがある場合は、ピンを入力します。
    !!**102938**!!または、パスワードを次のように入力します‐**P@55w.rd1234**!!

![A screenshot of a computer Description automatically
generated](./media/image45.png)

1.  **Settings**ウィンドに**Account**を選択する**。**

![A screenshot of a computer Description automatically
generated](./media/image46.png)

2.  左側ナビゲーションペインで、**Accounts**に移動してクリックする**。Accounts**ページで**Access
    work or school**を選択する。

![A screenshot of a computer Description automatically
generated](./media/image47.png)

3.  **Access work or school**ページに以下の画像で示すように **Connected
    to Contoso's Azure
    ADの**横にあるドロップダウンを選択する**。Disconnect**をクリックして**Yes**を選択する。

![](./media/image48.png)

![A screenshot of a computer Description automatically
generated](./media/image49.png)

![A screenshot of a computer Description automatically
generated](./media/image50.png)

4.  **Disconnect from the
    organization**ページに**Disconnect**を選択する。

![A blue box with white text Description automatically
generated](./media/image51.png)

5.  **Windows Security**ダイアログボックスで**Email
    addressボックスに**!!Admin!! を入力して**Passwordボックスに**!!Pa55w.rd!!を入力する。**OK**を選択する。

![Graphical user interface Description automatically
generated](./media/image52.png)

6.  **Restart your PC**ダイアログボックスで**Restart
    now**を選択する**。SEA-WS1**が再起動します。

![A blue box with white text Description automatically
generated](./media/image53.png)

**結果**: この手順を完了すると、Microsoft Entra
デバイス設定が構成され、デバイスが Entra にjoinし、Entra
からデバイスが削除されます。

**手順 2: Microsoft Entra hybrid joinの構成**

**シナリオ**

Contoso 社の一部の Windows デバイスは現在、ローカルの Active Directory
ドメイン サービスにjoinしています。これらのデバイスがクラウド
サービスにシームレスにアクセスできるようにするため、Microsoft Entra
のハイブリッド参加を有効にする予定です。Azure AD Connect
を再構成し、SEA-CL2 でプロセスをテストすることで、Microsoft Entra
のハイブリッドjoinをテストします。

**タスク 1: 環境を準備する**

1.  [SEA-SVR1](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)に切り替える。

![A picture containing text Description automatically
generated](./media/image54.png)

2.  **Windows** **Start icon**ボタンを選択して**Windows Administrative
    Tools**を拡張してから**Active Directory Users and
    Computers**を選択する。

![](./media/image55.png)

3.  **Active Directory Users and
    Computers**に**Contoso.com**を右クリックし、**New**に移動してから**Organizational
    Unit**を選択する。

![](./media/image56.png)

4.  **New-Object - Organizational Unit**ダイアログボックスで!!**Entra
    clients**!!を入力して**OK**を選択する。

![A screenshot of a computer Description automatically
generated](./media/image57.png)

5.  ナビゲーションウィンドウで**Seattle
    Clients**を選択する**。SEA-CL2** を右クリックし、**Move**を選択する。

![](./media/image58.png)

6.  **Move**ダイアログボックスで **Entra
    clients**を選択して**OK**を選択する。

![A screenshot of a computer Description automatically
generated](./media/image59.png)

7.  **Active Directory Users and Computers**を閉じる。

![A screenshot of a computer Description automatically
generated](./media/image60.png)

**タスク 2: Entra Connectを再構成**

1.  [SEA-SVR1](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)でデスクトップ上Azure
    AD Connectをダブルクリックする。

![A black rectangle with blue lines Description automatically
generated](./media/image61.png)

2.  **Microsoft Azure Active Directory
    Connect**ウィンドに**Configure**を選択する。

![](./media/image62.png)

3.  On the **Additional** タスクページで **Customize synchronization
    options**を選択してから **Next**を選択する。

![A screenshot of a computer Description automatically
generated](./media/image63.png)

4.  **Connect to
    Entra**ページで**USERNAME**と**PASSWORD**のボックスに**Office 365
    Tenant credentials**を入力して**Next**を選択する。

![A screenshot of a computer Description automatically
generated](./media/image64.png)

5.  **Connect your directoriesページで**Next buttonをクリックする。

![A screenshot of a computer Description automatically
generated](./media/image65.png)

6.  **Domain and OU filtering**ページで**Sync selected domains and
    Ous**が選択されていることを確認する。

7.   **Contoso.com**を拡張して**Entra
    clients**を選択し**、Next**をクリックする。

![A screenshot of a computer Description automatically
generated](./media/image66.png)

8.  **Optional features**ページに**Password hash
    synchronization**が選択されていることを確認してから**Next**を選択する。

9.  **Ready to configure**ページに**Start the synchronization process
    when configuration
    completes**が選択していることを確認して**Configure**を選択する。

![A screenshot of a computer Description automatically
generated](./media/image67.png)

10. 構成が完了したら**Exit**を選択する。

![](./media/image68.png)

注: 同期が完了するまで約 5 分間待ちます。

**タスク 3: Azure AD Connect を使用して Microsoft Entra hybrid
joinを構成する**

1.  [SEA-SVR1](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)
    VM **Desktop**で**Azure AD Connect**をダブルクリックする。

![Text Description automatically generated with medium
confidence](./media/image69.png)

2.  **Microsoft Azure Active Directory
    Connect**ウィンドに**Configure**を選択する。

![](./media/image70.png)

3.  **Additional タスク**ページで **Configure device
    options**を選択して**Next**を選択する。

![](./media/image71.png)

4.  **Overview**ページで**Next**を選択する。

![A screenshot of a computer Description automatically
generated](./media/image72.png)

5.  **Connect to Entra**ページでAdmin Tenant
    passwordを**PASSWORD**ボックスに入力してから**Next**を選択する。

![](./media/image73.png)

6.  **Device options**ページで**Configure Hybrid Azure AD
    Join**を選択してから**Next**を選択する。

![A screenshot of a computer Description automatically
generated](./media/image74.png)

7.  **Device operating systemsページでWindows 10 or later domain-joined
    devices**を選択してから**Next**を選択する。

![A screenshot of a computer Description automatically
generated](./media/image75.png)

8.  **SCP
    configuration**ページで **Contoso.com**の横にあるチェックボックスをオンにして、
    Select **Azure Active Directory** from the **Authentication
    Service**ドロップダウンから**Azure Active
    Directory** を選択し、**Add**を選択する。

![](./media/image76.png)

9.  **Enterprise Admin
    Credentials**ウィンドに**Contoso\Administrator** を**Username**として**、**!!**Pa55w.rd**!!を**Password**として入力する**。OK**を選択し**、Next**を選択する。

![A screenshot of a computer security Description automatically
generated](./media/image77.png)

![](./media/image78.png)

10. **Ready to
    configure**ページに**Configure**を選択し、構成を実行する**。**![A
    screenshot of a computer Description automatically
    generated](./media/image79.png)

11. 構成が完了したら**Exit**を選択する。

![A screenshot of a computer Description automatically
generated](./media/image80.png)

12. タスクバーで**Windows Start button icon**を右クリックし**、Windows
    Powershell (Admin)**を選択する。

![A screenshot of a computer Description automatically
generated](./media/image81.png)

13. **Windows
    PowerShell**ウィンドに次のコマンドを入力して**Enter**を押す。

!!**Start-ADSyncSyncCycle -PolicyType Initial**!!

![A screenshot of a computer Description automatically
generated](./media/image82.png)

14. PowerShellウィンドを閉じる。

注: 同期が完了するまで約 5 分間待ちます。

**タスク 4: Entra 登録の確認**

1.  [SEA-CL2](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)に切り替える。

2.  At the sign-in page, select
    the サインインページに**Power**ボタンを選択してから**Restart**を選択する。

![Graphical user interface, application Description automatically
generated](./media/image83.png)

***注**:再起動すると、ハイブリッドMicrosoft Entra Join On
[SEA-CL2がトリガーされます](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)。*

3.  After **SEA-CL2**が再起動してから**Contoso\Administrator**としてサインインし、パスワードを!!**Pa55w.rd**!!使用する**。**

![Graphical user interface, application Description automatically
generated](./media/image84.png)

4.  タスクバーで**Windows Start icon button**を右クリックし**、Windows
    Terminal (Admin)**を選択する。

![A screenshot of a computer Description automatically
generated](./media/image81.png)

5.  In the **Windows
    PowerShell**ウィンドに以下のコマンドを入力してから**Enter**を入力する。

!!**dsregcmd /status**!!

6.  **Device State**の下にあるアウトプットに、次を確認する。 

- **AzureAdJoined : YES** 

- **DomainJoined : YES** が表示

![](./media/image85.png)

***注：デバイスがまだEntraに接続されていない場合は、Entra
Connectの同期が完了するまで待つ。その後、SEA-CL2を再起動してください。ステータスが更新されるまで5～10分かかる場合があります。***

さらに、**SEA-SVR1** にログインし、**Windows PowerShell**
ウィンドウで次のコマンドを入力して同期を高速化できます.

!!**Start-ADSyncSyncCycle -PolicyType Initial**!!

7.  [SEA-CL2](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)上全てのウィンドを閉じて、サインアウトする。

8.  [SEA-SVR1](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)に切り替えて、**Microsoft
    Entra admin
    center**ウィンドに移動して**、Identity**に移動し、クリックする。

![A screenshot of a computer Description automatically
generated](./media/image7.png)

9.  **Identity**セクションの下に**Devices**を選択して、以下の画像で示すよう**All
    devices**に移動し、クリックする**。**

![A screenshot of a computer Description automatically
generated](./media/image8.png)

10. **SEA-CL2** に、**Join type**値として **Microsoft Entra** **hybrid
    joined** があることを確認します。SEA-CL2がリストにない場合は、**Refresh**ボタンをクリックします。

![A screenshot of a computer Description automatically
generated](./media/image86.png)

11. [SEA-SVR1](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)で全てのウィンドを閉じる。

**結果:** この手順を完了すると、Microsoft Entra hybrid
joinが正常に構成および検証されます。
