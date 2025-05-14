Laboratorio 13: Configure las App Protection Policies para dispositivos
móviles

**Resumen**

En este laboratorio, configurará un App protection policy para un
dispositivo móvil.

**Escenario**

Todos los desarrolladores en Contoso tienen iPhones y iPads con las
versiones más recientes de iOS/iPadOS. El departamento de seguridad se
preocupa por la fuga de datos y quiere prevenir la copia de datos del
email empresarial a otras aplicaciones móviles. Tiene que proporcionar
una solución que aborda las precupaciones de seguridad. También tiene
que considerar lo siguiente:

- Se tiene que restringir el backup de los datos de Outlook a iTunes o
  iCloud.

- Solo las aplicaciones gestionadas por políticas pueden mandar o
  recibir datos de Outlook.

- Solo las aplicaciones gestionadas por políticas pueden cortar, copiar
  o pegar cosas del Outlook.

- Los usuarios deben proporcionar sus credenciales de Work or school
  account para el acceso a Outlook.

Tarea 1: Cree un App protection policy para los dispositivos iOS/iPadOS

1.  En [***SEA-SVR1***](urn:gd:lg:a:select-vm), si es necesario, inicie
    sesión
    como [**Contoso\Administrator**](urn:gd:lg:a:send-vm-keys) con la
    contraseña !\![**Pa55w.rd**](urn:gd:lg:a:send-vm-keys)!!

2.  En el taskbar, seleccione **Microsoft Edge** y navegue a **Microsoft
    Intune admin center** !!**https://intune.microsoft.com**!!  en la
    barra de direcciones, y presione **Enter**.

3.  Inicie sesión con las Office 365 Tenant admin credentials desde la
    pestaña Home.

4.  En la página **Microsoft Intune admin center**, seleccione **Apps**.

> ![A screenshot of a computer Description automatically
> generated](./media/image1.png)

5.  En el **Apps | Overview** blade, en **Policy**, seleccione **App
    protection policies**.

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)

6.  En el panel details, seleccione **+Create policy** y
    seleccione **iOS/iPadOS**.

> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)

7.  En la pestaña **Basics**, configure las siguientes opciones y
    seleccione **Next**:

    - Name: !\![**Outlook – Developers**](urn:gd:lg:a:send-vm-keys)!!

    - Description: !\![**Policy to prevent cut/copy and paste from
      Outlook**](urn:gd:lg:a:send-vm-keys)!!

> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

8.  En la pestaña **Apps**, haga clic en + **Select public apps**.

9.  En el **Select apps to target** blade, en el cuadro de texto, tecle
    !!**Outlook**!! Seleccione **Microsoft Outlook** y haga clic en el
    botón **Select**, y luego seleccione **Next**.

> ![Screens screenshot of a computer Description automatically
> generated](./media/image5.png)

10. En la pestaña **Data protection**, configure las siguientes opciones
    y seleccione **Next**:

    - Backup Org data to iTunes and iCloud backups: **Block**

    - Send Org data to other apps: **Policy managed apps**

    - Receive data from other apps: **Policy managed apps**

    - Restrict cut, copy, and paste between other apps: **Policy managed
      apps**

> Deje todo el resto en su estado predeterminado
>
> ![](./media/image6.png)

11. En la pestaña **Access requirements**, configure las siguientes
    opciones y seleccione **Next**:

    - PIN for access: **Not required**

    - Work or school account credentials for access: **Require**

> ![A screenshot of a computer Description automatically
> generated](./media/image7.png)

12. En la pestaña **Conditional launch**, revise las configuraciones.
    Seleccione **Next**.

> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)
>
> **Ojo**: Aquí puede establecer los requisitos de seguridad de sign-in
> para su access protection policy. Puede seleccionar un setting e
> introducir el valor que los usuarios deben cumplir para iniciar sesión
> en la aplicación de su empresa. Tome nota de varias configuraciones
> pero no cambie nada.

13. En la pestaña **Assignments**, seleccione **Next**.

> ![A screenshot of a computer Description automatically
> generated](./media/image9.png)

14. En la pestaña **Review + create**, revise las configuraciones y
    seleccione **Create**.

> ![A screenshot of a computer Description automatically
> generated](./media/image10.png)

15. En el **Apps | App protection policies** blade, en el panel de
    details, verifique si está enlistado el **Outlook - Developers**.

> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)

16. Cierre Microsoft Edge.

**Resultados**: Después de completar este ejercicio, habrá configurado
un App protection policy para un dispositivo móvil.
