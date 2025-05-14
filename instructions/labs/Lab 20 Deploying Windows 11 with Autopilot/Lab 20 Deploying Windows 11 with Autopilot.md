实验 20：使用 Autopilot 部署 Windows 11

**总结**

在本实验中，您将学习如何使用用户驱动模式为 Windows 11 设备配置
Autopilot。

**先决条件**

在此实验之前，必须完成以下实验：

- 实验 01 - 在 Microsoft Entra ID 中管理身份

- 实验 02 - 使用 Azure AD Connect 同步身份

- 实验 11 - 使用 Microsoft 部署工具包部署 Windows 11

**场景**

Contoso IT 计划使用 Autopilot 推出新 Windows 11
设备的部署。这些设备默认安装了 Windows 11。用户应该能够在 OOBE
期间使用其 Microsoft Entra ID
凭据登录来连接设备、打开设备并回答最少的问题。该过程应自动注册并加入
Entra ID 域。系统要求您使用 SEA-WS4 配置和测试体验，您最近使用 Hyper-V
安装和配置了 SEA-WS4。

任务 1：在 Microsoft Entra 管理中心创建组。

1.  切换并登录 [***SEA-SVR1***](urn:gd:lg:a:select-vm) 作为!!  使用密码 [**Pa55w.rd**](urn:gd:lg:a:send-vm-keys) 并关闭 **Server
    Manager**.**Contoso\Administrator**!! 用密码 !!!!  并关闭 **Server
    Manager**。

2.  在任务栏上，选择 **Microsoft Edge**。

3.  在 Microsoft Edge 的地址栏中，键入 !!﷟HYPERLINK
    "https://entra.microsoft.com"**ttps://entra.microsoft.com**!!,
    然后按 **Enter**如果出现提示，请使用您和
    password.[**admin@M365xXXXXXXXX.onmicrosoft.com**](mailto:admin@M365xXXXXXXXX.onmicrosoft.com)!!
     和密码。

![](./media/image1.png)

4.  在导航窗格中，选择 **Identity** （身份）。

5.  在 **Identity** （身份） 下，选择 **Groups** （组）。

> ![](./media/image2.png)

6.  在 “**Groups | All groups**” 边栏选项卡中，选择 “**New group**” 。

> ![](./media/image3.png)

7.  在 **New Group** （新建组） 边栏选项卡的 **Group type** （组类型）
    列表中，选择 **Security** （安全性）。

8.  在 **Group name** （组名称） 框中，键入 !!﷟HYPERLINK
    "http://urn:gd:lg:a:send-vm-keys"**IT Devices**!!.

9.  在 **Group description** （组描述） 框中，键入 !!﷟HYPERLINK
    "http://urn:gd:lg:a:send-vm-keys"**IT Department Devices**!!.

10. 在 “**Membership type**” 列表中，选择 “**Dynamic Device**” 。

11. 选择 **Add dynamic query**（添加动态查询）。

> ![](./media/image4.png)

12. 在 **Dynamic membership rules** 边栏选项卡上，选择 **Rule syntax**
    框上方的 **Edit**。

> ![](./media/image5.png)

13. 在 Edit rule syntax （编辑规则语法）
    文本框中，添加以下简单成员身份规则，然后选择 **OK** （确定）。

14. !!(device.devicePhysicalIDs -any (\_ -contains "\[ZTDId\]"))!!

> ![](./media/image6.png)

15. 选择 **Save** 以关闭 **Dynamic membership rules**，然后选择
    **Create** 以创建组。

> ![A screenshot of a computer Description automatically
> generated](./media/image7.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)
>
> ![](./media/image9.png)

任务 2：生成特定于设备的逗号分隔值 （CSV） 文件

1.  切换到 [***SEA-SVR2***](urn:gd:lg:a:select-vm) 并以 [**Contoso\Administrator**](urn:gd:lg:a:send-vm-keys) 身份登录，密码为
    !!﷟HYPERLINK "http://urn:gd:lg:a:send-vm-keys"**Pa55w.rd**!!.

> ![A screenshot of a computer Description automatically
> generated](./media/image10.png)

2.  在任务栏中选择 **Hyper-V Manager**。

> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)

3.  在虚拟机下，右键单击 **SEA-WS4** 并选择 **Connect**。

> ![](./media/image12.png)

4.  在 **SEA-WS4** 窗口中，选择 **Start**
    开始。当计算机启动时，将窗口最大化。

> ![A screenshot of a computer Description automatically
> generated](./media/image13.png)

5.  以 [**Administrator**](urn:gd:lg:a:send-vm-keys) 身份登录
    **SEA-WS4**，密码为 !!﷟HYPERLINK
    "http://urn:gd:lg:a:send-vm-keys"**Pa55w.rd**!!.

> ![A screenshot of a computer Description automatically
> generated](./media/image14.png)

6.  右键单击 “**Start**”，选择 “**Windows Terminal (Admin)**” ，然后在
    “**User Account Control**” 提示符处选择 “**Yes**” 。

> ![](./media/image15.png)
>
> ![A screenshot of a computer error Description automatically
> generated](./media/image16.png)

7.  在 Windows PowerShell 命令行提示符下，键入以下 cmdlet，然后按
    **Enter**：

> !! Install-Script -Name Get-WindowsAutoPilotInfo!!

![A screenshot of a computer Description automatically
generated](./media/image17.png)

8.  您将收到 3
    个提示。每次键入 [**Y**](urn:gd:lg:a:send-vm-keys)，然后按
    **Enter**。

> ![](./media/image18.png)

9.  在 Windows PowerShell 命令行提示符下，键入以下 cmdlet，然后按
    **Enter**：

> !!**Set**-ExecutionPolicy *RemoteSigned*!!

10. 出现提示时，键入 [**Y**](urn:gd:lg:a:send-vm-keys)，然后按 Enter。

11. 在 Windows PowerShell 命令行提示符下，键入以下 cmdlet，然后按
    **Enter**：

> !!Get-WindowsAutoPilotInfo.ps1 -OutputFile C:\Computer.csv!!
>
> ![](./media/image19.png)

12. 在 Windows PowerShell 命令行提示符下，键入以下命令，按
    **Enter**，然后查看文件内容：

13. **type** !!C:\Computer.csv!!

> ![](./media/image20.png)

14. 在 Windows PowerShell 命令行提示符下，键入以下命令，然后按
    **Enter**。这会将文件复制到 **SEA-SVR2**：

15. copy !!c:\computer.csv \\sea-svr2\labfiles!!

> ![A screenshot of a computer screen Description automatically
> generated](./media/image21.png)

16. 关闭 Windows PowerShell 命令提示符。

任务 3：使用 Windows Autopilot 部署配置文件

1.  切换到 [***SEA-SVR1***](urn:gd:lg:a:select-vm)。

> ![](./media/image22.png)

2.  在 **Microsoft Edge** 中，打开一个新选项卡并导航到 !!﷟HYPERLINK
    "https://intune.microsoft.com"**https://intune.microsoft.com**!!
    如果出现提示，请登录并password.[**admin@M365xXXXXXXX.onmicrosoft.com**](mailto:admin@M365xXXXXXXX.onmicrosoft.com)!!
    和密码。

3.  在 **Microsoft Intune 管理中心**，选择 “**Devices**” 。

4.  在 **Device enrollment** （设备注册） 部分中，选择 **Enroll
    devices** （注册设备）。

5.  在详细信息窗格中，向下滚动到 **Windows Autopilot Deployment
    Program**，然后选择 **Devices**。

> ![A screenshot of a computer Description automatically
> generated](./media/image23.png)

6.  在菜单栏上的 **Windows Autopilot devices** 边栏选项卡中，选择
    “**Import**” ，选择 **folder icon**，然后浏览到 !!﷟HYPERLINK
    "http://urn:gd:lg:a:send-vm-keys"**\\SEA-SVR2\Labfiles**!!,
    选择**Computer.csv**，选择 **Open**，然后选择 “**Import**” 。

> ![](./media/image24.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image25.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image26.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image27.png)
>
> **注意：** 导入过程最多可能需要 15 分钟，但通常需要大约 5 分钟。
>
> **重要提示：**该过程完成后，设备可能不会显示。如果是这种情况，请选择
> **Sync** （同步） 按钮，等待几分钟，然后选择 **Refresh** （刷新）。

7.  选择 “**X**” 以关闭 “**Windows Autopilot devices**” 边栏选项卡。

> ![](./media/image28.png)

8.  在 Windows enrollment （Windows 注册）
    边栏选项卡上的详细信息窗格中，选择 **Deployment
    Profiles**（部署配置文件）。

> ![](./media/image29.png)

9.  在 “**Windows AutoPilot deployment profiles**” 边栏选项卡上，选择
    “**Create profile**” ，然后选择 “**Windows PC**” 。

> ![](./media/image30.png)

10. 在 **Basics** 选项卡的 **Name** 文本框中，键入 !!﷟HYPERLINK
    "http://urn:gd:lg:a:send-vm-keys"**Contoso profile1**!!.

11. 对于 “**Convert all targeted devices to Autopilot**” ，选择
    “**No**”，然后选择 “**Next**” 。

> ![A screenshot of a computer Description automatically
> generated](./media/image31.png)

12. 在 “**Out-of-box experience（OOBE）**” 选项卡上，确保将
    “**Deployment mode**” 设置为 “**User-Driven**” 。

13. 确保将 **Join to Microsoft Entra ID as** 设置为 **Microsoft Entra
    Joined**。

14. 确保设置了以下选项：

    - Microsoft 软件许可条款：**Hide**

    - 隐私设置：**Hide**

    - 隐藏更改帐户选项：**Hide**

    - 用户帐户类型：**Administrator**。

    - 允许预配置部署：**No**

    - 语言 （区域） ：**Operating system default**

    - 自动配置键盘：**Yes**

    - 应用设备名称模板： **No**

15. 选择 **Next**。

> ![](./media/image32.png)

16. 在 **Assignments** （分配） 选项卡上的 **Included groups**
    （包含的组） 下，选择 **Add groups** （添加组）。

17. 选择 **IT Devices** 组，然后单击 **Select**。选择
    **Next**（下一步）。

> ![](./media/image33.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image34.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image35.png)

18. 在 “**Review + create**” 边栏选项卡上，查看信息，然后选择
    “**Create**” 。

> ![A screenshot of a computer Description automatically
> generated](./media/image36.png)
>
> ![](./media/image37.png)

任务 4：重置电脑

1.  切换到 [***SEA-SVR2***](urn:gd:lg:a:select-vm)。 **SEA-WS4**
    计算机仍应最大化。

> ![](./media/image38.png)

2.  在 **SEA-WS4** 上，选择 **Start** 开始，键入 !!﷟HYPERLINK
    "http://urn:gd:lg:a:send-vm-keys"**reset**!! ，然后选择 **Reset this
    PC**。

> ![](./media/image39.png)

3.  在 “**Reset this PC**” 部分中，选择 “**Reset PC**” 。

> ![A screenshot of a computer Description automatically
> generated](./media/image40.png)

4.  选择 **Remove everything** （删除所有内容），然后选择 **Local
    reinstall**（本地重新安装）。

> ![A blue screen with white text Description automatically
> generated](./media/image41.png)
>
> ![A blue screen with white text Description automatically
> generated](./media/image42.png)

5.  选择 **Next** ，然后选择 **Reset**。

> ![A screenshot of a computer Description automatically
> generated](./media/image43.png)
>
> ![A blue screen with white text Description automatically
> generated](./media/image44.png)
>
> **注意：**通常，新部署物理设备不需要此任务。设备的 Autopilot
> 信息由制造商提供，也可以在 OOBE
> 之前从设备获取。在本实验中，我们必须启动重置以模拟新设备 OOBE。
>
> **注意：** 此过程可能需要 45-60
> 分钟，并且在此过程中会重新启动几次。在此任务完成时，您的教师可以继续学习下一个模块。请务必在下一次实验期间返回完成任务
> 5。

任务 5：验证 Autopilot 部署

1.  在 **Contoso Corp. 登录页面上**，输入 !!﷟HYPERLINK
    "mailto:Cindy@M365x19242953.onmicrosoft.com"**Cindy@M365x19242953.onmicrosoft.com**!!
    ，然后选择 **Next**。

2.  在 Password 页面，输入 !!﷟HYPERLINK
    "mailto:P@55w.rd1234"**P@55w.rd1234**!!，然后选择 **Sign in**
    （登录）。

3.  在 “**Use Windows Hello with your account**” 中，选择 “**OK**” 。

> ![A screenshot of a computer Description automatically
> generated](./media/image45.png)

4.  在 **Verify your identity** （验证您的身份） 页面上，选择 Text
    verification method （文本验证方法）。

> ![A screenshot of a computer Description automatically
> generated](./media/image46.png)

5.  在 **Enter code** （输入代码）
    页面上，输入已发送到您的移动设备的代码，然后选择 **Verify**
    （验证）。

> ![A screenshot of a computer Description automatically
> generated](./media/image47.png)

6.  在 **Setup up a PIN** 对话框的 **New PIN** 和 **Confirm PIN**
    字段中，输入 [**102938**](urn:gd:lg:a:send-vm-keys)，然后选择
    **OK**。

> ![A screenshot of a computer Description automatically
> generated](./media/image48.png)

7.  在 **All set！**页面上，选择 **OK**。

8.  选择 **Start** （开始），然后选择 **Settings** （设置）。

> ![A screenshot of a computer Description automatically
> generated](./media/image49.png)

9.  选择 “**Accounts**”，然后选择 “**Access work or school**”
    。验证设备是否已连接到 Contoso 的 Azure AD。

> ![A screenshot of a computer Description automatically
> generated](./media/image50.png)

10. 选择 “**Connected to Contoso's Azure AD**”，然后选择 “**Info**” 。

> ![A screenshot of a computer Description automatically
> generated](./media/image51.png)

11. 在 **Managed by Contoso** （由 Contoso 管理）
    页面上，向下滚动，然后选择 **Sync** （同步）。

> ![A screenshot of a computer Description automatically
> generated](./media/image52.png)
>
> ![](./media/image53.png)

12. 在 **SEA-WS4** 上，关闭 **Settings** 窗口。

13. 切换到 [***SEA-SVR1***](urn:gd:lg:a:select-vm)。

14. 在 Microsoft Entra 管理中心，选择 “**Identity**”，选择 “**Devices**”
    ，然后选择 “**All devices**” 。

> ![](./media/image54.png)
>
> 请注意，新设备显示的名称以 “**DESKTOP-**” 开头。另请注意，加入类型是
> **Microsoft Entra ID joined**，Cindy White 作为所有者加入。

15. 选择 Autopilot 设备。查看顶部菜单栏中的管理选项。

> 请注意，您可以 **Retire、Wipe、Sync** 和 **Restart** 设备。

16. 选择菜单栏末尾的省略号，并注意其他管理功能。

> ![A screenshot of a computer Description automatically
> generated](./media/image55.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image56.png)
>
> 其他功能包括 Fresh Start、Autopilot Reset、Quick scan、Full scan 等。

17. 关闭Microsoft Edge。

**结果：**完成本练习后，您将使用用户驱动模式为 Windows 11 设备配置了
Autopilot。
