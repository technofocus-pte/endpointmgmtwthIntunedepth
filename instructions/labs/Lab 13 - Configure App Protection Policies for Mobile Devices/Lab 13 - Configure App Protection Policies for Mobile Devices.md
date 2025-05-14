ラボ 13: モバイル デバイスのアプリ保護ポリシーを構成する

**要約**

このラボでは、モバイル デバイスのアプリ保護ポリシーを構成します.

**シナリオ**

Contoso 社の開発者全員が、最新の iOS/iPadOS を搭載した iPhone と iPad
を使用しています。セキュリティ部門はデータ漏洩を懸念しており、社内メールのデータがモバイルデバイス上の他のアプリにコピーされるのを防ぎたいと考えています。セキュリティ部門の懸念事項に対応するソリューションを提供する必要があります。具体的には、以下の点を確認する必要があります：

- • Outlook データは iTunes または iCloud
  へのバックアップを制限してください。

- • ポリシー管理対象アプリのみが Outlook とのデータの送受信を行えます。

- • ポリシー管理対象アプリのみが Outlook
  での切り取り、コピー、貼り付けを行えます。

- • ユーザーは Outlook
  にアクセスするために、職場または学校のアカウントの資格情報を提供する必要があります。.

タスク 1: iOS/iPadOS デバイスのアプリ保護ポリシーを作成する

1.  必要に応じて、[***SEA-SVR1***](urn:gd:lg:a:select-vm)で [**Contoso\Administrator**](urn:gd:lg:a:send-vm-keys)として、!\![**Pa55w.rd**](urn:gd:lg:a:send-vm-keys)!!をでサインインする。

2.  On the タスクバーで **Microsoft Edgeを選択してから** **Microsoft
    Intune admin
    center**に移動する。アドレスバ‐に !!**https://intune.microsoft.com**!!を入力して、**Enter**を押します。

3.  ホームタブからOffice 365 Tenant
    アドミンの資格情報を使用してサインインする。

4.  **Microsoft Intune admin center**ページで**Apps**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image1.png)

5.  **Apps | Overviewブレードで、** **Policyの下に** **App protection
    policies**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)

6.  詳細ペインで**+Create
    policyを選択して、** **iOS/iPadOS**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)

7.  **Basicsタブで、以下のオプションを構成してNext**を選択する。

    - Name: !\![**Outlook – Developers**](urn:gd:lg:a:send-vm-keys)!!

    - Description: !\![**Policy to prevent cut/copy and paste from
      Outlook**](urn:gd:lg:a:send-vm-keys)!!

> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

8.  **Appsタブで** + **Select public apps**をクリックする。

9.  On the **Select apps to
    target**ブレードで**、テキストボックスに**!!**Outlook**!!を入力して**Microsoft
    Outlook**を選択し、**Select**ボタンを選択してから**Next**を選択する。

> ![Screens screenshot of a computer Description automatically
> generated](./media/image5.png)

10. **Data
    protectionタブで以下のオプションを構成して、Next**を選択する。

    - Backup Org data to ITunes and iCloud backups: **Block**

    - Send Org data to other apps: **Policy managed apps**

    - Receive data from other apps: **Policy managed apps**

    - Restrict cut, copy, and paste between other apps: **Policy managed
      apps**

> 他のすべての設定はデフォルトのままにします。
>
> ![](./media/image6.png)

11. **Access
    requirements**タブで以下のオプションを構成してから**Next**を選択する：

    - PIN for access: **Not required**

    - Work or school account credentials for access: **Require**

> ![A screenshot of a computer Description automatically
> generated](./media/image7.png)

12. **Conditional
    launch**タブで、設定を確認してから **Next**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)
>
> **注:**
> ここでは、アクセス保護ポリシーのサインインセキュリティ要件を設定できます。設定を選択し、会社のアプリにサインインするためにユーザーが満たす必要がある値を入力できます。各種設定をメモして置く、ただし、何も変更しない**。**.

13. **Assignments**タブで**Next**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image9.png)

14. **Review + create**タブで、**設定を確認して、Create**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image10.png)

15. **Apps | App protection
    policies**ブレードで、詳細のウィンドに、**Outlook -
    Developers** がリストされていることを確認する。

> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)

16. Microsoft Edgeを閉じる。

**結果**: この**手順**を完了すると、モバイル
デバイスのアプリ保護ポリシーが正常に構成されます。
