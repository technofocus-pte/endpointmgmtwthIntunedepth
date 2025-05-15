# **實驗 19 - 使用 Microsoft 部署工具包部署 Windows 11**

**總結**

在本實驗中，您將使用 Microsoft 部署工具包創建和部署 Windows
11作系統映像。

**場景**

您需要部署一個名為 SEA-WS11 的新 Windows 4 虛擬機。您決定使用 Microsoft
Deployment Toolkit 將作系統部署到在 Hyper-V 中創建的虛擬機。您將在 MDT
中配置新的部署共享，然後配置將執行部署 SEA-WS4 步驟的任務序列。

### **任務 1：創建新的部署共享**

1.  切換到 [**SEA-SVR2**](urn:gd:lg:a:select-vm),
    以 !!**[Contoso\Administrator](urn:gd:lg:a:send-vm-keys)!!** 用密碼 !!**[Pa55w.rd](urn:gd:lg:a:send-vm-keys)!!**

> ![Screenshot](./media/image1.png)

2.  在任務欄上，選擇 **File
    Explorer**，然後瀏覽到 !!**[E:\Labfiles\ISOs](urn:gd:lg:a:send-vm-keys)!!**

> ![Screenshot](./media/image2.png)

3.  右鍵單擊 **Win11_21H2_Eval.iso**，然後選擇 **Mount**。ISO 作為 DVD
    驅動器 **D** 安裝。

> ![Screenshot](./media/image3.png)
>
> ![Screenshot](./media/image4.png)

4.  關閉 **File Explorer**。

5.  選擇 **Start menu**，展開 “**Microsoft Deployment
    Toolkit**”，然後選擇 “**Deployment Workbench**” 。

> ![Screenshot](./media/image5.png)

6.  在 **Deployment Workbench** 中，右鍵單擊 **Deployment
    Shares**，然後選擇 **New Deployment Share**。

> ![Screenshot](./media/image6.png)
>
> 此時將打開 **New Deployment Share Wizard**。

7.  在 **Path** （路徑） 頁面的 **Deployment share path**
    （部署共享路徑）
    下，將值更改為 !!**[E:\DeploymentShare](urn:gd:lg:a:send-vm-keys)!!**，然後選擇
    **Next**。

> ![Screenshot](./media/image7.png)

8.  在 **Share** （共享） 頁面上，記下 **Share name**
    （共享名稱），但不要更改它。選擇 **Next**（下一步）。

> ![Screenshot](./media/image8.png)

9.  在 **Descriptive Name** （描述性名稱） 頁面上，接受默認值，然後選擇
    **Next** （下一步）。

> ![Screenshot](./media/image9.png)

10. 在 **Options** （選項） 頁面上，配置以下內容，然後選擇 **Next**
    （下一步）：

    - 要求設置本地管理員密碼： **Enabled**

    - 所有其他複選框： **Disabled**

> ![Screenshot](./media/image10.png)

11. 在 **Summary** （摘要） 頁面上，查看信息，然後選擇 **Next**
    （下一步）。

> ![Screenshot](./media/image11.png)

12. 在 **Confirmation** 頁面上，確保該過程已成功完成，然後選擇
    **Finish**。

> ![Screenshot](./media/image12.png)

13. 在 **Deployment Shares** （部署共享） 下，展開 **MDT Deployment
    Share** （MDT 部署共享） 文件夾。

> 記下可為部署共享配置的各種節點。

### **任務 2：將作系統文件添加到部署共享**

1.  在 Deployment Workbench 中，展開 **Deployment Shares**，展開 **MDT
    Deployment Share**，然後選擇 **Operating Systems**。

> ![Screenshot](./media/image13.png)

2.  右鍵單擊 **Operating Systems**（作系統），然後選擇 **Import
    Operating System**（導入作系統）。此時將打開 Import Operating System
    Wizard。

> ![Screenshot](./media/image14.png)

3.  在 **Import Operating System Wizard** 的 **OS Type** 頁面上，選擇
    **Full set of source files**，然後選擇 **Next**。

> ![Screenshot](./media/image15.png)

4.  在 **Source** （源） 頁面的 **Source Directory** （源目錄）
    下，輸入 !!**[D:\\](urn:gd:lg:a:send-vm-keys)!!**，然後選擇
    **Next**。

> ![Screenshot](./media/image16.png)

5.  在 **Destination** （目標）
    頁面上，將默認目標目錄名稱更改為 !!**[Windows 11 Enterprise
    x64](urn:gd:lg:a:send-vm-keys)!!**，然後選擇 **Next**。

> ![Screenshot](./media/image17.png)

6.  在 **Summary** （摘要） 頁面上，查看信息，然後選擇 **Next**
    （下一步）。

> ![Screenshot](./media/image18.png)
>
> 作系統源文件將複製到部署共享中。

7.  在 **Confirmation** 頁面上，確保該過程已成功完成，然後選擇
    **Finish**。

> ![Screenshot](./media/image19.png)

8.  在 **Deployment Workbench** 中，選中 **Operating Systems**
    後，驗證是否顯示作系統。

### **任務 3：將應用程序添加到部署共享**

1.  在 Deployment Workbench 中，展開 **Deployment
    Shares**（部署共享），展開 **MDT Deployment Share**（MDT
    部署共享），然後選擇 **Applications**（應用程序）。

2.  右鍵單擊 **Applications**（應用程序），然後選擇 **New
    Application**（新建應用程序）。此時將打開 New Application Wizard。

> ![Screenshot](./media/image20.png)

3.  在 **New Application Wizard** 的 **Application Type** 頁面上，選擇
    **Application with source files** （包含源文件的應用程序），然後選擇
    **Next** （下一步）。

> ![Screenshot](./media/image21.png)

4.  在 **Details** （詳細信息） 頁面上，配置以下內容，然後選擇 **Next**
    （下一步）：

    - 發行人： !!**[Microsoft](urn:gd:lg:a:send-vm-keys)!!**

    - 應用名稱： !!**[XML Notepad](urn:gd:lg:a:send-vm-keys)!!**

> ![Screenshot](./media/image22.png)

5.  在 **Source** （源） 頁面的 **Source directory** （源目錄）
    下，輸入 !!**[E:\Labfiles\Apps](urn:gd:lg:a:send-vm-keys)!!**，然後選擇
    **Next**。

> ![Screenshot](./media/image23.png)

6.  在 **Destination** （目標） 頁面上，接受默認目標目錄名稱，然後選擇
    **Next** （下一步）。

> ![Screenshot](./media/image24.png)

7.  在 **Command Details** （命令詳細信息） 頁面的 **Command line**
    （命令行） 下輸入 !!**[XmlNotepadSetup.msi
    /q](urn:gd:lg:a:send-vm-keys)!!**，然後選擇 **Next**。

> ![Screenshot](./media/image25.png)

8.  在 **Summary** （摘要） 頁面上，查看信息，然後選擇 **Next**
    （下一步）。

> ![Screenshot](./media/image26.png)

9.  在 **Confirmation** 頁面上，確保該過程已成功完成，然後選擇
    **Finish**。

### **任務 4：創建 MDT 任務序列**

1.  在 Deployment Workbench 中，展開 **Deployment
    Shares**（部署共享），展開 **MDT Deployment Share**（MDT
    部署共享），然後選擇 **Task Sequences**（任務序列）。

2.  右鍵單擊 **Task Sequences** （任務序列），然後選擇 **New Task
    Sequence** （新建任務序列）。此時將打開 **New Task Sequence
    Wizard**。

> ![Screenshot](./media/image27.png)

3.  在 **General Settings** 頁面上，配置以下內容，然後選擇 **Next**：

    - 任務序列 ID： !!**[001](urn:gd:lg:a:send-vm-keys)!!**

    - 任務序列名稱： !!**[Deploy Windows 11
      Enterprise](urn:gd:lg:a:send-vm-keys)!!**

> ![Screenshot](./media/image28.png)

4.  在 “**Select Template**” 頁面上，選擇 “**Standard Client Task
    Sequence**” ，然後選擇 “**Next**” 。

> ![Screenshot](./media/image29.png)

5.  在 “**Select OS**” 頁面上，選擇 “**Windows 10 Enterprise
    Evaluation**” ，然後選擇 “**Next**” 。

> ![Screenshot](./media/image30.png)

6.  在 **Specify Product Key** （指定產品密鑰） 頁面上，選擇 **Do not
    specify a product key at this time**
    （此時不指定產品密鑰），然後選擇 **Next** （下一步）。

> ![Screenshot](./media/image31.png)

7.  在 **OS Settings** （作系統設置） 頁面上，配置以下內容，然後選擇
    **Next** （下一步）：

    - 全名： !!**[User](urn:gd:lg:a:send-vm-keys)!!**

    - 組織： !!**[Contoso Corporation](urn:gd:lg:a:send-vm-keys)!!**

    - Internet Explorer
      主頁： !!**[about:blank](urn:gd:lg:a:send-vm-keys)!!**

> ![Screenshot](./media/image32.png)

8.  在 **Admin Password** 頁面上，選擇 **Use the specified local
    Administrator
    password**（使用指定的本地管理員密碼），然後輸入 !!**[Pa55w.rd](urn:gd:lg:a:send-vm-keys)!!** 在兩個文本框中。選擇
    **Next**（下一步）。

> ![Screenshot](./media/image33.png)

9.  在 **Summary** （摘要） 頁面上，查看信息，然後選擇 **Next**
    （下一步）。

> ![Screenshot](./media/image34.png)

10. 在 **Confirmation** 頁面上，確保該過程已成功完成，然後選擇
    **Finish**。

> ![Screenshot](./media/image35.png)

11. 在 **Deployment Workbench** 中，選中 **Task Sequences** （任務序列）
    後，驗證是否顯示 **Deploy Windows 11 Enterprise** （部署 Windows 11
    企業版） 任務序列。

> ![Screenshot](./media/image36.png)

12. 右鍵單擊 **Deploy Windows 11 Enterprise** 任務序列，然後選擇
    **Properties** （屬性）。

> ![Screenshot](./media/image37.png)

13. 選擇 **Task Sequence** 選項卡。

14. 展開 **Validation** （驗證） 節點，然後選擇 **Validate** （驗證）。

15. 在 **Properties** （屬性） 頁面上，刪除 **Ensure minimum memory**
    （確保最小內存） 和 **Ensure minimum processor speed**
    （確保最低處理器速度） 旁邊的複選標記。

> 請勿進行任何其他更改。

16. 在 “**Deploy Windows 11 Enterprise Properties**” 窗口中，選擇
    “**OK**” 。

> ![Screenshot](./media/image38.png)

### **任務 5：配置部署共享屬性和 Windows PE 設置**

1.  在 Deployment Workbench 中，展開 **Deployment Shares**，然後選擇
    **MDT Deployment Share**。

2.  右鍵單擊 **MDT Deployment Share**，然後選擇 **Properties**。

> ![Screenshot](./media/image39.png)

3.  在 **MDT Deployment Share Properties** 窗口的 **General**
    選項卡上，記下創建部署共享時提供的信息。

> ![Screenshot](./media/image40.png)

4.  選擇 **Rules** 選項卡。

> Rules （規則） 選項卡顯示 CustomSettings.ini
> 文件的內容。這些值也是在創建部署共享期間提供的。
>
> ![Screenshot](./media/image41.png)

5.  選擇 **Windows PE** 選項卡。

> Windows PE 選項卡提供了用於創建 Windows PE 啟動磁盤的選項。

6.  在 **Windows PE** 選項卡上的 **Platform** 旁邊，選擇 **x64**。

7.  在 **Windows PE Customizations** （Windows PE 自定義） 部分的
    **Scratch space size** （暫存空間大小） 旁邊，選擇 **64**。

> ![Screenshot](./media/image42.png)

8.  選擇 **Features** （功能） 選項卡，然後選中以下 Feature Pack
    旁邊的複選框：

    - DISM Cmdlets

    - Windows PowerShell

    - Microsoft Data Access Components (MDAC/ADO) support

> ![Screenshot](./media/image43.png)
>
> ![Screenshot](./media/image44.png)

9.  選擇 **Monitoring** （監控） 選項卡。

10. 在 **Monitoring** （監控） 選項卡上，選中 **Enable monitoring for
    this deployment share** （啟用此部署共享的監控） 旁邊的複選框。

11. 在 **MDT Deployment Share Properties** 窗口中，選擇 **OK**。

> ![Screenshot](./media/image45.png)

12. 右鍵單擊 **MDT Deployment Share** ，然後選擇 **Update Deployment
    Share**。此時將打開 Update Deployment Share Wizard。

> ![Screenshot](./media/image46.png)

13. 在 **Options** （選項） 頁面上，選擇 **Optimize the boot image
    updating process** （優化啟動映像更新過程），然後選擇 **Next**
    （下一步）。

> ![Screenshot](./media/image47.png)

14. 在 **Summary** （摘要） 頁面上，選擇 **Next** （下一步）。

> ![Screenshot](./media/image48.png)
>
> 部署共享開始更新並創建 Windows PE 文件。這將需要幾分鐘才能完成。

15. 在 **Confirmation** 頁面上，確保該過程已成功完成，然後選擇
    **Finish**。

> ![Screenshot](./media/image49.png)

### **任務 6：使用 MDT 部署 Windows 11**

1.  在 [**SEA-SVR2**](urn:gd:lg:a:select-vm) 的任務欄上，選擇 **Hyper-V
    Manager**。

> ![Screenshot](./media/image50.png)

2.  在 Hyper-V 管理器中，選擇 “**Virtual Switch Manager**” 。

> ![Screenshot](./media/image51.png)

3.  在列表中選擇 **External**，然後單擊 **Create Virtual Switch**。

> ![Screenshot](./media/image52.png)

4.  在 **Virtual Switch Properties** （虛擬交換機屬性） 頁面的 **Name**
    （名稱） 下，輸入 [**External
    network**](urn:gd:lg:a:send-vm-keys)，選擇 **OK**（確定），然後選擇
    **Yes**（是）。

> ![Screenshot](./media/image53.png)
>
> ![Screenshot](./media/image54.png)

5.  在 Hyper-V 管理器中，選擇
    **SEA-SVR2**，然後在作窗格中，選擇新建，然後選擇 **Virtual
    Machine**。

> ![Screenshot](./media/image55.png)

6.  在 “**Before you Begin**” 頁面上，選擇 “**Next**” 。

> ![Screenshot](./media/image56.png)

7.  在 **Specify Name and Location** （指定名稱和位置） 頁面的 **Name**
    （名稱） 框中，鍵入 !!**[SEA-WS4](urn:gd:lg:a:send-vm-keys)!!**.

8.  選中 **Store the virtual machine in a different location**
    旁邊的複選框，然後選中 **Location**
    類型 !!**[E:\Labfiles\VirtualMachines](urn:gd:lg:a:send-vm-keys)!!**。
    選擇 **Next**（下一步）。

> ![Screenshot](./media/image57.png)

9.  在 **Specify Generation** （指定生成） 頁面上，確保選擇 **Generation
    2** （第 2 代），然後選擇 **Next** （下一步）。

> ![Screenshot](./media/image58.png)

10. 在 **Assign Memory** （分配內存） 頁面上，在 **Startup memory** type
    （啟動內存類型） 旁邊
    !!**[8192](urn:gd:lg:a:send-vm-keys)!!，**然後選擇 Next。

> ![Screenshot](./media/image59.png)

11. 在 **Configure Networking** （配置網絡） 頁面的 **Connection**
    （連接） 旁邊，選擇 **External Network** （外部網絡），然後選擇
    **Next** （下一步）。

> ![Screenshot](./media/image60.png)

12. 在 **Connect Virtual Hard Disk** （連接虛擬硬盤） 頁面上，選擇
    **Create a virtual hard disk** （創建虛擬硬盤）
    並輸入以下內容，然後單擊 **Next** （下一步）：

    - 名字： !!**[SEA-WS4.vhdx](urn:gd:lg:a:send-vm-keys)!!**

    - 位置： !!**[E:\Labfiles\VirtualMachines](urn:gd:lg:a:send-vm-keys)!!**

    - 大小： !!**[60](urn:gd:lg:a:send-vm-keys)!!**

> ![Screenshot](./media/image61.png)

13. 在 **Installation Options** 頁面上，選擇 **Install an operating
    system from a bootable image file** 並配置以下內容：

    - 圖像文件
      (.iso): !!**[E:\DeploymentShare\Boot\LiteTouchPE_x64.iso](urn:gd:lg:a:send-vm-keys)!!**

> ![Screenshot](./media/image62.png)

14. 選擇 **Next**（下一步），然後選擇 **Finish**（完成）。

> ![Screenshot](./media/image63.png)

15. 在 Hyper-V 管理器中，右鍵單擊 **SEA-WS4**，然後選擇 “**Settings**”
    。

> ![Screenshot](./media/image64.png)

16. 選擇 **Security**（安全性），然後選中 **Enable Trusted Platform
    Module**（啟用可信平臺模塊）旁邊的複選框。

> ![Screenshot](./media/image65.png)

17. 選擇 **Processor** （處理器），然後將虛擬處理器的數量更改為
    !!**[2](urn:gd:lg:a:send-vm-keys)!!**.

18. 選擇 **OK** 關閉 Settings （設置） 對話框。

> ![Screenshot](./media/image66.png)

19. 在 Hyper-V 管理器中，選擇 **SEA-WS4**，選擇 **Connect**，然後選擇
    **Start**。

> ![Screenshot](./media/image67.png)
>
> ![Screenshot](./media/image68.png)

20. 當計算機啟動時，按鍵盤上的任意鍵以調用 MDT
    部署嚮導。根據需要最大化窗口。

> ![Screenshot](./media/image69.png)

21. 在 **Welcome** （歡迎） 頁面上，選擇 **Run the Deployment Wizard to
    install a new Operating System**。

> ![Screenshot](./media/image70.png)

22. 在 **Specify credentials for connecting to network shares**
    （指定用於連接到網絡共享的憑據） 窗口中，輸入以下內容，然後選擇
    **OK** （確定）：

    - 用戶名： !!**[Administrator](urn:gd:lg:a:send-vm-keys)!!**

    - 密碼： !!**[Pa55w.rd](urn:gd:lg:a:send-vm-keys)!!**

    - 域： !!**[Contoso](urn:gd:lg:a:send-vm-keys)!!**

> ![Screenshot](./media/image71.png)

23. 在 **Task sequence** （任務序列） 頁面上，選擇 **Deploy Windows 11
    Enterprise** （部署 Windows 11 企業版），然後選擇 **Next**
    （下一步）。

> ![Screenshot](./media/image72.png)

24. 在 **Computer Details** （計算機詳細信息） 頁面上，在 **Computer
    name** （計算機名稱）
    旁邊輸入 !!**[SEA-WS4](urn:gd:lg:a:send-vm-keys)!!** ，然後選擇
    **Next**。

> ![Screenshot](./media/image73.png)

25. 在 **Move Data and Settings** （移動數據和設置） 頁面上，選擇
    **Next** （下一步）。

> ![Screenshot](./media/image74.png)

26. 在 **User Data （Restore）** （用戶數據（還原） ） 頁面上，選擇
    **Next** （下一步）。

> ![Screenshot](./media/image75.png)

27. 在 **Locale and Time** （區域設置和時間） 頁面上，選擇 **Next**
    （下一步）。

> ![Screenshot](./media/image76.png)

28. 在 **Applications**（應用程序）頁面上，選擇 **Next**（下一步）。

> ![Screenshot](./media/image77.png)

29. 在 **Administrator Password**
    頁面上，輸入 !!**[Pa55w.rd](urn:gd:lg:a:send-vm-keys)!!**，然後選擇
    **Next**。

> ![Screenshot](./media/image78.png)

30. 在 **Ready** （就緒） 頁面上，選擇 **Begin** （開始）。

> ![Screenshot](./media/image79.png)
>
> 安裝開始。完成需要一些時間，並將在安裝過程中根據需要重新啟動
> **SEA-WS4**。

31. 切換到 **Deployment Workbench**。

32. 在 Deployment Workbench 中，展開 **Deployment Shares**，然後展開
    **MDT Deployment Share**。

33. 選擇 “**Monitoring**” ，然後在詳細信息窗格中雙擊 **SEA-WS4**。

> ![Screenshot](./media/image80.png)
>
> 查看部署期間的監控狀態。
>
> ![A screenshot of a computer Description automatically
> generated](./media/image81.png)

34. 切換到 **SEA-WS4**。

35. 安裝完成後，桌面將打開並完成部署。在部署摘要中，選擇 **Finish**。

> ![Screenshot](./media/image82.png)

36. 關閉 **SEA-WS4** 並關閉 Virtual Machine Connection 窗口。

> ![Screenshot](./media/image83.png)

37. 在 Hyper-V 管理器中，右鍵單擊 **SEA-WS4**，然後選擇 **Settings**。

> ![Screenshot](./media/image84.png)

38. 在 **Settings for SEA-WS4** 中，展開 **SCSI Controller**，然後選擇
    **DVD Drive**。

39. 在詳細信息窗格中的 **Media** （媒體） 下，選擇
    **None**（無），然後選擇 **OK**（確定）。

> ![Screenshot](./media/image85.png)

40. 右鍵單擊 **SEA-WS4**，然後選擇 **Checkpoint** 創建 SEA-WS4
    當前狀態的檢查點。

> ![Screenshot](./media/image86.png)
>
> ![Screenshot](./media/image87.png)

41. 在 [**SEA-SVR2**](urn:gd:lg:a:select-vm) 上， 關閉 **Hyper-V
    Manager** 並關閉 **Deployment Workbench**。

42. 打開 **File Explorer**，右鍵單擊 **DVD Drive D**，然後選擇
    **Eject**。

> ![Screenshot](./media/image88.png)
>
> ![Screenshot](./media/image89.png)

43. 關閉 **File Explorer** 並注銷 **SEA-SVR2**。

**結果：**完成本練習後，您將成功使用 Microsoft 部署工具包創建和部署
Windows 11 工作站。
