ラボ 02 - Microsoft Entra Connect を使用した**アイデンティティー**の同期

**要約**

このラボでは、Active Directory Domain Services から Microsoft
Entra**アイデンティティー**への同期を構成します

**シナリオ**

Contoso Corporation では現在、AD DS と Microsoft Entra ID
の両方のユーザーを別々のプロセスで管理しています。これは時間がかかり、情報の不整合につながっています。Microsoft
Entra Connect 同期ツールを使用して 2
つのディレクトリを接続することで、この問題を解決することが課題となっています。

## タスク 0: **PowerShell スクリプトを使用して TLS 1.2 を有効にする**

1.  **SEA-SVR1**で、**Contoso\Administrator**としてサインインするためにパスワードとして**Pa55w.rd**を使用する。

2.  スタートメニューで[**PowerShell**](urn:gd:lg:a:send-vm-keys)を入力して、PowerShellを右クリックし、**run
    as administrator**を選択する。

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

4.  Windows Server VM を再起動します。

![](./media/image3.png)

タスク 1: Microsoft Entra Connectを使用したディレクトリ同期の構成

1.  [***SEA-SVR1***](urn:gd:lg:a:select-vm)では、必要に応じて、パスワード
    !! [**Pa55w.rd**](urn:gd:lg:a:send-vm-keys)!! を使用して
    [**Contoso\Administrator**](urn:gd:lg:a:send-vm-keys)としてサインインします。

2.  タスクバーで**Microsoft Edge**を選択する。

3.  アドレスバーで!\![**http://www.microsoft.com/en-us/download/details.aspx?id=47594**](urn:gd:lg:a:send-vm-keys)!!を入力する。

4.  Microsoft Entra Connectページで**Download**を選択する。

> Microsoft Entra
> Connectは自動的に**SEA-SVR1でDownloads** folderでダウンロード します。
>
> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

5.  ダウンロードされたファイル**AzureADConnect.msi**の**Open
    file**をクリックする**。**

> ![A screenshot of a phone Description automatically
> generated](./media/image5.png)

6.  **Microsoft Azure Active Directory Connect** ウィザードに、**Welcome
    to Azure AD ConnectページでI agree to the license terms and privacy
    noticeチェックボックスをオンにしてからContinue**を選択する。

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image6.png)

7.  **Express SettingsパージでCustomize**を選択する。

> ![](./media/image7.png)

8.  **Install required componentsページでInstall**を選択する。

> ![](./media/image8.png)

9.  **User sign-inページでPassword Hash
    Synchronizationが選択されることを確認してからNext**を選択する。

> ![](./media/image9.png)

10. On the **Connect to Azure
    ADページで、USERNAMEとPASSWORD** のボックスに**Office 365 Tenant
    資格情報を入力してからNext**を選択する。

> ![](./media/image10.png)

11. **Connect your
    directoriesページでContoso.comがFORESTの下にリストされることを確認してからAdd
    Directory**を選択する。

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image11.png)

12. In the **AD forest account**ウィザードに**Create New AD
    Account**オプションを選択して**、ENTERPRISE ADMIN
    USERNAME**フィールドに[**Contoso\Administrator**](urn:gd:lg:a:send-vm-keys),
    を入力して、!\![**Pa55w.rd**](urn:gd:lg:a:send-vm-keys)!!を**PASSWORD**フィールドに入力する**。OK**を選択して、**Next**を選択する。

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image12.png)
>
> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image13.png)

13. **Azure AD sign-in configurationページで** page, ensure that in
    the **USER PRINCIPAL
    NAME**のドロップダウンリストに **userPrincipalName**が選択されていることを確認する**。**

> ![](./media/image14.png)

14. **Continue without matching all UPN suffixes to verified
    domainsを選択してからNext**を選択する。

15. **Domain and OU filteringページでSync selected domains and
    Ous**を選択する。

16. Expand **Contoso.com**を拡張して**Contoso.com**の横のチェックボックスをオフにして、以下のチェックボックスのみがオンにしたことを確認する： **IT**, **Managers**, **Marketing**, **Research**,
    と **Sales**。**Next**を選択する。

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image15.png)

17. **Uniquely identifying your usersページでNext**を選択する。

18. **Filter users and devices** ページで**Nextを**選択する。

19. **Optional
    featuresページで利用可能なオプション**を確認するが変更をしません。**Password
    hash
    synchronization**が選択していることを確認し**、Next**を選択する。

> ![](./media/image16.png)

20. **Ready to configure**ページで**Start the synchronization process
    when configuration
    completes**が選択していることを確認してから**Install**を選択する。

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image17.png)

21. 構成は完了したら**Exit**を選択する。

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image18.png)
>
> **注:** この時点で、ローカルの Active Directory Domain Services (AD
> DS) と Microsoft Entra ID
> からのオブジェクトの同期が開始されます。このプロセスが完了するまで約3〜4分待つ必要があります.

22. 開いているすべてのウィンドウを閉じます。

タスク 2: Microsoft Entra IDで同期を確認する

1.  In the **Microsoft Edgeで新しいタブを開き、**Microsoft Entra admin
    Centerユーザーページに移動する-
    !\![**https://entra.microsoft.com/#view/Microsoft_AAD_UsersAndTenants/UserManagementMenuBlade/~/AllUsers/menuId/**](https://entra.microsoft.com/#view/Microsoft_AAD_UsersAndTenants/UserManagementMenuBlade/~/AllUsers/menuId/)!!
    サインインを求められた場合は、ラボ インターフェイスの \[Home\]
    タブから Office 365 Tenantの資格情報を使用します。

> ![A screenshot of a computer Description automatically
> generated](./media/image19.png)

2.  ローカル AD DS
    のユーザーが表示されていることを確認します。これらのユーザー**の
    \[On-premise sync enabled**\] 列の値が \[**Yes**\]
    であることを確認する。

> ![](./media/image20.png)

3.  ナビゲーションウィンドウで**Groupsを拡張してAll groups**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image21.png)

1.  ローカル AD DS () からのグループが表示されていることを確認する。

> ![A screenshot of a computer Description automatically
> generated](./media/image22.png)

4.  **Managers**グループを選択する**。**

> ![A screenshot of a computer Description automatically
> generated](./media/image23.png)

5.  **Managersグループページで** **Members**を選択して**、**ユーザーが表示されることを確認する**。**

> ![A screenshot of a computer Description automatically
> generated](./media/image24.png)
>
> ![A screenshot of a group of people Description automatically
> generated](./media/image25.png)
>
> **注意：このグループはローカルのAD
> DSから取得されるため、メンバーを追加したり削除したりすることはできません。**

15. Microsoft Edgeをクロースする。

**結果：**この手順が完了すると、Active Directory Domain Services から
Microsoft Entra ID に アイデンティティー を同期するように Microsoft
Entra Connect が正常に構成されます
