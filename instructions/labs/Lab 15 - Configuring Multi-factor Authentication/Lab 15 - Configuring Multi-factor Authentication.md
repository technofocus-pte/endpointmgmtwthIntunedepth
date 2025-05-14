实验 15 - 配置多重身份验证

**总结**

在本实验中，您将配置每用户多重身份验证 （MFA） 并使用条件访问策略应用
MFA。

练习 1：配置每用户多重身份验证。

**场景**

要为用户登录事件提供额外的安全性，您需要配置和测试多重身份验证
（MFA）。您决定首先测试每用户 MFA。Alex Wilber 已同意为您验证设置。

任务 1：在启用 MFA 之前验证登录

1.  切换并登录 [**SEA-WS3**](urn:gd:lg:a:select-vm) 为 !\![**Admin**](urn:gd:lg:a:send-vm-keys)!!
    用密码 !\![**Pa55w.rd**](urn:gd:lg:a:send-vm-keys)!!

2.  在任务栏上，选择 **Microsoft
    Edge**。在地址栏中，输入 !\![**outlook.office.com**](urn:gd:lg:a:send-vm-keys)!!，然后按
    Enter 键。

3.  在 **Sign in** （登录） 页面，输入
    !!**AlexW@M365xXXXXXXX.onmicrosoft.com**!!，然后选择 **Next**。

4.  在 **Enter password** （输入密码） 页面上，输入 !!**P@55w.rd1234**!!
    ，然后选择 **Sign in** （登录）。在 Edge Save password
    提示符处，选择 **Save** （保存）。

> Outlook 网页版将打开。请注意，登录 Outlook 网页版只需要密码。

5.  在右上角，选择 **Account manager for Alex Wilber**，然后选择 **Sign
    out** （注销）。

> ![](./media/image1.png)

6.  关闭 Microsoft Edge。

任务 2：为用户启用 MFA

1.  切换到 [**SEA-SVR1**](urn:gd:lg:a:select-vm)。
    在 [**SEA-SVR1**](urn:gd:lg:a:select-vm)上，如有必要，请以
     [**Contoso\Administrator**](urn:gd:lg:a:send-vm-keys) 请使用密码 !!
    [**Pa55w.rd**](urn:gd:lg:a:send-vm-keys)!!  并关闭 **Server
    Manager**。

2.  在任务栏上选择 **Microsoft Edge**，导航到 **Microsoft Entra
    管理中心** !!**https://Entra.Microsoft.com**!!

3.  使用 **Office 365 Tenant admin** 凭据登录。

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)
>
> 此时将打开 **Microsoft Entra 管理中心**。

4.  在 **Microsoft Entra 管理中心**的导航窗格中，展开 “**Identity**”
    ，然后选择 “**Users**” 。

5.  选择 **All users** （所有用户），然后在结果窗格顶部选择 **Per-user
    MFA** （每用户 MFA）。您可能需要先选择省略号才能查看 **Per-user
    MFA** （每用户 MFA） 选项。

> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)

6.  在 Multi-Factor Authentication 页面上，选择 **Service settings**
    （服务设置）。

> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

7.  向下滚动到 **verification options** （验证选项） 部分。

> 记下可为用户验证配置的各种方法。

8.  在 **Remember multi-factor authentication on trusted device**
    （在受信任的设备上记住多重身份验证） 部分中，选中 **Allow users to
    remember multi-factor authentication on devices they trust**
    （允许用户在他们信任的设备上记住多重身份验证） 旁边的复选框。

9.  在 **Number of days users can trust devices for**
    （用户可以信任设备的天数） 旁边，输入 **30** 并选择 **Save**
    （保存）。出现提示时选择 **close** 。

> ![](./media/image5.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image6.png)

10. 在页面顶部的 **multi-factor authentication** （多重身份验证）
    下，选择 **users** （用户）。

> ![A screenshot of a computer Description automatically
> generated](./media/image7.png)

11. 在用户列表中，选中 **Alex Wilber** 旁边的复选框。

12. 在 Alex Wilber 页面中，选择 **Enable**。

> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)

13. 在 **About enabling multi-factor auth** （关于启用多重身份验证）
    消息中，选择 **enable multi-factor auth** （启用多重身份验证）。

> ![A screenshot of a computer Description automatically
> generated](./media/image9.png)

14. 在 **Updates successful**（更新成功）消息中，选择
    **close**（关闭）。请注意，Alex Wilber 的 **Multi-Factor Auth
    Status** （多重身份验证状态） 现在为 **Enabled** （已启用）。

> ![A screenshot of a computer Description automatically
> generated](./media/image10.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)

15. 关闭 Microsoft Edge。

任务 3：注册和验证 MFA

1.  切换到 [**SEA-WS3**](urn:gd:lg:a:select-vm)。 在任务栏上，选择
    **Microsoft Edge**。

2.  在地址栏中，输入 !\![**outlook.office.com**](urn:gd:lg:a:send-vm-keys)!!，然后按
    **Enter** 键。

3.  在 **Pick an account** （选择帐户）
    页面上，选择 !\![**AlexW@M365xXXXXXXX.onmicrosoft.com**](mailto:AlexW@M365xXXXXXXX.onmicrosoft.com)!!

> ![A screenshot of a computer Description automatically
> generated](./media/image12.png)

4.  在 **Enter password** （输入密码）
    页面上，输入 !!**P@55w.rd1234**!!**，**然后选择 **Sign in**
    （登录）。

5.  在 “**More information required**” 页面上，选择 “**Next”**
    。此时将打开 Keep your account secure 页面。

> ![A screenshot of a computer Description automatically
> generated](./media/image13.png)
>
> 通常，您需要使用 Microsoft Authenticator
> 应用程序来管理多重身份验证。但是，对于此实验方案，您将使用短信。

6.  在 **Keep your account secure** （确保您的账户安全） 页面上，选择
    **I want to set up a different method** （我想设置其他方法）。

> ![A screenshot of a computer Description automatically
> generated](./media/image14.png)

7.  在 **Choose a different method** 对话框中，选择 **Phone**
    （电话），然后选择 **Confirm** （确认）。

> ![A screenshot of a computer Description automatically
> generated](./media/image15.png)

8.  在 **Phone** （电话） 页面上，输入您可以接收短信的手机号码，然后选择
    **Next** （下一步）。

> ![A screenshot of a computer screen Description automatically
> generated](./media/image16.png)

9.  收到短信形式的验证码后，在 **Phone** （电话）
    页面上指示的位置输入验证码，然后选择 **Next** （下一步）。

> ![](./media/image17.png)

10. 在 SMS 验证消息中，选择 **Next**（下一步），然后选择
    **Done**（完成）。

> ![A screenshot of a computer screen Description automatically
> generated](./media/image18.png)
>
> ![](./media/image19.png)

11. 在 “保持登录状态” 消息中，选择 “**No**”。

> ![A screenshot of a computer error Description automatically
> generated](./media/image20.png)
>
> Outlook 网页版将打开 Alex Wilber 的收件箱。

12. 在右上角，选择 **Account manager for Alex Wilber**，然后选择 **Sign
    out** （注销）。

> ![](./media/image21.png)
>
> **注意：**用户只需在首次使用 MFA
> 时进行注册。后续登录只需要提供验证码，该验证码会发送到您在注册时输入的电话号码。

13. 在地址栏中，输入 !\![**outlook.office.com**](urn:gd:lg:a:send-vm-keys)!!，然后按
    Enter 键。

14. 在 **Pick an account** （选择帐户）
    页面上，选择 !!**AlexW@M365xXXXXXXXX.onmicrosoft.com**!!

15. 在 **Enter password** （输入密码）
    页面上，输入 !!**P@55w.rd1234**!!**，**然后选择 **Sign in**
    （登录）。

> ![A screenshot of a computer error Description automatically
> generated](./media/image22.png)
>
> **Verify your identity** （验证您的身份）
> 提示随即打开。请注意，它包含电话号码的最后两位数字。

16. 在 **Verify your identity** （验证您的身份）
    提示符处，选择您的文本电话号码。

17. 在 **Enter code** （输入代码）
    页面上，输入发送到您的移动电话的代码，然后选择 **Verify** （验证）。

> ![A screenshot of a computer error message Description automatically
> generated](./media/image23.png)
>
> 请注意，您可以选中一个复选框，在 30 天内不再要求验证。

18. 由于 **Microsoft Authenticator App**
    确保更高的安全性和流畅的体验，系统将提示您配置相同的内容，现在单击
    **Skip for now**

> ![A screenshot of a computer error Description automatically
> generated](./media/image24.png)

19. 在 “保持登录状态” 消息中，选择 “**No**”。Outlook 网页版将打开 Alex
    Wilber 的收件箱。

> ![A screenshot of a computer error Description automatically
> generated](./media/image25.png)

20. 在右上角，选择 **Account manager for Alex Wilber**，然后选择 **Sign
    out** （注销）。

> ![A computer screen shot of a computer screen Description
> automatically generated](./media/image26.png)

21. 关闭 Microsoft Edge。

任务 3：删除每用户 MFA

1.  切换到 [**SEA-SVR1**](urn:gd:lg:a:select-vm)。在 [**SEA-SVR1**](urn:gd:lg:a:select-vm)上，
    如有必要，请以 [**Contoso\Administrator**](urn:gd:lg:a:send-vm-keys) 使用密码 
    !\![**Pa55w.rd**](urn:gd:lg:a:send-vm-keys)!! 并关闭 **Server
    Manager**。

2.  在任务栏上选择 **Microsoft Edge**，导航到 **Microsoft Entra
    管理中心** !!**https://Entra.Microsoft.com**!!

3.  使用 **Office 365 租户管理员**凭据登录。

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)
>
> 此时将打开 **Microsoft Entra 管理中心**。

4.  在 **Microsoft Entra 管理中心**的导航窗格中，展开 “**Identity**”
    ，然后选择 “**Users**” 。

5.  选择 **All users** （所有用户），然后在结果窗格顶部选择 **Per-user
    MFA** （每用户 MFA）。您可能需要先选择省略号才能查看 **Per-user
    MFA** （每用户 MFA） 选项。

> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)

6.  在页面顶部的 **multi-factor authentication** （多重身份验证）
    下，选择 **users** （用户）。

7.  在用户列表中，选中 **Alex Wilber** 旁边的复选框。

> 请注意，Alex Wilber 的 **Multi-Factor Auth Status** 现在设置为
> **Enforced**（强制）（之前设置为 Enabled）。这是因为 Alex
> 已注册并正在使用 MFA。
>
> ![A screenshot of a computer Description automatically
> generated](./media/image27.png)

8.  在 Alex Wilber 页面中，选择 **Manage user settings**
    （管理用户设置）。

> ![A screenshot of a computer Description automatically
> generated](./media/image28.png)

9.  在 Manage user settings （管理用户设置）
    框中，选中所有三个选项旁边的复选框，选择 **Save** （保存），然后选择
    **close** （关闭）。

> ![A screenshot of a computer Description automatically
> generated](./media/image29.png)
>
> 这些选项将删除 Alex 的所有已保存 MFA 设置。
>
> ![A white rectangular frame with black border Description
> automatically generated](./media/image30.png)

10. 在用户列表中，选中 **Alex Wilber** 旁边的复选框。

11. 在 Alex Wilber 页面中，选择 **Disable** （禁用）。

> ![A screenshot of a computer Description automatically
> generated](./media/image31.png)

12. 在 **Disable multi-factor authentication** 消息中，选择 **yes**。

> ![](./media/image32.png)

13. 在 **Updates successful**（更新成功）消息中，选择
    **close**（关闭）。

> ![A white screen with black text Description automatically
> generated](./media/image33.png)
>
> 请注意，Alex Wilber 的 **Multi-Factor Auth Status**
> （多重身份验证状态） 现在为 **Disabled** （禁用）。
>
> ![A screenshot of a computer Description automatically
> generated](./media/image34.png)

14. 关闭 Microsoft Edge。

**结果：**完成本练习后，您将成功配置每用户多重身份验证。

练习 2：使用条件访问配置多重身份验证

**场景**

要为用户登录事件提供额外的安全性，您需要配置和测试多重身份验证
（MFA）。您决定使用条件访问策略为您的 MFA 要求提供更大的灵活性。Alex
Wilber 已同意为您验证设置。

任务 1：在使用 MFA 启用条件访问之前验证登录

1.  切换并登录 [**SEA-WS3**](urn:gd:lg:a:select-vm) 为 !\![**Admin**](urn:gd:lg:a:send-vm-keys)!!
     用密码 !\![**Pa55w.rd**](urn:gd:lg:a:send-vm-keys)!!

2.  在任务栏上，选择 **Microsoft
    Edge**。在地址栏中，输入 !\![**outlook.office.com**](urn:gd:lg:a:send-vm-keys)!!
    ，然后按 Enter 键。

3.  在 **Sign in** （登录）
    页面，输入 !!**AlexW@M365xXXXXXXX.onmicrosoft.com**!! ，然后选择
    **Next**。

4.  在  **Enter password** （输入密码）
    页面上，输入 !!**P@55w.rd1234**!!，然后选择 **Sign in** （登录）。在
    Edge Save password 提示符处，选择 **Save** （保存）。

> Outlook 网页版将打开。请注意，登录 Outlook 网页版只需要密码。

5.  在右上角，选择 **Account manager for Alex Wilber**，然后选择 **Sign
    out** （注销）。

> ![A screenshot of a computer Description automatically
> generated](./media/image1.png)

6.  关闭 Microsoft Edge。

任务 2：使用 MFA 配置条件访问

1.  切换到 [**SEA-SVR1**](urn:gd:lg:a:select-vm).
    在 [**SEA-SVR1**](urn:gd:lg:a:select-vm)上，如有必要，请以 [**Contoso\Administrator**](urn:gd:lg:a:send-vm-keys) 使用密码 
    !\![**Pa55w.rd**](urn:gd:lg:a:send-vm-keys)!!  并关闭 **Server
    Manager**。

2.  在任务栏上选择 **Microsoft Edge**，导航到 **Microsoft Entra
    管理中心** !!**https://Entra.Microsoft.com**!!

3.  使用 **Office 365 租户管理员**凭据登录。

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)
>
> 此时将打开 **Microsoft Entra 管理中心**。

4.  在 **Microsoft Entra 管理中心**的导航窗格中，依次展开 “**Identity**”
    、 “**Protection**”和“**Conditional Access**” 。

> ![A screenshot of a computer Description automatically
> generated](./media/image35.png)

5.  在 “**Conditional Access**” 页上，选择 “**Policies**”，然后选择 “**+
    New policy**” 。

> ![A screenshot of a computer Description automatically
> generated](./media/image36.png)

6.  在 **New Conditional access policy** （新建条件访问策略） 页面的
    **Name** （名称） 框中，输入 !\![**Contoso MFA
    Policy**](urn:gd:lg:a:send-vm-keys)!!。

7.  在 “**Assignments**” 下，选择 “**0 users or workload identities
    selected**” 。

> ![A screenshot of a computer Description automatically
> generated](./media/image37.png)

8.  在 Users and groups （用户和组） 窗格中，选择 **Select users and
    groups** （选择用户和组） 旁边的选项，然后选中 **Users and groups**
    （用户和组） 旁边的复选框。

9.  在 **Select** 页面上，选择 **Alex Wilber**，然后单击 **Select**。

> ![A screenshot of a computer Description automatically
> generated](./media/image38.png)
>
> 请注意，通常您会指定一个组，但在本练习中，我们只在 Alex Wilber
> 上测试设置。

10. 在 Target resources （目标资源） 下选择 **No target resources
    selected** （未选择目标资源），然后单击 **Select
    apps**（选择应用程序）。

> ![A screenshot of a computer Description automatically
> generated](./media/image39.png)

11. 在 **Select** （选择） 页面上，选中  **Office
    365** 旁边的复选框，然后单击 **Select** （选择）。

> ![A screenshot of a computer Description automatically
> generated](./media/image40.png)

12. 在 **Access controls** 下的 **Grant** 部分中，选择 **0 controls
    selected**。

> ![A screenshot of a computer Description automatically
> generated](./media/image41.png)

13. 在 **Grant** （授予） 页面上，选择 **Grant access**
    （授予访问权限），选中 **Require multi-factor authentication**
    （需要多重身份验证） 旁边的复选框，然后单击 **Select** （选择）。

> ![A screenshot of a computer Description automatically
> generated](./media/image42.png)

14. 在 **Enable policy** （启用策略） 下，选择 **On** （打开）。

15. 选择 **Create** （创建） 以创建 Contoso MFA 策略。请注意，该策略以
    State （状态） 为 **On** （开启） 列出。

> ![A screenshot of a computer Description automatically
> generated](./media/image43.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image44.png)

16. 在 **Microsoft Entra 管理中心**中，选择 “**Users**” 。在 User
    （用户） 列表中，选择 **Alex Wilber**。

> ![A screenshot of a computer Description automatically
> generated](./media/image45.png)

17. 在 Alex Wilber 页面上，选择 **Authentication methods**。

> ![](./media/image46.png)
>
> 请注意，已经为 Alex 配置了电话号码，

18. 关闭Microsoft Edge。

任务 3：验证条件访问 MFA

1.  切换到 [**SEA-WS3**](urn:gd:lg:a:select-vm)。 在任务栏上，选择
    **Microsoft Edge**。

2.  在地址栏中，输入 !\![**outlook.office.com**](urn:gd:lg:a:send-vm-keys)!!，然后按
    Enter 键。

3.  在 **Pick an account** （选择帐户） 页面上，选择
    !!**AlexW@M365xXXXXXXX.onmicrosoft.com**!!

> ![A screenshot of a computer Description automatically
> generated](./media/image12.png)

4.  在 **Enter password** （输入密码）
    页面上，输入 !!**P@55w.rd1234**!!**，**然后选择 **Sign in**
    （登录）。

5.  在 **Verify your identity** （验证您的身份）
    提示符处，选择您的文本电话号码。

> ![A screenshot of a computer error Description automatically
> generated](./media/image22.png)

6.  在 **Enter code** （输入代码）
    页面上，输入发送到您的移动电话的代码，然后选择 **Verify** （验证）。

> ![A screenshot of a computer error message Description automatically
> generated](./media/image23.png)
>
> 请注意，您可以选中一个复选框，在 30 天内不再要求验证。

7.  在 “保持登录状态” 消息中，选择 “**No**”。Outlook 网页版将打开 Alex
    Wilber 的收件箱。

> ![A screenshot of a computer error Description automatically
> generated](./media/image25.png)

8.  在右上角，选择 **Account manager for Alex Wilber**，然后选择 **Sign
    out** （注销）。

> ![A computer screen shot of a computer screen Description
> automatically generated](./media/image26.png)

9.  关闭Microsoft Edge。

任务 4：删除条件访问 MFA

1.  切换到 [**SEA-SVR1**](urn:gd:lg:a:select-vm)。
    在 [**SEA-SVR1**](urn:gd:lg:a:select-vm)上，如有必要，请以 [**Contoso\Administrator**](urn:gd:lg:a:send-vm-keys) 使用密码
    !\![**Pa55w.rd**](urn:gd:lg:a:send-vm-keys)!!  并关闭 **Server
    Manager**。

2.  在任务栏上选择 **Microsoft Edge**，导航到 **Microsoft Entra
    管理中心**!!**https://Entra.Microsoft.com**!!

3.  使用 **Office 365 租户管理员**凭据登录。

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)
>
> 此时将打开 **Microsoft Entra 管理中心**。

4.  在 **Microsoft Entra 管理中心**的导航窗格中，依次展开 “**Identity**”
    、 “**Protection**” 和“**Conditional Access**” 。

> ![A screenshot of a computer Description automatically
> generated](./media/image35.png)

5.  在 “**Conditional Access**” 页面上，选择 “**Policies**” ，然后选择
    “**Contoso MFA Policy**” 。

6.  在 **Contoso MFA Policy** （Contoso MFA 策略） 页面上，选择
    **Delete** （删除），然后选择 **Delete** （删除）。

> ![A screenshot of a computer Description automatically
> generated](./media/image47.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image48.png)

7.  对于 **Delete** 确认，单击 **Delete** 按钮。

> ![A screenshot of a computer error Description automatically
> generated](./media/image49.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image50.png)

8.  关闭Microsoft Edge。

**结果：**完成本练习后，您将使用条件访问策略成功配置多重身份验证。
