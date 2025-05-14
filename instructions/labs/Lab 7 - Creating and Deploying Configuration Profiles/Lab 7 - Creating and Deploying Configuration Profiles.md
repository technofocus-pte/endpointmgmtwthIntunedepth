**实验 7 - 创建和部署配置文件**

**总结**

在本实验中，我们将使用 Microsoft Intune 为 Windows 11
设备创建和应用配置文件。

**先决条件**

在此实验之前，必须完成以下实验：

- 实验 \#1 - 在 Microsoft Entra ID 中管理身份

- 实验 \#2 - 使用 Microsoft Entra Connect 同步标识

- 实验 \#5 - 管理设备注册到 Microsoft Intune

- 实验 \#6 - 将设备注册到 Microsoft Intune

注意：您还需要一部可以接收短信的移动电话，该短信用于保护 Windows Hello
登录身份验证对 Microsoft Entra ID 的安全。

**练习 1：创建并应用配置文件。**

**场景**

您需要使用 Microsoft Entra 和 Microsoft Intune 来管理 Contoso
开发人员部门的成员。您被要求评估使用户能够在 Windows 11
设备上有效且安全地工作的解决方案。Cindy White
自愿帮助您测试和评估解决方案并提供反馈。他还为您提供了一些初始要求，这些要求必须包含并应用于开发人员的
Windows 设备：

- Settings （设置） 中的 Gaming （游戏） 部分应该不可见。

- 应尽可能限制 Settings （设置） 中的 Privacy （隐私） 部分。

- **C：\DevProjects** 文件夹必须从 Windows Defender 中排除。

- 必须从 Windows Defender 中排除devbuild.exe进程。

- 最常用的应用程序和最近添加的应用程序不应显示在“开始”菜单上。

**任务 1：验证设备设置**

1.  使用她的凭据以 **Cindy** White
    的身份登录 [*SEA-WS1*](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10) 
    !!**Cindy@M365xXXXXXX.onmicrosoft.com**!! 用 PIN 码 !!**102938**!!
    或密码!!**P@55w.rd1234**!!

![A screenshot of a computer Description automatically
generated](./media/image1.png)

2.  在任务栏上，选择“**Start**”，然后选择“**Settings**”。

![A screenshot of a computer Description automatically
generated](./media/image2.png)

3.  在 **Settings** （设置） 导航列表中，验证您是否可以看到 **Gaming**
    （游戏） 设置。

![A screenshot of a computer Description automatically
generated](./media/image3.png)

4.  选择 **Personalization** 设置，然后在 个性化 页面上，选择
    **Start**。记下 **Show recently added apps**
    （显示最近添加的应用程序） 和 **Show most used apps**
    （显示最常用的应用程序） 设置。

![](./media/image4.png)

![A screenshot of a computer Description automatically
generated](./media/image5.png)

5.  在 **Settings** 应用中，选择 **Privacy & security**。

6.  在 **Privacy & security**
    页面上，**注意安全、Windows权限**和**应用程序权限**下的选项。

![A screenshot of a computer Description automatically
generated](./media/image6.png)

7.  在 **Privacy & security** 页面上，选择**Windows
    Security**，然后选择**Open Windows Security**。

![](./media/image7.png)

![A screenshot of a computer security Description automatically
generated](./media/image8.png)

8.  在 **Windows Security** 页面上，选择 **Virus & threat protection**。

9.  在 **Virus & threat protection** 页面的 **Virus & threat protection
    settings**下，选择 **Manage settings**。

![A screenshot of a computer Description automatically
generated](./media/image9.png)

10. 向下滚动到 **Exclusions** （排除项），然后选择 **Add or remove
    exclusions** （添加或删除排除项）。在 User Account Control
    （用户帐户控制） 对话框中，选择 **Yes** （是）。

![A screenshot of a computer Description automatically
generated](./media/image10.png)

![A screenshot of a computer Description automatically
generated](./media/image11.png)

11. 在 **Exclusions** （排除项） 页面上，验证是否未配置任何排除项。

12. 关闭 **Windows 安全**窗口。

![A screenshot of a computer Description automatically
generated](./media/image12.png)

13. 关闭 **Settings** （设置） 窗口。

**任务 2：根据方案要求创建配置文件**

1.  切换到 [*SEA-SVR1*](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)。

2.  切换回打开**Microsoft
    Intune管理中心**的选项卡，从导航栏中选择“**Devices**”。

![A screenshot of a computer Description automatically
generated](./media/image13.png)

3.  在 **Devices | Overview** 页中，选择 “**Windows**”，如下图所示。

![A screenshot of a computer Description automatically
generated](./media/image14.png)

4.  在 **Windows | Windows devices** 页面上，导航并单击 **Configuration
    profiles**。

![A screenshot of a computer Description automatically
generated](./media/image15.png)

5.  在 **Windows | Configuration profiles** 页面的 **Policies**
    选项卡中，单击 **+ Create** 并选择 **+ New Policy**。

![A screenshot of a computer Description automatically
generated](./media/image16.png)

6.  在右侧显示的 **Create a profile** （创建配置文件）
    窗格中，选择以下选项，然后选择 **Create** （创建）：

- 平台： **Windows 10 and later**

- 配置文件类型： **Templates**

- 模板名称： !!!!

![A screenshot of a profile Description automatically
generated](./media/image17.png)

7.  在 **Basics** 边栏选项卡中，输入以下信息，然后选择“**Next**”：

- 名字： !!Contoso Developer - standard!!

- 描述： !!Basic restrictions and configuration for Contoso
  Developers.!!

![](./media/image18.png)

8.  在 “**Configurations settings**” 边栏选项卡上，展开 “**Control Panel
    and Settings**”。

![A screenshot of a computer Description automatically
generated](./media/image19.png)

9.  选择 **Block** 在 **Gaming** 和 **Privacy** 选项。

![A screenshot of a computer Description automatically
generated](./media/image20.png)

10. 在 **Device restrictions** （设备限制） 边栏选项卡上，展开
    **Start**（启动）。

![A screenshot of a computer Description automatically
generated](./media/image21.png)

11. 向下滚动并选择 “ **Most used apps**, **Recently added
    apps** 和 **Recently opened items in Jump Lists**” 旁边的
    “**Block**”。

![A screenshot of a computer Description automatically
generated](./media/image22.png)

12. 在“**Device restrictions**”边栏选项卡上，向下滚动并展开“**Microsoft
    Defender Antivirus**”。

![A screenshot of a computer Description automatically
generated](./media/image23.png)

13. 在 **Microsoft Defender Antivirus**下，向下滚动并展开 **Microsoft
    Defender Antivirus Exclusions**。

![](./media/image24.png)

14. 在 **Microsoft Defender Antivirus Exclusions**
    下，提供以下详细信息，然后单击“**Next**”按钮：

- 文件和文件夹框 - !!**C:\DevProjects**!!

- 流程盒 -  !!**DevBuild.exe**!!

![](./media/image25.png)

15. 在 **Assignments** 选项卡中，单击 **Next** 按钮。

![A screenshot of a computer Description automatically
generated](./media/image26.png)

16. 在 **Applicability Rules** 选项卡中，单击 **Next** 按钮。

![A screenshot of a computer Description automatically
generated](./media/image27.png)

17. 在 **Review + create** 选项卡中，单击 **Create** 按钮。

![A screenshot of a computer Description automatically
generated](./media/image28.png)

18. Configuration profile （配置文件） 现在应该列出。

![A screenshot of a computer Description automatically
generated](./media/image29.png)

**任务 3：创建 Contoso 开发人员设备组**

1.  在 Microsoft Intune 管理中心的导航窗格中，选择“**Groups**”。

![A screenshot of a computer Description automatically
generated](./media/image30.png)

2.  在 “**Groups | All groups**” 边栏选项卡中，选择“**New group**”。

![A screenshot of a computer Description automatically
generated](./media/image31.png)

3.  在 **New Group** （新建组） 边栏选项卡上，输入以下信息：

- 组类型： **Security**

- 组名： !!Contoso Developer devices!!

- 组介绍： !!All Windows devices in Contoso Developer department!!

- 成员身份类型： **Assigned**

4.  在 **Members** （成员） 下，选择 **No members selected**
    （未选择成员）。

![](./media/image32.png)

5.  在 **Add members** 边栏选项卡的 **Search** 框中键入 !!Sea!!。选择
    **SEA-WS1**，然后选择 **Select**。

![A screenshot of a computer Description automatically
generated](./media/image33.png)

6.  在 **New Group** 边栏选项卡上，选择 **Create**。

![](./media/image34.png)

7.  在 “**Groups | All groups**” 边栏选项卡中，验证是否显示“**Contoso
    developer devices**”组。

![](./media/image35.png)

**任务 4：创建动态 Azure AD 设备组**

1.  在“**Groups | All Groups**”边栏选项卡的详细信息窗格上，选择“**New
    group**”。

![A screenshot of a computer Description automatically
generated](./media/image36.png)

2.  在 **Group** （组） 边栏选项卡上，提供以下值：

- 组类型： **Security**

- 组名： !!Windows Devices!!

- 成员身份类型： **Dynamic Device**

3.  在 **Dynamic Device Members** 部分下，选择 **Add dynamic query**。

![A screenshot of a computer Description automatically
generated](./media/image37.png)

4.  在 **Dynamic membership rules** 边栏选项卡上的 **Rule syntax**
    部分，选择 **Edit**。

![A screenshot of a computer Description automatically
generated](./media/image38.png)

5.  在 **Edit rule syntax** （编辑规则语法）
    文本框中，添加以下简单成员身份规则，然后选择 **OK** （确定）。

!!**(device.deviceOSType -contains "Windows")**!!

![A screenshot of a computer Description automatically
generated](./media/image39.png)

6.  在 **Dynamic membership rules** （动态成员身份规则）
    边栏选项卡上，选择 **Save** （保存）。

![A screenshot of a computer Description automatically
generated](./media/image40.png)

7.  在 **New Group** （新建组） 页面上，选择 **Create** （创建）。

![A screenshot of a computer Description automatically
generated](./media/image41.png)

**任务 5：将配置文件分配给 Windows 设备**

1.  在 **Microsoft Intune
    管理中心**页面上，从导航栏中选择“**Devices**”。

![](./media/image42.png)

2.  在 **Devices | Overview** 页中，选择 “**Windows**”，如下图所示。

![](./media/image43.png)

3.  在 **Windows | Windows devices** 页面上，导航并单击 **Configuration
    profiles**。

![](./media/image44.png)

4.  在 **Devices | Configuration profiles**
    边栏选项卡，在详细信息窗格中，选择 **Contoso Developer – standard**
    配置文件。

![A screenshot of a computer Description automatically
generated](./media/image45.png)

5.  在“**Contoso Developer –
    standard**”边栏选项卡上，向下滚动到“**Assignments**”部分，然后选择“**Edit**”。.

![A screenshot of a computer Description automatically
generated](./media/image46.png)

6.  在 Assignments （分配） 页面的 **Included groups** （包含的组）
    下，选择 **Add groups** （添加组）。

![A screenshot of a computer Description automatically
generated](./media/image47.png)

7.  在 **Select groups to include** 边栏选项卡的 **Search**
    框中，键入并选择 !!**Contoso Developer devices**!!  然后单击
    **Select** 按钮。

![](./media/image48.png)

14. 返回“**Device restrictions**”边栏选项卡，选择“**Review +
    save**”，然后选择“**Save**”。

![A screenshot of a computer Description automatically
generated](./media/image49.png)

![](./media/image50.png)

**任务 6：验证是否已应用配置文件**

1.  切换到 [*SEA-WS1*](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)。使用
    Cindy White 的帐户登录。

- 用户名 - !!**Cindy@M365xXXXXXXX.onmicrosoft.com**!!

- 密码 – !!**P@55w.rd1234**!!

2.  在任务栏上，选择“**Start**”，然后选择“**Settings**”。

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)

3.  在 **Settings** （设置） 窗口中，选择 **Accounts** （帐户）。在
    “帐户 ”页上，选择 “**Access work or school**”。

![A screenshot of a computer Description automatically
generated](./media/image51.png)

4.  单击 “**Connected to Contoso’s Azure AD**”
    旁边的下拉列表，然后选择“**Info**”按钮。

![](./media/image52.png)

5.  在 “**Managed by Contoso**”页中，向下滚动，然后在
    “设备同步状态”下，选择 “**Sync**”。等待同步完成。

6.  ![A screenshot of a computer Description automatically
    generated](./media/image53.png)

![A screenshot of a computer Description automatically
generated](./media/image54.png)

7.  关闭 **Settings** 应用程序。

> **注意：**同步进度可能需要长达 15 分钟的时间，然后才能将配置文件应用于
> Windows 11 设备。注销或重启设备可以加速此过程。

8.  在 [*SEA-WS1*](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)上，
    再次选择 **Start** 开始 然后选择 **Settings**。验证 **Gaming**
    （游戏） 设置是否已删除。

![A screenshot of a computer Description automatically
generated](./media/image2.png)

![A screenshot of a computer Description automatically
generated](./media/image55.png)

9.  选择 **Privacy & security** ，并注意到许多隐私设置现在都被隐藏了。

![](./media/image56.png)

10. 选择 **Personalization** 设置，然后选择 **Start**。确认 **Show
    recently added apps** 和 **Show most used apps** 已设置为 **Off**
    并灰显。

![](./media/image57.png)

![A screenshot of a computer Description automatically
generated](./media/image58.png)

11. 在“**Settings**”应用中，选择“**Privacy and Security**”。

12. 在 **Privacy and Security** 页面上，选择**Windows
    Security**，然后选择**Open Windows Security**。

![](./media/image59.png)

![A screenshot of a computer security Description automatically
generated](./media/image60.png)

13. 在 **Windows Security** 页面上，选择 **Virus & threat protection**。

14. 在 **Virus & threat protection** 页面上，选择 **Virus & threat
    protection settings** 下的**Manage settings**。

![A screenshot of a computer Description automatically
generated](./media/image9.png)

15. 向下滚动到 **Exclusions** （排除项），然后选择 **Add or remove
    exclusions** （添加或删除排除项）。在 User Account Control
    消息中选择 **Yes**。

![A screenshot of a computer Description automatically
generated](./media/image61.png)

![A screenshot of a computer Description automatically
generated](./media/image62.png)

16. 在 **Exclusions** （排除项） 页面上，验证是否显示
    **C：\DevProjects** 和 **DevBuild.exe**。

![A screenshot of a computer Description automatically
generated](./media/image63.png)

17. 关闭 **Windows Security** 页面，然后关闭 **Settings** 应用程序。

**结果：**完成本练习后，您将成功为 Windows 11 设备创建并分配配置文件。

**练习 2：修改分配的配置文件策略。**

**场景**

Contoso
的策略有一个例外，该策略指定开发人员部门的成员不应在其设备上的“设置”中阻止“隐私”选项。应实施和测试此更改。

**任务 1：更改分配的配置文件中的设置**

1.  切换到 **SEA-SVR1**。切换回 **Microsoft Intune admin center**
    选项卡，从导航栏中选择“**Devices**”。

![](./media/image42.png)

2.  在 **Devices | Overview** 页中，选择 “**Windows**”，如下图所示。

![](./media/image43.png)

3.  在 **Windows | Windows devices** 页面上，导航并单击 **Configuration
    profiles**。

![](./media/image44.png)

4.  在 **Devices | Configuration profiles**
    边栏选项卡中，在详细信息窗格中选择“**Contoso Developer -
    standard**”。

![](./media/image64.png)

5.  在 “**Contoso Developer - standard**” 边栏选项卡上，向下滚动到
    “**Configuration settings**” 部分，然后选择 “**Edit**”。

![A screenshot of a computer Description automatically
generated](./media/image65.png)

6.  在 **Device restrictions** （设备限制） 页面上，展开 **Control Panel
    and Settings**。

![A screenshot of a computer Description automatically
generated](./media/image66.png)

7.  在 **Privacy** （隐私） 旁边，确保 **Not configured** （未配置）
    处于选中状态。

![A screenshot of a computer Description automatically
generated](./media/image67.png)

8.  选择 “**Review + save** ”，然后选择 “**Save**”。

![](./media/image68.png)

**任务 2：从 Microsoft Intune 管理中心强制同步设备**

1.  在 [*SEA-SVR1*](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)
    上，在 **Microsoft Intune
    管理中心**，选择导航窗格中的“**Devices**”，然后选择 “**All
    devices**”，然后选择“**SEA-WS1**”。

![A screenshot of a computer Description automatically
generated](./media/image69.png)

2.  在 **SEA-WS1** 边栏选项卡上，选择 “**Sync**”，并在出现提示时选择
    “**Yes**”。

![](./media/image70.png)

**注意：**Intune 将连接设备并同步所有策略。这可能需要长达 5 分钟的时间。

**任务
3：验证 [*SEA-WS1*](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)
上的更改**

1.  切换到
     [*SEA-WS1*](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)。在任务栏上，选择“**Start**”，然后选择“**Settings**”。

![A screenshot of a computer Description automatically
generated](./media/image2.png)

2.  在 **Settings** 应用中，选择 **Privacy &
    security**，并验证所有自定义选项都已恢复。

![A screenshot of a computer Description automatically
generated](./media/image71.png)

3.  关闭所有打开的窗口并注销 **SEA-WS1**。

**结果：**完成本练习后，您将成功修改已分配的配置文件、修改配置文件并验证更改。
