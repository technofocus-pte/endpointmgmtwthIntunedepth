**ラボ 10 - グループ ポリシー分析を使用して Microsoft Intune での GPO
サポートを検証する**

**要約**

このラボでは、グループ ポリシー分析を使用して Active Directory グループ
ポリシー オブジェクト (GPO) をインポートし、同等の Microsoft Intune MDM
ポリシーをサポートする設定を特定します。

**シナリオ**

Contoso 社では、従来、Active Directory の GPO
を使用して、ドメイン全体にコンピューターおよびユーザーのポリシー設定を展開してきました。そこで、サポートされているすべての
GPO 設定を Microsoft Intune
構成プロファイルに移行する予定です。「Windows クライアント
ポリシー」という GPO があります。グループ
ポリシー分析を使用して、Windows クライアント ポリシー GPO
の設定を検証し、Intune に正常に移行できる設定を特定する必要があります。

**タスク 1: Windows クライアント ポリシー GPO を XML
ファイルにエクスポートする**

1.  提供された資格情報を使用して[***SEA-SVR1***]()にログインし、検索バーに!!**Server
    Manager**!! を入力して選択する**。**

> ![](./media/image1.png)

2.  **Server Manager – Dashboard**に**Toolsを選択してGroup Policy
    Management**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)

3.  Group Policy
    Managementコンソールに**Forest:Contoso.com**、それから**Domains**、とそして**Contoso.com**を拡張して**Group
    Policy Objects**を選択する。

> 複数なGroup Policy Objectsがリストされていることを確認する。

4.  詳細のペインにGPOの**Windows Client Policy**を選択する。

> ![](./media/image3.png)

5.  **Windows Client Policy**を右クリックし**、Save Report**を選択する。

> ![](./media/image4.png)

6.  Save GPO Reportダイアログボックスで**Documents**を選択して **Save as
    typeをXML file**に変更し、**Save**を選択する。

> ![](./media/image5.png)

7.  Group Policy Managementコンソールを閉じる。

8.  Server Managerを閉じる。

**タスク 2: Group Policy Analyticsを使用してWindows Client
GPOを分析する。**

1.  Open Microsoft
    Edgeを開き、アドレスバーに!!**https://intune.microsoft.com**!!を入力して、**Enter**を押す。

2.  求めたらOffice 365 Tenant資格情報でサインインする。

3.  **Microsoft Intune admin center**に**、Devices**へ移動し、選択する。

> ![](./media/image6.png)

4.  **Manage devices**セクションに移動して**、Group Policy
    analytics**を選択する。

> ![](./media/image7.png)

5.  **Devices | Group Policy
    analytics** ブレードで**Import**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)

6.  **GPO file upload**タブで、以下の画像で示すよう**Select a
    file**検索バーの横にあるフォルダをクリックする 。

> ![A screenshot of a computer Description automatically
> generated](./media/image9.png)

7.  **Open**ボックスに**Documents**を選択して**Windows Client
    Policy.xml**を選択する。それから**Open**ボタンをクリックする**。**

> ![A screenshot of a computer Description automatically
> generated](./media/image10.png)

8.  **Next**ボタンをクリックする**。**

> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)

9.  **Scope tags**に**Next**ボタンをクリックする**。**

> ![A screenshot of a computer Description automatically
> generated](./media/image12.png)

10. **Review + create**タブに**Create**ボタンをクリックする**。**

> ![A screenshot of a computer Description automatically
> generated](./media/image13.png)

11. Windows Client Policy
    GPOが即時にインポートされ分析されます。**Import GPO
    files**ページを閉じる**。**

12. **Devices | Group Policy analytics**ブレードで **Windows Client
    Policy**の横にある情報をレビューする。

> 設定の 89% が MDM をサポートしていることに注意する。
>
> ![A screenshot of a computer Description automatically
> generated](./media/image14.png)

13. MDM Supportの下に**89%**を選択する。

> サポートされているSetting Name, MDM Support, CSP Name, と CSP Mapping
> を注意する。どの設定が対応するCSPマッピングがないについては、必ず注意する。
>
> ![A screenshot of a computer Description automatically
> generated](./media/image15.png)

14. **Windows Client Policy**ウィンドを閉じる**。**

**タスク 3: Review the Group Policy Analytics Summary Report**

1.  **Microsoft Intune admin
    center**ナビゲーションメニューに**Reports**を選択する。

> ![](./media/image16.png)

2.  **Reports**ページに**Device management**セクションで**Group Policy
    analytics**を選択する。

> ![](./media/image17.png)

3.  詳細ペインに**Summary**の下に**Refresh**を選択する。数回更新する必要がある可能性です

> サマリー レポートを更新して作成するには、5 分から 10
> 分かかる場合があります。

4.  **Group policy migration readiness**情報をレビューする**。**

> ![A screenshot of a computer Description automatically
> generated](./media/image18.png)
>
> 移行の準備ができているポリシーとサポートされていないポリシーが多数ある必要があります。

5.  **Reports**タブを選択して**、** **Group policy migration
    readiness**を選択する。

> ![A screenshot of a group policy migration Description automatically
> generated](./media/image19.png)

6.  **Generate report**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image20.png)

7.  Group policy migration
    readinessレポートが各設定とサポートされるプロファイルタイプに関して情報を提供します。

> ![A screenshot of a computer Description automatically
> generated](./media/image21.png)

8.  **Group policy migration readiness**ウィンドを閉じる**。**

**結果:** この手順を完了すると、GPO を正常にエクスポートし、グループ
ポリシー分析を使用して Intune
で同等のポリシー設定を検証できるようになります。
