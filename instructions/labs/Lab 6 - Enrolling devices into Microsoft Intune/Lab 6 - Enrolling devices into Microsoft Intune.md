**Laboratorio 6 – Inscripción de dispositivos en Microsoft Intune**

**Resumen**

En este laboratorio, se unirá un cliente Windows client a Entra ID y
verifique que el dispositivo se inscribe de forma automática en
Microsoft Intune.

**Prerrequisitos**

Se deben completar los siguientes laboratorios antes de este
laboratorio:

- Laboratorio \#1-Gestionar Identities en Microsoft Entra ID

- Laboratorio \#2-Sincronizar Identities mediante Microsoft Entra
  Connect

- Laboratorio \#5- Gestione Device Enrollment en Microsoft Intune

Ojo: Puede que necesite un celular que recibe mensajes de texto para
asegurar la autenticación de inicio de sesión Windows Hello a Entra ID.

**Escenario**

Ha asignado licencias apropriadas a Cindy White y ahora va a probar el
proceso de juntar un dispositivo Windows a Entra ID y hacerlo
inscribirse automáticamente en Microsoft Intune.

**Tarea 1: Inscriba un Windows device a Microsoft Intune
automáticamente**

1.  Cambie a
    [*SEA-WS1*](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10) e
    inicie sesión como **Admin** con la contraseña !!**Pa55w.rd**!!

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image1.png)

2.  En el taskbar, seleccione **Start** y seleccione **Settings**.

![A screenshot of a computer Description automatically
generated](./media/image2.png)

3.  En la ventana **Settings**, seleccione **Accounts**.

![A screenshot of a computer Description automatically
generated](./media/image3.png)

4.  En la página Accounts, seleccione **Access work or school**.

![A screenshot of a computer Description automatically
generated](./media/image4.png)

5.  En la página **Access work or school**, seleccione **Connect**.

![A screenshot of a computer Description automatically
generated](./media/image5.png)

6.  En la ventana **Microsoft account**, seleccione **Join this device
    to Microsoft Entra ID**.

![](./media/image6.png)

7.  En la página **Sign in**,
    tecle !\![**Cindy@M365x51282399.onmicrosoft.com**](mailto:Cindy@M365x51282399.onmicrosoft.com)!!
     Y seleccione **Next**.

![](./media/image7.png)

8.  En la página **Enter password**, introduzca la contraseña:
    !\![**P@55w.rd1234**](mailto:!!P@55w.rd1234)!! y seleccione **Sign
    in**.

![A screenshot of a computer Description automatically
generated](./media/image8.png)

9.  Aparece el cuadro de diálogo **Make sure this is your
    organization**, y seleccione **Join**.

![](./media/image9.png)

10. En la página **You're all set!**, lea la información y
    seleccione **Done**.

![A screenshot of a computer Description automatically
generated](./media/image10.png)

11. En la sección **Access work or school**, verifique que se
    ve **Connected to Contoso's Azure AD**.

12. Seleccione **Connected to Contoso's Azure AD** y luego
    seleccione **Info**.

![A screenshot of a computer Description automatically
generated](./media/image11.png)

13. Tome nota de la infomación sobre los áreas gestionados por Contoso,
    baje, y seleccione **Sync**. Esto obliga un Device sync con Intune.

![A screenshot of a computer Description automatically
generated](./media/image12.png)

14. Cierre la ventana **Settings**.

**Tarea 2: Valide el device enrollment en Microsoft Entra y Intune**

1.  En el **SEA-WS1** taskbar, seleccione **Start**,
    tecle !!**certlm.msc**!! presione **Enter**.

![A screenshot of a computer Description automatically
generated](./media/image13.png)

2.  En el cuadro de diálogo User Account Control, seleccione el botón
    **Yes**.

![](./media/image14.png)

3.  En la consola **Certificates**, en el panel de navegación,
    expanda **Personal** y seleccione **Certificate** node. Verifique
    que se enlistan los siguientes certificados en el details pane:

- Microsoft Intune MDM Device CA

- MS-Organization-Access

- MS-Organization-P2P-Access \[2024\]

Esto indica que el dispositivo está inscrito en Microsoft Entra y
Intune.

![](./media/image15.png)

4.  Cierre la ventana Certificates.

5.  Haga clic derecho en el botón **Start** y seleccione **Windows
    Terminal (Admin)**.

![A screenshot of a computer Description automatically
generated](./media/image16.png)

6.  En el cuadro de diálogo **User Account Control**, haga clic en el
    botón **Yes**.

![A screenshot of a computer error Description automatically
generated](./media/image17.png)

7.  En el PowerShell console, tecle lo siguiente y presione **Enter**:

!!**dsregcmd /status**!!

8.  En el output, en **Device State**, verifique que se
    ve **AzureAdJoined : YES**. Esto indica que el dispositivo es Azure
    AD joined.

![A screenshot of a computer Description automatically
generated](./media/image18.png)

9.  En el output en **Tenant Details**, verifique que existen estas tres
    entradas:

- mdmUrl:https://enrollment.manage.microsoft.com/enrollmentserver/discovery.svc

- mdmTouUrl:https://portal.manage.microsoft.com/TermsofUse.aspxmdm

- ComplianceUrl:https://portal.manage.microsoft.com/?portalAction=Compliance

![](./media/image19.png)

*Ojo: estas en tradas indican que el dispositivo está inscrito en
Intune.*

**Tarea 3: Inicie sesión como un usuario de Microsoft Entra ID**

1.  Cierre la sesión de **SEA-WS1** ya que ha iniciado sesión con la
    cuenta de admin local.

2.  En la pantalla Sign in seleccione Other user e inicie sesión
    como !!**Cindy@M365xXXXXXXX.onmicrosoft.com**!!  Con la contraseña:
     !\![**P@55w.rd1234**](mailto:P@55w.rd1234)!!

![](./media/image20.png)

3.  Espere a que se crea el perfil

![A screenshot of a computer Description automatically
generated](./media/image21.png)

**Ojo** – Si le pide por **Windows Hello**, pues complete el proceso de
sign in y en la página de **Set up a PIN**, en las casillas **New
PIN** y **Confirm PIN**, tecle !!**102938**!!  y seleccione **OK**.

![A screenshot of a computer Description automatically
generated](./media/image22.png)

4.  Cierre la sesión de **SEA-WS1**.

**Tarea 4: Verificar el device enrollment en el Microsoft Intune
console**

1.  Cambie
    a *[SEA-SVR1](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)*
    e inicie sesión con las credenciales proporcionadas.

2.  En el navegador Microsoft Edge,
    tecle !!**https://intune.microsoft.com**!! en el address bar, y
    presione **Enter**. Inicie sesión con su cuenta Office 365 Tenant
    administrator.

3.  En el panel de navegación, seleccione **Devices**.

![A screenshot of a computer Description automatically
generated](./media/image23.png)

4.  En la página **Devices | Overview**, navegue y haga clic en
    **Windows**.

![](./media/image24.png)

5.  Navegue y haga clic en **Windows devices**. Verifique que se
    enlista **SEA-WS1**.

Note que para SEA-WS1, la columna **Managed by** muestra **Intune** y la
columna **Ownership** muestra **Corporate**.

![A screenshot of a computer Description automatically
generated](./media/image25.png)

**Ojo**: Esta view enumera dispositivos que están inscritos en Intune.
Porque ha configurado el automatic enrollment en Microsoft Entra y
Microsoft Intune, cualquier dispositivo que se junta o se registra en
Microsoft Entra está inscrito de forma automática en Microsoft Intune.
Cualquier dispositivo juntado antes de la configuración de enrollment
están juntados o registrados solo en Entra, pero no en Intune.

6.  Abra una pestaña y navegue a **Microsoft Entra admin center**
    !!**https://entra.microsoft.com**!!. haga clic en **Devices** y
    seleccione **All devices**.

![A screenshot of a computer Description automatically
generated](./media/image26.png)

7.  Tome nota de **SEA-WS1**. Note que la columna **Join Type** muestra
    Microsoft Entra joined y la columna **MDM** muestra Microsoft
    Intune.

![A screenshot of a computer Description automatically
generated](./media/image27.png)

**Resultados**: Después de completar este ejercicio, tendrá juntado un
cliente Windows a Microsoft Entra ID exitosamente y verificado que se ha
inscrito automáticamente el dispositivo en Microsoft Intune.
