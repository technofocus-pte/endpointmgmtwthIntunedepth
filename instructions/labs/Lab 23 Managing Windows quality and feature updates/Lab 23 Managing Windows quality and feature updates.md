Laboratorio 23: Gestionar las actualizaciones Windows de quality y
feature

**Resumen**

En este laboratorio, configurará las configuraciones de las
actualizaciones Windows quality y feature mediante Intune.

**Prerrequisitos**

Se deben completar los siguientes laboratorios antes de este
laboratorio:

- Laboratorio 01-Gestione Device Enrollment en Intune

- Laboratorio 06-Inscripción de dispositivos en Intune

- Laboratorio 07-Crear e implementar Configuration Profiles

**Ojo**: También necesitará un celular que puede recibir textos de
mensajes para asegurar la autenticación del inicio de sesión Windows
Hello a Azure AD.

**Escenario**

Se le ha pedido conifgurar un update ring para solo afectar los
dispositivos que son miembros del Contoso Developer Devices group. Este
grupo debe cumplir los siguientes requisitos:

- Quality update deferral period (days): **15**

- Feature update deferral period (days): **45**

- Option to pause Windows updates: **Disable**

- Option to check for Windows updates: **Enable**

- Delivery optimization: Download Mode: **HTTP only, no peering (0)**

Tarea 1: Verifique los update settings actuales para un solo
dispositivos

1.  Cambie a [***SEA-WS1***](urn:gd:lg:a:select-vm), inicie sesión
    como **Cindy White** con el PIN [**102938**](urn:gd:lg:a:select-vm).

2.  Seleccione **Start**, y seleccione el ícono **Settings**.

> ![](./media/image1.png)

3.  En **Settings**, seleccione **Windows Update**.

> Note que tiene la opción de pausar actualizaciones para un período del
> tiempo específico.

4.  En la página **Windows Update**, seleccione **Advanced options**.

> ![](./media/image2.png)

5.  En la página **Advanced options** seleccione **Delivery
    Optimization**.

> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)

6.  En la página **Delivery Optimization**, verifique que está
    habilitado la opción **Allow downloads from other PCs**.

7.  Seleccione **Devices on the internet and my local network**.

> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

8.  En **Settings**, seleccione **Windows Update**.

> ![A screenshot of a computer Description automatically
> generated](./media/image5.png)

9.  Seleccione **Advanced options**, y luego seleccione **Configured
    update policies**.

> ![A screenshot of a computer Description automatically
> generated](./media/image6.png)
>
> Tome nota que no se ha establecido ningún update policy en el
> dispositivo.
>
> ![A screenshot of a computer Description automatically
> generated](./media/image7.png)

10. En el panel de navegación, seleccione **Windows Update**.

Tarea 2: Revise las configuraciones aplicadas

1.  En la página **Windows Update**, seleccione **Update history**.

> ![A screenshot of a computer update Description automatically
> generated](./media/image8.png)

2.  Revise las actualizaciones enlistadas, y seleccione **Uninstall
    updates**.

> ![A screenshot of a computer update Description automatically
> generated](./media/image9.png)

3.  Revise las actualizaciones enlistadas en **Installed Updates**.
    Cierre Installed Updates.

> ![A screenshot of a computer Description automatically
> generated](./media/image10.png)

4.  Cierre la aplicación **Settings**.

Tarea 3: Configure update settings con Intune

1.  Cambie a [***SEA-SVR1***](urn:gd:lg:a:send-vm-keys) e inicie sesión
    como [**Contoso\Administrator**](urn:gd:lg:a:send-vm-keys) con la
    contraseña [**Pa55w.rd**](urn:gd:lg:a:send-vm-keys).

2.  En el taskbar, seleccione **Microsoft Edge**.

3.  En Microsoft Edge,
    tecle [**https://intune.microsoft.com**](urn:gd:lg:a:send-vm-keys) en
    el address bar, y presione **Enter**.

4.  Inicie sesión
    como [**admin@M365x19242953.onmicrosoft.com**](urn:gd:lg:a:send-vm-keys) con
    la contraseña.

5.  En el panel de navegación, seleccione **Devices** y luego seleccione
    **Windows 10 and later Updates**.

> ![](./media/image11.png)

6.  En el **Devices | Update rings for Windows 10 and later** blade
    seleccione **Create profile**.

> ![](./media/image12.png)

7.  En el **Basics** blade, introduzca la siguiente información, y
    seleccione **Next**:

    - Name: !\![**Contoso Updates -
      standard**](urn:gd:lg:a:send-vm-keys)!!

    - Description: !\![**Standard Windows updates
      configuration**](urn:gd:lg:a:select-vm)!!

> ![](./media/image13.png)

8.  En el **Update ring settings** blade, introduzca la siguiente
    información, y seleccione **Next**:

    - Quality update deferral period
      (days): [**15**](urn:gd:lg:a:send-vm-keys)

    - Feature update deferral period
      (days): [**45**](urn:gd:lg:a:send-vm-keys)

    - Option to pause Windows updates: **Disable**

    - Option to check for Windows updates: **Enable**

> ![](./media/image14.png)

9.  En el **Assignments** blade, en **Included groups** seleccione **Add
    groups**.

10. En el **Select groups to include** blade, en el cuadro
    de **Search**, seleccione **Contoso Developer devices** y luego
    seleccione **Select**.

> ![A screenshot of a computer Description automatically
> generated](./media/image15.png)
>
> ![](./media/image16.png)

11. Seleccione **Next** y en **Review + create** blade
    seleccione **Create**.

12. Desde la barra de navegación, seleccione **Configuration profiles**.

13. En el **Devices | Configuration** blade, en el panel de detalles,
    seleccione **Create policy**.

> ![](./media/image17.png)

14. En el **Create a profile** blade, seleccione las siguientes
    opciones, y luego seleccione **Create**:

    - Platform: **Windows 10 and later**

    - Profile type: **Templates**

    - Template name: **Delivery Optimization**

> ![](./media/image18.png)

15. En el **Basics** blade, introduzca la siguiente información, y luego
    seleccione **Next**:

    - Name: !\![**Contoso Developer - Delivery
      optimization**](urn:gd:lg:a:send-vm-keys)!!

    - Description: !\![**Delivery optimization for
      Developer**](urn:gd:lg:a:send-vm-keys)!!

> ![](./media/image19.png)

16. En el **Configuration settings** blade, introduzca la siguiente
    información, y luego seleccione **Next**:

    - Download Mode: **HTTP only, no peering (0)**

> ![A screenshot of a computer Description automatically
> generated](./media/image20.png)

17. En el **Assignments** blade, en **Included groups** seleccione **Add
    groups**.

18. En el **Select groups to include** blade, seleccione **Contoso
    Developer devices** y luego seleccione **Select**.

> ![A screenshot of a computer Description automatically
> generated](./media/image21.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image22.png)

19. Seleccione **Next** dos veces, y en el **Review + create** blade
    seleccione **Create**.

> ![Screenshot](./media/image23.png)

Tarea 4: Verifique que el update settings del dispositivo se gestionan
centralmente

1.  Cambie a [***SEA-WS1***](https://intune.microsoft.com).

2.  Seleccione **Start**, y luego seleccione el ícono **Settings**.

> ![](./media/image24.png)

3.  En la aplicación **Settings**, seleccione **Accounts** y luego
    seleccione **Access work or school**.

> ![A screenshot of a computer Description automatically
> generated](./media/image25.png)

4.  En la sección **Access work or school**, seleccione el
    enlace **Connected to Contoso's Azure AD** y luego
    seleccione **Info**.

> ![A screenshot of a computer Description automatically
> generated](./media/image26.png)

5.  En el cuadro de diálogo **Areas Managed by Contoso**,
    seleccione **Sync**. Espere a que se complete la sincronización.

> ![A screenshot of a computer Description automatically
> generated](./media/image27.png)

6.  En la aplicación **Settings**, seleccione **Windows Update**.

> Note que no puede pausar actualizaciones.

7.  Seleccione **Advanced options**.

> ![](./media/image28.png)

8.  Seleccione **Delivery Optimization**.

> ![A screenshot of a computer Description automatically
> generated](./media/image29.png)
>
> Note que no está disponible **Allow downloads from other PCs**.

9.  En la aplicación **Settings**, seleccione **Windows Update**,
    seleccione **Advanced options**, y luego seleccione **Configured
    update policies**.

> ![](./media/image30.png)
>
> Tome nota de todas las políticas establecidas en el dispositivo.

10. Cierre todas las aplicaciones y ventanas abiertas.

> **Ojo**: Se configura el entorno del laboratorio para prevenir que se
> aplique Windows Updates para evitar retrasos e impactos no
> intencionados durante la ejecución del laboratorio.
