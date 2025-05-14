Laboratorio 03: Configurar y gestionar Microsoft Entra ID Join

**Resumen**

En este laboratorio, configurará Microsoft Entra ID Join settings y
realizará escenarios both standard y Microsoft Entra hybrid join para
dispositivos Windows.

**Prerrequisitos**

Se debe completar lo(s) siguiente(s) laboratorio(s) antes de este
laboratorio:

- Laboratorio \#2: Sincronizar Identities mediante Microsoft Entra
  Connect

**Ojo**: tambíen necesita un celular que puede recibir mensajes para
asegurar la autenticación de inicio de sesión Windows Hello a Entra ID.

**Ejercicio 1: Configuración de Microsoft Entra Join**

**Escenario**

Necesita configurar Entra ID device para asegurar de que todos los
usuarios puedan juntar los dispositivos a Entra ID. También necesita
asegurar de que los usuarios puedan juntas un máximo de 20 dispositivos
y que esté agregado Allan Deyoung como un local administrator en todos
los Microsoft Entra Joined devices. Finalmente, verificará que el
Microsoft Entra Join funciona como esperado al hacer que Joni Sherman se
una SEA-WS1 al tenant.

## Tarea 0: Habilite TLS 1.2 mediante PowerShell script.

1.  En SEA-WS1, inicie sesión como Contoso\Administrator con la
    contraseña Pa55w.rd

2.  En el start menu tecle [**PowerShell**](urn:gd:lg:a:send-vm-keys),
    haga clic derecho en PowerShell y seleccione run as administrator.

![](./media/image1.png)

3.  Ejecute el siguiente script en el PowerShell.

**If** (-Not (Test-Path
'HKLM:\SOFTWARE\WOW6432Node\Microsoft\\NETFramework\v4.0.30319'))

{

New-Item 'HKLM:\SOFTWARE\WOW6432Node\Microsoft\\NETFramework\v4.0.30319'
-Force | Out-Null

}

New-ItemProperty -Path
'HKLM:\SOFTWARE\WOW6432Node\Microsoft\\NETFramework\v4.0.30319' -Name
'SystemDefaultTlsVersions' -Value '1' -PropertyType 'DWord' -Force |
Out-Null

New-ItemProperty -Path
'HKLM:\SOFTWARE\WOW6432Node\Microsoft\\NETFramework\v4.0.30319' -Name
'SchUseStrongCrypto' -Value '1' -PropertyType 'DWord' -Force | Out-Null

**If** (-Not (Test-Path
'HKLM:\SOFTWARE\Microsoft\\NETFramework\v4.0.30319'))

{

New-Item 'HKLM:\SOFTWARE\Microsoft\\NETFramework\v4.0.30319' -Force |
Out-Null

}

New-ItemProperty -Path
'HKLM:\SOFTWARE\Microsoft\\NETFramework\v4.0.30319' -Name
'SystemDefaultTlsVersions' -Value '1' -PropertyType 'DWord' -Force |
Out-Null

New-ItemProperty -Path
'HKLM:\SOFTWARE\Microsoft\\NETFramework\v4.0.30319' -Name
'SchUseStrongCrypto' -Value '1' -PropertyType 'DWord' -Force | Out-Null

**If** (-Not (Test-Path
'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS
1.2\Server'))

{

New-Item
'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS
1.2\Server' -Force | Out-Null

}

New-ItemProperty -Path
'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS
1.2\Server' -Name 'Enabled' -Value '1' -PropertyType 'DWord' -Force |
Out-Null

New-ItemProperty -Path
'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS
1.2\Server' -Name 'DisabledByDefault' -Value '0' -PropertyType 'DWord'
-Force | Out-Null

**If** (-Not (Test-Path
'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS
1.2\Client'))

{

New-Item
'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS
1.2\Client' -Force | Out-Null

}

New-ItemProperty -Path
'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS
1.2\Client' -Name 'Enabled' -Value '1' -PropertyType 'DWord' -Force |
Out-Null

New-ItemProperty -Path
'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS
1.2\Client' -Name 'DisabledByDefault' -Value '0' -PropertyType 'DWord'
-Force | Out-Null

Write-Host 'TLS 1.2 has been enabled. You must restart the Windows
Server for the changes to take affect.' -ForegroundColor Cyan

![](./media/image2.png)

4.  Reinicie el Windows Server VM.

![](./media/image3.png)

## Tarea 1: Configure los Microsoft Entra ID join Device settings

1.  Cambie a **SEA-SVR1**. En la barraa de direcciones de **Microsoft
    Edge** browser, tecle el siguiente URL:
    !\![**https://entra.microsoft.com**](https://entra.microsoft.com)!!
    y presione el botón **Enter**.

2.  Inicie sesión con su O365 tenant ID:
    !!**admin@M365xXXXXXXXX.onmicrosoft.com**!!, y use la contraseña de
    tenant Admin.

![A screenshot of a computer Description automatically
generated](./media/image4.png)

![A screenshot of a login box Description automatically
generated](./media/image5.png)

3.  En el cuadro de diálogo **Stay signed in?**, seleccione el botón
    **Yes**.

![A screenshot of a computer Description automatically
generated](./media/image6.png)

4.  En la ventana **Microsoft Entra admin center**, navegue y haga clic
    en **Identity**.

![A screenshot of a computer Description automatically
generated](./media/image7.png)

5.  En la sección **Identity**, seleccione **Devices**, navegue y haga
    clic en navigate **All devices** como se ve en la imagen.

![A screenshot of a computer Description automatically
generated](./media/image8.png)

Note que no hay dispositivos, ya que todavía no ha juntado ningún
dispositivo.

![](./media/image9.png)

6.  En la página **Devices** | All devices, seleccione **Device
    settings**.

![A screenshot of a computer Description automatically
generated](./media/image10.png)

7.  En la página **Devices | Device settings**, en el panel details,
    en **Users may join devices to Entra**, verifique que está
    seleccionado **All**.

Esto señala que todos los usuarios de Entra tienen el permiso de juntar
dispositivos Windows 10 o superiores a Microsoft Entra. Note que no se
aplica esta configuración a Entra hybrid joined devices, o dispositivos
juntados mediante Windows Autopilot self-deployment mode.

8.  En la sección **Require Multi-factor Authentication to register or
    join devices with Entra**, verifique que el setting está en **No**.

![A screenshot of a computer Description automatically
generated](./media/image11.png)

9.  En la sección **Maximum number of devices per user**,
    seleccione **20 (Recommended)**.

10. Haga clic en **Manage** **Additional local administrators on all
    Microsoft Entra Joined devices**. Se abre la página **Device
    Administrators**.

![A screenshot of a computer Description automatically
generated](./media/image12.png)

11. En la página **Device Administrators | Assignments**,
    seleccione **Add assignments**.

![A screenshot of a computer Description automatically
generated](./media/image13.png)

12. En el cuadro Search, introduzca !!**Allan Deyoung**!!, seleccione
    el **Allan Deyoung** user object, y seleccione **Add**.

![A screenshot of a computer Description automatically
generated](./media/image14.png)

13. Allan Deyoung será añadido como Device Administrator en todos
    Microsoft Entra Joined devices.

![A screenshot of a computer screen Description automatically
generated](./media/image15.png)

14. Haga clic en el enlace **Devices | Device settings** debajo de Azure
    portal search bar para volver a la página **Device Settings**.

![A screenshot of a computer Description automatically
generated](./media/image16.png)

15. En la página **Device settings**, seleccione **Save**.

![A screenshot of a computer Description automatically
generated](./media/image17.png)

**Tarea 2: Realice Microsoft Entra ID Join**

1.  Cambie
    a [SEA-WS1](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10) e
    inicie sesión como **Admin** con la contraseña !!**Pa55w.rd**!!.

![](./media/image18.png)

2.  En el taskbar, seleccione el ícono **Windows Start button** y
    seleccione **Settings**.

![](./media/image19.png)

3.  En la ventana **Settings**, seleccione **Accounts**.

![A screenshot of a computer Description automatically
generated](./media/image20.png)

4.  En la página **Accounts**, seleccione **Access work or school**.

![A screenshot of a computer Description automatically
generated](./media/image21.png)

5.  En la página **Access work or school**, seleccione **Connect**.

![A screenshot of a computer Description automatically
generated](./media/image22.png)

6.  En la ventana **Microsoft account**, seleccione **Join this device
    to Microsoft Entra ID**.

![A screenshot of a computer screen Description automatically
generated](./media/image23.png)

7.  En la página **Sign in**, tecle
    !!JoniS@M365xXXXXXXX.onmicrosoft.com!!  Y seleccione **Next**.

![Graphical user interface, application, Teams Description automatically
generated](./media/image24.png)

8.  En la página **Enter password**, introduzca el tenant password:
    !\![**P@55w.rd1234**](mailto:P@55w.rd1234)!! y seleccione **Sign
    in**.

![Graphical user interface, application Description automatically
generated](./media/image25.png)

9.  En el cuadro de diálogo **Make sure this is your organization**,
    seleccione **Join**.

![A screenshot of a computer error Description automatically
generated](./media/image26.png)

10. En la página **You're all set!**, seleccione **Done**.

![A screenshot of a computer Description automatically
generated](./media/image27.png)

11. En la página **Access work or school**, verifique que se
    ve **Connected to Contoso's Azure AD**.

![A screenshot of a computer Description automatically
generated](./media/image28.png)

12. Cierre la página **Settings**.

**Tarea 3: Valide Microsoft Entra Join**

1.  En [SEA-WS1](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10),
    haga clic derecho en el ícono **Windows** **Start button**, y
    seleccione **Windows Terminal (Admin)** como se ve en la imagen.

![](./media/image29.png)

2.  En el cuadro de diálogo **User Account Control**,
    seleccione **Yes**.

![](./media/image30.png)

3.  En el PowerShell console, tecle el siguiente command y presione el
    botón **Enter**:

!!**dsregcmd /status**!!

4.  En el output, en **Device State**, verifique que se
    ve **AzureAdJoined : YES**.

Esto señala que el dispositivo está Microsoft Entra Joined.

![](./media/image31.png)

5.  Cierre PowerShell.

6.  Haga clic derecho en **Windows** **Start** **button** de nuevo y
    seleccione **Computer Management**.

![A screenshot of a computer Description automatically
generated](./media/image32.png)

7.  En la ventana **Computer Management**, expanda **Local Users and
    Groups**, y seleccione **Groups**.

![](./media/image33.png)

![A screenshot of a computer Description automatically
generated](./media/image34.png)

8.  Haga doble clic en **Administrators** group.

![A screenshot of a computer Description automatically
generated](./media/image35.png)

Note que se ha agregado Joni Sherman como el local Administrator
en [SEA-WS1](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10).
También note los dos security principals representados por su security
identifiers (SID). Estos dos SIDs representan el Entra global
administrator role y el Microsoft Entra Joined device administrator
role.

![](./media/image36.png)

9.  Cierre todas las ventanas abiertas y cierre la sesión de SEA-WS1 al
    hacer clic en **Windows Start button icon \> Admin \> Sign out**.

![](./media/image37.png)

10. Cambie a **SEA-SVR1** e inicie sesión con las credenciales
    **Contoso\Administrator** y contraseña !!**Pa55w.rd**!!

![A screenshot of a computer Description automatically
generated](./media/image38.png)

11. En **Microsoft Entra admin center**, navegue y haga clic en
    **Identity**.

12. Navegue y seleccione **Devices**, y haga clic en **All devices**.

13. En la página **Devices | All devices**, note que está enumerado
    **SEA-WS1**.

![](./media/image39.png)

14. Verifique que está **Join Type** como **Microsoft Entra Joined** y
    el owner es **Joni Sherman**.

![](./media/image40.png)

15. También note que la columna MDM muestra **None**. Esto indica que el
    dispositivo todavía no está gestionado por Microsoft Intune.

![A screenshot of a computer Description automatically
generated](./media/image41.png)

**Tarea 4: Inicie sesión en Windows como Microsoft Entra User**

1.  Cambie a **SEA-WS1** y haga clic en **Other user.**

![](./media/image42.png)

2.  **Inicie sesión** como !!**JoniS@M365xXXXXXXX.onmicrosoft.com**!!
     con el tenant password: !!**P@55w.rd1234**!!

**Ojo: Espere a que se cree el perfil.**

![](./media/image43.png)

**Ojo** – si le pide **Windows Hello**, pues complete el proceso de
inicio de sesión y en la página de **Set up a PIN**, en las
casillas **New PIN** y **Confirm PIN**, tecle !!**102938**!!  y
seleccione **OK**.

![](./media/image44.png)

**Tarea 5: Quite un Windows device desde Entra**

1.  En [SEA-WS1](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10),
    inicie sesión como Joni Sherman si le pide y, si está disponible la
    opción de introducir el Pin, pues introduzca el pin: !!**102938**!!
    o introduzca la contraseña !!**P@55w.rd1234**!!

![A screenshot of a computer Description automatically
generated](./media/image45.png)

2.  En la ventana **Settings**, seleccione **Accounts**.

![A screenshot of a computer Description automatically
generated](./media/image46.png)

3.  En el panel de navegación izquierda, navegue y haga clic en
    **Accounts**. En la página **Accounts**, seleccione **Access work or
    school**.

![A screenshot of a computer Description automatically
generated](./media/image47.png)

4.  En la página **Access work or school**, seleccione el dropdown junto
    a **Connected to Contoso's Azure AD** como se ve en la imagen. Haga
    clic en **Disconnect** y seleccione **Yes**.

![](./media/image48.png)

![A screenshot of a computer Description automatically
generated](./media/image49.png)

![A screenshot of a computer Description automatically
generated](./media/image50.png)

5.  En la página **Disconnect from the organization**,
    seleccione **Disconnect**.

![A blue box with white text Description automatically
generated](./media/image51.png)

6.  En el cuadro de diálogo **Windows Security**, en la casilla **Email
    address**, introduzca !!Admin!! y el cuadro de **Password**,
    tecle !!Pa55w.rd!!. Seleccione **OK**.

![Graphical user interface Description automatically
generated](./media/image52.png)

7.  En el cuadro de diálogo **Restart your PC**, seleccione **Restart
    now**. Se reinicia **SEA-WS1**.

![A blue box with white text Description automatically
generated](./media/image53.png)

**Resultados**: Después de completar este ejercicio, tendrá configurado
el Microsoft Entra device settings, juntado un dispositivo a Entra, y
quitado un dispositivo desde Entra.

**Ejercicio 2: Configurar Microsoft Entra hybrid join**

**Escenario**

Unos dispositivos Contoso Windows de momento están juntados al Active
Directory Domain Services local. Para habilitar esto dispositivos para
acceder los servicios cloud que planea habilitar Microsoft Entra hybrid
join sin problemas. Probará el Microsoft Entra hybrid join al
reconfigurar Azure AD Connect y probar el proceso en SEA-CL2.

**Tarea 1: Prepare el entorno**

1.  Cambie
    a [SEA-SVR1](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10).

![A picture containing text Description automatically
generated](./media/image54.png)

2.  Seleccione el botón **Windows** **Start icon**, expanda **Windows
    Administrative Tools**, y seleccione **Active Directory Users and
    Computers**.

![](./media/image55.png)

3.  En **Active Directory Users and Computers**, haga clic derecho
    en **Contoso.com**, apunte a **New**, y ahora
    seleccione **Organizational Unit**.

![](./media/image56.png)

4.  En el cuadro de diálogo **New-Object - Organizational Unit**,
    tecle !!**Entra clients**!! Y seleccione **OK**.

![A screenshot of a computer Description automatically
generated](./media/image57.png)

5.  En el panel de navegación, seleccione **Seattle Clients**. Haga clic
    derecho en **SEA-CL2** y seleccione **Move**.

![](./media/image58.png)

6.  En el cuadro de diálogo **Move**, seleccione **Entra clients** y
    seleccione **OK**.

![A screenshot of a computer Description automatically
generated](./media/image59.png)

7.  Cierre **Active Directory Users and Computers**.

![A screenshot of a computer Description automatically
generated](./media/image60.png)

**Tarea 2: Reconfigure Entra Connect**

1.  En [SEA-SVR1](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10),
    haga doble clic en Azure AD Connect en el Desktop

![A black rectangle with blue lines Description automatically
generated](./media/image61.png)

2.  En la ventana **Microsoft Azure Active Directory Connect**,
    seleccione **Configure**.

![](./media/image62.png)

3.  En la página **Additional tasks**, seleccione **Customize
    synchronization options** y seleccione **Next**.

![A screenshot of a computer Description automatically
generated](./media/image63.png)

4.  En la página **Connect to Entra**, en las
    casillas **USERNAME** y **PASSWORD**, introduzca sus **Office 365
    Tenant credentials** y seleccione **Next**.

![A screenshot of a computer Description automatically
generated](./media/image64.png)

5.  En la página **Connect your directories**, haga clic en el botón.

![A screenshot of a computer Description automatically
generated](./media/image65.png)

6.  En la página **Domain and OU filtering**, asegure de que está
    seleccionado **Sync selected domains and Ous**.

7.  Expanda **Contoso.com**, seleccione **Entra clients,** y haga clic
    en **Next**.

![A screenshot of a computer Description automatically
generated](./media/image66.png)

8.  En la página **Optional features**, asegure de que esté
    seleccionado **Password hash synchronization**, y
    seleccione **Next**.

9.  En la página **Ready to configure**, asegure de que está
    seleccionado **Start the synchronization process when configuration
    completes**, y luego seleccione **Configure**.

![A screenshot of a computer Description automatically
generated](./media/image67.png)

10. Cuando se completa la configuración, seleccione **Exit**.

![](./media/image68.png)

Ojo: Espere 5 minutos a que se complete la sincronización.

**Tarea 3: Configure Microsoft Entra hybrid Join mediante Azure AD
Connect**

1.  En [SEA-SVR1](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)
    VM **Desktop**, haga doble clic en **Azure AD Connect**.

![Text Description automatically generated with medium
confidence](./media/image69.png)

2.  En la ventana **Microsoft Azure Active Directory Connect**,
    seleccione **Configure**.

![](./media/image70.png)

3.  En la página **Additional tasks**, seleccione **Configure device
    options** y seleccione **Next**.

![](./media/image71.png)

4.  En la página **Overview**, seleccione **Next**.

![A screenshot of a computer Description automatically
generated](./media/image72.png)

5.  En la página **Connect to Entra**, introduzca la contraseña Admin
    Tenant en el cuadro **PASSWORD**, y seleccione **Next**.

![](./media/image73.png)

6.  En la página **Device options**, seleccione **Configure Hybrid Azure
    AD Join**, y seleccione **Next**.

![A screenshot of a computer Description automatically
generated](./media/image74.png)

7.  En la página **Device operating systems**, seleccione **Windows 10
    or later domain-joined devices**, y seleccione **Next**.

![A screenshot of a computer Description automatically
generated](./media/image75.png)

8.  En la página **SCP configuration**, seleccione la casilla de
    verificación junto a **Contoso.com**. Seleccione **Azure Active
    Directory** desde el **Authentication Service** dropdown y
    seleccione **Add**.

![](./media/image76.png)

9.  En la ventana **Enterprise Admin Credentials**
    introduzca **Contoso\Administrator** como **Username** y !!**Pa55w.rd**!! as **Password**.
    Seleccione **OK** y seleccione **Next**.

![A screenshot of a computer security Description automatically
generated](./media/image77.png)

![](./media/image78.png)

10. En la página **Ready to configure**, seleccione **Configure** para
    ejecutar la configuración.

![A screenshot of a computer Description automatically
generated](./media/image79.png)

11. Cuando se termine la configuración, seleccione **Exit**.

![A screenshot of a computer Description automatically
generated](./media/image80.png)

12. En el taskbar, haga clic derecho en **Windows Start button icon** y
    seleccione **Windows Powershell (Admin)**.

![A screenshot of a computer Description automatically
generated](./media/image81.png)

13. En la ventana **Windows PowerShell**, tecle el siguiente command, y
    presione **Enter**:

!!**Start-ADSyncSyncCycle -PolicyType Initial**!!

![A screenshot of a computer Description automatically
generated](./media/image82.png)

14. Cierre la ventana PowerShell.

Ojo: Espere unos 5 minutos para que se complete la sincronización.

**Tarea 4: Verifique la registración de Entra**

1.  Cambie
    a [SEA-CL2](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10).

2.  En la página de inicio de sesión, seleccione el botón **Power** y
    seleccione **Restart**.

![Graphical user interface, application Description automatically
generated](./media/image83.png)

***Ojo**: el reboot iniciará el hybrid Microsoft Entra Join
en [SEA-CL2](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10).*

3.  Después de que se reinicie el **SEA-CL2**, inicie sesión
    como **Contoso\Administrator** con la contraseña !!**Pa55w.rd**!!

![Graphical user interface, application Description automatically
generated](./media/image84.png)

4.  En el taskbar, haga clic derecho en **Windows Start icon button** y
    seleccione **Windows Terminal (Admin)**.

![A screenshot of a computer Description automatically
generated](./media/image81.png)

5.  En la ventana **Windows PowerShell**, tecle en siguiente command, y
    presione **Enter**:

!!**dsregcmd /status**!!

6.  En el output en **Device State**, verifíquelo. 

- **AzureAdJoined : YES** 

- **DomainJoined : YES** are displayed.

![](./media/image85.png)

***Ojo: Si no se ha juntado el dipositivo a Entra espere a que se
complete la sincronización Entra Connect e inicie SEA-CL2 de nuevo.
Puede tardar unos 5-10 minutos para que se actualice el estado.***

Además, puede iniciar sesión en **SEA-SVR1** y en la ventana **Windows
PowerShell**, tecle el siguiente command para acelerar la
sincronización.

!!**Start-ADSyncSyncCycle -PolicyType Initial**!!

7.  Cierre todas las ventanas
    en [SEA-CL2](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10) y
    cierre la sesión.

8.  Cambie
    a [SEA-SVR1](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10) y
    vaya a la ventana **Microsoft Entra admin center**, navegue y haga
    clic en **Identity**.

![A screenshot of a computer Description automatically
generated](./media/image7.png)

9.  En la sección **Identity**, seleccione **Devices**, navegue y haga
    clic en **All devices** como se ve en la siguiente imagen.

![A screenshot of a computer Description automatically
generated](./media/image8.png)

10. Verifique que **SEA-CL2** tiene **Microsoft Entra** **hybrid
    joined** como un valor para la fila **Join type**. Haga clic en el
    botón **Refresh** si no se enumera SEA-CL2.

![A screenshot of a computer Description automatically
generated](./media/image86.png)

11. Cierre todas las ventanas
    en [SEA-SVR1](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10).

**Resultados**: después de completar este ejercicio, habrá configurado y
validado Microsoft Entra hybrid join de forma exitosa.
