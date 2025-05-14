Lab14 - 使用 Endpoint Configuration Manager 部署应用程序

**总结**

在本实验中，您将使用 Microsoft Endpoint Configuration Manager
将应用程序部署到桌面客户端工作站。

**场景**

Contoso 使用 Microsoft Endpoint Configuration Manager 管理本地 Active
Directory 网络环境中的桌面工作站。您需要将名为 Microsoft Power BI
Desktop 的新应用程序部署到 Windows 11 Configuration Manager
客户端。Endpoint Configuration Manager
管理员已为您创建了应用程序对象。您的任务包括为目标设备创建集合、将应用程序内容分发到分发点，然后创建分配给目标集合的部署。您将通过确保应用程序显示在
SEA-CL1 上的软件中心来验证该过程。

任务 1：创建设备集合

1.  切换到 [***SEA-CFG1***](urn:gd:lg:a:select-vm)，使用密码以
    [**Contoso\Administrator**](urn:gd:lg:a:send-vm-keys) 身份登录 !\![**Pa55w.rd**](urn:gd:lg:a:send-vm-keys)!!。

2.  在任务栏上，选择 **Configuration Manager Console**。此时将打开
    Microsoft Endpoint Configuration Manager 控制台。

> ![](./media/image1.png)

3.  在 **Assets and Compliance** 工作区中，选择 **Device Collections**。

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)

4.  右键单击 **Device Collections** （设备集合），然后选择 **Create
    Device Collection** （创建设备集合）。此时将打开 Create Device
    Collection Wizard。

> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)

5.  在 **General** （常规） 页面上，配置以下内容，然后选择 **Next**
    （下一步）：

    - 名字： !\![**Power BI App
      Deployment**](urn:gd:lg:a:send-vm-keys)!!

    - 评论： !\![**Devices targeted to install Power BI
      Desktop**](urn:gd:lg:a:send-vm-keys)!!

    - 限制收集： **All Windows 11 Workstations**

> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

6.  在 “**Membership Rules**” 页上，选择 “**Next**” 。在 Configuration
    Manager 警告处，选择 “**OK**” 。您将在后续步骤中添加直接成员。

> ![A screenshot of a computer Description automatically
> generated](./media/image5.png)
>
> ![A screenshot of a computer error Description automatically
> generated](./media/image6.png)

7.  在 **Summary** （摘要） 页面上，选择 **Next** （下一步），然后在
    **Completion** （完成） 页面上，选择 **Close** （关闭）。

> ![A screenshot of a computer Description automatically
> generated](./media/image7.png)
>
> **Power BI App Deployment** 集合显示在 Device Collections 列表中。
>
> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)

任务 2：将设备分配给现有集合

1.  在 **Assets and Compliance** （资产和合规性） 工作区中，选择
    **Devices** （设备）。

> 记下列出的设备。任何带有绿色圆圈和白色对勾标记的设备当前都处于活动状态。
>
> ![](./media/image9.png)

2.  在详细信息窗格中，选择 **SEA-CL1**。

3.  右键单击 [***SEA-CL1***](urn:gd:lg:a:select-vm)，指向 “**Add
    Selected Items** “，然后选择 “**Add Selected Items to Existing
    Device Collection**”。

> ![](./media/image10.png)

4.  在 **Select Collection** 对话框中，选择 **Power BI App
    Deployment**，然后选择 **OK**。

> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)

5.  若要验证，请在 “**Assets and Compliance**” 工作区中选择 “**Device
    Collections**”，然后双击 “**Power BI App Deployment**” 。

> ![A screenshot of a computer Description automatically
> generated](./media/image12.png)
>
> [***SEA-CL1***](urn:gd:lg:a:select-vm) 应列为此集合的成员。
>
> ![A screenshot of a computer Description automatically
> generated](./media/image13.png)

任务 3：配置部署类型

1.  在 Microsoft Endpoint Configuration Manager 控制台中，选择
    “**Software Library**” 工作区。

> ![A screenshot of a software library Description automatically
> generated](./media/image14.png)

2.  在 **Software Library** 工作区中，展开 **Application
    Management**，然后选择 **Applications**。

> ![A screenshot of a software library Description automatically
> generated](./media/image15.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image16.png)
>
> 请注意 Endpoint Configuration Manager 管理员创建的应用程序。

3.  在详细信息窗格中，选择 **Microsoft Power BI Desktop （x64）。**

> ![A screenshot of a computer Description automatically
> generated](./media/image17.png)

4.  在结果窗格中，选择 **Deployment Types** （部署类型）
    选项卡。请注意，有一种基于 Windows Installer 的部署类型。

> ![A screenshot of a computer Description automatically
> generated](./media/image18.png)

5.  右键单击 **Microsoft Power BI Desktop (x64) - Windows installer**
    部署类型，然后选择 “**Properties**” 。

> ![A screenshot of a computer Description automatically
> generated](./media/image19.png)

6.  在 **Properties** 对话框中，选择 **Programs**
    选项卡。记下应用程序的安装方式。它将使用带有 /q 开关的 msiexec
    来执行静默安装。

> ![](./media/image20.png)

7.  在 **Properties** （属性） 对话框中，选择 **Requirements** （要求）
    选项卡，然后选择 **Add** （添加）。

> ![A screenshot of a computer Description automatically
> generated](./media/image21.png)

8.  在 **Create Requirement** 对话框中，配置以下内容，然后选择 **OK**：

    - 类别： **Device**

    - 条件： **Operating System**

    - 规则类型：**Value**

    - 作员： **One of Windows 11 (Select the check box next to Windows
      11)**

> ![A screenshot of a computer program Description automatically
> generated](./media/image22.png)

9.  在 **Properties** （属性） 对话框中，选择 **OK**
    （确定）。此要求将阻止该应用程序安装在除 Windows 11
    之外的任何作系统上。

> ![A screenshot of a computer Description automatically
> generated](./media/image23.png)

任务 4：将内容分发到分发点

1.  在 “**Software Library**” 工作区中，选择 “**Microsoft Power BI
    Desktop （x64）**” 。

2.  右键单击 **Microsoft Power BI Desktop （x64），**然后选择
    “**Distribute Content**” 。

> ![A screenshot of a computer Description automatically
> generated](./media/image24.png)

3.  在 **General** （常规） 页面上，选择 **Next** （下一步）。

> ![A screenshot of a computer Description automatically
> generated](./media/image25.png)

4.  在 **Content** （内容） 页面上，选择 **Next** （下一步）。

> ![A screenshot of a computer Description automatically
> generated](./media/image26.png)

5.  在 **Content Destination** 页面上，选择 **Add** ，然后选择
    **Distribution Point**。

> ![A screenshot of a computer Description automatically
> generated](./media/image27.png)

6.  在 **Add distribution Points** （添加分发点） 对话框中，选中
    **SEA-CFG1.CONTOSO.COM** 旁边的复选框，然后选择 **OK** （确定）。

> ![A screenshot of a computer Description automatically
> generated](./media/image28.png)

7.  在 **Content Destination** （内容目标） 页面上，选择 **Next**
    （下一步）。

> ![A screenshot of a computer Description automatically
> generated](./media/image29.png)

8.  在 **Summary** （摘要） 页面上，选择 **Next** （下一步），然后选择
    **Close** （关闭）。

> ![A screenshot of a computer Description automatically
> generated](./media/image30.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image31.png)

9.  在 **Summary** 选项卡中，选择 **Content Status**。

> ![A screenshot of a computer Description automatically
> generated](./media/image32.png)
>
> 此时将打开 Microsoft Power BI Desktop
> 的“内容状态”页面。在结果窗格中，验证是否显示绿色圆圈，以及圆圈旁边是否显示
> Success：1。这表示内容现在已分发到分发点，现在可以部署到设备。您可能需要选择功能区中的
> Refresh （刷新） 按钮。
>
> ![A screenshot of a computer Description automatically
> generated](./media/image33.png)

10. 在左上角，选择 **Back to Applications**（返回应用程序）箭头以返回到
    Software Library Applications（软件库应用程序）节点。

任务 5：创建部署

1.  在 “**Software Library**” 工作区中，选择 “**Microsoft Power BI
    Desktop （x64）**” 。

2.  右键单击 **Microsoft Power BI Desktop （x64），**然后选择
    **Deploy**。此时将打开 **Deploy Software Wizard**。

> ![A screenshot of a computer Description automatically
> generated](./media/image34.png)

3.  在 **General** （常规） 页面的 **Collection** （集合） 旁边，选择
    **Browse** （浏览）。

> ![A screenshot of a computer Description automatically
> generated](./media/image35.png)

4.  在 “**Select Collection**” 页面上，选择 “**User Collections**”
    ，然后选择 “**Device Collections**” 。

5.  在 **Device Collections** 列表中，选择 **Power BI App
    Deployment**，然后选择 **OK**。

> ![A screenshot of a computer Description automatically
> generated](./media/image36.png)

6.  在 **General** （常规） 页面上，选择 **Next** （下一步）。

> ![A screenshot of a computer Description automatically
> generated](./media/image37.png)

7.  在 **Content** （内容） 页面上，选择 **Next** （下一步）。

> ![A screenshot of a computer Description automatically
> generated](./media/image38.png)

8.  在 **Deployment Settings** （部署设置） 页面上，验证 **Action**
    （作） 是否设置为 **Install** （安装） ，并将 **Purpose** （目的）
    设置为 **Available** （可用）。选择 **Next**（下一步）。

> ![A screenshot of a computer Description automatically
> generated](./media/image39.png)

9.  在 **Scheduling** （计划） 页面上，选择 **Next**
    （下一步）。默认情况下，该应用程序将尽快可用。

> ![A screenshot of a computer Description automatically
> generated](./media/image40.png)

10. 在 “**User Experience**” 页上的 “**User notifications**” 旁边，选择
    “**Display in Software Center and show all notifications**” 。选择
    **Next**（下一步）。

> ![A screenshot of a computer Description automatically
> generated](./media/image41.png)

11. 在 **Alerts** （警报） 页面上，选择 **Next** （下一步）。

> ![A screenshot of a computer Description automatically
> generated](./media/image42.png)

12. 在 **Summary** （摘要） 页面上，选择 **Next** （下一步），然后选择
    **Close** （关闭）。

> ![A screenshot of a computer Description automatically
> generated](./media/image43.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image44.png)

13. 在结果窗格中的 **Deployments** （部署） 选项卡上，验证是否显示部署。

> ![A screenshot of a computer Description automatically
> generated](./media/image45.png)

14. 关闭 Microsoft Endpoint Configuration Manager 控制台。

15. 注销 [***SEA-CFG1***](urn:gd:lg:a:select-vm)。

任务 6：使用软件中心安装已部署的应用

1.  切换到 [***SEA-CL1***](urn:gd:lg:a:select-vm)，然后以 [**Contoso\Administrator**](urn:gd:lg:a:send-vm-keys) 身份登录，密码为 !\![**Pa55w.rd**](urn:gd:lg:a:send-vm-keys)!!.

2.  单击 **Start Menu**，然后进入 **Control Panel**。

3.  在结果中，选择 **Control Panel**。

> ![A screenshot of a computer Description automatically
> generated](./media/image46.png)

4.  在 **Control panel** 中，选择 **System and Security**
    （系统和安全）。

> ![A screenshot of a computer Description automatically
> generated](./media/image47.png)

5.  在 **System and Security**（系统和安全）中，选择 **Configuration
    Manager**（配置管理器）。此时将显示 Configuration Manager 属性。

> ![A screenshot of a computer Description automatically
> generated](./media/image48.png)

6.  在 **Configuration Manager Properties** 对话框中，选择 **Actions**
    选项卡。

> ![A screenshot of a computer program Description automatically
> generated](./media/image49.png)

7.  在 **Actions** 项卡上，选择 **Machine Policy Retrieval & Evaluation
    Cycle**，然后选择 **Run Now**。在消息提示符处，选择 **OK**（确定）。

> ![A screenshot of a computer program Description automatically
> generated](./media/image50.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image51.png)

8.  选择 “**OK**” 以关闭 **Configuration Manager Properties**，然后关闭
    **Control Panel**。

> ![A screenshot of a computer program Description automatically
> generated](./media/image52.png)

9.  在通知区域中，选择 “**New Software is Available**” ，然后选择
    “**Open Software Center**”
    。您可能需要展开通知区域箭头才能显示图标。

> ![](./media/image53.png)
>
> 如果软件中心未启动，请单击 **Start Menu** 并向下滚动并单击
> !!**Software Center**!!
>
> ![A screenshot of a computer Description automatically
> generated](./media/image54.png)

10. 在 **Software Center** 的 **Applications** 页面上，请注意名为
    **Microsoft Power BI Desktop （x64）**
    的新应用程序。此应用程序现在可用于之前创建的 **Power BI App
    Deployment** 集合成员的任何设备。

> ![A screenshot of a computer Description automatically
> generated](./media/image55.png)

11. 选择 **Microsoft Power BI Desktop （x64），**然后选择 **Install**。

> ![A screenshot of a computer Description automatically
> generated](./media/image56.png)
>
> ![](./media/image57.png)
>
> 应用程序无需用户输入即可下载和安装。当 **Power BI Desktop**
> 快捷方式显示在桌面上时，您将知道安装成功。
>
> ![A screenshot of a computer Description automatically
> generated](./media/image58.png)

12. 关闭Software Center。

13. 注销 [***SEA-CL1***](urn:gd:lg:a:select-vm)。

**结果：**完成本练习后，您将成功使用 Microsoft Endpoint Configuration
Manager 将应用程序部署到桌面客户端工作站。
