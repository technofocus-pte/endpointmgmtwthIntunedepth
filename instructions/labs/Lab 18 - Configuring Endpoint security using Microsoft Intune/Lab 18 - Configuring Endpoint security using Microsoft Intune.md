Laboratorio 18 - Configurar Endpoint security mediante Microsoft Intune

**Resumen**

En este laboratorio, creará una política para configurar Microsoft
Defender para managed devices en Microsoft Intune.

**Prerrequisitos**

Debe completar los siguientes laboratorios antes de este laboratorio:

- Laboratorio \#5-Gestione Device Enrollment en Microsoft Intune

- Laboratorio \#6-Inscripción de dispositivos en Microsoft Intune

- Laboratorio \#7-Crear e implementar Configuration Profiles

**Escenario**

Se le han pedido que asegure que el Contoso Developers Group ha
configurado correctamente el Microsoft Defender. Le han pedido:

- Prevención de tamper protection.

- Esconder el Account protection, App y browser control, Device
  security, Device performance and health, y áreas Family options en el
  Windows Security app

- Se debe añadir company name y phone number.

- También se tiene que configura real-time protection, Remediation, y
  scan settings.

Se verificarán las configuraciones probándolo en un dispositivo
inscrito, SEA-WS1 y un dispositivo no inscrito non-enrolled, SEA-CL1.

Tarea 1: Configure el Windows Security Experience en Intune

1.  Cambie e inicie sesión
    en [***SEA-SVR1***](urn:gd:lg:a:select-vm) como !!**[Contoso\Administrator](urn:gd:lg:a:send-vm-keys)!!** con
    la contraseña !!**[Pa55w.rd](urn:gd:lg:a:send-vm-keys)!!**

2.  En el taskbar, seleccione **Microsoft Edge**.

3.  En Microsoft Edge, tecle !!**https://Intune.microsoft.com!!** en la
    barra de direcciones, y presione **Enter**.

4.  Inicie sesión como Office 365 Tenant Admin.

> ![A screenshot of a computer Description automatically
> generated](./media/image1.png)

5.  Desde el panel de navegación, seleccione **Endpoint security**, y
    seleccione **Antivirus**.

> ![](./media/image2.png)

6.  En el panel de **Endpoint security |Antivirus**, seleccione **+
    Create Policy**.

> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)

7.  En el panel **Create a profile**, para **Platform**,
    seleccione **Windows 10, Windows 11, and Windows Server**.

8.  En la lista **Profile**, seleccione **Windows Security experience**.
    Y seleccione **Create**.

> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

9.  En la pestaña Basics, en el campo **Name**, introduzca !!**[Windows
    Security Settings](urn:gd:lg:a:send-vm-keys)!!**.
    Seleccione **Next**.

> ![A screenshot of a computer Description automatically
> generated](./media/image5.png)

10. En **Defender**, configure lo siguiente:

    - TamperProtection (Device): **On**

> ![A screenshot of a computer Description automatically
> generated](./media/image6.png)

11. En **Windows Defender Security Center**, configure lo siguiente:

    - Disable Account Protection UI: **Enable**

    - Disable App Browser UI: **Enable**

    - Disable Device Security UI: **Enable**

    - Disable Family UI: **Enable**

    - Disable Health UI: **Enable**

> ![A screenshot of a computer Description automatically
> generated](./media/image7.png)

12. Junto a **Enable Customized Toasts** seleccione **Enable**.

13. En el campo **Company name**, seleccione **Configured**, e
    introduzca !!**[Contoso IT](urn:gd:lg:a:send-vm-keys)!!**

14. Para **Phone**, seleccione **Configured** e
    introduzca !!**[555-1234](urn:gd:lg:a:send-vm-keys)!!** Y
    seleccione **Next**.

> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)

15. En la página **Scope tags**, seleccione **Next**.

> ![A screenshot of a computer Description automatically
> generated](./media/image9.png)

16. En la pestaña **Assignments**, en **Included
    groups** seleccione **Add groups**. Elija el **Contoso Developer
    Devices** group, haga clic en **Select** y seleccione **Next**.

> ![A screenshot of a computer Description automatically
> generated](./media/image10.png)

17. En la pestaña **Review + create**, revise la información y
    seleccione **Save**.

> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)

Tarea 2: Configure la política Microsoft Defender Antivirus en Intune

1.  En el panel **Endpoint security |Antivirus**, seleccione **Create
    Policy**.

> ![A screenshot of a computer Description automatically
> generated](./media/image12.png)

2.  En el panel **Create a profile**, para **Platform**,
    seleccione **Windows 10, Windows 11, and Windows Server**.

3.  En la lista **Profile**, seleccione **Microsoft Defender
    Antivirus**, y luego seleccione **Create**.

> ![A screenshot of a computer Description automatically
> generated](./media/image13.png)

4.  En la pestaña **Basics**, en el campo **Name**,
    introduzca !!**[Microsoft Defender Antivirus
    Settings](urn:gd:lg:a:send-vm-keys)!!**. Seleccione **Next**.

> ![A screenshot of a computer Description automatically
> generated](./media/image14.png)

5.  En la pestaña **Configuration settings**, configure lo siguiente:

    - Allow Intrusion Prevention System: **Allowed**

    - Allow scanning of all downloaded files and
      attachments: **Allowed**

    - Allow Realtime Monitoring: **Allowed**

> ![](./media/image15.png)

- Check For Signatures Before Running Scan: **Enabled**

- Days to Retain Cleaned Malware: !!**[60](urn:gd:lg:a:send-vm-keys)!!**

> ![A screenshot of a computer Description automatically
> generated](./media/image16.png)

- Schedule Quick Scan
  Time: !!**[60](urn:gd:lg:a:send-vm-keys)!!** (represents 1:00AM)

> ![A screenshot of a computer Description automatically
> generated](./media/image17.png)

- Submit samples consent: **Send safe samples automatically**

> ![A screenshot of a computer Description automatically
> generated](./media/image18.png)

6.  En la pestaña **Configuration settings**, seleccione **Next**.

7.  En la página **Scope tags**, seleccione **Next**.

> ![A screenshot of a computer Description automatically
> generated](./media/image19.png)

8.  En la pestaña **Assignments**, en **Included
    groups** seleccione **Add groups**.

9.  Elija **Contoso Developer Devices** group y elija **Select** y luego
    seleccione **Next**.

> ![A screenshot of a computer Description automatically
> generated](./media/image20.png)

10. En la pestaña **Review + create**, revise la información y
    seleccione **Save**.

> ![A screenshot of a computer Description automatically
> generated](./media/image21.png)

Tarea 3: Sincronice los managed devices

1.  En el **Microsoft Intune admin center**, seleccione **Devices** y
    luego seleccione **All devices**.

2.  En el panel **Devices | All devices**, seleccione **SEA-WS1** y en
    el **SEA-WS1** blade, seleccione **Sync** en el toolbar, y luego
    seleccione **Yes**.

> ![](./media/image22.png)
>
> Espere unos minutos a que se complete la sincronización.

3.  Cierre Microsoft Edge.

Tarea 4: Verifique la configuración

1.  Cambie a [***SEA-CL1***](urn:gd:lg:a:select-vm). Si es necesario,
    inicie sesión
    en !!**[Contoso\Administrator](urn:gd:lg:a:send-vm-keys)!!** con la
    contraseña !!**[Pa55w.rd](urn:gd:lg:a:send-vm-keys)!!**.

2.  En [***SEA-CL1***](urn:gd:lg:a:select-vm), seleccione **Start**,
    tecle !!**[Windows Security](urn:gd:lg:a:send-vm-keys)!!**, y en el
    ícono Windows Security seleccione **Open**.

> ![](./media/image23.png)
>
> Note que se ven todas las opciones de seguridad. Esto porque SEA-CL1
> no está inscrito en Intune.
>
> ![A screenshot of a computer security system Description automatically
> generated](./media/image24.png)

3.  Cierre **Windows Security** y cierre sesión
    de [***SEA-CL1***](urn:gd:lg:a:select-vm).

4.  Cambie a [***SEA-WS1***](urn:gd:lg:a:select-vm), e inicie sesión
    como **!!Cindy@M365x27131290.onmicrosoft.com!!** Con la contraseña
    **!!P@55w.rd12345!!** .

5.  Seleccione **Start**, tecle !!**[Windows
    Security](urn:gd:lg:a:send-vm-keys)!!**, y luego en el ícono Windows
    Security seleccione **Open**.

> ![](./media/image25.png)
>
> Note que no se muestran todas las áreas restringidas configuradas en
> Intune policy. [***SEA-WS1***](urn:gd:lg:a:select-vm) está inscrito en
> Intune, lo que aplicó los security settings.
>
> ![A screenshot of a computer Description automatically
> generated](./media/image26.png)

6.  Cierre **Windows Security** y cierre sesión
    de [***SEA-WS1***](urn:gd:lg:a:select-vm).

**Resultados**: Después de completar este ejercicio, habrá creado y
aplicado una política para configurar Microsoft Defender para
dispositivos gestionados en Intune.
