**实验 6 - 将设备注册到 Microsoft Intune**

**总结**

在本实验中，你将将 Windows 客户端加入 Entra
ID，并验证设备是否已自动注册到 Microsoft Intune。

**先决条件**

在此实验之前，必须完成以下实验：

- 实验 \#1 - 在 Microsoft Entra ID 中管理身份

- 实验 \#2 - 使用 Microsoft Entra Connect 同步标识

- 实验 \#5 - 管理设备注册到 Microsoft Intune

注意：您可能还需要一部可以接收短信的移动电话，该短信用于保护 Windows
Hello 登录对 Entra ID 的身份验证。

**场景**

您已为 Cindy White 分配了适当的许可证，现在将测试将 Windows 设备加入
Entra ID 的过程，并使其自动注册到 Microsoft Intune。

**任务 1：自动将 Windows 设备注册到 Microsoft Intune**

1.  切换到
     [*SEA-WS1*](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10) 并以
    Admin 身份登录，密码为 !!**Pa55w.rd**!!

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image1.png)

2.  在任务栏上，选择“**Start**”，然后选择“**Settings**”。

![A screenshot of a computer Description automatically
generated](./media/image2.png)

3.  在 **Settings** （设置） 窗口中，选择 **Accounts** （帐户）。

![A screenshot of a computer Description automatically
generated](./media/image3.png)

4.  在 “帐户 ”页上，选择 “**Access work or school**”。

![A screenshot of a computer Description automatically
generated](./media/image4.png)

5.  在 “**Access work or school**” 页面中，选择 “**Connect**”。

![A screenshot of a computer Description automatically
generated](./media/image5.png)

6.  在 **Microsoft 帐户**窗口中，选择 **Join this device to Microsoft
    Entra ID**。

![](./media/image6.png)

7.  在 **Sign in** （登录）
    页面上，键入 !\![**Cindy@M365x51282399.onmicrosoft.com**](mailto:Cindy@M365x51282399.onmicrosoft.com)!!，然后选择
    **Next**。

![](./media/image7.png)

8.  在 **Enter password** （输入密码） 页面上，输入密码：
    !\![**P@55w.rd1234**](mailto:!!P@55w.rd1234)!!，然后选择 **Sign in**
    （登录）。

![A screenshot of a computer Description automatically
generated](./media/image8.png)

9.  **Make sure this is your organization** （这是您的组织）
    对话框，然后选择 **Join** （加入）。

![](./media/image9.png)

10. 在 **You're all set！**页面上，阅读信息，然后选择 **Done**。

![A screenshot of a computer Description automatically
generated](./media/image10.png)

11. 在 “**Access work or school**” 部分中，验证是否显示 “**Connected to
    Contoso's Azure AD**”。

12. 选择“**Connected to Contoso's Azure AD**”，然后选择“**Info**”。

![A screenshot of a computer Description automatically
generated](./media/image11.png)

13. 记下有关 Contoso 管理的区域的信息，向下滚动，然后选择 **Sync**
    （同步）。这将强制设备与 Intune 同步。

![A screenshot of a computer Description automatically
generated](./media/image12.png)

14. 关闭 **Settings** （设置） 窗口。

**任务 2：验证设备注册到 Microsoft Entra 和 Intune**

1.  在 **SEA-WS1** 任务栏上，选择 **Start**
    开始，键入 !!**certlm.msc**!! 按 **Enter** 键。

![A screenshot of a computer Description automatically
generated](./media/image13.png)

2.  在 User Account Control （用户帐户控制） 对话框中，选择 **Yes**
    （是） 按钮。

![](./media/image14.png)

3.  在 **Certificates** （证书） 控制台的导航窗格中，展开 **Personal**
    （个人） 并选择 **Certificate** （证书）
    节点。验证详细信息窗格中是否列出了以下证书：

- Microsoft Intune MDM 设备 CA

- MS-组织访问

- MS-Organization-P2P-Access \[2024\]

这表示设备已在 Microsoft Entra 和 Intune 中注册。

![](./media/image15.png)

4.  关闭 Certificates （证书） 窗口。

5.  右键单击 **Start** 开始 按钮，然后选择 **Windows Terminal
    (Admin)**。

![A screenshot of a computer Description automatically
generated](./media/image16.png)

6.  在 **User Account Control** （用户帐户控制） 对话框中，单击 **Yes**
    （是） 按钮。

![A screenshot of a computer error Description automatically
generated](./media/image17.png)

7.  在 PowerShell 控制台中，键入以下内容，然后按 **Enter**：

!!**dsregcmd /status**!!

8.  在输出中，在 **Device State**（设备状态）下，验证是否显示
    **AzureAdJoined ： YES**。这表示设备已加入 Azure AD。

![A screenshot of a computer Description automatically
generated](./media/image18.png)

9.  在 **Tenant Details** （租户详细信息）
    下的输出中，验证是否存在以下三个条目：

- mdmUrl:https://enrollment.manage.microsoft.com/enrollmentserver/discovery.svc

- mdmTouUrl:https://portal.manage.microsoft.com/TermsofUse.aspxmdm

- ComplianceUrl:https://portal.manage.microsoft.com/?portalAction=Compliance

![](./media/image19.png)

*注意：这些条目表示设备已在 Intune 中注册。*

**任务 3：以 Microsoft Entra ID 用户身份登录**

1.  当您使用本地管理员帐户登录时注销 **SEA-WS1**。

2.  在 登录 屏幕上，选择 其他用户 并以
     !!**Cindy@M365xXXXXXXX.onmicrosoft.com**!!  使用密码：
     !\![**P@55w.rd1234**](mailto:P@55w.rd1234)!!

![](./media/image20.png)

3.  等待创建配置文件

![A screenshot of a computer Description automatically
generated](./media/image21.png)

**注意 –** 如果系统提示您使用 **Windows
Hello，**请相应地完成登录过程，然后在 **Set up a PIN** 页面的 **New
PIN** 和 **Confirm PIN** 框中，键入 !!**102938**!!  ，然后选择 **OK**。

![A screenshot of a computer Description automatically
generated](./media/image22.png)

4.  注销 **SEA-WS1**。

**任务 4：在 Microsoft Intune 控制台中验证设备注册**

1.  切换到 *[SEA-SVR1](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)*
    并使用提供的凭据登录。

2.  在 Microsoft Edge
    浏览器中，键入 !!**https://intune.microsoft.com**!! ，然后按
    **Enter**。使用您的 Office 365 租户管理员帐户登录。

3.  在导航窗格中，选择 **Devices**（设备）。

![A screenshot of a computer Description automatically
generated](./media/image23.png)

4.  在 **Devices | Overview** 页面，导航并单击 **Windows**。

![](./media/image24.png)

5.  导航并单击 **Windows devices**。验证 **SEA-WS1** 是否已列出。

请注意，对于 SEA-WS1，“**托管者**”列显示 **Intune**，“**Ownership**”
列显示“**Corporate**”。

![A screenshot of a computer Description automatically
generated](./media/image25.png)

**注意：**此视图列出了已注册到 Intune 的设备。请记住，您在 Microsoft
Entra 和 Microsoft Intune 之间配置了自动注册，因此，加入或注册到
Microsoft Entra 的任何设备都会自动注册到 Microsoft
Intune。在设置注册之前加入的任何设备仅加入或注册到 Entra，但不会在
Intune 中注册。

6.  打开一个新选项卡并导航到 **Microsoft Entra 管理中心**
    !!**https://entra.microsoft.com**!!。单击 **Devices**，然后选择
    **All devices**。

![A screenshot of a computer Description automatically
generated](./media/image26.png)

7.  请注意 **SEA-WS1**。请注意，“**Join Type**”列显示“已加入 Microsoft
    Entra”，而“**MDM**”列显示“Microsoft Intune”。

![A screenshot of a computer Description automatically
generated](./media/image27.png)

**结果：**完成本练习后，您将成功将 Windows 客户端加入 Microsoft Entra
ID，并验证设备是否已自动注册到 Microsoft Intune。
