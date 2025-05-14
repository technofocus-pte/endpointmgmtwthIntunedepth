**Laboratorio 9 – Usar un Configuring Profile para configurar configure
iOS y iPadOS Wi-Fi settings.**

**Resumen**

En este laboratorio, usaremos Microsoft Intune para crear y aplicar un
Configuration profile para ejecutar configure Wi-Fi settings para los
dispositivos iOS y iPadOS.

**Ejercicio 1: Crear un Configuration profile.**

**Escenario**

Se le pide crear un Configuration profile para su uso en la
configuración automática de Wi-Fi settings para dispositivos inscritos
de iOS y iPadOS. Tiene que asegurar que se configuran los Wi-Fi settings
como mencionado a continuación:

- Network name: **Contoso Wi-Fi**

- SSID: **MainOffice**

- Connect automatically: **Enable**

- Security type: **WPA/WPA2-Personal**

- Pre-Shared key: **ContosoWiFi123**

- Assigned to: **A new security group named iOS_iPadOS Devices**

**Tarea 1: Cree el iOS_iPadOS device group**

1.  Cambie
    a *[SEA-SVR1](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10).* En
    la ventana **Microsoft Entra admin center**, navegue y seleccione
    **Groups**, y haga clic en **All groups**.

> ![A screenshot of a computer Description automatically
> generated](./media/image1.png)

2.  En el **Groups | All groups** blade, seleccione **New group**.

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)

3.  En el **New Group** blade, introduzca la siguiente información y
    haga clic en **Create** button como se ve en la imagen:

    - Group type: **Security**

    - Group name: !!**iOS_iPadOS Devices**!!

    - Group description: !!**All iOS and iPadOS devices**!!

    - Membership type: **Assigned**

> ![A screenshot of a group Description automatically
> generated](./media/image3.png)

4.  En el **Groups | All groups** blade, actualice la página y verifique
    si se ve el **iOS_iPadOS Devices** group.

> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

**Tarea 2: Cree un Configuration profile en función de los requisitos
del escenario**

1.  Cambie a la pestaña **Microsoft Intune admin center**,
    seleccione **Devices** desde la barra de navegación.

> ![A screenshot of a computer Description automatically
> generated](./media/image5.png)

2.  En la página **Devices | Overview**, seleccione **iOS/iPadOS** como
    se ve en la imagen.

> ![A screenshot of a computer Description automatically
> generated](./media/image6.png)

3.  En la página **iOS/iPadOS**, navegue y haga clic en **Configuration
    profiles**.

4.  En la página **iOS/iPadOS | Configuration profiles**, en la pestaña
    **Policies**, haga clic en **+ Create** y seleccione **+ New
    Policy**.

> ![](./media/image7.png)

5.  En el **Create a profile** blade, seleccione las siguientes
    opciones, y luego seleccione **Create**:

    - Platform: **iOS/iPadOS**

    - Profile type: **Templates**

    - Template name: **Wi-Fi**

> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)

6.  En el **Basics** blade, introduzca la siguiente información, y
    seleccione **Next**:

    - Name: !!**iOS/iPadOS Wi-Fi Policy**!!

    - Description: !!**Wi-Fi settings for iOS/iPadOS Devices**!!

> ![A screenshot of a computer Description automatically
> generated](./media/image9.png)

7.  En el **Configuration settings** blade, junto a **Wi-Fi type**,
    seleccione **Basic**.

> Se ven opciones adicionales en función del type seleccionado.

8.  En el **Configuration settings** blade, seleccione las siguientes
    opciones, y luego seleccione **Next**:

    - Network name: !!**Contoso Wi-Fi**!!

    - SSID: !! **MainOffice**!!

    - Connect automatically: **Enable**

    - Security type: **WPA/WPA2-Personal**

    - Pre-Shared key: !!**ContosoWiFi123**!!

> ![A screenshot of a computer Description automatically
> generated](./media/image10.png)

9.  En el **Assignments** blade, en **Included groups**,
    seleccione **Add groups**.

> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)

10. En la ventana **Select groups to include**, seleccione **iOS_iPadOS
    Devices**, y luego seleccione **Select**.

> ![](./media/image12.png)

11. En la pestaña **Assignments**, haga clic en el botón **Next**.

> ![A screenshot of a computer Description automatically
> generated](./media/image13.png)

12. En la pestaña **Review + create**, haga clic en el botón **Create**.

> ![A screenshot of a computer Description automatically
> generated](./media/image14.png)

13. Verifique que se enlista el **iOS/iPadOS Wi-Fi Policy**.

> ![A screenshot of a computer Description automatically
> generated](./media/image15.png)
>
> **Resultados**: Después de completar este ejercicio, habrá configurado
> y creado un Configuration profile exitosamente para configurar Wi-Fi
> settings para los dispositivos iOS y iPadOS.
