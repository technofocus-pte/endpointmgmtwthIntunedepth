ラボ14 - Endpoint Configuration Managerを使用してアプリのデプロイ

**要約**

このラボでは、Microsoft Endpoint Configuration Manager
を使用して、アプリケーションをデスクトップ クライアント
ワークステーションにデプロイします。

**シナリオ**

Contoso 社は、オンプレミスの Active Directory
ネットワーク環境内のデスクトップ
ワークステーションを管理するために、Microsoft Endpoint Configuration
Manager を使用しています。Windows 11 Configuration Manager
クライアントに、Microsoft Power BI Desktop
という新しいアプリケーションを展開する必要があります。Endpoint
Configuration Manager 管理者は、既にアプリケーション
オブジェクトを作成しています。担当するタスクには、対象デバイスのコレクションの作成、配布ポイントへのアプリケーション
コンテンツの配布、そして対象コレクションに割り当てられた展開の作成が含まれます。SEA-CL1
のソフトウェア
センターにアプリケーションが表示されることを確認することで、このプロセスを検証します。.

タスク 1: デバイス コレクションを作成する

1.  Switch
    to [***SE-CFG1***](urn:gd:lg:a:select-vm)に切り替えて、[**Contoso\Administrator**](urn:gd:lg:a:send-vm-keys)としてサインインし、!\![**Pa55w.rd**](urn:gd:lg:a:send-vm-keys)!!パスワードを使用する。

2.  タスクバーで**Configuration Manager Consoleを選択する。**Microsoft
    Endpoint Configuration Managerコンソールが開きます。

> ![](./media/image1.png)

3.  **Assets and Compliance**ワークスペース内**、Device
    Collections**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)

4.  **Device** を右クリックし**、Create Device
    Collection**を選択する。Create Device Collection Wizardが開きます。

> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)

5.  **General**ページで以下を構成してから**Next**を選択する:

    - Name: !\![**Power BI App Deployment**](urn:gd:lg:a:send-vm-keys)!!

    - Comment: !\![**Devices targeted to install Power BI
      Desktop**](urn:gd:lg:a:send-vm-keys)!!

    - Limiting collection: **All Windows 11 Workstations**

> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

6.  **Membership RulesページでNext**を選択します。Configuration Manager
    警告で**OK**を選択する。
    直接のメンバーは、後のステップで追加します。

> ![A screenshot of a computer Description automatically
> generated](./media/image5.png)
>
> ![A screenshot of a computer error Description automatically
> generated](./media/image6.png)

7.  **Summary**ページで**Next**を選択してから**Completion**ページで**Close**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image7.png)
>
> **Power BI App Deployment**コレクションがDevice
> Collectionsリストに表示されます。
>
> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)

タスク 2: 既存のコレクションにデバイスを割り当てる

1.  **Assets and Compliance**ワークスペースに**Devices**を選択する。

> リストされているデバイスに注意する。緑色の円と白いチェックマークが付いているデバイスは、現在アクティブです。
>
> ![](./media/image9.png)

2.  詳細ウィンドに**SEA-CL1**を選択する。

3.  [***SEA-CL1***](urn:gd:lg:a:select-vm)を右クリックし、**Add Selected
    Items**にカーソルを移動して**Add Selected Items to Existing Device
    Collection**を選択する。

> ![](./media/image10.png)

4.  **Select Collection**ダイアログボックスで**Power BI App
    Deployment**を選択してから**OK**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)

5.  確認するために、**Assets and Compliance**ワークスペースで**Device
    Collections**を選択して**、Power BI App
    Deployment**をダブルクリックする。

> ![A screenshot of a computer Description automatically
> generated](./media/image12.png)
>
> [***SEA-CL1***](urn:gd:lg:a:select-vm)はこのコレクションのメンバーとしてリストされるはずです。 
>
> ![A screenshot of a computer Description automatically
> generated](./media/image13.png)

タスク 3: デプロイの種類を構成する

1.  Microsoft Endpoint Configuration Managerコンソールに**Software
    Libraryワークスペースを選択する。**

> ![A screenshot of a software library Description automatically
> generated](./media/image14.png)

2.  **Software Library**ワークスペースに**Application
    Management**を拡張してから**Applications**を選択する。

> ![A screenshot of a software library Description automatically
> generated](./media/image15.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image16.png)
>
> Endpoint Configuration Manager
> 管理者から作成されたアプリケーションに注意する。

3.  詳細ウィンドに**Microsoft Power BI Desktop (x64)**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image17.png)

4.  結果ウィンドに**Deployment Types**タブを選択する**。** Windows
    インストーラーに基づくデプロイの種類が 1 つあることに注意する。

> ![A screenshot of a computer Description automatically
> generated](./media/image18.png)

5.  **Microsoft Power BI Desktop (x64) - Windows
    installerデプロイメントタイプに右クリックしてからProperties**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image19.png)

1.  **PropertiesダイアログボックスでPrograms**を選択する。アプリケーションのインストール方法をメモします。msiexec
    を /q スイッチと共に使用し、静かなインストールを実行します。

> ![](./media/image20.png)

6.  **Properties**ダイアログボックスで**Requirements**タブ選択してから**Add**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image21.png)

7.  **Create
    Requirementダイアログボックスで以下を構成してからOK**を選択する。:

    - Category: **Device**

    - Condition: **Operating System**

    - Rule type: **Value**

    - Operator: **One of Windows 11 (Select the check box next to
      Windows 11)**

> ![A screenshot of a computer program Description automatically
> generated](./media/image22.png)

8.  In the **Properties大ログボックスにOK**を選択する。
    この要件により、Windows 11 以外のオペレーティング
    システムにアプリをインストールできなくなります。

> ![A screenshot of a computer Description automatically
> generated](./media/image23.png)

タスク 4: 配布ポイントにコンテンツを配布する

1.  **Software Library**ワークスペースに**Microsoft Power BI Desktop
    (x64)**を選択する。

2.  **Microsoft Power BI Desktop (x64)**を右クリックし**、Distribute
    Content**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image24.png)

3.  **General**ページで**Next**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image25.png)

4.  **ContentページでNext**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image26.png)

5.  **Content Destination**ページで**Add**を選択し**、Distribution
    Point**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image27.png)

6.  **Add Distribution
    Points**ダイアログボックスで **SEA-CFG1.CONTOSO.COM**の横にあるチェックボックスをオンにして**、OK**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image28.png)

7.  **Content Destination**ページで**Next**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image29.png)

8.  **Summary**ページで**Next**を選択して**Close**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image30.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image31.png)

9.  **Summary**タブで**Content Status**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image32.png)
>
> Microsoft Power BI Desktop の「Content
> Status」ページが開きます。結果ペインで、緑色の円が表示され、その横に「Success:1」と表示されていることを確認します。これは、コンテンツが配布ポイントに配布され、デバイスに展開できる状態になったことを示します。リボンの「Refresh」ボタンを選択する必要がある場合があります。
>
> ![A screenshot of a computer Description automatically
> generated](./media/image33.png)

10. 右上隅にある**Back to Applications**矢印を選択して**、**Software
    Library Applicationsノードに戻ります。

タスク 5: デプロイの作成

1.  **Software LibraryワークスペースにMicrosoft Power BI Desktop
    (x64)**を選択する。

2.  **Microsoft Power BI Desktop
    (x64)**を右クリックし**、Deploy**を選択する**。Deploy Software
    Wizard**が開きます。

> ![A screenshot of a computer Description automatically
> generated](./media/image34.png)

3.  **General**ページで**Collection**の横に**Browse**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image35.png)

4.  **Select Collection**ページで**、User
    Collections**を選択してから**Device Collections**を選択する。

5.  **Device Collections**リストに**Power BI App
    Deployment**を選択し**、OK**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image36.png)

6.  **General**ページで**Next**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image37.png)

7.  **Content**ページで**Next**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image38.png)

8.  On the **Deployment
    Settings**ページで**Action**が**Installに**設定していることを確認、と**Purpose**が**Available**に設定していることを確認する**。Next**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image39.png)

1.  **Scheduling**ページで**Next**を選択する**。**
    このアプリケーションは、デフォルトでできるだけ早く利用可能になります。

> ![A screenshot of a computer Description automatically
> generated](./media/image40.png)

9.  **User Experience**ページで**User notifications**の横に**Display in
    Software Center and show all
    notifications**を選択する。**Next**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image41.png)

10. **Alerts**ページで**Next**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image42.png)

11. **Summary**ページで**Next**を選択してから**Close**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image43.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image44.png)

12. 結果ウィンドに**Deployments**タブでデプロイメントが表示されることを確認する。

> ![A screenshot of a computer Description automatically
> generated](./media/image45.png)

13. Microsoft Endpoint Configuration Managerコンソールを閉じる。

14. [***SEA-CFG1***](urn:gd:lg:a:select-vm)からサインアウトする。

タスク 6: ソフトウェア
センターによりデプロイされたアプリをインストールする

1.  Switch
    to [***SEA-CL1***](urn:gd:lg:a:select-vm)に切り替えて[**Contoso\Administrator**](urn:gd:lg:a:send-vm-keys)としてサインインし、!\![**Pa55w.rd**](urn:gd:lg:a:send-vm-keys)!!パスワードを使用する。

2.  **Start Menu**にクリックし**、Control Panel**に入る。

3.  結果で**Control Panel**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image46.png)

4.  **Control panel**中に**System and Security**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image47.png)

5.  **System and Security**の中に**Configuration Manager**を選択する。
    Configuration Manager Propertiesが表示される。

> ![A screenshot of a computer Description automatically
> generated](./media/image48.png)

6.  **Configuration Manager
    Properties**ダイアログボックスで**Actions**タブを選択する。 

> ![A screenshot of a computer program Description automatically
> generated](./media/image49.png)

7.  **Actions**タブで**Machine Policy Retrieval & Evaluation
    Cycle**を選択してから**Run
    Now**を選択する**。**メセッジプロンプトで**OK**を選択する。

> ![A screenshot of a computer program Description automatically
> generated](./media/image50.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image51.png)

8.  **Configuration Manager
    Properties**を閉じるために**OK**を選択してから**Control
    Panel**を閉じる。

> ![A screenshot of a computer program Description automatically
> generated](./media/image52.png)

9.  通知の領域で**New Software is Available**を選択してから**Open
    Software
    Center**を選択する**。**アイコンを表示するために通知領域を拡張する必要がある可能性です。

> ![](./media/image53.png)
>
> If the Software Center does not launch, then click on the
> ソフトウェアセンターが起動しない場合は**Start
> Menuをクリックして、下にスクロールしてから**!!**Software
> Center**!\!にクリックする。
>
> ![A screenshot of a computer Description automatically
> generated](./media/image54.png)

10. **Software
    CenterにApplications**ページで利用可能の新しいアプリケーション**Microsoft
    Power BI Desktop
    (x64)**を注意する**。**このアプリケーションは、 前に作成された**Power
    BI App
    Deployment**コレクションのメンバーであるどのデバイスにも利用可能となります。

> ![A screenshot of a computer Description automatically
> generated](./media/image55.png)

11. **Microsoft Power BI Desktop
    (x64)**を選択してから**Install**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image56.png)
>
> ![](./media/image57.png)
>
> アプリケーションはユーザー入力なしでダウンロードおよびインストールされます。デスクトップに**Power
> BI Desktop**のショートカットが表示されれば、インストールは成功です。
>
> ![A screenshot of a computer Description automatically
> generated](./media/image58.png)

12. Software Centerを閉じる。

13. [***SEA-CL1***](urn:gd:lg:a:select-vm)からサインアウトする。

**結果**: この手順を完了すると、Microsoft Endpoint Configuration Manager
を使用して、アプリケーションをデスクトップ クライアント
ワークステーションに正常に展開できます.
