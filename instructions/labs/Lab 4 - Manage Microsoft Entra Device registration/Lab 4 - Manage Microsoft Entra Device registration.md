# 实验 4 - 管理 Microsoft Entra 设备注册。

**总结**

在本实验中，我们将使用 Windows 设备执行 Microsoft Entra 注册。

**练习 1：配置 Microsoft Entra 设备注册**

**场景**

一些用户要求使用其个人 iOS、Android 和 Windows 设备访问 Contoso
云资源。由于 Contoso 不拥有设备，因此您不希望让用户执行 Entra
加入以进行完整的设备管理。相反，你需要确保用户能够向 Microsoft Entra
注册其设备，它仍然允许你根据需要将公司策略应用于应用程序，并且仍然允许用户访问
Contoso 资源。您将使用 Windows 11 设备测试 Microsoft Entra 设备注册。

**任务 1：配置 Azure AD 设备注册**

1.  在
    [*SEA-SVR1*](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)上，在
    Edge 浏览器中打开一个新选项卡并输入以下 URL，
    !!**https://entra.microsoft.com**!!，然后按 **Enter** 按钮。

2.  使用您的 O365 租户 ID 登录
    !!**admin@M365xXXXXXXXX.onmicrosoft.com**!! 并使用租户管理员密码。

> ![A screenshot of a computer Description automatically
> generated](./media/image1.png)
>
> ![A screenshot of a login box Description automatically
> generated](./media/image2.png)

3.  在 **Stay signed in?** 对话框中，选择 **Yes** 按钮。

> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)

4.  在 **Microsoft Entra 管理中心**窗口中，导航并单击“**Identity**”。

![A screenshot of a computer Description automatically
generated](./media/image4.png)

5.  选择“**Devices**”，然后选择“**Device
    settings**”页，在详细信息窗格中，验证“**Users may register their
    devices with Microsoft Entra**”是否设置为“**All** ”并灰显。

> 在租户中启用 Microsoft Intune
> 时，此选项灰显并默认设置为“**All**”。这可确保所有用户都能够向 Azure AD
> 注册 Windows 10 或更高版本的个人、iOS、Android 和 macOS 设备。
>
> ![](./media/image5.png)

**任务 2：执行 Microsoft Entra 注册**

1.  切换到[*SEA-WS1*](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10) 并以
    Admin 身份登录，密码为 !!**Pa55w.rd**!!。

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image6.png)

2.  在任务栏上，选择“**Start**”，然后选择“**Settings**”。

![A screenshot of a computer Description automatically
generated](./media/image7.png)

3.  在 **Settings** （设置） 窗口中，选择 **Accounts** （帐户）。

![A screenshot of a computer Description automatically
generated](./media/image8.png)

4.  在 “**Accounts**”页上，选择 “**Access work or school**”。

![A screenshot of a computer Description automatically
generated](./media/image9.png)

5.  在 “**Access work or school**” 页面中，选择 “**Connect**”。

![A screenshot of a computer Description automatically
generated](./media/image10.png)

6.  在 **Sign in** （登录）
    页面上，键入 !!**JoniS@M365xXXXXXXX.onmicrosoft.com**!!，然后选择
    **Next**。

![](./media/image11.png)

7.  在 **Enter password** （输入密码） 页面上，输入租户密码：
    !\![**P@55w.rd1234**](mailto:P@55w.rd1234)!! ，然后选择 **Sign in**

![A screenshot of a computer Description automatically
generated](./media/image12.png)

8.  在 **You're all set！**页面上，选择 “**Done**”。

![A screenshot of a computer Description automatically
generated](./media/image13.png)

9.  在 **Access work or school** （访问工作或学校） 页面上，验证是否显示
    Joni 的 **Work or school account**。

![A screenshot of a computer Description automatically
generated](./media/image14.png)

10. 关闭 **Settings** （设置） 页面。

**任务 3：验证 Microsoft Entra 注册**

1.  在 [*SEA-WS1*](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)，上，右键单击
    **Start button**，然后选择 **Windows Terminal (Admin)**。

> ![A screenshot of a computer Description automatically
> generated](./media/image15.png)

2.  在 **User Account Control** （用户帐户控制） 对话框中，选择 **Yes**
    （是）。

> ![A screenshot of a computer error Description automatically
> generated](./media/image16.png)

3.  在 PowerShell 控制台中，键入以下内容，然后按 **Enter**：

> !!**dsregcmd /status**!!

4.  在 **User State** （用户状态） 下的输出中，验证是否显示
    **WorkplaceJoined ： YES** 。这表示用户已在 Microsoft Entra
    中执行了设备注册。

> ![A screenshot of a computer Description automatically
> generated](./media/image17.png)

5.  关闭 PowerShell，然后注销 **SEA-WS1**。

6.  切换到 SEA-SVR1。转到 **Microsoft Entra
    管理中心**窗口，导航并单击“**Identity**”。

> ![A screenshot of a computer Description automatically
> generated](./media/image18.png)
>
> 7\. 在“**Identity**”部分下，选择“**Devices**”，然后导航并单击“**All
> devices**”，如下图所示。
>
> ![A screenshot of a computer Description automatically
> generated](./media/image19.png)

8.  验证 **Join Type** 是否列为 **Microsoft Entra registered**
    以及所有者是否为 **Joni Sherman**。

> ![](./media/image20.png)
>
> 请注意，设备已注册 Microsoft Entra，而不是已加入 Microsoft Entra。注册
> Entra 的设备通常是无法加入 Entra
> 的设备，或者是用户个人拥有的设备。注册设备将提供对基于云的资源的访问权限。

9.  关闭Microsoft Edge。

**任务 4：登录到 Windows 并断开与组织的连接**

1.  切换到 [*SEA-WS1*](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)。在任务栏上，选择
    **Windows Start icon** 按钮，然后选择**Settings**。

![A screenshot of a computer Description automatically
generated](./media/image7.png)

2.  在 **Settings** （设置） 窗口中，选择 **Accounts** （帐户）。

> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)

3.  在 “**Accounts**”页上，选择 “**Access work or school**”。

> ![A screenshot of a computer Description automatically
> generated](./media/image9.png)

4.  在 “**Access work or school**”页面中，单击 **JJoniS@M3654xXXXXXXXX
    Work or school** 帐户 “旁边的下拉列表，如下图所示。

> ![](./media/image21.png)

5.  单击 **Disconnect** 按钮。

> ![A screenshot of a computer Description automatically
> generated](./media/image22.png)

6.  点击 **Yes** 按钮确认删除帐户。

> ![A screenshot of a computer Description automatically
> generated](./media/image23.png)
>
> 请注意，无需重启即可断开已注册 Microsoft Entra 的设备。

7.  注销 **SEA-WS1**。

![A screenshot of a computer Description automatically
generated](./media/image24.png)

**结果：**完成本练习后，您将配置 Microsoft Entra 设备注册。
