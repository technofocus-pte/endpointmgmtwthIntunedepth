# **实验 19 - 使用 Microsoft 部署工具包部署 Windows 11**

**总结**

在本实验中，您将使用 Microsoft 部署工具包创建和部署 Windows
11作系统映像。

**场景**

您需要部署一个名为 SEA-WS11 的新 Windows 4 虚拟机。您决定使用 Microsoft
Deployment Toolkit 将作系统部署到在 Hyper-V 中创建的虚拟机。您将在 MDT
中配置新的部署共享，然后配置将执行部署 SEA-WS4 步骤的任务序列。

### **任务 1：创建新的部署共享**

1.  切换到 [**SEA-SVR2**](urn:gd:lg:a:select-vm),
    以 !!**[Contoso\Administrator](urn:gd:lg:a:send-vm-keys)!!** 用密码 !!**[Pa55w.rd](urn:gd:lg:a:send-vm-keys)!!**

> ![Screenshot](./media/image1.png)

2.  在任务栏上，选择 **File
    Explorer**，然后浏览到 !!**[E:\Labfiles\ISOs](urn:gd:lg:a:send-vm-keys)!!**

> ![Screenshot](./media/image2.png)

3.  右键单击 **Win11_21H2_Eval.iso**，然后选择 **Mount**。ISO 作为 DVD
    驱动器 **D** 安装。

> ![Screenshot](./media/image3.png)
>
> ![Screenshot](./media/image4.png)

4.  关闭 **File Explorer**。

5.  选择 **Start menu**，展开 “**Microsoft Deployment
    Toolkit**”，然后选择 “**Deployment Workbench**” 。

> ![Screenshot](./media/image5.png)

6.  在 **Deployment Workbench** 中，右键单击 **Deployment
    Shares**，然后选择 **New Deployment Share**。

> ![Screenshot](./media/image6.png)
>
> 此时将打开 **New Deployment Share Wizard**。

7.  在 **Path** （路径） 页面的 **Deployment share path**
    （部署共享路径）
    下，将值更改为 !!**[E:\DeploymentShare](urn:gd:lg:a:send-vm-keys)!!**，然后选择
    **Next**。

> ![Screenshot](./media/image7.png)

8.  在 **Share** （共享） 页面上，记下 **Share name**
    （共享名称），但不要更改它。选择 **Next**（下一步）。

> ![Screenshot](./media/image8.png)

9.  在 **Descriptive Name** （描述性名称） 页面上，接受默认值，然后选择
    **Next** （下一步）。

> ![Screenshot](./media/image9.png)

10. 在 **Options** （选项） 页面上，配置以下内容，然后选择 **Next**
    （下一步）：

    - 要求设置本地管理员密码： **Enabled**

    - 所有其他复选框： **Disabled**

> ![Screenshot](./media/image10.png)

11. 在 **Summary** （摘要） 页面上，查看信息，然后选择 **Next**
    （下一步）。

> ![Screenshot](./media/image11.png)

12. 在 **Confirmation** 页面上，确保该过程已成功完成，然后选择
    **Finish**。

> ![Screenshot](./media/image12.png)

13. 在 **Deployment Shares** （部署共享） 下，展开 **MDT Deployment
    Share** （MDT 部署共享） 文件夹。

> 记下可为部署共享配置的各种节点。

### **任务 2：将作系统文件添加到部署共享**

1.  在 Deployment Workbench 中，展开 **Deployment Shares**，展开 **MDT
    Deployment Share**，然后选择 **Operating Systems**。

> ![Screenshot](./media/image13.png)

2.  右键单击 **Operating Systems**（作系统），然后选择 **Import
    Operating System**（导入作系统）。此时将打开 Import Operating System
    Wizard。

> ![Screenshot](./media/image14.png)

3.  在 **Import Operating System Wizard** 的 **OS Type** 页面上，选择
    **Full set of source files**，然后选择 **Next**。

> ![Screenshot](./media/image15.png)

4.  在 **Source** （源） 页面的 **Source Directory** （源目录）
    下，输入 !!**[D:\\](urn:gd:lg:a:send-vm-keys)!!**，然后选择
    **Next**。

> ![Screenshot](./media/image16.png)

5.  在 **Destination** （目标）
    页面上，将默认目标目录名称更改为 !!**[Windows 11 Enterprise
    x64](urn:gd:lg:a:send-vm-keys)!!**，然后选择 **Next**。

> ![Screenshot](./media/image17.png)

6.  在 **Summary** （摘要） 页面上，查看信息，然后选择 **Next**
    （下一步）。

> ![Screenshot](./media/image18.png)
>
> 作系统源文件将复制到部署共享中。

7.  在 **Confirmation** 页面上，确保该过程已成功完成，然后选择
    **Finish**。

> ![Screenshot](./media/image19.png)

8.  在 **Deployment Workbench** 中，选中 **Operating Systems**
    后，验证是否显示作系统。

### **任务 3：将应用程序添加到部署共享**

1.  在 Deployment Workbench 中，展开 **Deployment
    Shares**（部署共享），展开 **MDT Deployment Share**（MDT
    部署共享），然后选择 **Applications**（应用程序）。

2.  右键单击 **Applications**（应用程序），然后选择 **New
    Application**（新建应用程序）。此时将打开 New Application Wizard。

> ![Screenshot](./media/image20.png)

3.  在 **New Application Wizard** 的 **Application Type** 页面上，选择
    **Application with source files** （包含源文件的应用程序），然后选择
    **Next** （下一步）。

> ![Screenshot](./media/image21.png)

4.  在 **Details** （详细信息） 页面上，配置以下内容，然后选择 **Next**
    （下一步）：

    - 发行人： !!**[Microsoft](urn:gd:lg:a:send-vm-keys)!!**

    - 应用名称： !!**[XML Notepad](urn:gd:lg:a:send-vm-keys)!!**

> ![Screenshot](./media/image22.png)

5.  在 **Source** （源） 页面的 **Source directory** （源目录）
    下，输入 !!**[E:\Labfiles\Apps](urn:gd:lg:a:send-vm-keys)!!**，然后选择
    **Next**。

> ![Screenshot](./media/image23.png)

6.  在 **Destination** （目标） 页面上，接受默认目标目录名称，然后选择
    **Next** （下一步）。

> ![Screenshot](./media/image24.png)

7.  在 **Command Details** （命令详细信息） 页面的 **Command line**
    （命令行） 下输入 !!**[XmlNotepadSetup.msi
    /q](urn:gd:lg:a:send-vm-keys)!!**，然后选择 **Next**。

> ![Screenshot](./media/image25.png)

8.  在 **Summary** （摘要） 页面上，查看信息，然后选择 **Next**
    （下一步）。

> ![Screenshot](./media/image26.png)

9.  在 **Confirmation** 页面上，确保该过程已成功完成，然后选择
    **Finish**。

### **任务 4：创建 MDT 任务序列**

1.  在 Deployment Workbench 中，展开 **Deployment
    Shares**（部署共享），展开 **MDT Deployment Share**（MDT
    部署共享），然后选择 **Task Sequences**（任务序列）。

2.  右键单击 **Task Sequences** （任务序列），然后选择 **New Task
    Sequence** （新建任务序列）。此时将打开 **New Task Sequence
    Wizard**。

> ![Screenshot](./media/image27.png)

3.  在 **General Settings** 页面上，配置以下内容，然后选择 **Next**：

    - 任务序列 ID： !!**[001](urn:gd:lg:a:send-vm-keys)!!**

    - 任务序列名称： !!**[Deploy Windows 11
      Enterprise](urn:gd:lg:a:send-vm-keys)!!**

> ![Screenshot](./media/image28.png)

4.  在 “**Select Template**” 页面上，选择 “**Standard Client Task
    Sequence**” ，然后选择 “**Next**” 。

> ![Screenshot](./media/image29.png)

5.  在 “**Select OS**” 页面上，选择 “**Windows 10 Enterprise
    Evaluation**” ，然后选择 “**Next**” 。

> ![Screenshot](./media/image30.png)

6.  在 **Specify Product Key** （指定产品密钥） 页面上，选择 **Do not
    specify a product key at this time**
    （此时不指定产品密钥），然后选择 **Next** （下一步）。

> ![Screenshot](./media/image31.png)

7.  在 **OS Settings** （作系统设置） 页面上，配置以下内容，然后选择
    **Next** （下一步）：

    - 全名： !!**[User](urn:gd:lg:a:send-vm-keys)!!**

    - 组织： !!**[Contoso Corporation](urn:gd:lg:a:send-vm-keys)!!**

    - Internet Explorer
      主页： !!**[about:blank](urn:gd:lg:a:send-vm-keys)!!**

> ![Screenshot](./media/image32.png)

8.  在 **Admin Password** 页面上，选择 **Use the specified local
    Administrator
    password**（使用指定的本地管理员密码），然后输入 !!**[Pa55w.rd](urn:gd:lg:a:send-vm-keys)!!** 在两个文本框中。选择
    **Next**（下一步）。

> ![Screenshot](./media/image33.png)

9.  在 **Summary** （摘要） 页面上，查看信息，然后选择 **Next**
    （下一步）。

> ![Screenshot](./media/image34.png)

10. 在 **Confirmation** 页面上，确保该过程已成功完成，然后选择
    **Finish**。

> ![Screenshot](./media/image35.png)

11. 在 **Deployment Workbench** 中，选中 **Task Sequences** （任务序列）
    后，验证是否显示 **Deploy Windows 11 Enterprise** （部署 Windows 11
    企业版） 任务序列。

> ![Screenshot](./media/image36.png)

12. 右键单击 **Deploy Windows 11 Enterprise** 任务序列，然后选择
    **Properties** （属性）。

> ![Screenshot](./media/image37.png)

13. 选择 **Task Sequence** 选项卡。

14. 展开 **Validation** （验证） 节点，然后选择 **Validate** （验证）。

15. 在 **Properties** （属性） 页面上，删除 **Ensure minimum memory**
    （确保最小内存） 和 **Ensure minimum processor speed**
    （确保最低处理器速度） 旁边的复选标记。

> 请勿进行任何其他更改。

16. 在 “**Deploy Windows 11 Enterprise Properties**” 窗口中，选择
    “**OK**” 。

> ![Screenshot](./media/image38.png)

### **任务 5：配置部署共享属性和 Windows PE 设置**

1.  在 Deployment Workbench 中，展开 **Deployment Shares**，然后选择
    **MDT Deployment Share**。

2.  右键单击 **MDT Deployment Share**，然后选择 **Properties**。

> ![Screenshot](./media/image39.png)

3.  在 **MDT Deployment Share Properties** 窗口的 **General**
    选项卡上，记下创建部署共享时提供的信息。

> ![Screenshot](./media/image40.png)

4.  选择 **Rules** 选项卡。

> Rules （规则） 选项卡显示 CustomSettings.ini
> 文件的内容。这些值也是在创建部署共享期间提供的。
>
> ![Screenshot](./media/image41.png)

5.  选择 **Windows PE** 选项卡。

> Windows PE 选项卡提供了用于创建 Windows PE 启动磁盘的选项。

6.  在 **Windows PE** 选项卡上的 **Platform** 旁边，选择 **x64**。

7.  在 **Windows PE Customizations** （Windows PE 自定义） 部分的
    **Scratch space size** （暂存空间大小） 旁边，选择 **64**。

> ![Screenshot](./media/image42.png)

8.  选择 **Features** （功能） 选项卡，然后选中以下 Feature Pack
    旁边的复选框：

    - DISM Cmdlets

    - Windows PowerShell

    - Microsoft Data Access Components (MDAC/ADO) support

> ![Screenshot](./media/image43.png)
>
> ![Screenshot](./media/image44.png)

9.  选择 **Monitoring** （监控） 选项卡。

10. 在 **Monitoring** （监控） 选项卡上，选中 **Enable monitoring for
    this deployment share** （启用此部署共享的监控） 旁边的复选框。

11. 在 **MDT Deployment Share Properties** 窗口中，选择 **OK**。

> ![Screenshot](./media/image45.png)

12. 右键单击 **MDT Deployment Share** ，然后选择 **Update Deployment
    Share**。此时将打开 Update Deployment Share Wizard。

> ![Screenshot](./media/image46.png)

13. 在 **Options** （选项） 页面上，选择 **Optimize the boot image
    updating process** （优化启动映像更新过程），然后选择 **Next**
    （下一步）。

> ![Screenshot](./media/image47.png)

14. 在 **Summary** （摘要） 页面上，选择 **Next** （下一步）。

> ![Screenshot](./media/image48.png)
>
> 部署共享开始更新并创建 Windows PE 文件。这将需要几分钟才能完成。

15. 在 **Confirmation** 页面上，确保该过程已成功完成，然后选择
    **Finish**。

> ![Screenshot](./media/image49.png)

### **任务 6：使用 MDT 部署 Windows 11**

1.  在 [**SEA-SVR2**](urn:gd:lg:a:select-vm) 的任务栏上，选择 **Hyper-V
    Manager**。

> ![Screenshot](./media/image50.png)

2.  在 Hyper-V 管理器中，选择 “**Virtual Switch Manager**” 。

> ![Screenshot](./media/image51.png)

3.  在列表中选择 **External**，然后单击 **Create Virtual Switch**。

> ![Screenshot](./media/image52.png)

4.  在 **Virtual Switch Properties** （虚拟交换机属性） 页面的 **Name**
    （名称） 下，输入 [**External
    network**](urn:gd:lg:a:send-vm-keys)，选择 **OK**（确定），然后选择
    **Yes**（是）。

> ![Screenshot](./media/image53.png)
>
> ![Screenshot](./media/image54.png)

5.  在 Hyper-V 管理器中，选择
    **SEA-SVR2**，然后在作窗格中，选择新建，然后选择 **Virtual
    Machine**。

> ![Screenshot](./media/image55.png)

6.  在 “**Before you Begin**” 页面上，选择 “**Next**” 。

> ![Screenshot](./media/image56.png)

7.  在 **Specify Name and Location** （指定名称和位置） 页面的 **Name**
    （名称） 框中，键入 !!**[SEA-WS4](urn:gd:lg:a:send-vm-keys)!!**.

8.  选中 **Store the virtual machine in a different location**
    旁边的复选框，然后选中 **Location**
    类型 !!**[E:\Labfiles\VirtualMachines](urn:gd:lg:a:send-vm-keys)!!**。
    选择 **Next**（下一步）。

> ![Screenshot](./media/image57.png)

9.  在 **Specify Generation** （指定生成） 页面上，确保选择 **Generation
    2** （第 2 代），然后选择 **Next** （下一步）。

> ![Screenshot](./media/image58.png)

10. 在 **Assign Memory** （分配内存） 页面上，在 **Startup memory** type
    （启动内存类型） 旁边
    !!**[8192](urn:gd:lg:a:send-vm-keys)!!，**然后选择 Next。

> ![Screenshot](./media/image59.png)

11. 在 **Configure Networking** （配置网络） 页面的 **Connection**
    （连接） 旁边，选择 **External Network** （外部网络），然后选择
    **Next** （下一步）。

> ![Screenshot](./media/image60.png)

12. 在 **Connect Virtual Hard Disk** （连接虚拟硬盘） 页面上，选择
    **Create a virtual hard disk** （创建虚拟硬盘）
    并输入以下内容，然后单击 **Next** （下一步）：

    - 名字： !!**[SEA-WS4.vhdx](urn:gd:lg:a:send-vm-keys)!!**

    - 位置： !!**[E:\Labfiles\VirtualMachines](urn:gd:lg:a:send-vm-keys)!!**

    - 大小： !!**[60](urn:gd:lg:a:send-vm-keys)!!**

> ![Screenshot](./media/image61.png)

13. 在 **Installation Options** 页面上，选择 **Install an operating
    system from a bootable image file** 并配置以下内容：

    - 图像文件
      (.iso): !!**[E:\DeploymentShare\Boot\LiteTouchPE_x64.iso](urn:gd:lg:a:send-vm-keys)!!**

> ![Screenshot](./media/image62.png)

14. 选择 **Next**（下一步），然后选择 **Finish**（完成）。

> ![Screenshot](./media/image63.png)

15. 在 Hyper-V 管理器中，右键单击 **SEA-WS4**，然后选择 “**Settings**”
    。

> ![Screenshot](./media/image64.png)

16. 选择 **Security**（安全性），然后选中 **Enable Trusted Platform
    Module**（启用可信平台模块）旁边的复选框。

> ![Screenshot](./media/image65.png)

17. 选择 **Processor** （处理器），然后将虚拟处理器的数量更改为
    !!**[2](urn:gd:lg:a:send-vm-keys)!!**.

18. 选择 **OK** 关闭 Settings （设置） 对话框。

> ![Screenshot](./media/image66.png)

19. 在 Hyper-V 管理器中，选择 **SEA-WS4**，选择 **Connect**，然后选择
    **Start**。

> ![Screenshot](./media/image67.png)
>
> ![Screenshot](./media/image68.png)

20. 当计算机启动时，按键盘上的任意键以调用 MDT
    部署向导。根据需要最大化窗口。

> ![Screenshot](./media/image69.png)

21. 在 **Welcome** （欢迎） 页面上，选择 **Run the Deployment Wizard to
    install a new Operating System**。

> ![Screenshot](./media/image70.png)

22. 在 **Specify credentials for connecting to network shares**
    （指定用于连接到网络共享的凭据） 窗口中，输入以下内容，然后选择
    **OK** （确定）：

    - 用户名： !!**[Administrator](urn:gd:lg:a:send-vm-keys)!!**

    - 密码： !!**[Pa55w.rd](urn:gd:lg:a:send-vm-keys)!!**

    - 域： !!**[Contoso](urn:gd:lg:a:send-vm-keys)!!**

> ![Screenshot](./media/image71.png)

23. 在 **Task sequence** （任务序列） 页面上，选择 **Deploy Windows 11
    Enterprise** （部署 Windows 11 企业版），然后选择 **Next**
    （下一步）。

> ![Screenshot](./media/image72.png)

24. 在 **Computer Details** （计算机详细信息） 页面上，在 **Computer
    name** （计算机名称）
    旁边输入 !!**[SEA-WS4](urn:gd:lg:a:send-vm-keys)!!** ，然后选择
    **Next**。

> ![Screenshot](./media/image73.png)

25. 在 **Move Data and Settings** （移动数据和设置） 页面上，选择
    **Next** （下一步）。

> ![Screenshot](./media/image74.png)

26. 在 **User Data （Restore）** （用户数据（还原） ） 页面上，选择
    **Next** （下一步）。

> ![Screenshot](./media/image75.png)

27. 在 **Locale and Time** （区域设置和时间） 页面上，选择 **Next**
    （下一步）。

> ![Screenshot](./media/image76.png)

28. 在 **Applications**（应用程序）页面上，选择 **Next**（下一步）。

> ![Screenshot](./media/image77.png)

29. 在 **Administrator Password**
    页面上，输入 !!**[Pa55w.rd](urn:gd:lg:a:send-vm-keys)!!**，然后选择
    **Next**。

> ![Screenshot](./media/image78.png)

30. 在 **Ready** （就绪） 页面上，选择 **Begin** （开始）。

> ![Screenshot](./media/image79.png)
>
> 安装开始。完成需要一些时间，并将在安装过程中根据需要重新启动
> **SEA-WS4**。

31. 切换到 **Deployment Workbench**。

32. 在 Deployment Workbench 中，展开 **Deployment Shares**，然后展开
    **MDT Deployment Share**。

33. 选择 “**Monitoring**” ，然后在详细信息窗格中双击 **SEA-WS4**。

> ![Screenshot](./media/image80.png)
>
> 查看部署期间的监控状态。
>
> ![A screenshot of a computer Description automatically
> generated](./media/image81.png)

34. 切换到 **SEA-WS4**。

35. 安装完成后，桌面将打开并完成部署。在部署摘要中，选择 **Finish**。

> ![Screenshot](./media/image82.png)

36. 关闭 **SEA-WS4** 并关闭 Virtual Machine Connection 窗口。

> ![Screenshot](./media/image83.png)

37. 在 Hyper-V 管理器中，右键单击 **SEA-WS4**，然后选择 **Settings**。

> ![Screenshot](./media/image84.png)

38. 在 **Settings for SEA-WS4** 中，展开 **SCSI Controller**，然后选择
    **DVD Drive**。

39. 在详细信息窗格中的 **Media** （媒体） 下，选择
    **None**（无），然后选择 **OK**（确定）。

> ![Screenshot](./media/image85.png)

40. 右键单击 **SEA-WS4**，然后选择 **Checkpoint** 创建 SEA-WS4
    当前状态的检查点。

> ![Screenshot](./media/image86.png)
>
> ![Screenshot](./media/image87.png)

41. 在 [**SEA-SVR2**](urn:gd:lg:a:select-vm) 上， 关闭 **Hyper-V
    Manager** 并关闭 **Deployment Workbench**。

42. 打开 **File Explorer**，右键单击 **DVD Drive D**，然后选择
    **Eject**。

> ![Screenshot](./media/image88.png)
>
> ![Screenshot](./media/image89.png)

43. 关闭 **File Explorer** 并注销 **SEA-SVR2**。

**结果：**完成本练习后，您将成功使用 Microsoft 部署工具包创建和部署
Windows 11 工作站。
