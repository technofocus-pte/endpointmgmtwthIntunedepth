ラボ 16 - Microsoft Entra のユーザー アカウントのセルフサービス
パスワード リセットの構成

**要約**

このラボでは、Microsoft Entra ID のユーザー アカウントのSelf service
password reset (SSPR) を構成および検証します。

**Prerequisites**

このラボの前に次のラボが完了する必要です：

1.  ラボ \#2 - Microsoft Entra Connect を使用した ID の同期

2.  ラボ \#5 - Microsoft Intune へのデバイス登録の管理

**シナリオ**

ヘルプデスクから、パスワードのリセットに関するサポートチケットが多数寄せられているとの報告を受けました。ユーザーが自身のパスワードをリセットするための解決策を提案していただくよう依頼されています。AD
DSから同期されているアカウントの場合、このプロセスでMicrosoft EntraとAD
DSの両方のパスワードをリセットする必要があります。

タスク 1: パスワードの書き戻しを構成する

1.  [***SEA-SVR1***](urn:gd:lg:a:select-vm)に、!!**[Contoso\Administrator](urn:gd:lg:a:send-vm-keys)!!としてログインし、**!!**[Pa55w.rd](urn:gd:lg:a:send-vm-keys)!!** パスワードを使用して、**Server
    Manager**を閉じる。

2.  デスクトップで**Azure AD Connect**をダブルクリックする。

> ![A screenshot of a computer Description automatically
> generated](./media/image1.png)

3.  **Welcome to Azure AD Connectページで** **Configure**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)

4.  **Additional タスクページで、Customize synchronization
    options**を選択して、**Next**を選択する、

> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)

5.  **Connect to Azure
    ADページで、必要に応じて** !!**admin@M365xXXXXXXX.onmicrosoft.com!!** を入力し、**USERNAME** に**PASSWORD**
    を入力して、**Nextを選択する。**.

> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

6.  **Connect to your directories**ページで**Next**を選択する

7.  **Domain and OU filteringページでNext**を選択する。

8.  **Optional featuresページにPassword
    writeback**を選択して、**Next**を設定する。

> ![A screenshot of a computer Description automatically
> generated](./media/image5.png)

9.  **Ready to configureページでConfigure**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image6.png)
>
> ![A computer screen shot of a computer Description automatically
> generated](./media/image7.png)
>
> **注**: 構成には数分かかる場合があります.

10. **Configuration complete**ページで**Exit**選択託する。

> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)

タスク 2: セルフサービス パスワード リセットを有効にする.

1.  タスクバーで**Microsoft Edge**を選択して、**Microsoft Entra admin
    center** **https://Entra.Microsoft.com**に移動する。

2.  **Office 365 Tenant admin**の資格情報でログインする。

> ![A screenshot of a computer Description automatically
> generated](./media/image9.png)
>
> **Microsoft Entra admin center**が開きます。

3.  **Microsoft Entra admin
    center**に、ナビゲーションウィンドウでで**Identity**を拡張してから**Users**を選択する。

4.  **UsersのナビゲーションウィンドウにPassword reset**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image10.png)

5.  **Password reset |
    PropertiesウィンドにAllを選択することにより、全てのユーザーに対してセルフサービスパスワードれせっとを有効にします。Save**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)
>
> ![A screenshot of a computer screen Description automatically
> generated](./media/image12.png)

6.  **Password reset | Properties**ブレードで**、Authentication
    methods**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image13.png)

7.  Methods available to usersに対して**Mobile Phone**と
    **Email**が選択されていることを確認し**、Security
    Questions**を選択する。

8.  **Number of questions required to
    register**に対して**3**を選択する。

9.  **Number of questions required to reset**に対して**3**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image14.png)

10. **Select security questions**セクションに**No security questions
    configured**を選択してから**Predefined**を選択する。 任意の質問を 3
    つ選択し、\[**OK**\] を 2 回選択します。

> ![A screenshot of a computer Description automatically
> generated](./media/image15.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image16.png)

11. **Save**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image17.png)

12. **Registration**を選択し**、Require users to register when signing
    inに対してYes**を選択する、 と **Number of days before users are
    asked to re-confirm their authentication
    information**に対して値を**90**に設定してから**Save**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image18.png)

13. ナビゲーションウィンドウで**On-premises integration**を選択する。

14. オンプレミスのライトバッククライアントが実行中であることを確認し、「
    **Enable password write back for synced
    users**」チェックボックスがオンになっていることを確認します。必要に応じて、**Save**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image19.png)

15. Microsoft Edgeを閉じる。

タスク 3: セルフサービス パスワード リセットの検証

1.  [***SEA-WS3***](urn:gd:lg:a:select-vm)に切り替える。必要に応じて、!!**[Admin](urn:gd:lg:a:send-vm-keys)!!** としてサインインし、!!**[Pa55w.rd](urn:gd:lg:a:send-vm-keys)!!**パスワードを使用する。

2.  タスクバーで**Microsoft
    Edge**を選択する。!!**https://mysignins.microsoft.com/!!**に観覧する。

3.  **Pick an account**ページで**Use another account**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image20.png)

4.  **Sign
    inページで** !!**Cindy@M365xXXXXXX.onmicrosoft.com!!** を入力し、**Next**を選択する。

&nbsp;

1.  **Enter password**ページで **!!P@55w.rd1234!!** を入力し、**Sign
    in**を選択する**。** Microsoft Edge
    でパスワードの保存を求められた場合は、\[**Save**\] を選択します。

> ![A screenshot of a computer error Description automatically
> generated](./media/image21.png)

1.  「**More information
    required」**と入力するよう求められますので、「**Next**」をクリックします。

> ![A screenshot of a computer error Description automatically
> generated](./media/image22.png)

5.  情報を入力し、**Next**を選択する**。**

> ![A screenshot of a computer Description automatically
> generated](./media/image23.png)

1.  **6**桁のコードを入力し、\[**Next**\]をクリックします

> ![](./media/image24.png)

6.  またNextをクリックする。

> ![A screenshot of a computer Description automatically
> generated](./media/image25.png)

7.  **Done**をクリックする。

> ![](./media/image26.png)

8.  **My Account**ページに移動できます。

> ![](./media/image27.png)

9.  **Password**を変更するためにリンクをみる -
    **!!https://mysignins.microsoft.com/security-info!!**

10. Text +XXXXXXXXXXXXXXをクリックして検証を完了する。

> ![A screenshot of a computer error Description automatically
> generated](./media/image28.png)

11. 6-桁のコードを提供してVerifyをクリックする。

> ![A screenshot of a computer error Description automatically
> generated](./media/image29.png)

12. **Skip for now**をクリックする。

> ![A screenshot of a computer error Description automatically
> generated](./media/image30.png)

13. **Security info**ページで**Password**に対して**Change**
    をクリックする。![A screenshot of a login page Description
    automatically generated](./media/image31.png)

14. **Change your
    password**ページで以下の情報を入力し**、Submit**を選択する：

    - Create new password: **!!P@55w.rd12345!!**

    - Confirm new password: **!!P@55w.rd12345!!**

> ![A screenshot of a login box Description automatically
> generated](./media/image32.png)

15. Doneボタンをクリックする。

> ![](./media/image33.png)

16. Microsoft
    Edgeをクロースして[***SEA-WS3***](urn:gd:lg:a:select-vm)からサインアウトする。

タスク 4: RAzure AD Connect Syncを実行

この手順は通常、パスワード
ライトバックには必要ありませんが、ラボ環境に固有の問題に対処し、AD DS が
Microsoft Entra と同期されていることを確認するために推奨されます。

1.  [***SEA-SVR1***](urn:gd:lg:a:select-vm)に切り替えて**Start**を右クリックし**、Windows
    PowerShell (Admin)**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image34.png)

2.  **Windows
    PowerShell**コマンドプロンプトで以下のコマンドを入力し**、Enter**を押します：

> **!!Start-ADSyncSyncCycle -PolicyType Delta!!**
>
> ![A screenshot of a computer Description automatically
> generated](./media/image35.png)

3.  Windows PowerShellをクロースして、約3-4分を待つ。

タスク 5: パスワードの書き戻しを確認する

1.  [***SEA-CL1***](urn:gd:lg:a:select-vm)に切り替えて必要に応じて、サインアウトする。[***SEA-CL1***](urn:gd:lg:a:select-vm)で、**Other
    user**を選択して、!!**Contoso\Cindy!!** としてサインインを試み、!!**P@55w.rd1234!!**
    パスワードを使用する**。**

> ![A screenshot of a computer Description automatically
> generated](./media/image36.png)

1.  ユーザー名またはパスワードが正しくないというメッセージが表示されることを確認する。

> ![A screenshot of a computer screen Description automatically
> generated](./media/image37.png)

2.  SSPR機能を使用して設定したパスワード!!P@55w.rd12345!!を使用して、!!Contoso\Cindy!!としてサインインします。

3.  今回は**新しいパスワード**で正常にサインインできるはずです。

これは、My Sign in ポータルで変更したパスワードがローカルの Active
Directory Domain Services (AD DS)
アカウントに書き戻されたことを確認します。

![A screenshot of a computer error Description automatically
generated](./media/image38.png)

> **注** –
> ログイン中に上記のメッセージが表示された場合は、***認証は成功した***ものの、グループメンバーシップの問題によりアカウントにSEA-CL1へのログイン権限がなかったことを示しています。.

**結果**: この手順を完了すると、セルフサービス パスワード
リセットの構成と検証が正常に完了します。
