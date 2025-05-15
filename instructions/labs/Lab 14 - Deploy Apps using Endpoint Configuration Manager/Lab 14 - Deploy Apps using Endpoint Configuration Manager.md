Lab14 - 使用 Endpoint Configuration Manager 部署應用程序

**總結**

在本實驗中，您將使用 Microsoft Endpoint Configuration Manager
將應用程序部署到桌面客戶端工作站。

**場景**

Contoso 使用 Microsoft Endpoint Configuration Manager 管理本地 Active
Directory 網絡環境中的桌面工作站。您需要將名為 Microsoft Power BI
Desktop 的新應用程序部署到 Windows 11 Configuration Manager
客戶端。Endpoint Configuration Manager
管理員已為您創建了應用程序對象。您的任務包括為目標設備創建集合、將應用程序內容分發到分發點，然後創建分配給目標集合的部署。您將通過確保應用程序顯示在
SEA-CL1 上的軟件中心來驗證該過程。

任務 1：創建設備集合

1.  切換到 [***SEA-CFG1***](urn:gd:lg:a:select-vm)，使用密碼以
    [**Contoso\Administrator**](urn:gd:lg:a:send-vm-keys) 身份登錄 !\![**Pa55w.rd**](urn:gd:lg:a:send-vm-keys)!!。

2.  在任務欄上，選擇 **Configuration Manager Console**。此時將打開
    Microsoft Endpoint Configuration Manager 控制台。

> ![](./media/image1.png)

3.  在 **Assets and Compliance** 工作區中，選擇 **Device Collections**。

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)

4.  右鍵單擊 **Device Collections** （設備集合），然後選擇 **Create
    Device Collection** （創建設備集合）。此時將打開 Create Device
    Collection Wizard。

> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)

5.  在 **General** （常規） 頁面上，配置以下內容，然後選擇 **Next**
    （下一步）：

    - 名字： !\![**Power BI App
      Deployment**](urn:gd:lg:a:send-vm-keys)!!

    - 評論： !\![**Devices targeted to install Power BI
      Desktop**](urn:gd:lg:a:send-vm-keys)!!

    - 限制收集： **All Windows 11 Workstations**

> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

6.  在 “**Membership Rules**” 頁上，選擇 “**Next**” 。在 Configuration
    Manager 警告處，選擇 “**OK**” 。您將在後續步驟中添加直接成員。

> ![A screenshot of a computer Description automatically
> generated](./media/image5.png)
>
> ![A screenshot of a computer error Description automatically
> generated](./media/image6.png)

7.  在 **Summary** （摘要） 頁面上，選擇 **Next** （下一步），然後在
    **Completion** （完成） 頁面上，選擇 **Close** （關閉）。

> ![A screenshot of a computer Description automatically
> generated](./media/image7.png)
>
> **Power BI App Deployment** 集合顯示在 Device Collections 列表中。
>
> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)

任務 2：將設備分配給現有集合

1.  在 **Assets and Compliance** （資產和合規性） 工作區中，選擇
    **Devices** （設備）。

> 記下列出的設備。任何帶有綠色圓圈和白色對勾標記的設備當前都處於活動狀態。
>
> ![](./media/image9.png)

2.  在詳細信息窗格中，選擇 **SEA-CL1**。

3.  右鍵單擊 [***SEA-CL1***](urn:gd:lg:a:select-vm)，指向 “**Add
    Selected Items** “，然後選擇 “**Add Selected Items to Existing
    Device Collection**”。

> ![](./media/image10.png)

4.  在 **Select Collection** 對話框中，選擇 **Power BI App
    Deployment**，然後選擇 **OK**。

> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)

5.  若要驗證，請在 “**Assets and Compliance**” 工作區中選擇 “**Device
    Collections**”，然後雙擊 “**Power BI App Deployment**” 。

> ![A screenshot of a computer Description automatically
> generated](./media/image12.png)
>
> [***SEA-CL1***](urn:gd:lg:a:select-vm) 應列為此集合的成員。
>
> ![A screenshot of a computer Description automatically
> generated](./media/image13.png)

任務 3：配置部署類型

1.  在 Microsoft Endpoint Configuration Manager 控制台中，選擇
    “**Software Library**” 工作區。

> ![A screenshot of a software library Description automatically
> generated](./media/image14.png)

2.  在 **Software Library** 工作區中，展開 **Application
    Management**，然後選擇 **Applications**。

> ![A screenshot of a software library Description automatically
> generated](./media/image15.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image16.png)
>
> 請注意 Endpoint Configuration Manager 管理員創建的應用程序。

3.  在詳細信息窗格中，選擇 **Microsoft Power BI Desktop （x64）。**

> ![A screenshot of a computer Description automatically
> generated](./media/image17.png)

4.  在結果窗格中，選擇 **Deployment Types** （部署類型）
    選項卡。請注意，有一種基於 Windows Installer 的部署類型。

> ![A screenshot of a computer Description automatically
> generated](./media/image18.png)

5.  右鍵單擊 **Microsoft Power BI Desktop (x64) - Windows installer**
    部署類型，然後選擇 “**Properties**” 。

> ![A screenshot of a computer Description automatically
> generated](./media/image19.png)

6.  在 **Properties** 對話框中，選擇 **Programs**
    選項卡。記下應用程序的安裝方式。它將使用帶有 /q 開關的 msiexec
    來執行靜默安裝。

> ![](./media/image20.png)

7.  在 **Properties** （屬性） 對話框中，選擇 **Requirements** （要求）
    選項卡，然後選擇 **Add** （添加）。

> ![A screenshot of a computer Description automatically
> generated](./media/image21.png)

8.  在 **Create Requirement** 對話框中，配置以下內容，然後選擇 **OK**：

    - 類別： **Device**

    - 條件： **Operating System**

    - 規則類型：**Value**

    - 作員： **One of Windows 11 (Select the check box next to Windows
      11)**

> ![A screenshot of a computer program Description automatically
> generated](./media/image22.png)

9.  在 **Properties** （屬性） 對話框中，選擇 **OK**
    （確定）。此要求將阻止該應用程序安裝在除 Windows 11
    之外的任何作系統上。

> ![A screenshot of a computer Description automatically
> generated](./media/image23.png)

任務 4：將內容分發到分發點

1.  在 “**Software Library**” 工作區中，選擇 “**Microsoft Power BI
    Desktop （x64）**” 。

2.  右鍵單擊 **Microsoft Power BI Desktop （x64），**然後選擇
    “**Distribute Content**” 。

> ![A screenshot of a computer Description automatically
> generated](./media/image24.png)

3.  在 **General** （常規） 頁面上，選擇 **Next** （下一步）。

> ![A screenshot of a computer Description automatically
> generated](./media/image25.png)

4.  在 **Content** （內容） 頁面上，選擇 **Next** （下一步）。

> ![A screenshot of a computer Description automatically
> generated](./media/image26.png)

5.  在 **Content Destination** 頁面上，選擇 **Add** ，然後選擇
    **Distribution Point**。

> ![A screenshot of a computer Description automatically
> generated](./media/image27.png)

6.  在 **Add distribution Points** （添加分發點） 對話框中，選中
    **SEA-CFG1.CONTOSO.COM** 旁邊的複選框，然後選擇 **OK** （確定）。

> ![A screenshot of a computer Description automatically
> generated](./media/image28.png)

7.  在 **Content Destination** （內容目標） 頁面上，選擇 **Next**
    （下一步）。

> ![A screenshot of a computer Description automatically
> generated](./media/image29.png)

8.  在 **Summary** （摘要） 頁面上，選擇 **Next** （下一步），然後選擇
    **Close** （關閉）。

> ![A screenshot of a computer Description automatically
> generated](./media/image30.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image31.png)

9.  在 **Summary** 選項卡中，選擇 **Content Status**。

> ![A screenshot of a computer Description automatically
> generated](./media/image32.png)
>
> 此時將打開 Microsoft Power BI Desktop
> 的“內容狀態”頁面。在結果窗格中，驗證是否顯示綠色圓圈，以及圓圈旁邊是否顯示
> Success：1。這表示內容現在已分發到分發點，現在可以部署到設備。您可能需要選擇功能區中的
> Refresh （刷新） 按鈕。
>
> ![A screenshot of a computer Description automatically
> generated](./media/image33.png)

10. 在左上角，選擇 **Back to Applications**（返回應用程序）箭頭以返回到
    Software Library Applications（軟件庫應用程序）節點。

任務 5：創建部署

1.  在 “**Software Library**” 工作區中，選擇 “**Microsoft Power BI
    Desktop （x64）**” 。

2.  右鍵單擊 **Microsoft Power BI Desktop （x64），**然後選擇
    **Deploy**。此時將打開 **Deploy Software Wizard**。

> ![A screenshot of a computer Description automatically
> generated](./media/image34.png)

3.  在 **General** （常規） 頁面的 **Collection** （集合） 旁邊，選擇
    **Browse** （瀏覽）。

> ![A screenshot of a computer Description automatically
> generated](./media/image35.png)

4.  在 “**Select Collection**” 頁面上，選擇 “**User Collections**”
    ，然後選擇 “**Device Collections**” 。

5.  在 **Device Collections** 列表中，選擇 **Power BI App
    Deployment**，然後選擇 **OK**。

> ![A screenshot of a computer Description automatically
> generated](./media/image36.png)

6.  在 **General** （常規） 頁面上，選擇 **Next** （下一步）。

> ![A screenshot of a computer Description automatically
> generated](./media/image37.png)

7.  在 **Content** （內容） 頁面上，選擇 **Next** （下一步）。

> ![A screenshot of a computer Description automatically
> generated](./media/image38.png)

8.  在 **Deployment Settings** （部署設置） 頁面上，驗證 **Action**
    （作） 是否設置為 **Install** （安裝） ，並將 **Purpose** （目的）
    設置為 **Available** （可用）。選擇 **Next**（下一步）。

> ![A screenshot of a computer Description automatically
> generated](./media/image39.png)

9.  在 **Scheduling** （計劃） 頁面上，選擇 **Next**
    （下一步）。默認情況下，該應用程序將儘快可用。

> ![A screenshot of a computer Description automatically
> generated](./media/image40.png)

10. 在 “**User Experience**” 頁上的 “**User notifications**” 旁邊，選擇
    “**Display in Software Center and show all notifications**” 。選擇
    **Next**（下一步）。

> ![A screenshot of a computer Description automatically
> generated](./media/image41.png)

11. 在 **Alerts** （警報） 頁面上，選擇 **Next** （下一步）。

> ![A screenshot of a computer Description automatically
> generated](./media/image42.png)

12. 在 **Summary** （摘要） 頁面上，選擇 **Next** （下一步），然後選擇
    **Close** （關閉）。

> ![A screenshot of a computer Description automatically
> generated](./media/image43.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image44.png)

13. 在結果窗格中的 **Deployments** （部署） 選項卡上，驗證是否顯示部署。

> ![A screenshot of a computer Description automatically
> generated](./media/image45.png)

14. 關閉 Microsoft Endpoint Configuration Manager 控制台。

15. 注銷 [***SEA-CFG1***](urn:gd:lg:a:select-vm)。

任務 6：使用軟件中心安裝已部署的應用

1.  切換到 [***SEA-CL1***](urn:gd:lg:a:select-vm)，然後以 [**Contoso\Administrator**](urn:gd:lg:a:send-vm-keys) 身份登錄，密碼為 !\![**Pa55w.rd**](urn:gd:lg:a:send-vm-keys)!!.

2.  單擊 **Start Menu**，然後進入 **Control Panel**。

3.  在結果中，選擇 **Control Panel**。

> ![A screenshot of a computer Description automatically
> generated](./media/image46.png)

4.  在 **Control panel** 中，選擇 **System and Security**
    （系統和安全）。

> ![A screenshot of a computer Description automatically
> generated](./media/image47.png)

5.  在 **System and Security**（系統和安全）中，選擇 **Configuration
    Manager**（配置管理器）。此時將顯示 Configuration Manager 屬性。

> ![A screenshot of a computer Description automatically
> generated](./media/image48.png)

6.  在 **Configuration Manager Properties** 對話框中，選擇 **Actions**
    選項卡。

> ![A screenshot of a computer program Description automatically
> generated](./media/image49.png)

7.  在 **Actions** 項卡上，選擇 **Machine Policy Retrieval & Evaluation
    Cycle**，然後選擇 **Run Now**。在消息提示符處，選擇 **OK**（確定）。

> ![A screenshot of a computer program Description automatically
> generated](./media/image50.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image51.png)

8.  選擇 “**OK**” 以關閉 **Configuration Manager Properties**，然後關閉
    **Control Panel**。

> ![A screenshot of a computer program Description automatically
> generated](./media/image52.png)

9.  在通知區域中，選擇 “**New Software is Available**” ，然後選擇
    “**Open Software Center**”
    。您可能需要展開通知區域箭頭才能顯示圖標。

> ![](./media/image53.png)
>
> 如果軟件中心未啟動，請單擊 **Start Menu** 並向下滾動並單擊
> !!**Software Center**!!
>
> ![A screenshot of a computer Description automatically
> generated](./media/image54.png)

10. 在 **Software Center** 的 **Applications** 頁面上，請注意名為
    **Microsoft Power BI Desktop （x64）**
    的新應用程序。此應用程序現在可用於之前創建的 **Power BI App
    Deployment** 集合成員的任何設備。

> ![A screenshot of a computer Description automatically
> generated](./media/image55.png)

11. 選擇 **Microsoft Power BI Desktop （x64），**然後選擇 **Install**。

> ![A screenshot of a computer Description automatically
> generated](./media/image56.png)
>
> ![](./media/image57.png)
>
> 應用程序無需用戶輸入即可下載和安裝。當 **Power BI Desktop**
> 快捷方式顯示在桌面上時，您將知道安裝成功。
>
> ![A screenshot of a computer Description automatically
> generated](./media/image58.png)

12. 關閉Software Center。

13. 注銷 [***SEA-CL1***](urn:gd:lg:a:select-vm)。

**結果：**完成本練習後，您將成功使用 Microsoft Endpoint Configuration
Manager 將應用程序部署到桌面客戶端工作站。
