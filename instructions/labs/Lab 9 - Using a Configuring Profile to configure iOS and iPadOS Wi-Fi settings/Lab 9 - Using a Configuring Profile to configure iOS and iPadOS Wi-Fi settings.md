**ラボ 9 - Configuringプロファイルを使用して iOS と iPadOS の Wi-Fi
設定を構成する方法。**

**要約**

このラボでは、Microsoft Intune を使用して、iOS および iPadOS デバイスの
Wi-Fi
設定の構成を実行するためのConfigurationプロファイルを作成および適用します。

**Exercise 1: Configurationプロファイルの作成。**

**シナリオ**

登録済みのiOSおよびiPadOSデバイスのWi-Fi設定を自動構成するために使用する構成プロファイルを作成するよう求められました。Wi-Fi設定が以下のように構成されていることを確認してください：

- Network name: **Contoso Wi-Fi**

- SSID: **MainOffice**

- Connect automatically: **Enable**

- Security type: **WPA/WPA2-Personal**

- Pre-Shared key: **ContosoWiFi123**

- Assigned to: **A new security group named iOS_iPadOS Devices**

**Task 1: iOS_iPadOSデバイスグループの作成**

1.  [*SEA-SVR1*](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)に切り替える。
     In the **Microsoft Entra admin
    center**ウィンドに、**Groupsに移動して選択し、All
    groups**をクリックする。

> ![A screenshot of a computer Description automatically
> generated](./media/image1.png)

2.  **Groups | All groups**ブレードで**New group**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)

3.  **New
    Group**ブレードでで次の情報を入力して以下の画像で示すようCreateボタンをクリックする**：**

    - Group type: **Security**

    - Group name: !!**iOS_iPadOS Devices**!!

    - Group description: !!**All iOS and iPadOS devices**!!

    - Membership type: **Assigned**

> ![A screenshot of a group Description automatically
> generated](./media/image3.png)

4.  **Groups | All groups**ブレードでページを更新して iOS_iPadOS
    Devicesグループがが表示されることを確認する**。** 

> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

**Task 2: シナリオ要件に基づく構成プロファイルの作成**

1.  **Microsoft Intune admin
    center**タブに切り替える。ナビゲーションバーから**Devices**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image5.png)

2.  **Devices |
    Overview**ページで以下の画像で示すよう**iOS/iPadOS**を選択する**。**

> ![A screenshot of a computer Description automatically
> generated](./media/image6.png)

3.  **iOS/iPadOSページでConfiguration profiles**に移動して選択する。

4.  **iOS/iPadOS | Configuration profilesページでPoliciesタブに+
    Createをクリックして、+ New Policy**を選択する。

> ![](./media/image7.png)

5.  **Create a
    profile**ブレードで以下のオプション選択して**Create**を選択する。

    - Platform: **iOS/iPadOS**

    - Profile type: **Templates**

    - Template name: **Wi-Fi**

> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)

6.  **Basics**ブレードで次の情報を入力してから**Next**を選択する。

    - Name: !!**iOS/iPadOS Wi-Fi Policy**!!

    - Description: !!**Wi-Fi settings for iOS/iPadOS Devices**!!

> ![A screenshot of a computer Description automatically
> generated](./media/image9.png)

7.  **Configuration settings**ブレードで**Wi-Fi
    type**の横に**Basic**を選択する。

> 選択されたタイプに基づき追加のオプションが表示される。

8.  **Configuration
    settingsブレードで**次のオプションを選択し、**Next**を選択する。

    - Network name: !!**Contoso Wi-Fi**!!

    - SSID: !! **MainOffice**!!

    - Connect automatically: **Enable**

    - Security type: **WPA/WPA2-Personal**

    - Pre-Shared key: !!**ContosoWiFi123**!!

> ![A screenshot of a computer Description automatically
> generated](./media/image10.png)

9.  **Assignments**ブレードで**Included groups**の下に**Add
    groups**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)

10. **Select groups to include**ウィンドに **iOS_iPadOS
    Devices**を選択して**Select**をクリックする。

> ![](./media/image12.png)

11. **Assignments**タブに**Next**ボタンをクリックする。

> ![A screenshot of a computer Description automatically
> generated](./media/image13.png)

12. **Review + create**タブに**Create**ボタンをクリックする**。**

> ![A screenshot of a computer Description automatically
> generated](./media/image14.png)

13. **iOS/iPadOS Wi-Fi Policy**がリストされていることを確認する

> ![A screenshot of a computer Description automatically
> generated](./media/image15.png)
>
> **結果:** この手順を完了すると、iOS および iPadOS デバイスの Wi-Fi
> 設定を構成するためのConfigurationプロファイルが正常に作成され、割り当てられるようになります。
