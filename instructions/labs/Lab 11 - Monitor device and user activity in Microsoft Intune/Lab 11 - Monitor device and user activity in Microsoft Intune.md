**实验 11 - 在 Intune 中监视设备和用户活动**

**总结**

在本实验中，您将监控用户登录活动、审核日志和设备活动。

**先决条件**

在此实验之前，必须完成以下实验：

- 实验 \#1 - 在 Microsoft Entra ID 中管理身份

- 实验 \#2 - 使用 Microsoft Entra Connect 同步标识

- 实验 \#5 - 管理设备注册到 Microsoft Intune

- 实验 \#6 - 将设备注册到 Microsoft Intune

- 实验 \#7 - 创建和部署配置文件

**注意：**您还需要一部可以接收短信的移动电话，该短信用于保护 Windows
Hello 登录身份验证对 Microsoft Entra ID 的安全。

**场景**

您需要查看 Cindy White
登录活动以及审核日志提供的一般信息。您还需要验证硬件
在 [*SEA-WS1*](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10) 上，
并确认分配给此设备的配置文件已成功应用。

**任务 1：监视用户活动**

1.  切换到
    *[SEA-SVR1](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)*
    并在需要时使用提供的凭据登录。

2.  在 **Microsoft Entra 管理中心**页面上，导航并选择
    “**Users**”，然后单击 “**All users**”。

> ![](./media/image1.png)

3.  在 **Users** （用户） 页面中，导航并选择 **Allan Deyoung**。

> ![](./media/image2.png)

4.  在 **Allan Deyoung** User 页面中，导航并单击 **Sign-in logs**。

> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)

5.  在 **Allan Deyoung | Sign-in logs** 页面中，单击 **User sign-ins
    （interactive）** （用户登录（交互式）） 选项卡下的第一个条目。

> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

6.  选择每个主页，包括 **Basic
    info**（基本信息）、**Location**（位置）、**Device
    info**（设备信息）、**Authentication Details**（身份验证详细信息）和
    **Conditional
    Access**（条件访问）。向下滚动并检查每个页面上的信息。仔细查看每个页面中提供的信息后，关闭该窗格。

> ![](./media/image5.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image6.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image7.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image9.png)

7.  在 Users （用户） 导航窗格中，选择 **Audit logs** （审核日志）。

8.  在详细信息窗格中，将显示有关用户管理更改的审核信息。通过选择各种条目来检查信息。

> ![A screenshot of a computer Description automatically
> generated](./media/image10.png)
>
> ![](./media/image11.png)

**任务 2：监控设备活动**

1.  切换到 **Microsoft Intune 管理中心**窗口，导航并单击“**Devices**”。

![](./media/image12.png)

2.  在 Devices （设备） 导航窗格中，选择 **Overview** （概述）。

> ![A screenshot of a computer Description automatically
> generated](./media/image13.png)

3.  向下滚动并查看以下内容：

- 配置策略分配失败

- 不合规的设备。

- 每个 Windows 更新通道的部署状态。

> ![](./media/image14.png)

4.  向下滚动到 **Manage devices** 部分，然后单击
    **Configuration**。查看配置详细信息。

> ![](./media/image15.png)

5.  向上滚动并选择 **All devices**（所有设备）。在 “**Devices | All
    devices** ”
    页面中，将显示有关设备的信息，例如设备名称、管理者、所有权、合规性、作系统和作系统版本。点击
    **SEA-WS1**。

> ![](./media/image16.png)

6.  在 SEA-WS1 导航窗格中，选择 “**Hardware**” 并检查硬件清单。

> ![A screenshot of a computer Description automatically
> generated](./media/image17.png)

7.  在 SEA-WS1 导航窗格中，选择 **Discovered apps** （发现的应用程序）
    并检查应用程序清单。

> ![A screenshot of a computer Description automatically
> generated](./media/image18.png)

8.  在 SEA-WS1 导航窗格中，选择 **Device configuration**
    并在详细信息窗格中记下分配给设备的 设备配置文件。**State** 列应显示
    **Succeeded**，这意味着配置文件已成功应用于设备。

> ![](./media/image19.png)

9.  在 **SEA-WS1 | Device configuration** 页面，单击 **Contoso Developer
    – standard**。

> ![](./media/image20.png)

10. 在 “**Contoso Developer – standard**”
    边栏选项卡上，记下在配置文件中配置的每个设置。

> **State** 应在所有旁边显示 **Succeeded**。
>
> ![](./media/image21.png)

**结果：**完成本练习后，您将成功监控用户登录活动、审核日志和设备活动。
