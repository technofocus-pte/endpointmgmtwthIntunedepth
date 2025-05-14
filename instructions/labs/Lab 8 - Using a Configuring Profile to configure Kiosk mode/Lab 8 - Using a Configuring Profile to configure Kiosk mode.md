**实验 8 - 使用配置配置文件配置 Kiosk 模式**

**总结**

在本实验中，我们将使用 Microsoft Intune 创建并应用配置文件，以在 Windows
11 设备上运行单应用展台模式。

**先决条件**

在此实验之前，必须完成以下实验：

- 实验 05 - 管理设备注册到 Microsoft Intune

注意：您还需要一部可以接收短信的移动电话，该短信用于保护 Windows Hello
登录对 Entra ID 的身份验证。

**练习 1：创建并应用配置文件**

**场景**

系统要求您将 **SEA-WS2** 配置为 Windows 11 展台，以允许 Contoso
访问者浏览 Internet。您需要确保 Kiosk 的配置如下：

- 单个应用程序、全屏展台。

- 自动登录。

- 提供对 Microsoft Edge 浏览器的访问，该浏览器将在公共浏览 （InPrivate）
  模式下进行配置。应为 **http://bing.com** 配置主页。

**任务 1：将 SEA-WS2 注册到 Microsoft Intune**

1.  以 **Admin**
    身份登录 [*SEA-WS2*](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)，密码为!!**Pa55w.rd**!!。

2.  在任务栏上，选择“**Start**”，然后选择“**Settings**”。

![](./media/image1.png)

3.  在 **Settings** （设置） 窗口中，选择 **Accounts** （帐户）。

![A screenshot of a computer Description automatically
generated](./media/image2.png)

4.  在 “帐户 ”页上，选择 “**Access work or school**”。

![A screenshot of a computer Description automatically
generated](./media/image3.png)

5.  在 “**Access work or school** ” 页面中，选择 “**Connect**”。

![A screenshot of a computer Description automatically
generated](./media/image4.png)

6.  在 **Microsoft 帐户**窗口中，选择**Join this device to Microsoft
    Entra ID**。

![A screenshot of a computer screen Description automatically
generated](./media/image5.png)

7.  在 **Sign in** （登录）
    页面上，键入 !!**AllanD@M365xXXXXXX.onmicrosoft.com**!! ，然后选择
    **Next**。

![](./media/image6.png)

8.  在 **Enter password** （输入密码） 页面上，输入租户密码：
    !!**P@55w.rd1234**!! ，然后选择 **Sign in （**登录）。

![A screenshot of a computer Description automatically
generated](./media/image7.png)

9.  在 **Make sure this is your organization** （确保这是您的组织）
    对话框中，选择 **Join** （加入）。

![A screenshot of a computer error Description automatically
generated](./media/image8.png)

10. 在 **You're all set！**页面上，阅读信息，然后选择 **Done**。

![A screenshot of a computer screen Description automatically
generated](./media/image9.png)

11. 在 “**Access work or school**”部分中，验证是否显示 “**Connected to
    Contoso's Azure AD**”。

![A screenshot of a computer Description automatically
generated](./media/image10.png)

12. 选择“**Connected to Contoso's Azure AD**”，然后选择 “**Info**”。

![A screenshot of a computer Description automatically
generated](./media/image11.png)

13. 向下滚动，然后选择 **Sync** （同步）。这将强制设备与 Intune 同步。

![A screenshot of a computer Description automatically
generated](./media/image12.png)

14. 关闭 **Settings** （设置） 窗口。

**任务 2：创建 Contoso 展台设备组**

1.  在 [*SEA-SVR1*](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)
    上， 切换到 **Microsoft Entra 管理中心**选项卡。导航并选择
    **Groups**，然后单击 **All groups**。

![](./media/image13.png)

2.  在 “**Groups | All groups**” 页上，选择 “**New group**”。

![A screenshot of a computer Description automatically
generated](./media/image14.png)

3.  在 **New Group** （新建组） 边栏选项卡上，输入以下信息：

- 组类型： **Security**

- 组名： !! Contoso Kiosk Devices!!

- 组介绍： !!All Windows devices configured as a Kiosk!!

- 成员身份类型： **Assigned**

4.  在 **Members** （成员） 下，选择 **No members selected**
    （未选择成员）。

![](./media/image15.png)

5.  在“**Add members**”边栏选项卡上的“**Search**”框中，键入 **Sea**.
    选择 **SEA-WS2**，然后选择 **Select**。

![](./media/image16.png)

6.  在 **New Group** 边栏选项卡上，选择 **Create**。

![A screenshot of a computer Description automatically
generated](./media/image17.png)

7.  在 “**Groups | All groups**” 边栏选项卡刷新页面，并验证是否显示
    “**Contoso Kiosk Devices**” 组。

![](./media/image18.png)

**任务 3：根据方案要求创建配置文件**

1.  返回到 Microsoft Intune 管理中心，从导航栏中选择“**Devices** ”。

![A screenshot of a computer Description automatically
generated](./media/image19.png)

2.  在 **Devices | Overview** 页中，选择 “**Windows**”，如下图所示。

![A screenshot of a computer Description automatically
generated](./media/image20.png)

3.  在 **Windows | Windows devices** 页面上，导航并单击 **Configuration
    profiles**。

![A screenshot of a computer Description automatically
generated](./media/image21.png)

4.  在 **Windows | Configuration profiles** 页面的 **Policies**
    选项卡中，单击 **+ Create** 并选择 **+ New Policy**。

![A screenshot of a computer Description automatically
generated](./media/image22.png)

5.  在 **Create a profile** （创建配置文件）
    边栏选项卡中，选择以下选项，然后选择 **Create** （创建）：

- 平台： **Windows 10 and later**

- 配置文件类型： **Templates**

- 模板名称： !!**Kiosk**!!

![A screenshot of a computer Description automatically
generated](./media/image23.png)

6.  在“**Basics**”边栏选项卡中，输入以下信息，然后选择“**Next**”：

- 名字： !!Contoso Kiosk Policy!!

- 描述： !!Basic settings for Contoso Kiosk Devices.!!

![A screenshot of a computer Description automatically
generated](./media/image24.png)

7.  在“**Configuration settings**”边栏选项卡上，在“**Select a kiosk
    mode**”旁边，选择“**Single app, full-screen kiosk**”。

其他选项根据所选模式显示。

8.  在“**Configuration
    settings**”边栏选项卡上，选择以下选项，然后选择“**Next**”：

- 用户登录类型： **Auto logon (Windows 10, version 1803 and later, or
  Windows 11)**

- 应用程序类型： **Add Microsoft Edge browser**

- Edge Kiosk 网址： !! **http://bing.com**!!

- Microsoft Edge 展台模式类型： **Public Browsing (InPrivate)**

- 空闲时间后刷新浏览器： **5**

- 指定 App Restarts 的维护时段： **Not configured**

> ![A screenshot of a computer Description automatically
> generated](./media/image25.png)

9.  在 **Assignments** 边栏选项卡上的 **Included groups** 下，选择 **Add
    groups**。

![A screenshot of a computer Description automatically
generated](./media/image26.png)

10. 在 **Select groups to include** （选择要包含的组）
    窗口中，选择 !!**Contoso Kiosk Devices**!!，然后单击 **Select**。

![A screenshot of a computer Description automatically
generated](./media/image27.png)

11. 在 **Assignment** 选项卡中，单击 **Next** 按钮。

![A screenshot of a computer Description automatically
generated](./media/image28.png)

12. 在 **Applicability Rules** 选项卡中，单击 **Next** 按钮。

![A screenshot of a computer Description automatically
generated](./media/image29.png)

13. 在 **Review + create** 选项卡中，单击 **Create** 按钮。

![A screenshot of a computer Description automatically
generated](./media/image30.png)

14. 将列出 Configuration profile （配置文件）。

![A screenshot of a computer Description automatically
generated](./media/image31.png)

**任务 4：验证是否已应用配置文件**

1.  以 **Admin**
    身份登录 [*SEA-WS2*](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10) 密码为!!**Pa55w.rd**!!。

2.  在任务栏上，选择“**Start**”，然后选择“**Settings**”。

![A screenshot of a computer Description automatically
generated](./media/image1.png)

3.  在 **Settings** （设置） 窗口中，选择 **Accounts** （帐户）。

![A screenshot of a computer Description automatically
generated](./media/image2.png)

4.  在 “帐户 ”页上，选择 “**Access work or school**”。

![A screenshot of a computer Description automatically
generated](./media/image3.png)

5.  选择“**Connected to Contoso's Azure AD**”，然后选择“**Info**”。

![A screenshot of a computer Description automatically
generated](./media/image11.png)

6.  向下滚动，然后选择 **Sync** （同步）。这将强制设备与 Intune 同步。

![A screenshot of a computer Description automatically
generated](./media/image12.png)

7.  关闭 **Settings** （设置） 窗口。

> ![](./media/image32.png)

5.  重新启动 **SEA-WS2**。

请注意，**SEA-WS2** 会自动登录并创建配置文件。登录完成后，将显示配置了
InPrivate 浏览的 Microsoft Edge。如果 SEA-WS2 未自动登录，请重复步骤 1-7
以确保策略已在设备上刷新。

![](./media/image33.png)

**结果：**完成本练习后，您将成功创建并分配配置文件，以将 Windows 11
设备配置为单应用展台。
