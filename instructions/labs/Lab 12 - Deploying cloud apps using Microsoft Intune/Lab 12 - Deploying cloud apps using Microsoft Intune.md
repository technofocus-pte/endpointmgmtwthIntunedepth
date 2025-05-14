Lab12 - 使用 Microsoft Intune 部署云应用

**总结**

在本实验室中，你将使用 Intune 和公司门户网站创建和部署基于云的应用。

**先决条件**

在此实验之前，必须完成以下实验：

- 实验 \#1 - 在 Microsoft Entra ID 中管理身份

- 实验 \#2 - 使用 Microsoft Entra Connect 同步标识

- 实验 \#5 - 管理设备注册到 Microsoft Intune

- 实验 \#6 - 将设备注册到 Microsoft Intune

- 实验 \#7 - 创建和部署配置文件

**注意：**您还需要一部可以接收短信的移动电话，该短信用于保护 Windows
Hello 登录身份验证对 Microsoft Entra ID 的安全。

练习1: 将 Microsoft Store 应用添加到 Microsoft Intune

**场景**

使用 Microsoft Intune 管理 Contoso Corporation
的桌面和应用程序。研究部门经常连接到各种服务器来执行任务，并要求研究成员根据需要安装
Microsoft 远程桌面应用程序。Microsoft 远程桌面可从 Microsoft Store
获得，但你决定将应用添加到
Intune，以便用户可以从公司门户网站访问它。名为 Aaron Nicholls 的
Research 成员已同意在您将应用程序发布到门户后测试安装过程。

任务 1：将 Microsoft 远程桌面添加到 Microsoft Intune

1.  在 [***SEA-SVR1***](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17)
    上，如有必要，使用密码以 [**Contoso\Administrator**](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17) 身份登录 !\![**Pa55w.rd**](urn:gd:lg:a:select-vm)!!
     并关闭 **Server Manager**。

2.  在任务栏上，选择 **Microsoft Edge**。

3.  在 Microsoft Edge 中，键入!!
    [**https://Intune.microsoft.com**](urn:gd:lg:a:select-vm) !!
    ，然后按 **Enter**。

4.  使用 Home （主页） 选项卡中的 Office 365 Tenant 凭据登录。

5.  在 **Microsoft Intune 管理中心**页面上，选择 “**Apps**” 。

> ![A screenshot of a computer Description automatically
> generated](./media/image1.png)

6.  在 **Apps** （应用程序） 页面的导航窗格中，选择 **All apps**
    （所有应用程序）。

7.  在详细信息窗格中，选择 **+Add**。

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)

8.  在 **Select app type** 页面上，单击下拉菜单，然后选择 **Microsoft
    store app （new）。**

> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)
>
> 阅读有关 Microsoft Store 应用程序的信息，然后单击
> **Select**。此时将打开 **Add App** （添加应用程序） 页面。

9.  在 **App information** （应用程序信息） 页面上，单击 **Search the
    Microsoft Store app （new）** （搜索 Microsoft Store
    应用程序（新）） 链接。

> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

10. 在 **Search the Microsoft Store app （new）** 选项卡上，搜索并选择
    !\![**Microsoft Remote
    Desktop**](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17)!!
    然后点击 Select 按钮。

> ![A screenshot of a computer Description automatically
> generated](./media/image5.png)

11. 返回 Add App 选项卡，输入以下信息，然后选择 **Next**：

    - 类别： **Business**

    - 在公司门户中将此应用显示为特色应用： **Yes**

> ![A screenshot of a computer Description automatically
> generated](./media/image6.png)

12. 在 **Assignments** （分配） 选项卡上，单击 **+ Add group**
    （添加组）

> ![A screenshot of a computer Description automatically
> generated](./media/image7.png)

13. 在 **Select groups** （选择组） 页面上，选择 **Research,
    Sales** 组，然后单击 **Select** （选择）。

> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)

14. 点击 **Next** 按钮。

> ![A screenshot of a computer Description automatically
> generated](./media/image9.png)

15. 在 Review + create 选项卡上，单击 **Create** 按钮。

> ![](./media/image10.png)

16. 此时将打开 Microsoft 远程桌面页面。

> 记下 Properties （属性）、Device install status （设备安装状态） 和
> User install status （用户安装状态） 节点。
>
> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)

任务 2：从 Microsoft Intune 控制台强制同步策略

1.  在 **Microsoft Intune 管理中心**，选择 “**Devices**” ，然后选择
    “**All devices**” 。

2.  在详细信息窗格中，选择 **SEA-WS1**。

> ![A screenshot of a computer Description automatically
> generated](./media/image12.png)

3.  在 **SEA-WS1**
    边栏选项卡上，选择“**Sync**”，并在出现提示时选择“**Yes**”。

> ![A screenshot of a computer Description automatically
> generated](./media/image13.png)
>
> Microsoft Intune 将联系设备并同步所有策略。这可能需要长达 5
> 分钟的时间。

任务 3：从公司门户网站安装应用

1.  使用她的凭据以 **Cindy White** 的身份登录  
    !!**Cindy@M365xXXXXXX.onmicrosoft.com**!! 使用密码
    !!**P@55w.rd1234**!! 或使用 PIN 码 !!**102938**!!

2.  在任务栏上，选择 **Microsoft Edge**。

3.  如有必要，在 **Welcome to Microsoft Edge** 页面上，选择 **Confirm
    and continue**。关闭 Welcome （欢迎） 页面。

4.  在地址栏中浏览到 !\![**https://portal.manage.microsoft.com**](urn:gd:lg:a:send-vm-keys)!!

5.  登录身份 !!**Cindy@M365xXXXXXX.onmicrosoft.com**!!

> ![](./media/image14.png)

6.  在 Contoso Web 门户上，选择 “**Devices**” 。

> ![A screenshot of a computer Description automatically
> generated](./media/image15.png)

7.  在 Devices （设备） 页面上，选择 **Tap here to tell us which device
    you're using or add a new device**。

> ![](./media/image16.png)

8.  在 “**Which device are you using**” 对话框中，选择旁边的选项
    **SEA-WS1**，然后单击 “**Select**” 按钮。

> ![A screenshot of a computer Description automatically
> generated](./media/image17.png)
>
> 请注意，消息现在更改为 Apps will be installed onto：**SEA-WS1**
>
> ![](./media/image18.png)

9.  在左上角，选择导航按钮，然后选择**Downloads & updates**。

> ![A screenshot of a computer Description automatically
> generated](./media/image19.png)

10. 从列出的结果中，检查状态，**Microsoft Remote Desktop**
    应用程序应显示为 已 **Installed**。

> 注意 - 应用程序可能需要 10 到 20 分钟才能显示。
>
> ![A screenshot of a computer Description automatically
> generated](./media/image20.png)

11. 单击 **Start Menu** 并验证 “**Remote Desktop**” 是否显示在 “开始”
    菜单上。

> ![A screenshot of a computer Description automatically
> generated](./media/image21.png)

**结果：**完成本练习后，您将成功从 Microsoft Intune 添加和安装 Microsoft
Store 应用程序。

练习 2：从 Microsoft Intune 配置和部署 Microsoft 365 应用

**场景**

Contoso 研究部门的所有用户都需要 Microsoft 365 应用版。系统要求您将 64
位版本的 Microsoft Excel、Outlook、PowerPoint 和 Word 部署到其 Windows
设备。您还需要确保为 Current Channel （当前频道） 配置它们以进行更新。

任务 1：验证 SEA-WS1 上已安装的应用程序

1.  在 [***SEA-WS1***](urn:gd:lg:a:send-vm-keys) 的任务栏上，选择
    “**Start**”，然后选择“**Settings**”应用程序。

> ![A screenshot of a computer Description automatically
> generated](./media/image22.png)

2.  在 **Settings** 应用程序中，选择 **Apps**，然后选择 **Apps &
    features**。

> ![A screenshot of a computer Description automatically
> generated](./media/image23.png)
>
> 验证 **Microsoft 365 Apps for enterprise - en-us** 未列出。
>
> ![A screenshot of a computer Description automatically
> generated](./media/image24.png)

3.  关闭所有打开的窗口。

任务 2：将 Microsoft 365 应用添加到 Microsoft Intune

1.  切换到 [***SEA-SVR1***](urn:gd:lg:a:send-vm-keys)， 然后在
    **Microsoft Intune 管理中心**中选择“**Apps**”。

2.  在 “**Apps | Overview**” 边栏选项卡中，选择 “**All Apps**”
    。在详细信息窗格中，选择 **+Add**。

> ![A screenshot of a computer Description automatically
> generated](./media/image25.png)

3.  在 “**Select app type**” 边栏选项卡中的 “**Microsoft 365 应用版**”
    下，选择 “**Windows 10 and later** ”，然后单击 “**Select**” 。

> ![A screenshot of a computer Description automatically
> generated](./media/image26.png)

4.  在 “**Add Microsoft 365 Apps**” 边栏选项卡上，配置以下选项，然后选择
    “**Next**” ：

    - 套房名称： !\![**Microsoft 365 Apps
      (Research)**](urn:gd:lg:a:select-vm)!!

    - 套房描述： !\![**Microsoft 365 Apps for the Research department at
      Contoso**](urn:gd:lg:a:select-vm) !! (选择 **Edit Description**
      （编辑描述） 以输入此信息。)

> ![A screenshot of a computer Description automatically
> generated](./media/image27.png)

5.  在 **Configure app suite** 选项卡上，展开 **Select Office apps**
    下拉列表，选择以下 Office 应用：

    - Excel

    - Outlook

    - PowerPoint

    - Word

> ![A screenshot of a computer Description automatically
> generated](./media/image28.png)

6.  在 **Configure app suite** （配置应用程序套件）
    选项卡上，配置以下选项，然后选择 **Next** （下一步）：

    - 体系结构： **64-bit**

    - 默认文件格式： **Office Open XML Format**

    - Update channel： **Current Channel**

    - 代表用户接受 Microsoft 软件许可条款： **Yes**

> ![A screenshot of a computer Description automatically
> generated](./media/image29.png)

7.  在 **Assignments** 选项卡上的 **Required** 部分中，选择 **Add
    group**。

> ![A screenshot of a computer Description automatically
> generated](./media/image30.png)

8.  在 **Select groups** （选择组） 边栏选项卡上，选择 **Research**
    （研究），然后选择 **Select** （选择）。

> ![A screenshot of a group Description automatically
> generated](./media/image31.png)

9.  选择 **Next**。

> ![A screenshot of a computer Description automatically
> generated](./media/image32.png)

10. 在 **Review + Create** （查看 + 创建） 选项卡上，选择 **Create**
    （创建）。

> ![A screenshot of a computer Description automatically
> generated](./media/image33.png)

11. 在 **Microsoft 365 应用版 （研究）** 页上，选择 “**Properties**” 。

> ![A screenshot of a computer Description automatically
> generated](./media/image34.png)

12. 在详细信息窗格中，验证 **Research** 是否列在 **Assignments** 部分的
    **Required** 下。

> ![A screenshot of a computer Description automatically
> generated](./media/image35.png)

任务 3：从 Microsoft Intune 控制台强制同步策略

1.  在 **Microsoft Intune 管理中心**，选择 “**Devices**” ，然后选择
    “**All devices**” 。

2.  在详细信息窗格中，选择 **SEA-WS1**。

> ![A screenshot of a computer Description automatically
> generated](./media/image36.png)

3.  在 **SEA-WS1**
    边栏选项卡上，选择“**Sync**”，并在出现提示时选择“**Yes**”。

> ![A screenshot of a computer Description automatically
> generated](./media/image37.png)
>
> Microsoft Intune 将联系设备并同步所有策略。这可能需要长达 5
> 分钟的时间。

任务 4：验证是否已安装 Microsoft 365 应用

1.  如果您已以 **Cindy White**
    身份登录 [*SEA-WS1*](urn:gd:lg:a:send-vm-keys?rc=10)。

> **注意 –** 您可能需要等待大约 10-15 分钟才能在设备上安装 Microsoft 365
> 套件。

2.  使用她的凭据以 **Cindy White** 的身份注销并重新登录  
    !!**Cindy@M365xXXXXXX.onmicrosoft.com**!! 使用密码
    !!**P@55w.rd1234**!!

3.  在 [***SEA-WS1***](urn:gd:lg:a:send-vm-keys)
    的任务栏上，选择“**Start**”，然后选择“**Settings**”应用程序。

> ![A screenshot of a computer Description automatically
> generated](./media/image38.png)

4.  在 **Settings** 应用程序中，选择 **Apps** ，然后在 **Apps &
    features** 页面上。

> ![A screenshot of a computer Description automatically
> generated](./media/image23.png)

5.  寻找 !!**Microsoft 365**!! 并验证是否列出了 **Microsoft 365 Apps for
    enterprise - en-us**。

> ![A screenshot of a computer Description automatically
> generated](./media/image39.png)

6.  关闭 **Settings** 应用程序，然后选择 **Start** 开始 按钮。

7.  在 “**Recommended**” 部分中，您应该能够看到从 Microsoft Intune 中的
    Microsoft 365 Apps 中选择的新安装的应用程序。

> ![A screenshot of a computer Description automatically
> generated](./media/image40.png)

任务 5：在 Microsoft Intune 中监视应用安装状态

1.  切换到 [***SEA-SVR1***](urn:gd:lg:a:select-vm)， 然后在 **Microsoft
    Intune 管理中心**中选择“**Apps**”。

> ![](./media/image41.png)

2.  在 **Apps | Overview** 边栏选项卡中，选择 “**Monitor**”，然后选择
    “**App install status**” 。

> ![A screenshot of a computer Description automatically
> generated](./media/image42.png)

3.  在详细信息窗格中，选择 **Microsoft 365 Apps (Research)**。

> ![A screenshot of a computer Description automatically
> generated](./media/image43.png)

4.  在详细信息窗格中的 **Device status** （设备状态） 和 **User status**
    （用户状态） 下，验证 **1** 是否显示在 Installed （已安装） 下。

> ![A screenshot of a computer Description automatically
> generated](./media/image44.png)
>
> **注意：**这表示该应用程序安装在一台设备上，并且为一位用户安装。请注意，信息可能需要一些时间才能显示，并且可能会显示为
> **Install Pending** （待安装）。
>
> **注意 –** 您可以开始**实验室13**，然后在 **30-45** 分钟后回来查看。

![A screenshot of a computer Description automatically
generated](./media/image45.png)

5.  选择 **Device install status**（设备安装状态）。

> 在详细信息窗格中，您可以看到安装了应用程序的设备，以及用户的名称。**Device
> Name** 列应列出 **SEA-WS1**，**Status** 列应显示已
> **Installed**。这意味着该应用程序安装在 **SEA-WS1** 上。
>
> ![A screenshot of a computer Description automatically
> generated](./media/image46.png)

6.  在 **Microsoft Intune 管理中心**，选择 “**Devices**” 。

7.  在 **Devices | Overview** 边栏选项卡，选择 “**All devices**”
    ，然后在详细信息窗格中选择 “**SEA-WS1**” 。

> ![A screenshot of a computer Description automatically
> generated](./media/image47.png)

8.  在 **SEA-WS1** 边栏选项卡上，选择 “**Managed Apps**” 。

9.  在 **SEA-WS1 | Managed Apps** 边栏选项卡的 “详细信息窗格” 中，选择
    “**Microsoft 365 Apps (Research)**” 。

> ![A screenshot of a computer Description automatically
> generated](./media/image48.png)
>
> 在 **Microsoft 365 Apps (Research) - Installation details**
> 窗口中，你可以查看应用程序的整个生命周期，即 -
> 创建、分配、安装时间和状态以及设备上次签入（与 Microsoft Intune
> 同步）的时间。.
>
> ![A screenshot of a computer Description automatically
> generated](./media/image49.png)

10. 关闭所有打开的窗口。

**结果：**完成本练习后，您将成功从 Microsoft Intune 配置和部署 Microsoft
365 应用版。
