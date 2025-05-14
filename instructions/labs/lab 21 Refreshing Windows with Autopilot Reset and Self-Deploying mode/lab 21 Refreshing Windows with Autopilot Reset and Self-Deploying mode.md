Laboratorio 21: Actualizar Windows con Autopilot Reset y Self-Deploying
mode.

**Resumen**

En este laboratorio, aprenderá cómo realizar un Autopilot reset.

**Prerrequisitos**

Se debe completar los siguientes laboratorios antes de este laboratorio:

- Laboratorio 01-Gestionar Identities en Microsoft Entra ID

- Laboratorio 02-Sincronizar Identities mediante Azure AD Connect

- Laboratorio 21-Implementar Windows 11 mediante Microsoft Deployment
  Toolkit

- Laboratorio 20-Implementar Windows 11 mediante Autopilot

**Escenario**

Se ha implementado SEA-WS4 mediante Windows Autopilot. Necesita probar
otro escenario de aprovisionamiento que involucra a Autopilot Reset.
Creará un nuevo deployment profile configurado con el Windows Autopilot
Self-Deploying mode.

Tarea 1: Configure un Self-Deploying Windows Autopilot deployment
profile

1.  Cambie a [***SEA-SVR1***](urn:gd:lg:a:select-vm).

> ![](./media/image1.png)

2.  En **Microsoft Edge**, abra una nueva pestaña y navegue
    a [**https://intune.microsoft.com**](https://intune.microsoft.com).
    Si le pide, inicie sesión
    con [**admin@M365xXXXXXXXX.onmicrosoft.com**](mailto:admin@M365xXXXXXXXX.onmicrosoft.com) y
    contraseña.

3.  En el **Microsoft Intune admin center**, seleccione **Devices**.

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)

4.  En la sección **Device onboarding**, seleccione **Enrollment**.

> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)

5.  En el Windows enrollment blade, en el panel de detalles,
    seleccione **Deployment Profiles**.

> ![](./media/image4.png)

6.  En el **Windows AutoPilot deployment profiles** blade,
    seleccione **Contoso Profile 1** y seleccione **Properties**.

> ![](./media/image5.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image6.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image7.png)

7.  Baje a **Assignments** y seleccione **Edit**.

> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)

8.  Junto a **IT Devices**, seleccione **Remove**.

> ![](./media/image9.png)

9.  Seleccione **Review and save** y seleccione **Save**.

> ![A screenshot of a computer Description automatically
> generated](./media/image10.png)

10. Cierre la página **Contoso Profile 1|Properties**.

11. En el **Windows AutoPilot deployment profiles** blade,
    seleccione **Create profile** y luego seleccione **Windows PC**.

> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)

12. En la pestaña **Basics**, en el cuadro de texto **Name**,
    tecle [**Contoso profile 2**](urn:gd:lg:a:send-vm-keys).

13. Para **Convert all targeted devices to
    Autopilot** seleccione **No**, y luego seleccione **Next**.

> ![](./media/image12.png)

14. En la pestaña **Out-of-box experience (OOBE)**, asegure que
    **Deployment mode** está en **Self-Deploying**.

> ![](./media/image13.png)

15. Asegure que se establece las siguientes opciones:

    - Language (Region): **Operating system default**

    - Automatically configure keyboard: **Yes**

    - Apply device name template: **Yes**

    - Enter a name: [**Contoso-%RAND:2%**](urn:gd:lg:a:send-vm-keys)

> ![A screenshot of a computer Description automatically
> generated](./media/image14.png)

16. Seleccione **Next**.

17. En la pestaña **Assignments**, en **Included
    groups** seleccione **Add groups**.

> ![A screenshot of a computer Description automatically
> generated](./media/image15.png)

18. Seleccione el **IT Devices** group y haga clic en **Select**.
    Seleccione **Next**.

> ![](./media/image16.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image17.png)

19. En el **Review + create** blade, revise la información y
    seleccione **Create**.

> ![A screenshot of a computer Description automatically
> generated](./media/image18.png)

Tarea 2: Realice un Autopilot reset

1.  En el **Microsoft Intune admin center**, seleccione **Devices** y
    luego seleccione **All devices**.

2.  Seleccione el Autopilot PC (comienza con el nombre DESKTOP).

> ![A screenshot of a computer Description automatically
> generated](./media/image19.png)

3.  En el menu bar, seleccione los tres puntos y seleccione **Autopilot
    Reset**.

> ![A screenshot of a computer Description automatically
> generated](./media/image20.png)

4.  En el message prompt, seleccione **Yes**.

> ![A screenshot of a computer Description automatically
> generated](./media/image21.png)

5.  Cambie a [***SEA-SVR2***](urn:gd:lg:a:select-vm) y maximice la
    ventana **SEA-WS4**.

> **Ojo**: Se debe seguir ejecutando SEA-WS4 desde el laboratorio
> anterior.
>
> **Ojo**: Actualice el dispositivo a la versión más reciente y haga
> clic en restart.

6.  Reinicie **SEA-WS4**.

> ![A screenshot of a computer Description automatically
> generated](./media/image22.png)
>
> **Ojo**: Este proceso puede llevar 30 minutos y reiniciará varias
> veces durante este proceso. Su instructor puede continuar con el
> siguiente módulo mientras se completa esta tarea. Asegúrese de volver
> a completar Tarea 3 durante su próxima sesión del laboratorio.

Tarea 3: Verifique el Autopilot deployment

1.  En la página de inicio de sesión,
    introduzca [**Cindy@M365x19242953.onmicrosoft.com**](mailto:Cindy@M365x19242953.onmicrosoft.com) con
    la contraseña  [**P@55w.rd1234**](mailto:P@55w.rd1234).

2.  En el **Use Windows Hello with your account**, seleccione **OK**.

> ![A screenshot of a computer Description automatically
> generated](./media/image23.png)

3.  En la página **Verify your identity**, seleccione el Text
    verification method.

4.  En la página **Enter code**, introduzca el código que le mandaron a
    través de texto a su celular y seleccione **Verify**.

> ![A screenshot of a computer Description automatically
> generated](./media/image24.png)

5.  En el cuadro de diálogo **Setup up a PIN**, en los campos **New
    PIN** y **Confirm PIN**,
    introduzca [**102938**](urn:gd:lg:a:send-vm-keys), y
    seleccione **OK**.

> ![](./media/image25.png)

6.  En la página **All set!**, seleccione **OK**.

7.  Seleccione **Start** y seleccione **Settings**.

> ![](./media/image26.png)

8.  Seleccione **Accounts**, y luego seleccione **Access work or
    school**. Verifique que se conecta el dispositivo a Azure AD de
    Contoso.

> ![](./media/image27.png)

9.  Seleccione **Connected to Contoso's Azure AD** y
    seleccione **Info**.

> ![](./media/image28.png)

10. En la página **Managed by Contoso**, baje y seleccione **Sync**.

> ![](./media/image29.png)

11. En **SEA-WS4**, cierre la ventana **Settings**.

12. Apague **SEA-WS4** y cierre la ventana **SEA-WS4**.

13. En [***SEA-SVR2***](urn:gd:lg:a:select-vm), cierre Hyper-V Manager.

**Resultados**: Después de completar el ejercicio, habrá aprovisionado
un dispositivo Windows 11 con Autopilot Reset mediante Self-Deploying
mode.
