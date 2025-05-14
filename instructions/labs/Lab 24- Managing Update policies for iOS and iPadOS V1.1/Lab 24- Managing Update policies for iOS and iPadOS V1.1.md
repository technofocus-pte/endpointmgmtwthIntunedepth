実践ラボ26: iOSおよびiPadOSの更新ポリシーの管理

**要約**

このラボでは、iOS と iPadOS のオペレーティング
システムのアップデートを管理するために使用するアップデート
ポリシーを構成します。

**シナリオ**

Contoso のすべての開発者は、最新の iOS/iPadOS バージョンを実行している
iPhone と iPad を持っています。これらのデバイスは Apple
の自動デバイス登録を通じて登録されており、デバイス OS
の更新ポリシーを構成する必要があります。次のことを確認する必要があります:

- インストールするバージョン: 最新の更新プログラム。

&nbsp;

- 自動更新は、水曜日の午前 12 時から木曜日の午前 12
  時までの間にのみ許可してください.

タスク 1: Create an Update policy for
iOS/iPadOSデバイスようアップデートポリシーの作成

1.  [***SEA-SVR1***](urn:gd:lg:a:select-vm)で、必要に応じて、[**Contoso\Administrator**](urn:gd:lg:a:send-vm-keys) としてサインインし、パスワード [**Pa55w.rd**](urn:gd:lg:a:send-vm-keys) を使用して**Server
    Manager**を閉じる。

2.  タスクバーで**Microsoft Edge**を選択する。

3.  Microsoft
    Edgeにアドレスバーに[**https://intune.microsoft.com**](https://intune.microsoft.com) を入力してから**Enter**ボタンを押す。

4.  パスワードを使用して[**admin@M365x19242953.onmicrosoft.com**](urn:gd:lg:a:send-vm-keys) サインインする。

5.   **Microsoft Intune admin center**ページで**Devices**を選択する。

6.  **Devices|By
    platform** ブレードに**Policy**の下に**iOS/iPadOS**を選択する。

> ![](./media/image1.png)

7.  **Update Policies for iOS/iPadOS**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)

8.  詳細のペインに**Create profile**を選択する。

9.  **Basics**タブで次のオプションを構成して**Next**を選択する。

    - Name: !\![**iOS/iPadOS update
      policy**](urn:gd:lg:a:send-vm-keys)!!

    - Description: !\![**Policy to manage system updates for iOS and
      iPadOS**](urn:gd:lg:a:send-vm-keys)!!

> ![](./media/image3.png)

10. **Update policy
    settings**タブに次のオプションを構成してから**Next**を選択する:

    - Select version to install: **Latest update**

    - Schedule type: **Update during scheduled time**

    - Time zone: **UTC:00**

    - Time window:

    - Start day: **Wednesday**

      - Start time: **12 AM**

      - End day: **Thursday**

      - End time: **12 AM**

> ![](./media/image4.png)

11. **Assignments**タブで**Next**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image5.png)

12. **Review + create**タブで設定を確認してから**Create**を選択する。

13. **Devices | Update policies for
    iOS/iPadOS**ブレードに、詳細のペインに  **iOS/iPadOS update
    policy**がリストされていることを確認する**。**

> ![A screenshot of a computer Description automatically
> generated](./media/image6.png)

14. Microsoft Edgeを閉じる。

**結果**: この手順を完了すると、iOS と iPadOS
のアップデートポリシーが正常に構成されます。
