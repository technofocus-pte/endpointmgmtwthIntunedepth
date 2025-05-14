Laboratorio 01 – Gestión de Identities en Microsoft Entra ID

**Resumen**

En este laboratorio, usará el Microsoft Entra admin center para crear y
modificar usuarios, asignar roles administrativos, crear y modificar
grupos y gestionar la asignación de licencias en Microsoft Entra ID.

Ejercicio 1: Crear usuarios en Microsoft Entra ID

**Escenario**

Necesita crear cuentas de usuarios en Microsoft Entra ID para unos
nuevos empleados que empiezan la semana que viene. Los nuevos usuarios
son los menciondos aquí en la tabla:

[TABLE]

**Ojo**: como location use o su región local o United States.

También se le ha contado que se van a contratar muchos empleados más a
lo largo de próximos dos meses. Ha decidido que scripting será un método
mucho más eficiente para añadir esta cantidad de nuevos usuarios. Ha
decidido crear un PowerShell script y probarlo cuando crea la cuenta de
Cody Godinez.

Tarea 1: Cree usuarios con la ayuda de Microsoft Entra admin center

1.  En [***SEA-SVR1***](urn:gd:lg:a:select-vm), inicie sesión
    como [**Contoso\Administrator**](urn:gd:lg:a:send-vm-keys) con la
    contraseña !\![**Pa55w.rd**](urn:gd:lg:a:send-vm-keys)!!.

> ![Screenshot](./media/image1.png)

2.  Abra el **Microsoft Edge browser** y navegue a 

> !\![**https://entra.microsoft.com/#view/Microsoft_AAD_UsersAndTenants/UserManagementMenuBlade/~/AllUsers/menuId/**](https://entra.microsoft.com/#view/Microsoft_AAD_UsersAndTenants/UserManagementMenuBlade/~/AllUsers/menuId/)!!

3.  En el Sign-in prompt, introduzca los **Office 365 Tenant
    credentials** desde la pestaña Home tab del interfaz del
    laboratorio.

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)

**Ojo** – si le pide algo de MFA, complete el proceso de acceso con MFA.

4.  En el **Microsoft Entra admin center**, expanda **Identity** y en el
    panel de navegación, seleccione **Users**.

> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)
>
> Tome en cuenta los usuarios que ya existen como miembros en el
> Microsoft Entra ID domain. Se habilita a cada usuario como indicado en
> la columna **Account enabled**. La columna **On-premises
> synced** **enabled** dice **No** para todos los usuarios actuales.
> Esto indica que se crearon todos los usuarios directamente en
> Microsoft Entra ID y no sincronizaron desde un servicio de directorio
> local.
>
> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

5.  En la página **Users | All users**, seleccione **New user** y
    seleccione **Create new user**.

> ![](./media/image5.png)

6.  En la página **New User**, asegure que se selecciona **Create
    user**, introduzca lo siguiente:

    - User principal name: !\![**ereeve**](urn:gd:lg:a:send-vm-keys)!!

    - Display Name: !\![**Edmund Reeve**](urn:gd:lg:a:send-vm-keys)!!

    - Deseleccione **Auto-generate password.**

    - Password **–** !!**P@55w.rd1234**!!

> ![A screenshot of a computer Description automatically
> generated](./media/image6.png)

7.  En la pestaña **Properties**, proporcione la siguiente información y
    haga clic en **Next Assignments.**

    - **Job title**, introduzca !\![**HR
      Rep**](urn:gd:lg:a:send-vm-keys)!!

    - **Department**, introduzca  !!**H[R](urn:gd:lg:a:send-vm-keys)**!!

    - **Usage location - United States**

> ![](./media/image7.png)

8.  En la pestaña Assignments, haga clic en el botón **Review +
    create**.

> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)

9.  Verifique los detalles y haga clic en el botón **Create**.

> ![](./media/image9.png)
>
> ![A close-up of a computer screen Description automatically
> generated](./media/image10.png)

10. De manera similar, cree la cuenta del usuario para Miranda Snider
    con los siguientes detalles.

    - User principal name:  !\![**msnider**](urn:gd:lg:a:send-vm-keys)!!

    - Display Name: !! [**Miranda Snider**](urn:gd:lg:a:send-vm-keys)!!

    - Deseleccione **Auto-generate password.**

    - Password **–** !!**P@55w.rd1234**!!

    - Job title - !!**Helpdesk Manager**!!

    - Department **-** !!**Operations**!!

    - Usage location **- United States**

11. Seleccione la cuenta del usuario de **Allan Deyoung** y haga clic en
    **Edit properties** y actualice el Job information con los
    siguientes detalles y haga clic en el botón **Save**.

    - Job title- !\![**IT Admin**](urn:gd:lg:a:send-vm-keys)!!

    -  Department - !\![**IT**](urn:gd:lg:a:send-vm-keys)!!

> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)

12. Seleccione la cuenta del usuario **Joni Sherman** y haga clic en
    **Edit properties** y actualice el Job information con los
    siguientes detalles y haga clic en el botón **Save**.

    - Job title- !!**ParaLegal**!!

    -  Department - !!**Legal**!!

> ![A screenshot of a computer Description automatically
> generated](./media/image12.png)

13. Seleccione la cuenta del usuario **Alex Wilber** y haga clic en
    **Edit properties** y actualice el Job information con los
    siguientes detalles y haga clic en el botón **Save**.

    - Job title - !!**Marketing Assistant**!!

    -  Department – !\![**Marketing**](urn:gd:lg:a:send-vm-keys)!!

> ![](./media/image13.png)

Tarea 2: Cree usuarios mediante PowerShell

1.  En [***SEA-SVR1***](urn:gd:lg:a:select-vm), en el taskbar, haga clic
    derecho en **Start**, y seleccione **Windows PowerShell (Admin)**.

> ![](./media/image14.png)

2.  En la pantalla **Windows PowerShell**, tecle el siguiente command, y
    presione **Enter**. Si le pide, introduzca 
    !\![**Y**](urn:gd:lg:a:send-vm-keys)!!  en NuGet y repository
    messages:

> !!**Install-Module MSOnline**!!
>
> ![](./media/image15.png)

3.  En la pantalla **Windows PowerShell**, tecle en siguiente command, y
    presione **Enter**:

> !!**Connect-MsolService**!!
>
> ![A screenshot of a computer Description automatically
> generated](./media/image16.png)

4.  En el cuadro de diálogo **Sign in to your account**, inicie sesión
    con los Office 365 Tenant credentials desde la pestaña Home.

> **Ojo – Si le pide que cambie la contraseña de Tenant admin
> credentials, asegure de que proporciona la contraseña actualizada.**

5.  En la pantalla **Windows PowerShell**, tecle el siguiente código
    para crear un nuevo usuario, y presione **Enter**.

> Ojo – pegue el siguiente command en notepad y sustituya los Tenant
> details y copie y pegue el command en Windows PowerShell, si se
> requiere asegurar que la información del tenant es correcta
>
> !!**New-MsolUser -UserPrincipalName
> cgodinez@M365xXXXXXXXX.onmicrosoft.com -DisplayName "Cody Godinez"
> -FirstName "Cody" -LastName "Godinez" -Password ‘P@55w.rd1234’
> -ForceChangePassword $false -UsageLocation "US" -Title "Sales Rep"
> -Department "Sales"**!!
>
> ![A screenshot of a computer screen Description automatically
> generated](./media/image17.png)

6.  En la pantalla **Windows PowerShell**, tecle el siguiente command
    para reestablecer las contraseñas de Alew Wilber, Allan Deyoung y
    Joni Sherman

> !!**Get-MsolUser | Where-Object DisplayName -EQ "Alex Wilber" |
> Set-MsolUserPassword -NewPassword P@55w.rd1234 -ForceChangePassword
> $false**!!
>
> !!**Get-MsolUser | Where-Object DisplayName -EQ “Allan Deyoung” |
> Set-MsolUserPassword -NewPassword P@55w.rd1234 -ForceChangePassword
> $false**!!
>
> !!**Get-MsolUser | Where-Object DisplayName -EQ "Joni Sherman" |
> Set-MsolUserPassword -NewPassword P@55w.rd1234 -ForceChangePassword
> $false**!!
>
> ![A computer screen shot of a program Description automatically
> generated](./media/image18.png)

7.  En la ventana **Windows PowerShell**, tecle el siguiente command y
    presione **Enter**:

> !!**Get-MsolUser**!!

8.  Verifique que se ve la lista de usuarios desde su tenant. También
    tome nota de los usuarios que tienen una licencia asignada.
    Cualquier usuario con el valor de **isLicensed** como **False** no
    tiene una licencia asignada.

> ![A screenshot of a computer Description automatically
> generated](./media/image19.png)

**Resultados**: después de completar este ejercicio, habrá creado nuevas
cuentas de usuarios exitosamente en Microsoft Entra ID.

Ejercicio 2: Asignar Administrative Roles en Microsoft Entra ID

**Escenario**

Necesita revisar y modificar los roles administrativos actuales para su
tenant.

Tiene una lista de usuarios a los que tiene que asignar los roles
administrativos como se indica en la siguiente tabla.

[TABLE]

Tarea 1: Revise y asigne los Administrative Roles

1.  En [***SEA-SVR1***](urn:gd:lg:a:select-vm), cambie a **Microsoft
    Edge**.

2.  En el **Microsoft Entra admin center**, en el panel de navegación,
    expanda **Roles & admins.**

3.  Seleccione **Roles & admin** y busque !!**Global administrator**!! Y
    haga clic en el Role **Global Administrator**.

> ![A screenshot of a computer Description automatically
> generated](./media/image20.png)

4.  Haga clic en **Add assignments**.

> ![A screenshot of a computer Description automatically
> generated](./media/image21.png)

5.  En la página Add assignments, seleccione **Allan Deyoung** y
    seleccione **Add**.

> ![A screenshot of a computer Description automatically
> generated](./media/image22.png)

6.  En la parte superior de la página, en el enlace de la navegación,
    seleccione **Roles and administrators**.

> ![A screenshot of a computer Description automatically
> generated](./media/image23.png)

7.  En la página de **Roles and administrators**, busque y seleccione
    !!**User administrator**!!. Asegure que se
    selecciona **Assignments**.

> ![A screenshot of a chat Description automatically
> generated](./media/image24.png)
>
> Note que no hay usuarios actualmente asignados al User administrator
> role.

8.  Haga clic en + **Add assignments**.

> ![A screenshot of a computer Description automatically
> generated](./media/image25.png)

9.  En la página de Add assignments, seleccione **Edmund Reeve** y
    seleccione **Add**.

> ![A screenshot of a computer Description automatically
> generated](./media/image26.png)

10. Haga clic en el enlace **Roles and administrators**, y busque y
    seleccione !!**Helpdesk administrator**!!.

> ![A screenshot of a computer Description automatically
> generated](./media/image27.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image28.png)
>
> Note que no hay usuarios actualmente asignados a Helpdesk
> administrator role.

11. En la página **Helpdesk administrator | Assignments**,
    seleccione **Add assignments**.

> ![A screenshot of a computer Description automatically
> generated](./media/image29.png)

12. En la página Add assignments, seleccione **Miranda Snider** y
    seleccione **Add**.

> ![A screenshot of a computer Description automatically
> generated](./media/image30.png)

13. En la parte superior de la página, en el enlace de navegación,
    seleccione **Roles and administrators**.

> ![A screenshot of a computer Description automatically
> generated](./media/image31.png)

**Resultados**: Despúes de completar este ejercicio, debe haber asignado
los administrative roles a los usuarios.

Ejercicio 3: Crear y gestionar grupos y validar la asignación de
licencias.

**Escenario**

Necesita agregar tres nuevos usuarios a Security group y asignar
licencias como señalado en la siguiente tabla.

[TABLE]

También se le pide modificar el Company branding para la página de
acceso.

Tarea 1: Cree grupos mediante el Microsoft Entra admin center

1.  En [***SEA-SVR1***](urn:gd:lg:a:select-vm), en el **Microsoft Entra
    admin center**, en el panel de navegación, expanda **Identity** y
    seleccione **Groups** y haga clic en **New group.**

> ![A screenshot of a computer Description automatically
> generated](./media/image32.png)

2.  En la página **New Group**, introduzca lo siguiente:

    - Group type: **Security**

    - Group name: !\![**Contoso_Managers**](urn:gd:lg:a:send-vm-keys)!!

    - Membership type: **Assigned**

3.  En Members, haga clic en **No members selected**.

4.  En la página Add members agregue a **Edmund Reeve**, **Miranda
    Snider**, y haga clic en **Select**.

> ![A screenshot of a computer Description automatically
> generated](./media/image33.png)

5.  Seleccione **Create**.

Tarea 2: Cree grupos mediante PowerShell

1.  En [***SEA-SVR1***](urn:gd:lg:a:select-vm), cambie a Windows
    PowerShell.

2.  En la pantalla **Windows PowerShell**, tecle el siguinte code para
    crear un nuevo grupo, y presione **Enter**:

> !!**New-MsolGroup -DisplayName "Contoso_Sales" -Description "Contoso
> Sales team users"**!!
>
> ![A screenshot of a computer Description automatically
> generated](./media/image34.png)

3.  En la ventana **Windows PowerShell**, tecle el siguiente command, y
    presione **Enter**:

> !!**Get-MsolGroup**!!
>
> ![A screenshot of a computer screen Description automatically
> generated](./media/image35.png)

4.  Verifique que ha obtenido la lista de groups en su tenant, incluido
    el **Contoso_Sales** group que acaba de crear.

> ![](./media/image36.png)

5.  En la ventana **Windows PowerShell**, tecle el siguiente code para
    definir una variable como el Contoso_Sales group, y presione
    **Enter**:

> !!**$group = Get-MsolGroup | Where-Object {$\_.DisplayName -eq
> "Contoso_Sales"}**!!

6.  En la ventana **Windows PowerShell**, tecle el siguientecode para
    definir otra variable como el usuario, y presione **Enter**:

> !!**$user = Get-MsolUser | Where-Object {$\_.DisplayName -eq "Cody
> Godinez"}**!!

7.  En la ventana **Windows PowerShell**, tecle el siguiente code para
    agregar Cody to Contoso_Sales con set variables, y presione
    **Enter**:

> !!**Add-MsolGroupMember -GroupObjectId $group.ObjectId
> -GroupMemberType "User" -GroupMemberObjectId $user.ObjectId**!!

8.  En la ventana **Windows PowerShell**, tecle el siguiente code, y
    presione **Enter**:

> !! **Get-MsolGroupMember -GroupObjectId $group.ObjectId**!!

9.  Verifique que puede ver **Cody Godinez** en el resultado de command
    output.

> ![A screenshot of a computer program Description automatically
> generated](./media/image37.png)

10. Cierre Windows PowerShell.

Tarea 3: Revise las licencias y modifique el company branding

1.  En el Microsoft Entra admin center, en el panel de navegación,
    expanda **Identity**, y expanda **Billing** y
    seleccione **Licenses**.

> https://admin.microsoft.com/Adminportal/Home?referrer=entra#/licenses
>
> ![](./media/image38.png)

2.  En la página **Licenses**, en Subscriptions, vea todas licencias
    disponibles.

> ![](./media/image39.png)
>
> Ojo – tome nota de todas las licencias actualmente disponible y
> asignadas para **Enterprise Mobility + Security E5** and **Office 365
> E5 (no Teams)**
>
> ![](./media/image40.png)

3.  En el Microsoft 365 admin center, en el panel de navegación
    izquierda seleccione **Users** y luego **Active users**.

> ![](./media/image41.png)

4.  En la lista de usuarios, seleccione **Cody Godinez**.

> ![A screenshot of a computer Description automatically
> generated](./media/image42.png)

5.  En la página Cody Godinez, seleccione **Licenses and apps**

> ![A screenshot of a computer Description automatically
> generated](./media/image43.png)
>
> Note que Cody no tiene ninguna licencia actual asignada.

6.  En la página **Licenses and apps**, seleccione la casilla de
    verificación junto a **Enterprise Mobility + Security
    E5** y **Office 365 E5 (no Teams)** y haga clic en **Save changes**.

> ![A screenshot of a login page Description automatically
> generated](./media/image44.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image45.png)

**Ojo**: Repita los pasos 4 a 8 para asignar licencias Enterprise
Mobility + Security E5 and Office 365 E5 (no Teams) a Joni Sherman, Alex
Wilber y Allan Deyoung en el caso de que no se hayan asignado ninguna.

7.  En el Microsoft Entra admin center, en el panel de navegación,
    expanda **Identity** y seleccione **Groups**.

> ![](./media/image46.png)

8.  En la página **Groups | All groups**,
    seleccione **Contoso_Managers**.

> ![A screenshot of a computer Description automatically
> generated](./media/image47.png)

9.  En la página **Contoso_Managers**, seleccione **Licenses**.

> ![](./media/image48.png)
>
> **Note que el Contoso_Managers group no tiene ninguna licencia
> actualmente asignada.**

10. . Navegue a Microsoft 365 admin center y baje hasta licenses y
    seleccione **Enterprise Mobility + Security E5.**

> ![A screenshot of a computer Description automatically
> generated](./media/image49.png)

11. Haga clic en la pestaña **Groups** y haga clic en **Assign
    licenses.**

> ![](./media/image50.png)

12. Seleccione Contoso_Mangers desde la lista y haga clic en **Assign.**

13. En el Microsoft Entra admin center, en el panel de navegación,
    expanda **Identity**, y luego expanda **Billing** y
    seleccione **Licenses**.

> ![A screenshot of a computer Description automatically
> generated](./media/image51.png)![A screenshot of a computer
> Description automatically generated](./media/image52.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image53.png)

14. En la página **Licenses|Overview**, en **Manage**, seleccione **All
    products**.

> ![A screenshot of a computer Description automatically
> generated](./media/image54.png)
>
> ![](./media/image53.png)

15. Repita el mismo proceso y asigne Office 365 E5 (no Teams) license al
    equipo de Contoso_Managers.

> Tenga en cuenta los usuarios con la licencia Office 365 E5 (no Teams).
> Note la columna Assignment Paths que indica cómo se configura la
> asignación de licencias para cada usuario. Edmund y Miranda reciben
> sus sendas license assignment desde su membresía en el grupo
> Contoso_Managers. Puede que tenga que seleccionar **Refresh** un par
> de veces para actualizar el Assignment path column.
>
> ![](./media/image55.png)

16. Cierre Microsoft Edge.

**Resultados**: después de completar este ejercicio, tendrá grupos
creados y gestionados exitosamente, y licencias asignadas.
