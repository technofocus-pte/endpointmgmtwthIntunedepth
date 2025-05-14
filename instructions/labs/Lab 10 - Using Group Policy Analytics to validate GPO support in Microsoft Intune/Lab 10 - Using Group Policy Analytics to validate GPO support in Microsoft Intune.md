**Laboratorio 10 – Usar Group Policy Analytics para validar el GPO
support en Microsoft Intune**

**Resumen**

En este laboratorio, va a usar Group Policy Analytics para importar un
Active Directory Group Policy Object (GPO) e identificar las
configuraciones que admiten políticas de Microsoft Intune MDM
equivalente.

**Escenario**

Contoso anteriormente ha usado Active Directory GPOs para implementar
configuraciones de computer y user policy a lo largo del domain.
Pretende over todas las configuraciones GPO admitidas a Microsoft Intune
configuration profiles. Tiene un GPO llamado **Windows Client Policy**.
Tiene que usar Group Policy Analytics para validar las configuraciones
en Windows Client Policy GPO e identificar cuáles configuraciones se
pueden migrar exitosamente en Intune.

**Tarea 1: Exporte el Windows Client Policy GPO a un archivo XML**

1.  Inicie sesión en  con las credenciales propocionadas, y en la barra
    Search tecle !!**Server Manager**!! y luego selecciónelo.

> ![](./media/image1.png)

2.  En **Server Manager - Dashboard**, seleccione **Tools** y luego
    seleccione **Group Policy Management**.

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)

3.  En el Group Policy Management console,
    expanda **Forest:Contoso.com**, luego **Domains**, luego
    **Contoso.com**, y, a continuación, seleccione **Group Policy
    Objects**.

> Verifique que hay varios Group Policy Objects enumerados.

4.  En el panel details, seleccione el **Windows Client Policy** GPO.

> ![](./media/image3.png)

5.  Haga clic en **Windows Client Policy** y seleccione **Save Report**.

> ![](./media/image4.png)

6.  En el cuadro de diálogo Save GPO Report, seleccione **Documents**,
    cambie el **Save as type** a **XML file**, y luego
    seleccione **Save**.

> ![](./media/image5.png)

7.  Cierre el Group Policy Management console.

8.  Cierre el Server Manager.

**Tarea 2: Analice el Windows Client GPO con Group Policy Analytics**

1.  Abra Microsoft Edge, tecle !!**https://intune.microsoft.com**!! en
    la barra de direcciones, y luego seleccione **Enter**.

2.  Inicie sesión con las Office 365 Tenant credentials si le pide.

3.  En el **Microsoft Intune admin center**, navegue y
    seleccione **Devices**.

> ![](./media/image6.png)

4.  Navegue a la sección **Manage devices** y seleccione **Group Policy
    analytics**.

> ![](./media/image7.png)

5.  En el **Devices | Group Policy analytics** blade,
    seleccione **Import**.

> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)

6.  En la pestaña **GPO file upload**, haga clic en el folder junto a la
    barra de búsqueda **Select a file** como se ve en la siguiente
    imagen.

> ![A screenshot of a computer Description automatically
> generated](./media/image9.png)

7.  En el cuadro **Open**, seleccione **Documents** y luego
    seleccione **Windows Client Policy.xml**. a continuación, haga clic
    en **Open**.

> ![A screenshot of a computer Description automatically
> generated](./media/image10.png)

8.  Haga clic en el botón **Next**.

> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)

9.  En el **Scope tags**, haga clic en el botón **Next**.

> ![A screenshot of a computer Description automatically
> generated](./media/image12.png)

10. En la pestaña **Review + create**, haga clic en el botón **Create**.

> ![A screenshot of a computer Description automatically
> generated](./media/image13.png)

11. Se importa y se analiza el Windows Client Policy GPO de forma
    inmediata. Cierre la página **Import GPO files**.

12. En el **Devices | Group Policy analytics** blade, revise la
    información junto a **Windows Client Policy**.

> Note que 89% de las configuraciones tienen el MDM support.
>
> ![A screenshot of a computer Description automatically
> generated](./media/image14.png)

13. En MDM Support, seleccione **89%**.

> Note cada **Setting Name**, **MDM Support**, **CSP Name**, y el **CSP
> Mapping** para cada configuración admitida. Tome nota de las
> configuraciones que no tienen un CSP mapping equivalente.
>
> ![A screenshot of a computer Description automatically
> generated](./media/image15.png)

14. Cierre la ventana **Windows Client Policy**.

**Tarea 3: Revise el Group Policy Analytics Summary Report**

1.  En el menú de navegación **Microsoft Intune admin center**,
    seleccione **Reports**.

> ![](./media/image16.png)

2.  En la página **Reports**, en la sección **Device management**,
    seleccione **Group Policy analytics**.

> ![](./media/image17.png)

3.  En el panel details, en **Summary**, seleccione **Refresh**. Puede
    que tenga que actualizar la página un par de veces.

> Puede tardar unos 5-10 minutos para actualizar y construir un summary
> report.

4.  Revise la información de **Group policy migration readiness**.

> ![A screenshot of a computer Description automatically
> generated](./media/image18.png)
>
> Debe haber unas políticas listas para la migración y unas no
> admitidas.

5.  Seleccione la pestaña **Reports**, y luego seleccione **Group policy
    migration readiness**.

> ![A screenshot of a group policy migration Description automatically
> generated](./media/image19.png)

6.  Seleccione **Generate report**.

> ![A screenshot of a computer Description automatically
> generated](./media/image20.png)

7.  El Group policy migration readiness report proporciona información
    relacionada con cada configuración, y el Profile Type admitido.

> ![A screenshot of a computer Description automatically
> generated](./media/image21.png)

8.  Cierre la ventana **Group policy migration readiness**.

**Resultados**: después de completar este ejercicio, habrá exportado un
GPO exitosamente y usado un Group Policy Analytics para valiar policy
settings equivalentes en Intune.
