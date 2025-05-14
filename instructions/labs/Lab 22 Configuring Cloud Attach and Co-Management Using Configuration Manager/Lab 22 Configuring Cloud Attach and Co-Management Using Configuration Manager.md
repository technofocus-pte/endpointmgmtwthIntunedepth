ラボ 22: Configuration Manager を使用したCloud
AttachとCo-managementの構成

**要約**

このラボではMicrosoft Endpoint Configuration Manager と Microsoft Intune
を使用して、Cloud Attach を有効にして、Co-Managementを構成します

**前提 条件**

このラボの前に、次のラボを完了する必要があります。

- ラボ 01 - Microsoft Entra ID での ID の管理

- ラボ 02 - Azure AD Connect を使用した ID の同期

- ラボ 03-Microsoft Entra ID 参加の構成と管理

- ラボ 05 - Intune へのデバイス登録の管理

**シナリオ**

Contoso 社は、Microsoft Endpoint Configuration Manager と Microsoft
Intune の両方を導入しています。この 2
つのサービス間の統合を構成し、管理対象 Windows
デバイスのco-managementを有効にする必要があります。Cloud Attach
を有効にし、co-managementを構成してから、SEA-CL1
を使用して設定を検証します。.

タスク 1: 環境の準備

1.  [***SEA-SVR1***](urn:gd:lg:a:select-vm)に切り替えて、 [**Contoso\Administrator**](urn:gd:lg:a:send-vm-keys) としてサインインし、 !\![**Pa55w.rd**](urn:gd:lg:a:send-vm-keys)!!
    パスワードを使用する。

2.  Server Managerから**Tools**を選択してから**Active Directory Users
    and Computers**を選択する。

> ![](./media/image1.png)

3.  ナビゲーションウィンドウで**Seattle Clients**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)

4.  **SEA-CL1**を右クリックしてから**Move**を選択する。

> ![A computer screen shot of a computer Description automatically
> generated](./media/image3.png)

5.  **Move**ダイアログボックスに**Entra
    clients**を選択してから**OK**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

6.  **Active Directory Users and Computers**を閉じる。

7.  タスクバーで**Startを右クリックし、Windows Powershell
    (Admin)**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image5.png)

8.  **Windows
    PowerShellウィンドに**次のコマンドを入力してから**Enter**を押す。

> !!**Start**-ADSyncSyncCycle -PolicyType **Initial**!!
>
> ![A screenshot of a computer screen Description automatically
> generated](./media/image6.png)

9.  PowerShellウィンドを閉じる。

10. [***SEA-CL1***](urn:gd:lg:a:select-vm)に切り替える。

11. タスクバーで**Start**を右クリックし、**Shut down or sign
    out**を選択してから**Restart**を選択する。

> ![](./media/image7.png)
>
> **注**: 再起動すると、SEA-CL1 でのハイブリッド Azure AD
> joinがトリガーされます。

12.  [***SEA-CL1***](urn:gd:lg:a:select-vm)は再起度されたら[**Contoso\Administrator**](urn:gd:lg:a:send-vm-keys) としてサインインし、[**Pa55w.rd**](urn:gd:lg:a:send-vm-keys)パスワードを使用する。

13. タスクバーで**Start**を右クリックし、**Windows Terminal
    (Admin)**を選択する。

> ![](./media/image8.png)

14. **Windows
    PowerShell**ウィンドに以下のコマンドを入力してから**Enter**を押す。

> !!dsregcmd /**status**!!

15. アウトプットに、**Device State**の下で**AzureAdJoined :
    YES** と **DomainJoined : YES** が表示されていることを確認する。

> ![](./media/image9.png)
>
> **注**: デバイスがまだ Azure AD にjoinしていない場合は、Azure AD
> Connect の同期が完了するまで待ってから、SEA-CL1 を再度再起動します.

16. [***SEA-CL1***](urn:gd:lg:a:select-vm)上全てのウィンドを閉じる。

タスク 2: デバイス コレクションを作成する

1.  [***SEA-CFG1***](urn:gd:lg:a:select-vm)に切り替えて、[**Contoso\Administrator**](urn:gd:lg:a:send-vm-keys) としてサインインし、 [**Pa55w.rd**](urn:gd:lg:a:send-vm-keys)パスワードを使用する。

2.  タスクバーで **Configuration Manager Console**を選択する。Microsoft
    Endpoint Configuration Managerコンソールが開きます。

> ![A screenshot of a computer Description automatically
> generated](./media/image10.png)

3.  **Assets and Compliance**ワークスペースに**Device
    Collections**を選択する。

4.  **Device Collections**を右クリックし、**Create Device
    Collection**を選択する。Create Device Collection Wizardが開きます。

> ![](./media/image11.png)

5.  **Generalページに、以下を構成してからNext**を選択する：

    - Name: !\![**Co-managed Devices**](urn:gd:lg:a:send-vm-keys)!!

    - Limiting collection: **All Desktop and Server Clients**

> ![](./media/image12.png)
>
> ![](./media/image13.png)
>
> ![](./media/image14.png)

6.  **Membership RulesページでNext**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image15.png)

1.  Configuration Manager警告に**OK**を選択する。
    直接のメンバーは、後の手順で追加します。

> ![A screenshot of a computer error Description automatically
> generated](./media/image16.png)

7.  **Summary**ページで**Next**を選択してから**Completion**ページで**Close**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image17.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image18.png)

タスク 3: 既存のコレクションにデバイスをアサインする

1.  **Assets and ComplianceワークスペースにDevices**を選択する。

> リストされているデバイスに注意する。白いチェックマークが付いた緑の円があるデバイスは現在アクティブです。

2.  詳細のペインに**SEA-CL1**を選択する。

3.  **SEA-CL1**を右クリックし、**Add Selected Items**へ移動してから**Add
    Selected Items to Existing Device Collection**を選択する。

> ![](./media/image19.png)

4.  **Select Collection**ダイアログボックスで**Co-managed
    Devices**を選択してから**OK**を選択する。

> ![](./media/image20.png)

5.  確認するために、**Assets and ComplianceワークスペースにDevice
    Collectionsを選択してからCo-managed Devices**をダブルクリックする。

> ![](./media/image21.png)
>
> ![](./media/image22.png)
>
> **SEA-CL1は、このコレクションのメンバーとしてリストされるはずです。**

タスク 4: クラウド接続Endpoint Configuration Manager

1.  Microsoft Endpoint Configuration
    Managerコンソールに**Administrationワークスペースにを選択する。**

> ![](./media/image23.png)

2.  **AdministrationワークスペースにCloud
    Services**を拡張してから**Cloud Attach**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image24.png)

3.  リボン中に**Configure Cloud Attach**を選択する。**Cloud Attach
    Configuration Wizard**が開きます。

> ![](./media/image25.png)
>
> ![](./media/image26.png)

4.  **Cloud Attach Configuration Wizard**に**Cloud attachページでSign
    In**を選択する。

5.  [**admin@M365x19242953.onmicrosoft.com**](urn:gd:lg:a:send-vm-keys) としてサインインし、パスワード [**9whL~;H8ke=D1^95%D**](urn:gd:lg:a:send-vm-keys)を使用する。

6.  **Cloud attachページでCustomize
    settings**を選択してから**Next**を選択する。

> ![](./media/image27.png)

7.  **Create AAD Application警告でYes**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image28.png)

8.  **Configure
    uploadページで**デフォルトを受け取り、**Next**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image29.png)

9.  **Enablement**ページで**Automatic enrollment in
    Intune**の横に**Pilot**を選択する。

10. **Enablement**ページで**Intune Auto
    Enrollment**の横に**Browse**を選択する。

> ![](./media/image30.png)

11. **Select Collection**ダイアログボックスに**Co-managed
    Devices**を選択してから**OK**を選択し、**Next**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image31.png)

12. **Summary**ページで**Next**を選択して**、Completion**ページで**Close**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image32.png)

タスク 5: Workloadsの構成

1.  Microsoft Endpoint Configuration
    Managerコンソールに**Administration**ワークスペースを選択する**。**

2.  **Administration**ワークスペースに**Cloud
    Services**を拡張してから**Cloud Attach**を選択する。

3.  詳細のペインに**CoMgmtSettingsProd**を選択して、リボンから**Properties**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image33.png)
>
>  **CoMgmtSettingsProd Properties**ボックスが開きます**。**

4.  **Workloads**を選択する。**Workloads**ページで次のワークロードでスライダーを**Pilot
    Intune**に移動する**：**

    - **Compliance policies**

    - **Client apps**

    - **Windows Update policies**

> ![](./media/image34.png)

5.  **Staging page**を選択する。**Stagingページで** **Compliance
    policies**, **Client Apps**, と**Windows Update
    Policies**の横にある**Browse**を選択して**、**各ワークロードに対して**Co-managed
    Devices**コレクションを選択する**。**

6.  **CoMgmtSettingsProd
    Properties**ボックスを**Close**するために**OK**を選択する**。**

> ![](./media/image35.png)

タスク 6: SEA-CL1 が共同管理されていることの検証

1.  [***SEA-SVR1***](urn:gd:lg:a:select-vm)に切り替える。

2.  タスクバーで**Microsoft
    Edge**を選択して、アドレスバーに[**https://entra.microsoft.com**を入力してから**Enter**](https://entra.microsoft.comを入力してからEnter)を押す。

3.  ユーザ [**admin@M365x19242953.onmicrosoft.com**](urn:gd:lg:a:send-vm-keys)としてサインインし、パスワードを使用する。

4.  **Stay signed in?　**プロンプトが表示したら**No**を選択する。

> Microsoft Entraアドミンセンターが開きます。

5.  Microsoft
    Entraアドミンセンターに、ナビゲーションウィンドウで**Identity**を選択する。

> ![](./media/image36.png)

6.  **Devices|All
    devices**ページに**SEA-CL1**がリストされることと、**Join
    Type** は **Microsoft Entr hybrid Join**であることを確認する。

> ![](./media/image37.png)

7.  Microsoft
    Edgeで他のタブを開き、アドレスバーに [**https://intune.microsoft.com**](https://intune.microsoft.com) を入力してから**Enter**を押す。

8.  ナビゲーションウィンドウで**Devices**を選択してから**All
    devices**を選択する。

9.  Verify that **SEA-CL1**がリストされること**、**と**Managed
    by**の設定が**Co-managed**であることを確認する。

> ![](./media/image38.png)
>
> 表示されるまで時間がかかる場合があります。必要に応じて詳細ペインを更新してください。マシンが別の名前で表示される場合は、デバイスをクリックして「**SEA-CL1**」と表示されていることを確認してください。

10. **SEA-CL1**を選択して、詳細のペインにスクロールダウンして**、**Co-managementの状態に関連情報を表示する。 

11. Microsoft Edgeを閉じる。

**結果: この手順を完了すると、クラウド
アタッチを正常に有効化し、Microsoft Endpoint Configuration Manager と
Microsoft Intune を使用して**co-management**を構成しました。**
