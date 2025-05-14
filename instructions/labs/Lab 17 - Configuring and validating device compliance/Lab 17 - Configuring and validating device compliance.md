ラボ17 - デバイスのコンプライアンスの構成と検証

**要約**

このラボでは、管理対象デバイスのステータスを決定するために使用されるコンプライアンス
ポリシーと関連する条件付きアクセス
ルールを構成することによって、デバイスのコンプライアンスを検証します。

**Prerequisites**

このラボの前に、次のラボを完了する必要があります:

1.  ラボ \#1 - Microsoft Entra ID での ID の管理

2.  ラボ \#2 - Microsoft Entra Connect を使用した ID の同期

3.  ラボ \#5 - Microsoft Intune へのデバイス登録の管理

4.  ラボ \#6 - Microsoft Intune へのデバイスの登録

5.  ラボ \#7 - 構成プロファイルの作成と展開

手順 1: コンプライアンスポリシーの設定。

**シナリオ**

Contoso 社は、Microsoft Intune に登録されている Windows
デバイスが最小構成仕様を満たしていることを確認すると考えています。必要な仕様は次のとおりです：

- Windowsオペレーティングシステムの最小バージョン:10.0.19041.329

&nbsp;

- Microsoft Defender マルウェア対策が必要です。

デバイスがこれらの要件を満たしている場合は、「準拠」とマークされます。デバイスがこれらの要件を満たしていない場合は、「非準拠」とマークされます。

タスク 1: コンプライアンス ポリシーを作成して割り当てる

1.  [***SEA-SVR1***](urn:gd:lg:a:select-vm)にサインインするために !!**[Contoso\Administrator](urn:gd:lg:a:send-vm-keys)!!** として、パスワード !!**[Pa55w.rd](urn:gd:lg:a:send-vm-keys)!!** を使用する。

2.  タスクバーで**Microsoft Edge**を選択する。Microsoft
    Edgeでアドレスバーに !!**https://Intune.microsoft.com!!** を入力し、 **Enter**を押します。

3.  **Office 365 Tenant Admin 資格情報でサインインする。**

> ![A screenshot of a computer Description automatically
> generated](./media/image1.png)

4.  ナビゲーションウィンドウで**Devices**を選択し、**Manage
    devices**の下に**Compliance** を選択する。![A screenshot of a
    computer Description automatically generated](./media/image2.png)

5.  **Compliance | Policies**ブレードに、詳細のウィンドに**+ Create
    Policy**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)

6.  **Create a policy**ブレードで次の値を提供して**Create**を選択する：

    - Platform: **Windows 10 and later**

> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

7.  **Basics**タブで次の値を提供して**Next**を選択する：

    - Name: !!**[Compliance1](urn:gd:lg:a:send-vm-keys)!!**

> ![](./media/image5.png)

8.  **Compliance settings**タブで**Device
    Health**を拡張して 、使用可能な設定を確認する。

> ![A screenshot of a computer Description automatically
> generated](./media/image6.png)

9.  **Compliance settings**タブで**Device
    Properties**を拡張する。**Minimum OS
    version**フィールドに!!**[10.0.19041.329](urn:gd:lg:a:send-vm-keys)!!**を入力する**。**

> ![A screenshot of a computer Description automatically
> generated](./media/image7.png)

10. **Compliance settings**タブで**System Security**を拡張する。 Set
    the **Microsoft Defender
    Antimalware**設定を**Require**と設定し**、Next**を選択する。

> ![](./media/image8.png)

11. **Actions for noncompliance**タブで **Mark device noncompliant**
    のデフォルト設定は**immediately** であることに注意する。

> ![A screenshot of a computer Description automatically
> generated](./media/image9.png)
>
> デバイスが非準拠とマークされるまでの日数を設定する方法と、追加のアクションを設定する方法を確認します。

12. **Next**を選択する。**Assignmentsタブで** **Add
    groupを選択する。Windows
    Devices**を選択して、**Select**を選択し、**Next**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image10.png)
>
> **Note**: The **Windows Devicesグループは、** Creating and Deploying
> Configuration Profiles – Labに作成されました。

13. **Create**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)

14. ナビゲーションメニューで**Devices**を選択して、デバイスナビゲーションウィンドウでComplianceを選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image12.png)

15. **Compliance**ページで**Compliance settings**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image13.png)

16. **Compliance policy settings**ページで、**Mark devices with no
    compliance policy assigned as**の横に、**Not
    Compliant** を選択してから**Save**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image14.png)
>
> この設定により、コンプライアンスポリシーが割り当てられていないデバイスは**Not
> compliant**に設定されます。.

**結果:**
この手順を完了すると、コンプライアンスポリシーが正常に構成されます。

手順 2: コンプライアンスを適用するための条件付きアクセス
ポリシーを作成する。

**シナリオ**

ユーザーがnon-compliantとマークされたデバイスを使用する場合、メールにアクセスできないようにする必要があります。このルールを適用する条件付きアクセスポリシーを構成し、期待どおりに機能することを確認することを要求された。

タスク 1: 条件付きアクセス ポリシーを作成する

1.  [***SEA-SVR1***](urn:gd:lg:a:select-vm)で、**Microsoft Intune admin
    center** に、**Devices**を選択してから**Conditional
    access**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image15.png)

2.  **Policies**をクリックして**、+ New policy**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image16.png)

3.  **New**ブレードで**、Name**のテキストボックスに!\![**Conditional1!! **](urn:gd:lg:a:send-vm-keys)を入力して、**0
    users or workload identities selected**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image17.png)

4.  **Users and groups**ブレードで**All users**ラジオボタンを選択する。

> ![A screenshot of a computer screen Description automatically
> generated](./media/image18.png)

5.  **New**ブレードで**No target resources
    selected**を選択して、**Select
    apps**のラジオボタンを選択し**、** !!**Office 365 Exchange
    Online!!**を選択してから**Select**をクリックする。

> ![A screenshot of a computer Description automatically
> generated](./media/image19.png)

6.  **New**ブレードで**、Conditions**のセクションに **0 conditions
    selected**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image20.png)

7.  条件のリストで**Device platforms**の下に**Not
    configured**を選択する。**Configure**セクションに**Yes**を選択して**Select
    device
    platforms**ラジオボタンを選択し、Windowsチェックボックスを選択し**て**から**、Done**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image21.png)

8.  **Newブレードで、Access controls**の下に、**Grantセクションに0
    controls selected**を選択する。

9.  **Require device to be marked as
    compliantチェックボックスをオンにして、Select**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image22.png)

10. **New**ブレードで**、**   **Enable policy**オプションで **On**
    を選択してから**Create**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image23.png)

11. Microsoft Edgeを閉じる。

タスク 2: 条件付きアクセス ポリシーが機能していることを確認する

1.  [***SEA-WS3***](urn:gd:lg:a:select-vm)に切り替えて!!**[Admin](urn:gd:lg:a:send-vm-keys)!!** としてサインインし、!!**[Pa55w.rd](urn:gd:lg:a:send-vm-keys)!!**パスワードを使用する。

2.  [***SEA-WS3***](urn:gd:lg:a:select-vm)で、タスクバーで、**Microsoft
    Edge**を選択する。Microsoft
    Edgeで[**outlook.office.com**](urn:gd:lg:a:send-vm-keys)を入力して、Enterをクリックする。

3.  アカウント選択ダイアログボックスで!!**Cindy@M365xXXXXXXX.onmicrosoft.com!!　**を選択する。

4.  **password**ページで!!**P@55w.rd12345!!　**を入力して**、Sign
    in**を選択する。Microsoft Edge のSave
    passwordプロンプトが表示したら**Update**を選択する。

> ![A screenshot of a computer error Description automatically
> generated](./media/image24.png)

5.  **"** **Sign in with your work
    account"**のメセッジが表示することを確認する。

> ![A screenshot of a computer Description automatically
> generated](./media/image25.png)

6.  **More details**を選択する。
    ブロックされた理由についての詳細情報が表示されるはずです。

> ![A screenshot of a computer error Description automatically
> generated](./media/image26.png)
>
> **注:** これは、SEA-WS3 が Microsoft Entra ID
> に参加しておらず、Microsoft Intune
> によって管理されていないため、準拠としてマークされていないためです。

7.  ブラウザウィンドウを**Close** する。

8.  [***SEA-WS1***](urn:gd:lg:a:select-vm)に切り替える。!!**Cindy@M365xXXXXXXX.onmicrosoft.com!!**
    としてサインインし、**password**ページで !!**P@55w.rd12345!!** を入力する。

> **注:** SEA-WS1 は、Intune に登録されている管理対象の Windows 11
> デバイスです**。**

9.  タスクバーで**Microsoft Edgeを選択する。**Microsoft
    Edgeに、[**Outlook.office.com**](urn:gd:lg:a:send-vm-keys) を入力して、**Enter**をクリックする。

10. Cindyの受信トレーにアクセスすることを確認する。

> ![A screenshot of a computer Description automatically
> generated](./media/image27.png)
>
> **注:**
> この理由は、**SEA-WS1**が管理対象デバイスであり、準拠としてマークされているからです。

11. Microsoft
    Edgeをクローズして[***SEA-WS1***](urn:gd:lg:a:select-vm)からサインアウトする。

タスク 3: 条件付きアクセス ポリシーを無効にする

1.  [***SEA-SVR1***](urn:gd:lg:a:select-vm)で**Microsoft Intune admin
    center** !\!<https://intune.microsoft.com>!!
    に**Devices**を選択してから**All devices**を選択する。

> ![](./media/image28.png)

2.  SEA-WS1 が準拠しているため、Cindy
    はメールボックスにアクセスできたことに注意する。

> ナビゲーションウィンドウで**Devices**を選択してから**Conditional
> access**を選択する。
>
> ![](./media/image29.png)

3.  **Conditional
    AccessページでPolicies**を選択してから**Conditional1**をクリックする。

> ![A screenshot of a computer Description automatically
> generated](./media/image30.png)

4.  **Conditional1**ページで、ページの一番下に**Off**を選択してから**Save**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image31.png)

5.  Microsoft Edgeを閉じる。

**結果:**
この手順を完了すると、デバイスのコンプライアンスを決定するための条件付きアクセス
ポリシーが正常に構成されます。
