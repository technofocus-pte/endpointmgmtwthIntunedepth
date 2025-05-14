# ラボ 25: エンドポイント分析によるデバイスのパフォーマンスとユーザー エクスペリエンスの監視

**要約**

このラボでは、エンドポイント分析を有効にして、デバイスのパフォーマンスとユーザーエクスペリエンスのスコアとインサイトを監視します.

**前提 条件**

このラボの前に、次のラボを完了する必要があります:

- ラボ 05 - Intune へのデバイス登録の管理

- ラボ 06 - Intune へのデバイスの登録

- ラボ 07-構成プロファイルの作成とデプロイ

**シナリオ**

起動パフォーマンス、アプリケーションの信頼性、そしてユーザーがデバイスを再起動する頻度といったユーザーエクスペリエンスを監視するよう依頼されました。この情報を取得するには、エンドポイント分析を有効にする必要があります。

### タスク 1: エンドポイント分析の有効化

1.   [**SEA-SVR1**](urn:gd:lg:a:select-vm)で、必要に応じて、[**Contoso\Administrator**](urn:gd:lg:a:send-vm-keys)としてサインインし、 !\![**Pa55w.rd**](urn:gd:lg:a:send-vm-keys)!! パスワードを使用して、 **Server
    Manager**を閉じる。。

2.  タスクバーで**Microsoft Edge**を選択する。

3.  Microsoft
    Edgeにアドレスバーに!\![**https://intune.microsoft.com**](https://intune.microsoft.com)!! を入力してから**Enter**ボタンを押す。

4.  パスワードを使用して[**admin@M365x19242953.onmicrosoft.com**](urn:gd:lg:a:send-vm-keys) としてサインインする。

5.  **Microsoft Intune admin centerページでReports**を選択する。

6.  **ReportsブレードにAnalytics**の下に**Endpoint
    analytics**を選択する。

> ![](./media/image1.png)

7.  **Endpoint analytics**ページに **Collect device data from**が**All
    cloud-managed
    devices**と設定されていることを確認してから**Start**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)
>
> Overviewページの上にあるメセッジに注意する。スコアとインサイトがページ上に表示されるまで約24時間かかる場合があります。
>
> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)

8.  [**SEA-WS1**](urn:gd:lg:a:select-vm)に切り替えて、デバイスを再起動する。

9.  **Cindy
    White**としてサインインし、パスワード: [**102938**](urn:gd:lg:a:send-vm-keys)を使用する。

10.  [**SEA-SVR1**](urn:gd:lg:a:select-vm)に切り替える。

11. **Microsoft Intune admin centerページで** **DevicesAll
    devices**を選択する。を選択してから

12. **SEA-WS1**を選択する。

> ![](./media/image4.png)

13. **SEA-WS1**ページで**Sync**を選択してから**Yes**を選択する。

> ![A screenshot of a computer Description automatically
> generated](./media/image5.png)

14. **SEA-WS1**ページで**Monitor**の下に**User
    experience**を選択する。![A screenshot of a computer Description
    automatically generated](./media/image6.png)

15. **Endpoint analytics**, **Startup performance**, と**Application
    reliability** タブをレビュー　する。

> ![A screenshot of a computer Description automatically
> generated](./media/image7.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image9.png)
>
> 時間の遅れにより情報が報告されない場合がありますが、各タブに表示される内容の詳細を読みます。

16. **Microsoft Intune admin centerページでReports**を選択する。

17. **ReportsブレードにAnalytics**の下に**Endpoint
    analytics**を選択する。

> ![](./media/image10.png)
>
> エンドポイント分析でも同じ種類の情報を使用できますが、この情報は登録されているすべてのデバイスに基づいていることに注意する。
>
> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)

18. \[エンドポイント分析\] ページで使用できるレポートを参照します。

19. Microsoft Edgeを閉じる。

**結果:
この手順を完了すると、エンドポイント分析が、デバイスのパフォーマンスとユーザー
エクスペリエンスのスコアと分析情報を監視できるよう正常に有効とします。**
