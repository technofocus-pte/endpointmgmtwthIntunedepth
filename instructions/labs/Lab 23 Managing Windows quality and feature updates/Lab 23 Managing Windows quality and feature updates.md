实验 23：管理 Windows 质量和功能更新

**总结**

在本实验中，你将使用 Intune 配置 Windows 质量和功能更新设置。

**先决条件**

在此实验之前，必须完成以下实验：

- 实验 01 - 管理设备注册到 Intune

- 实验 06 - 将设备注册到 Intune

- 实验 07 - 创建和部署配置文件

**注意：**您还需要一部可以接收短信的移动电话，该短信用于保护 Azure AD 的
Windows Hello 登录身份验证。

**场景**

系统要求你将更新通道配置为仅影响属于 Contoso
开发人员设备组成员的设备。此组必须满足以下要求：

- 质量更新延迟期（天）：**15**

- 功能更新延迟期（天）： **45**

- 暂停 Windows 更新的选项：**Disable**

- 检查 Windows 更新的选项：**Enable**

- 传递优化：下载模式：**HTTP only, no peering (0)**

任务 1：验证单个设备的当前更新设置

1.  切换到 [***SEA-WS1***](urn:gd:lg:a:select-vm)，以 **Cindy White**
    的身份登录，PIN [**102938**](urn:gd:lg:a:select-vm)。

2.  选择 **Start** 开始，然后选择 **Settings** 图标。

> ![](./media/image1.png)

3.  在 “**Settings**” 中，选择 “**Windows Update**” 。

> 请注意，您可以选择将更新暂停特定时间。

4.  在 **Windows Update** 页面上，选择 **Advanced
    options**（高级选项）。

> ![](./media/image2.png)

5.  在 **Advanced options** （高级选项） 页面上，选择 **Delivery
    Optimization** （传递优化）。

> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)

6.  在 “**Delivery Optimization**” 页上，验证 “**Allow downloads from
    other PCs**” 选项是否已启用。

7.  选择 **Devices on internet and my local network**（Internet
    上的设备和我的本地网络）。

> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

8.  在 “**Settings**” 中，选择 “**Windows Update**” 。

> ![A screenshot of a computer Description automatically
> generated](./media/image5.png)

9.  选择 **Advanced options** （高级选项），然后选择 **Configure update
    policies** （配置的更新策略）。

> ![A screenshot of a computer Description automatically
> generated](./media/image6.png)
>
> 请注意，设备上未设置任何更新策略。
>
> ![A screenshot of a computer Description automatically
> generated](./media/image7.png)

10. 在导航窗格中，选择 **Windows Update**。

任务 2：查看应用的设置

1.  在 **Windows Update** 页面上，选择 **Update history**
    （更新历史记录）。

> ![A screenshot of a computer update Description automatically
> generated](./media/image8.png)

2.  查看列出的更新，然后选择 **Uninstall updates** （卸载更新）。

> ![A screenshot of a computer update Description automatically
> generated](./media/image9.png)

3.  查看 **Installed Updates** 中列出的更新。关闭已安装的更新。

> ![A screenshot of a computer Description automatically
> generated](./media/image10.png)

4.  关闭 Settings 应用程序。

任务 3：使用 Intune 配置更新设置

1.  切换到 [***SEA-SVR1***](urn:gd:lg:a:send-vm-keys) 并使用密码
    [**Pa55w.rd**](urn:gd:lg:a:send-vm-keys) 以
    [**Contoso\Administrator**](urn:gd:lg:a:send-vm-keys) 身份登录。

2.  在任务栏上，选择 **Microsoft Edge**。

3.  在 Microsoft Edge
    中，在地址栏中键入 [**https://intune.microsoft.com**](urn:gd:lg:a:send-vm-keys)，然后按
    Enter。

4.  使用密码以 [**admin@M365x19242953.onmicrosoft.com**](urn:gd:lg:a:send-vm-keys) 身份登录。

5.  在导航窗格中，选择 “**Devices**” ，然后选择 “**Windows 10 and later
    Updates**” 。

> ![](./media/image11.png)

6.  在 **Devices | Update rings for Windows 10 and later**
    边栏选项卡选择 “**Create profile**”。

> ![](./media/image12.png)

7.  在 “**Basics**” 边栏选项卡中，输入以下信息，然后选择 “**Next**” ：

    - 名字： !\![**Contoso Updates -
      standard**](urn:gd:lg:a:send-vm-keys)!!

    - 描述： !\![**Standard Windows updates
      configuration**](urn:gd:lg:a:select-vm)!!

> ![](./media/image13.png)

8.  在 **Update ring settings** 边栏选项卡中，输入以下信息，然后选择
    **Next**：

    - 质量更新延迟期（天）：[**15**](https://urn:gd:lg:a:send-vm-keys/)

    - 功能更新延迟期（天）：[**45**](https://urn:gd:lg:a:send-vm-keys/)

    - 暂停 Windows 更新的选项：**Disable**

    - 检查 Windows 更新的选项：**Enable**

> ![](./media/image14.png)

9.  在 “**Assignments**” 边栏选项卡上的 “**Included groups**” 下，选择
    “**Add groups**” 。

10. 在 “**Select groups to include**” 边栏选项卡上的 “**Search**”
    框中，选择 “**Contoso Developer devices**”，然后选择 “**Select**” 。

> ![A screenshot of a computer Description automatically
> generated](./media/image15.png)
>
> ![](./media/image16.png)

11. 选择 “**Next**”，然后在 “**Review + create**” 边栏选项卡上选择
    “**Create**” 。

12. 从导航栏中，选择 **Configuration profiles**。

13. 在 **Devices | Configuration** （配置）
    边栏选项卡的详细信息窗格中，选择 **Create policy**（创建策略）。

> ![](./media/image17.png)

14. 在 **Create a profile** （创建配置文件）
    边栏选项卡中，选择以下选项，然后选择 **Create** （创建）：

    - 平台：**Windows 10 and later**

    - 配置文件类型：**Templates**

    - 模板名称：**Delivery Optimization**

> ![](./media/image18.png)

15. 在 “**Basics**” 边栏选项卡中，输入以下信息，然后选择 “**Next**” ：

    - 名字： !\![**Contoso Developer - Delivery
      optimization**](urn:gd:lg:a:send-vm-keys)!!

    - 描述： !\![**Delivery optimization for
      Developer**](urn:gd:lg:a:send-vm-keys)!!

> ![](./media/image19.png)

16. 在 “**Configuration settings**” 边栏选项卡中，输入以下信息，然后选择
    “**Next**” ：

    - 下载模式： **HTTP only, no peering (0)**

> ![A screenshot of a computer Description automatically
> generated](./media/image20.png)

17. 在 “**Assignments**” 边栏选项卡上的 “**Included groups**” 下，选择
    “**Add groups**” 。

18. 在 “**Select groups to include**” 边栏选项卡上，选择 “**Contoso
    Developer devices**” ，然后选择 “**Select**” 。

> ![A screenshot of a computer Description automatically
> generated](./media/image21.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image22.png)

19. 选择 “**Next**” 两次，然后在 “**Review + create**” 边栏选项卡上选择
    “**Create**” 。

> ![Screenshot](./media/image23.png)

任务 4：验证设备的更新设置是否集中管理

1.  切换到 [***SEA-WS1***](https://intune.microsoft.com)。

2.  选择 **Start** 开始，然后选择 **Settings** 图标。

> ![](./media/image24.png)

3.  在 “**Settings**” 应用中，选择 “**Accounts**” ，然后选择 “**Access
    work or school**” 。

> ![A screenshot of a computer Description automatically
> generated](./media/image25.png)

4.  在 “**Access work or school**” 部分中，选择 “**Connected to
    Contoso's Azure AD**” 链接，然后选择 “**Info**” 。

> ![A screenshot of a computer Description automatically
> generated](./media/image26.png)

5.  在 “**Areas Managed by Contoso**” 对话框中，选择 “**Sync**”
    。等待同步完成。

> ![A screenshot of a computer Description automatically
> generated](./media/image27.png)

6.  在 “**Settings**” 应用中，选择 “**Windows Update**” 。

> 请注意，您无法暂停更新。

7.  选择 **Advanced options**（高级选项）。

> ![](./media/image28.png)

8.  选择 **Delivery Optimization** （传递优化）。

> ![A screenshot of a computer Description automatically
> generated](./media/image29.png)
>
> 请注意， “**Allow downloads from other PCs**” 不可用。

9.  在 “**Settings**” 应用中，选择 “**Windows Update**” ，选择
    “**Advanced options**” ，然后选择 “**Configured update policies**”
    。

> ![](./media/image30.png)
>
> 记下设备上设置的所有策略。

10. 关闭所有打开的应用程序和窗口。

> **注意：**练习环境配置为阻止应用 Windows
> 更新，以避免在练习期间出现延迟和意外影响。
