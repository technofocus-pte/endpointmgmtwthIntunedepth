**Laboratorio 8 – Usar un Configuring Profile para configurar el Kiosk
mode**

**Resumen**

En este laboratorio, usaremos Microsoft Intune para crear y aplicar un
Configuration profile para ejecutar single-app Kiosk mode en un
dispositivo Windows 11.

**Prerrequisitos**

Se debe completar los siguientes laboratorios antes de este laboratorio:

- Laboratorio 05 - Gestionar Device Enrollment en Microsoft Intune

Ojo: también necesita un celular que puede recibir textos para asegurar
la autenticación del inicio de sesión Windows Hello a Entra ID.

**Ejercicio 1: Cree y aplique un Configuration profile**

**Escenario**

Se le ha pedido que configure **SEA-WS2** como un Windows 11 kiosk para
que los visitantes de Contoso puedan navegar el Internet. Tiene que
asegurar que el kiosk se configura de la siguiente manera:

- Una sola aplicación, full-screen kiosk.

- Logon automático.

- Proporciona acceso al navegador Microsoft Edge, lo que se configura en
  Public Browsing (InPrivate) mode. Se debe configurar la página de
  inicio para **http://bing.com**.

**Tarea 1: Inscriba SEA-WS2 a Microsoft Intune**

1.  Inicie sesión
    en [*SEA-WS2*](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10) como **Admin** con
    la contraseña de !!**Pa55w.rd**!!.

2.  En el taskbar, seleccione **Start** y luego seleccione **Settings**.

![](./media/image1.png)

3.  En la ventana **Settings**, seleccione **Accounts**.

![A screenshot of a computer Description automatically
generated](./media/image2.png)

4.  En la página Accounts, seleccione **Access work or school**.

![A screenshot of a computer Description automatically
generated](./media/image3.png)

5.  En la página **Access work or school**, seleccione **Connect**.

![A screenshot of a computer Description automatically
generated](./media/image4.png)

6.  En la ventana **Microsoft account**, seleccione **Join this device
    to Microsoft Entra ID**.

![A screenshot of a computer screen Description automatically
generated](./media/image5.png)

7.  En la página **Sign in**,
    tecle !!**AllanD@M365xXXXXXX.onmicrosoft.com**!! Y luego
    seleccione **Next**.

![](./media/image6.png)

8.  En la página **Enter password**, introduzca el tenant password:
    !!**P@55w.rd1234**!! Y seleccione **Sign in**.

![A screenshot of a computer Description automatically
generated](./media/image7.png)

9.  En el cuadro de diálogo **Make sure this is your organization**,
    seleccione **Join**.

![A screenshot of a computer error Description automatically
generated](./media/image8.png)

10. En la página **You're all set!**, lea toda la información y
    seleccione **Done**.

![A screenshot of a computer screen Description automatically
generated](./media/image9.png)

11. En la sección **Access work or school**, verifique que se
    ve **Connected to Contoso's Azure AD**.

![A screenshot of a computer Description automatically
generated](./media/image10.png)

12. Seleccione **Connected to Contoso's Azure AD** y luego
    seleccione **Info**.

![A screenshot of a computer Description automatically
generated](./media/image11.png)

13. Baje y seleccione **Sync**. Esto obligará un Device sync con Intune.

![A screenshot of a computer Description automatically
generated](./media/image12.png)

14. Cierre la ventana **Settings**.

**Tarea 2: Cree el Contoso Kiosk device group**

1.  En [*SEA-SVR1*](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10),
    cambie a la pestaña **Microsoft Entra admin center**. Navegue y
    seleccione **Groups,** y haga clic en **All groups**.

![](./media/image13.png)

2.  En la página **Groups | All groups**, seleccione **New group**.

![A screenshot of a computer Description automatically
generated](./media/image14.png)

3.  En la **New Group** blade, introduzca los siguientes detalles:

- Group type: **Security**

- Group name: !!Contoso Kiosk Devices!!

- Group description: !!All Windows devices configured as a Kiosk!!

- Membership type: **Assigned**

4.  En **Members**, seleccione **No members selected**.

![](./media/image15.png)

5.  En el **Add members** blade, en el cuadro
    de **Search,** tecle **Sea**. Seleccione **SEA-WS2** y
    elija **Select**.

![](./media/image16.png)

6.  En el **New Group** blade, seleccione **Create**.

![A screenshot of a computer Description automatically
generated](./media/image17.png)

7.  En el **Groups | All groups** blade, actualice la página y verifique
    que se ve el **Contoso Kiosk Devices** group.

![](./media/image18.png)

**Tarea 3: Cree un Configuration profile en función de los requisitos
del escenario**

1.  Vuelva a Microsoft Intune admin center, seleccione **Devices** desde
    la barra de navegación.

![A screenshot of a computer Description automatically
generated](./media/image19.png)

2.  En la página **Devices | Overview**, seleccione **Windows** como se
    ve en la imagen.

![A screenshot of a computer Description automatically
generated](./media/image20.png)

3.  En la página **Windows | Windows devices**, navegue y haga clic en
    **Configuration profiles**.

![A screenshot of a computer Description automatically
generated](./media/image21.png)

4.  En la página **Windows | Configuration profiles**, en la pestaña
    **Policies**, haga clic en **+ Create** y seleccione **+ New
    Policy**.

![A screenshot of a computer Description automatically
generated](./media/image22.png)

5.  En el **Create a profile** blade, seleccione las siguientes
    opciones, y seleccione **Create**:

- Platform: **Windows 10 and later**

- Profile type: **Templates**

- Template name: !!**Kiosk**!!

![A screenshot of a computer Description automatically
generated](./media/image23.png)

6.  En el **Basics** blade, introduzca la siguiente información, y luego
    seleccione **Next**:

- Name: !!Contoso Kiosk Policy!!

- Description: !!Basic settings for Contoso Kiosk Devices.!!

![A screenshot of a computer Description automatically
generated](./media/image24.png)

7.  En el **Configuration settings** blade, junto a **Select a kiosk
    mode**, seleccione **Single app, full-screen kiosk**.

Se ve opciones adicionales en función del mode seleccionado.

8.  En el **Configuration settings** blade, seleccione las siguientes
    opciones y luego seleccione **Next**:

- User logon type: **Auto logon (Windows 10, version 1803 and later, or
  Windows 11)**

- Application type: **Add Microsoft Edge browser**

- Edge Kiosk URL: !! **http://bing.com**!!

- Microsoft Edge kiosk mode type: **Public Browsing (InPrivate)**

- Refresh browser after idle time: **5**

- Specify Maintenance Window for App Restarts: **Not configured**

> ![A screenshot of a computer Description automatically
> generated](./media/image25.png)

9.  En el **Assignments** blade, en **Included groups**,
    seleccione **Add groups**.

![A screenshot of a computer Description automatically
generated](./media/image26.png)

10. En la ventana **Select groups to include**, seleccione !!**Contoso
    Kiosk Devices**!!, y luego seleccione **Select**.

![A screenshot of a computer Description automatically
generated](./media/image27.png)

11. En la pestaña **Assignment**, haga clic en el botón **Next**.

![A screenshot of a computer Description automatically
generated](./media/image28.png)

12. En la pestaña **Applicability Rules**, haga clic en **Next**.

![A screenshot of a computer Description automatically
generated](./media/image29.png)

13. En la pestaña **Review + create**, haga clic en el botón **Create**.

![A screenshot of a computer Description automatically
generated](./media/image30.png)

14. Se enumera el Configuration profile.

![A screenshot of a computer Description automatically
generated](./media/image31.png)

**Tarea 4: Verifique que se aplica el Configuration profile**

1.  Inicie sesión
    en [*SEA-WS2*](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10) como **Admin** con
    la contraseña !!**Pa55w.rd**!!.

2.  En el taskbar, seleccione **Start** y seleccione **Settings**.

![A screenshot of a computer Description automatically
generated](./media/image1.png)

3.  En la ventana **Settings**, seleccione **Accounts**.

![A screenshot of a computer Description automatically
generated](./media/image2.png)

4.  En la página Accounts, seleccione **Access work or school**.

![A screenshot of a computer Description automatically
generated](./media/image3.png)

5.  Seleccione **Connected to Contoso's Azure AD** y luego
    seleccione **Info**.

![A screenshot of a computer Description automatically
generated](./media/image11.png)

6.  Baje y seleccione **Sync**. Esto obligará un Device sync con Intune.

![A screenshot of a computer Description automatically
generated](./media/image12.png)

7.  Cierre la ventana **Settings**.

> ![](./media/image32.png)

5.  Reinicie **SEA-WS2**.

Note que el **SEA-WS2** inicia sesión de forma automática y crea un
perfil. Después de que se complete el sign-in, se ve el Microsoft Edge
configurado con InPrivate browsing. Si SEA-WS2 no inicia sesión
automáticamente, repita los pasos 1-7 para asegurar que se actualiza la
política en el dispositivo.

![](./media/image33.png)

**Resultados**: después de completar el ejercicio, habrá creado y
asignado un Configuration profile exitosamente para configurar un
dispositivo Windows 11 como un single-app kiosk.
