Laboratorio 14 – Implemente las aplicaciones mediante Endpoint
Configuration Manager

**Resumen**

En este laboratorio, usará Microsoft Endpoint Configuration Manager para
implementar aplicaciones a desktop client workstations.

**Escenario**

Contoso usa Microsoft Endpoint Configuration Manager para gestionar los
desktop workstations en el entorno local de Active Directory network.
Tiene que implementar una nueva aplicación que se llama Microsoft Power
BI desktop a los Windows 11 Configuration Manager clients. El Endpoint
Configuration Manager administrator ya ha creado el application object
para usted. Sus tareas incluyen la creación de una colección para los
dispositivos finales, distribución del contenido de la aplicación a los
puntos de distribución, y luego crear la implementación asignada a la
colección final. Va a verificar el proceso asegurando que se ve la
aplicación en Software Center en SEA-CL1.

Tarea 1: Cree un device collection

1.  Cambie a [***SEA-CFG1***](urn:gd:lg:a:select-vm), inicie sesión
    como [**Contoso\Administrator**](urn:gd:lg:a:send-vm-keys) con la
    contraseña !\![**Pa55w.rd**](urn:gd:lg:a:send-vm-keys)!!.

2.  En el taskbar, seleccione **Configuration Manager Console**. Se abre
    el Microsoft Endpoint Configuration Manager console.

> ![](./media/image1.png)

3.  En el **Assets and Compliance** workspace, seleccione **Device
    Collections**.

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)

4.  Haga clic derecho en **Device Collections** y seleccione **Create
    Device Collection**. Se abre el Create Device Collection Wizard.

> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)

5.  En la página **General**, configure lo siguiente y luego
    seleccione **Next**:

    - Name: !\![**Power BI App Deployment**](urn:gd:lg:a:send-vm-keys)!!

    - Comment: !\![**Devices targeted to install Power BI
      Desktop**](urn:gd:lg:a:send-vm-keys)!!

    - Limiting collection: **All Windows 11 Workstations**

> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

6.  En la página **Membership Rules**, seleccione **Next**. En la alerta
    de Configuration Manager, seleccione **OK**. Agregará un direct
    member más tarde.

> ![A screenshot of a computer Description automatically
> generated](./media/image5.png)
>
> ![A screenshot of a computer error Description automatically
> generated](./media/image6.png)

7.  En la página **Summary**, seleccione **Next** y en la
    página **Completion**, seleccione **Close**.

> ![A screenshot of a computer Description automatically
> generated](./media/image7.png)
>
> Se ve la **Power BI App Deployment** collection en la lista Device
> Collections.
>
> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)

Tarea 2: Asigne un Device a un Collection existente

1.  En el **Assets and Compliance** workspace, seleccione **Devices**.

> Tome nota de los dispositivos enlistados. Cualquier dispositivo que
> tenga un círculo verde con una marca blanca está activo.
>
> ![](./media/image9.png)

2.  En el panel de details, seleccione **SEA-CL1**.

3.  Haga clic derecho en [***SEA-CL1***](urn:gd:lg:a:select-vm), apunte
    a **Add Selected Items**, y seleccione **Add Selected Items to
    Existing Device Collection**.

> ![](./media/image10.png)

4.  En el cuadro de diálogo **Select Collection**, seleccione **Power BI
    App Deployment**, y luego seleccione **OK**.

> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)

5.  Para verificarlo, en el **Assets and Compliance** workspace,
    seleccione **Device Collections** y haga doble clic en **Power BI
    App Deployment**.

> ![A screenshot of a computer Description automatically
> generated](./media/image12.png)
>
> Se debe enlistar [***SEA-CL1***](urn:gd:lg:a:select-vm) como un
> miembro de la colección.
>
> ![A screenshot of a computer Description automatically
> generated](./media/image13.png)

Tarea 3: Configure un deployment type

1.  En el Microsoft Endpoint Configuration Manager console seleccione
    el **Software Library** workspace.

> ![A screenshot of a software library Description automatically
> generated](./media/image14.png)

2.  En el **Software Library** workspace, expanda **Application
    Management** y luego seleccione **Applications**.

> ![A screenshot of a software library Description automatically
> generated](./media/image15.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image16.png)
>
> Note las aplicaciones que se han creado por Endpoint Configuration
> Manager administrator.

3.  En el panel details, seleccione **Microsoft Power BI Desktop
    (x64)**.

> ![A screenshot of a computer Description automatically
> generated](./media/image17.png)

4.  En el panel de resultados, seleccione la pestaña **Deployment
    Types**. Note que hay un deployment type que se basa en Windows
    Installer.

> ![A screenshot of a computer Description automatically
> generated](./media/image18.png)

5.  Haga clic derecho en **Microsoft Power BI Desktop (x64) - Windows
    installer** deployment type y seleccione **Properties**.

> ![A screenshot of a computer Description automatically
> generated](./media/image19.png)

6.  En el cuadro de diálogo **Properties**, seleccione la
    pestaña **Programs**. Tome nota de cómo se instala la aplicación.
    Usará un msiexec con el /q switch que realiza una instalación
    silenciosa.

> ![](./media/image20.png)

7.  En el cuadro de diálogo **Properties**, seleccione la
    pestaña **Requirements** y luego seleccione **Add**.

> ![A screenshot of a computer Description automatically
> generated](./media/image21.png)

8.  En el cuadro de diálogo **Create Requirement**, configure lo
    siguiente y luego seleccione **OK**:

    - Category: **Device**

    - Condition: **Operating System**

    - Rule type: **Value**

    - Operator: **One of Windows 11 (Seleccione la casilla junto a
      Windows 11)**

> ![A screenshot of a computer program Description automatically
> generated](./media/image22.png)

9.  En el cuadro de diálogo **Properties**, seleccione **OK**. Este
    requisito impedirá la instalación de la aplicación si el dispositivo
    no es de un sistema operativo Windows 11.

> ![A screenshot of a computer Description automatically
> generated](./media/image23.png)

Tarea 4: Distribuya el contenido a los puntos de distribución

1.  En el **Software Library** workspace, seleccione **Microsoft Power
    BI Desktop (x64)**.

2.  Haga clic derecho en **Microsoft Power BI Desktop (x64)** y
    seleccione **Distribute Content**.

> ![A screenshot of a computer Description automatically
> generated](./media/image24.png)

3.  En la página **General**, seleccione **Next**.

> ![A screenshot of a computer Description automatically
> generated](./media/image25.png)

4.  En la página **Content**, seleccione **Next**.

> ![A screenshot of a computer Description automatically
> generated](./media/image26.png)

5.  En la página **Content Destination**, seleccione **Add** y luego
    seleccione **Distribution Point**.

> ![A screenshot of a computer Description automatically
> generated](./media/image27.png)

6.  En el cuadro de diálogo **Add Distribution Points**, seleccione la
    casilla de verificación junto a **SEA-CFG1.CONTOSO.COM**, y
    seleccione **OK**.

> ![A screenshot of a computer Description automatically
> generated](./media/image28.png)

7.  En la página **Content Destination**, seleccione **Next**.

> ![A screenshot of a computer Description automatically
> generated](./media/image29.png)

8.  En la página **Summary**, seleccione **Next** y luego
    seleccione **Close**.

> ![A screenshot of a computer Description automatically
> generated](./media/image30.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image31.png)

9.  En la pestaña **Summary**, seleccione **Content Status**.

> ![A screenshot of a computer Description automatically
> generated](./media/image32.png)
>
> Se abre la página Content Status para Microsoft Power BI Desktop. En
> el panel de resultados, verifique que se ve un círculo verde y que se
> ve Success:1 junto a este círculo. Esto indica que el contenido ahora
> se ha distribuido y que ahora se lo puede implementar a los
> dispositivos. Puede tener que seleccionar el botón de Refresh en el
> ribbon.
>
> ![A screenshot of a computer Description automatically
> generated](./media/image33.png)

10. En la esquina superior izquierda, seleccione el **Back to
    Applications** arrow para volver a Software Library Applications
    node.

Tarea 5: Cree un deployment

1.  En el **Software Library** workspace, seleccione **Microsoft Power
    BI Desktop (x64)**.

2.  Haga clic derecho en **Microsoft Power BI Desktop (x64)** y
    seleccione **Deploy**. Se abre el **Deploy Software Wizard**.

> ![A screenshot of a computer Description automatically
> generated](./media/image34.png)

3.  En la página **General**, junto a **Collection**,
    seleccione **Browse**.

> ![A screenshot of a computer Description automatically
> generated](./media/image35.png)

4.  En la página **Select Collection**, seleccione **User
    Collections** y luego seleccione **Device Collections**.

5.  En la lista **Device Collections**, seleccione **Power BI App
    Deployment** y luego seleccione **OK**.

> ![A screenshot of a computer Description automatically
> generated](./media/image36.png)

6.  En la página **General**, seleccione **Next**.

> ![A screenshot of a computer Description automatically
> generated](./media/image37.png)

7.  En la página **Content**, seleccione **Next**.

> ![A screenshot of a computer Description automatically
> generated](./media/image38.png)

8.  En la página **Deployment Settings**, verifique que se establece
    **Action** a **Install** y el **Purpose** a **Available**.
    Seleccione **Next**.

> ![A screenshot of a computer Description automatically
> generated](./media/image39.png)

9.  En la página **Scheduling**, seleccione **Next**. La aplicación
    estará disponible cuanto antes posible por defecto.

> ![A screenshot of a computer Description automatically
> generated](./media/image40.png)

10. En la página **User Experience**, junto a **User notifications**,
    seleccione **Display in Software Center and show all
    notifications**. Seleccione **Next**.

> ![A screenshot of a computer Description automatically
> generated](./media/image41.png)

11. En la página de **Alerts**, seleccione **Next**.

> ![A screenshot of a computer Description automatically
> generated](./media/image42.png)

12. En la página **Summary**, seleccione **Next** y luego
    seleccione **Close**.

> ![A screenshot of a computer Description automatically
> generated](./media/image43.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image44.png)

13. En el panel de resultados, en la pestaña **Deployments**, verifique
    si se ve el deployment.

> ![A screenshot of a computer Description automatically
> generated](./media/image45.png)

14. Cierre el Microsoft Endpoint Configuration Manager console.

15. Cierre la sesión de [***SEA-CFG1***](urn:gd:lg:a:select-vm).

Tarea 6: Use el Software center para instalar una aplicación
implementada

1.  Cambie a [***SEA-CL1***](urn:gd:lg:a:select-vm), e inicie sesión
    como [**Contoso\Administrator**](urn:gd:lg:a:send-vm-keys) con la
    contraseña !\![**Pa55w.rd**](urn:gd:lg:a:send-vm-keys)!!.

2.  Haga clic en el **Start Menu** e introduzca **Control Panel**.

3.  En los resultados, seleccione **Control Panel**.

> ![A screenshot of a computer Description automatically
> generated](./media/image46.png)

4.  En el **Control panel**, seleccione **System and Security**.

> ![A screenshot of a computer Description automatically
> generated](./media/image47.png)

5.  En **System and Security**, seleccione **Configuration Manager**. Se
    ve los Configuration Manager Properties.

> ![A screenshot of a computer Description automatically
> generated](./media/image48.png)

6.  En el cuadro de diálogo **Configuration Manager Properties**,
    seleccione la pestaña **Actions**.

> ![A screenshot of a computer program Description automatically
> generated](./media/image49.png)

7.  En la pestaña **Actions**, seleccione **Machine Policy Retrieval &
    Evaluation Cycle**, y luego seleccione **Run Now**. En el message
    prompt, seleccione **OK**.

> ![A screenshot of a computer program Description automatically
> generated](./media/image50.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image51.png)

8.  Seleccione **OK** para cerrar **Configuration Manager Properties**,
    y luego cierre el **Control Panel**.

> ![A screenshot of a computer program Description automatically
> generated](./media/image52.png)

9.  En el área de notification, seleccione **New Software is
    Available** y luego seleccione **Open Software Center**. Puede que
    necesite expandir el área de notificación para ver el ícono.

> ![](./media/image53.png)
>
> Si no se abre el Software Center, haga clic en **Start Menu** y baje y
> haga clic en !!**Software Center**!!
>
> ![A screenshot of a computer Description automatically
> generated](./media/image54.png)

10. En el **Software Center**, en la página **Applications**, note la
    nueva aplicación disponible llamada **Microsoft Power BI Desktop
    (x64)**. Esta apliación ahora está disponible en cualquier
    dispositivo miembro de la colección **Power BI App
    Deployment** creada anteriormente.

> ![A screenshot of a computer Description automatically
> generated](./media/image55.png)

11. Seleccione **Microsoft Power BI Desktop (x64)** y luego
    seleccione **Install**.

> ![A screenshot of a computer Description automatically
> generated](./media/image56.png)
>
> ![](./media/image57.png)
>
> Se descarga e instala la aplicación sin la necesidad de una entrada
> del usuario. Se le avisará cuando se completa la instalación
> exitosamente cuando se ve un **Power BI Desktop** shortcut en el
> desktop.
>
> ![A screenshot of a computer Description automatically
> generated](./media/image58.png)

12. Cierre el Software Center.

13. Cierre la sesión de [***SEA-CL1***](urn:gd:lg:a:select-vm).

**Resultados**: Después de completar este ejercicio, habrá usado
Microsoft Endpoint Configuration Manager para implementar aplicaciones a
desktop client workstations.
