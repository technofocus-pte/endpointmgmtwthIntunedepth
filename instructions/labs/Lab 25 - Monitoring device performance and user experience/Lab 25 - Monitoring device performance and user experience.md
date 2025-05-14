# 实验 25：使用 Endpoint Analytics 监控设备性能和用户体验

**总结**

在此实验室中，您将启用 Endpoint analytics
来监控设备性能以及用户体验分数和见解。

**先决条件**

在此实验之前，必须完成以下实验：

- 实验 05 - 管理设备注册到 Intune

- 实验 06 - 将设备注册到 Intune

- 实验 07 - 创建和部署配置文件

**场景**

系统要求您监控启动性能、应用程序可靠性和用户体验，以及用户重启设备的频率。要获取此信息，您需要启用
Endpoint analytics。

### 任务 1：启用 Endpoint 分析

1.  在 [**SEA-SVR1**](urn:gd:lg:a:select-vm)上，如有必要，使用密码以 [**Contoso\Administrator**](urn:gd:lg:a:send-vm-keys) 身份登录 !\![**Pa55w.rd**](urn:gd:lg:a:send-vm-keys)!! 并关闭
    **Server Manager**。

2.  在任务栏上，选择 **Microsoft Edge**。

3.  在 Microsoft Edge 中，键入
    !\![**https://intune.microsoft.com**](https://intune.microsoft.com)!!，然后按
    **Enter**。

4.  使用密码以 [**admin@M365x19242953.onmicrosoft.com**](urn:gd:lg:a:send-vm-keys) 身份登录。

5.  在 **Microsoft Intune 管理中心**页面上，选择 “**Reports**” 。

6.  在 “**Reports**” 边栏选项卡上的 “**Analytics**” 下，选择 “**Endpoint
    analytics**”。

> ![](./media/image1.png)

7.  在 **Endpoint analytics** （终端节点分析） 页面上，确保 **Collect
    device data from** （收集设备数据来源） 设置为 **All cloud-managed
    devices**（所有云托管设备），然后选择 **Start**（启动）。

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)
>
> 记下 Overview （概述） 页面顶部的消息。分数和见解最多可能需要 24
> 小时才能显示在页面上。
>
> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)

8.  切换到 [**SEA-WS1**](urn:gd:lg:a:select-vm) 并重新启动设备。

9.  以 **Cindy White** 身份登录，密码为
    ： [**102938**](urn:gd:lg:a:send-vm-keys)。

10. 切换到[**SEA-SVR1**](urn:gd:lg:a:select-vm)。

11. 在 **Microsoft Intune 管理中心**页面上，选择 “**Devices**”
    ，然后选择 “**All devices**” 。

12. 选择 **SEA-WS1**。

> ![](./media/image4.png)

13. 在 **SEA-WS1** 页面上，选择 **Sync** 同步，然后选择 **Yes**。

> ![A screenshot of a computer Description automatically
> generated](./media/image5.png)

14. 在 **SEA-WS1** 页面的 “**Monitor**” 下，选择 “**User experience**”
    。 ![A screenshot of a computer Description automatically
    generated](./media/image6.png)

15. 查看 **Endpoint analytics** （终端节点分析）、**Startup
    performance** （启动性能） 和 **Application reliability**
    （应用程序可靠性） 选项卡。

> ![A screenshot of a computer Description automatically
> generated](./media/image7.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image9.png)
>
> 由于时间延迟，可能不会报告任何信息，但请阅读每个选项卡上可见内容的详细信息。

16. 在 **Microsoft Intune 管理中心**页面上，选择 “**Reports**” 。

17. 在 “**Reports**” 边栏选项卡上的 “**Analytics**” 下，选择 “**Endpoint
    analytics**” 。

> ![](./media/image10.png)
>
> 请注意，Endpoint Analytics
> 中提供了相同类型的信息，但此信息基于所有已注册的设备。
>
> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)

18. 浏览 Endpoint analytics （终端节点分析） 页面中提供的 Reports
    （报告）。

19. 关闭 Microsoft Edge。

**结果：**完成本练习后，您将成功启用 Endpoint Analytics
来监控设备性能以及用户体验分数和见解。
