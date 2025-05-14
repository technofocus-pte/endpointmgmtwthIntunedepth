Lab14 - Bereitstellen von Apps mit Endpoint Configuration Manager

**Zusammenfassung**

In dieser Übung verwenden Sie Microsoft Endpoint Configuration Manager,
um Anwendungen auf Desktopclientarbeitsstationen bereitzustellen.

**Szenario**

Contoso verwendet Microsoft Endpoint Configuration Manager zum Verwalten
von Desktoparbeitsstationen in der lokalen Active
Directory-Netzwerkumgebung. Sie müssen eine neue Anwendung mit dem Namen
Microsoft Power BI-Desktop für die Windows 11 Configuration
Manager-Clients bereitstellen. Der Endpoint Configuration
Manager-Administrator hat das Anwendungsobjekt bereits für Sie erstellt.
Zu den Aufgaben gehören das Erstellen einer Sammlung für die Zielgeräte,
das Verteilen des Anwendungsinhalts an Verteilungspunkte und das
anschließende Erstellen der Bereitstellung, die der Zielsammlung
zugewiesen ist. Sie verifizieren den Prozess, indem Sie sicherstellen,
dass die Anwendung im Software Center auf SEA-CL1 angezeigt wird.

Aufgabe 1: Erstellen einer Gerätesammlung

1.  Wechseln Sie zu [***SEA-CFG1***](urn:gd:lg:a:select-vm), melden Sie
    sich als [**Contoso\Administrator**](urn:gd:lg:a:send-vm-keys) mit
    dem Kennwort !\![**Pa55w.rd**](urn:gd:lg:a:send-vm-keys)!!an.

2.  Wählen Sie in der Taskleiste **Configuration Manager Console**. Die
    Microsoft Endpoint Configuration Manager-Konsole wird geöffnet.

> ![](./media/image1.png)

3.  Im Workspace **Assets and Compliance**, wählen Sie **Device
    Collections** aus.

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)

4.  Klicken Sie mit der rechten Maustaste auf **Device Collections** und
    wählen Sie dann **Create Device Collection**. Der Assistent zum
    Erstellen von Gerätesammlungen wird geöffnet.

> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)

5.  Auf der Seite **General**, konfigurieren Sie Folgendes, und wählen
    Sie dann **Next**:

    - Name: !\![**Power BI App Deployment**](urn:gd:lg:a:send-vm-keys)!!

    - Comment: !\![**Devices targeted to install Power BI
      Desktop**](urn:gd:lg:a:send-vm-keys)!!

    - Limiting collection: **All Windows 11 Workstations**

> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

6.  Wählen Sie auf der Seite **Membership Rules** die Option **Next**.
    Wählen Sie in der Configuration Manager-Warnung die Option **OK**
    aus. Sie werden in einem späteren Schritt ein direktes Mitglied
    hinzufügen.

> ![A screenshot of a computer Description automatically
> generated](./media/image5.png)
>
> ![A screenshot of a computer error Description automatically
> generated](./media/image6.png)

7.  Wählen Sie auf der Seite **Summary** die Option **Next** und dann
    auf der Seite **Completion** aus **Close**.

> ![A screenshot of a computer Description automatically
> generated](./media/image7.png)
>
> Die Sammlung **Power BI-App-Bereitstellung** wird in der Liste Device
> collection angezeigt.
>
> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)

Aufgabe 2: Zuweisen eines Geräts zu einer vorhandenen Sammlung

1.  Im Workspace **Assets and Compliance**, wählen Sie **Devices** aus.

> Notieren Sie sich die aufgelisteten Geräte. Alle Geräte, die einen
> grünen Kreis mit einem weißen Häkchen haben, sind derzeit aktiv.
>
> ![](./media/image9.png)

2.  Wählen Sie im Detailbereich**SEA-CL1**.

3.  Klicken Sie mit der rechten Maustaste auf
    [***SEA-CL1***](urn:gd:lg:a:select-vm), zeigen Sie auf **Add
    Selected Items**, und wählen Sie dann **Add Selected Items to
    Existing Device Collection** aus.

> ![](./media/image10.png)

4.  In der Dialogbox **Select Collection**, wählen Sie **Power BI App
    Deployment**, und wählen Sie dann **OK**.

> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)

5.  Wählen Sie zur Überprüfung im Workspace **Assets and
    Compliance** die Option **Device Collections** aus**,** und
    doppelklicken Sie dann auf **Power BI App Deployment**.

> ![A screenshot of a computer Description automatically
> generated](./media/image12.png)
>
> [***SEA-CL1***](urn:gd:lg:a:select-vm) sollte als Mitglied dieser
> Sammlung aufgeführt sein.
>
> ![A screenshot of a computer Description automatically
> generated](./media/image13.png)

Aufgabe 3: Konfigurieren eines Bereitstellungstyps

1.  Wählen Sie in der Microsoft Endpoint Configuration Manager-Konsole
    den Workspace **Software Library** aus.

> ![A screenshot of a software library Description automatically
> generated](./media/image14.png)

2.  Im Workspace **Software Library**, erweitern Sie **Application
    Management** und wählen dann **Applications** aus.

> ![A screenshot of a software library Description automatically
> generated](./media/image15.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image16.png)
>
> Beachten Sie die Anwendungen, die vom Endpoint Configuration
> Manager-Administrator erstellt wurden.

3.  Wählen Sie im Detailbereich **Microsoft Power BI Desktop (x64)**
    aus.

> ![A screenshot of a computer Description automatically
> generated](./media/image17.png)

4.  Wählen Sie im Ergebnisbereich die Registerkarte **Deployment Types**
    aus. Beachten Sie, dass es einen Bereitstellungstyp gibt, der auf
    Windows Installer basiert.

> ![A screenshot of a computer Description automatically
> generated](./media/image18.png)

5.  Klicken Sie mit der rechten Maustaste auf das Symbol **Microsoft
    Power BI Desktop (x64) - Windows installer** Bereitstellungstyp, und
    wählen Sie dann **Properties**.

> ![A screenshot of a computer Description automatically
> generated](./media/image19.png)

6.  Wählen Sie im Dialogfeld **Properties** die Registerkarte
    **Programs** aus. Notieren Sie sich, wie die Anwendung installiert
    wird. Es wird msiexec mit dem Schalter /q verwendet, der eine stille
    Installation durchführt.

> ![](./media/image20.png)

7.  Wählen Sie im Dialogfeld **Properties** die Registerkarte
    **Requirements** aus, und wählen Sie dann **Add**.

> ![A screenshot of a computer Description automatically
> generated](./media/image21.png)

8.  Konfigurieren Sie im Dialogfeld **Create Requirement** folgendes,
    und wählen Sie dann **OK**:

    - Category: **Device**

    - Condition: **Operating System**

    - Rule type: **Value**

    - Operator: **One of Windows 11 (Select the check box next to
      Windows 11)**

> ![A screenshot of a computer program Description automatically
> generated](./media/image22.png)

9.  Wählen Sie im Dialogfeld **Properties** die Option **OK** aus. Diese
    Anforderung verhindert, dass die App auf einem anderen
    Betriebssystem als Windows 11 installiert wird.

> ![A screenshot of a computer Description automatically
> generated](./media/image23.png)

Aufgabe 4: Verteilen von Inhalten an Verteilungspunkte

1.  Wählen Sie im Workspace **Software Library** die Option Microsoft
    Power BI Desktop (x64**)** aus.

2.  Klicken Sie mit der rechten Maustaste auf **Microsoft Power BI
    Desktop (x64)** und wählen Sie dann **Distribute Content** aus.

> ![A screenshot of a computer Description automatically
> generated](./media/image24.png)

3.  Auf der Seite **General**, wählen Sie **Next** aus.

> ![A screenshot of a computer Description automatically
> generated](./media/image25.png)

4.  Auf der **Content** Seite, wählen Sie **Next** aus.

> ![A screenshot of a computer Description automatically
> generated](./media/image26.png)

5.  Auf der **Content Destination** Seite, wählen Sie **Add** und wählen
    Sie dann **Distribution Point** aus.

> ![A screenshot of a computer Description automatically
> generated](./media/image27.png)

6.  In der Dialogbox **Add Distribution Points**, aktivieren Sie das
    Kontrollkästchen neben **SEA-CFG1.CONTOSO.COM**, und wählen Sie dann
    **OK**.

> ![A screenshot of a computer Description automatically
> generated](./media/image28.png)

7.  Auf der **Content Destination** Seite, wählen Sie **Next**.

> ![A screenshot of a computer Description automatically
> generated](./media/image29.png)

8.  Auf der **Summary** Seite, wählen Sie **Next** aus und wählen dann
    **Close**.

> ![A screenshot of a computer Description automatically
> generated](./media/image30.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image31.png)

9.  Wählen Sie auf der Registerkarte **Summary** \> **Content Status**
    aus.

> ![A screenshot of a computer Description automatically
> generated](./media/image32.png)
>
> Die Seite Inhaltsstatus wird für Microsoft Power BI Desktop geöffnet.
> Vergewissern Sie sich, dass im Ergebnisbereich ein grüner Kreis
> angezeigt wird und dass Success:1 neben dem Kreis angezeigt wird. Dies
> bedeutet, dass der Inhalt jetzt an die Verteilungspunkte verteilt ist
> und nun auf Geräten bereitgestellt werden kann. Möglicherweise müssen
> Sie im Menüband die Schaltfläche Refresh auswählen.
>
> ![A screenshot of a computer Description automatically
> generated](./media/image33.png)

10. Wählen Sie in der oberen linken Ecke den Pfeil **Back to
    Applications** aus, um zum Knoten Softwarebibliotheksanwendungen
    zurückzukehren.

Aufgabe 5: Erstellen einer Bereitstellung

1.  Wählen Sie im Workspace **Software Library** die Option **Microsoft
    Power BI Desktop (x64)**.

2.  Klicken Sie mit der rechten Maustaste auf **Microsoft Power BI
    Desktop (x64)** und wählen Sie dann **Deploy** aus. **Deploy
    Software Wizard** öffnet sich.

> ![A screenshot of a computer Description automatically
> generated](./media/image34.png)

3.  Auf der Seite **General**, neben **Collection**, wählen Sie
    **Browse** aus.

> ![A screenshot of a computer Description automatically
> generated](./media/image35.png)

4.  Auf der Seite **Select Collection**, wählen Sie **User
    Collections** und wählen Sie dann **Device Collections**.

5.  Wählen Sie in der Liste **Device Collections** die Option **Power
    BI-App Deployment** aus**,** und wählen Sie dann **OK**.

> ![A screenshot of a computer Description automatically
> generated](./media/image36.png)

6.  Auf der Seite **General**, wählen Sie **Next** aus.

> ![A screenshot of a computer Description automatically
> generated](./media/image37.png)

7.  Auf der Seite **Content**, wählen Sie **Next** aus.

> ![A screenshot of a computer Description automatically
> generated](./media/image38.png)

8.  Auf der Seite **Deployment Settings**, stellen Sie sicher, dass die
    **Action** auf **Install** festgelegt ist und der **Purpose** auf
    **Available** festgelegt ist. Wählen Sie **Next** aus.

> ![A screenshot of a computer Description automatically
> generated](./media/image39.png)

9.  Auf der Seite **Scheduling**, wählen Sie **Next** aus. Die Anwendung
    wird standardmäßig so schnell wie möglich verfügbar sein.

> ![A screenshot of a computer Description automatically
> generated](./media/image40.png)

10. Auf der Seite **User Experience**, neben **User notifications**,
    wählen Sie **Display in Software Center and show all notifications**
    aus. Wählen Sie dann **Next** aus.

> ![A screenshot of a computer Description automatically
> generated](./media/image41.png)

11. Auf der Seite **Alerts**, wählen Sie **Next** aus.

> ![A screenshot of a computer Description automatically
> generated](./media/image42.png)

12. Auf der Seite **Summary**, wählen Sie **Next** und wählen Sie dann
    **Close** aus.

> ![A screenshot of a computer Description automatically
> generated](./media/image43.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image44.png)

13. Überprüfen Sie im Ergebnisbereich auf der Registerkarte
    **Deployments,** ob die Bereitstellung angezeigt wird.

> ![A screenshot of a computer Description automatically
> generated](./media/image45.png)

14. Schließen Sie die Microsoft Endpoint Configuration Manager-Konsole.

15. Melden Sie sich von [***SEA-CFG1***](urn:gd:lg:a:select-vm) ab.

Aufgabe 6: Verwenden des Softwarecenters zum Installieren einer
bereitgestellten App

1.  Wechseln Sie zu [***SEA-CL1***](urn:gd:lg:a:select-vm), und melden
    Sie sich als [**Contoso\Administrator**](urn:gd:lg:a:send-vm-keys)
    mit dem Kennwort !\![**Pa55w.rd**](urn:gd:lg:a:send-vm-keys)!! an.

2.  Klicken Sie auf das **Start Menu** und geben Sie dann **Control
    Panel**.

3.  Wählen Sie in den Ergebnissen **Control Panel**.

> ![A screenshot of a computer Description automatically
> generated](./media/image46.png)

4.  Im **Control panel**, wählen Sie **System and Security** aus.

> ![A screenshot of a computer Description automatically
> generated](./media/image47.png)

5.  In **System and Security**, wählen Sie **Configuration Manager**.
    Configuration Manager-Eigenschaften werden angezeigt.

> ![A screenshot of a computer Description automatically
> generated](./media/image48.png)

6.  In der Dialogbox **Configuration Manager Properties**, wählen Sie
    die Schaltfläche **Actions**.

> ![A screenshot of a computer program Description automatically
> generated](./media/image49.png)

7.  Wählen Sie auf der Registerkarte **Actions** die Option **Machine
    Policy Retrieval & Evaluation Cycle** aus, und wählen Sie dann **Run
    Now** aus. Wählen Sie an der Eingabeaufforderung **OK**.

> ![A screenshot of a computer program Description automatically
> generated](./media/image50.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image51.png)

8.  Wählen Sie **OK** aus, um die **Configuration Manager Properties**
    zu schließen, und schließen Sie dann **Control Panel**.

> ![A screenshot of a computer program Description automatically
> generated](./media/image52.png)

9.  Wählen Sie im Infobereich **New Software is Available** und dann
    **Open Software Center** aus. Möglicherweise müssen Sie den Pfeil im
    Infobereich erweitern, um das Symbol anzuzeigen.

> ![](./media/image53.png)
>
> Wenn das Software Center nicht gestartet wird, klicken Sie auf das
> **Start Menu,** scrollen Sie nach unten und klicken Sie auf
> !!**Software Center**!!
>
> ![A screenshot of a computer Description automatically
> generated](./media/image54.png)

10. Beachten Sie im **Software Center** auf der Seite **Applications**
    die neue verfügbare Anwendung mit dem Namen **Microsoft Power BI
    Desktop (x64)**. Diese Anwendung ist jetzt für jedes Gerät
    verfügbar, das Mitglied der **Power BI App Deployment** Sammlung
    ist, die zuvor erstellt wurde.

> ![A screenshot of a computer Description automatically
> generated](./media/image55.png)

11. Wählen Sie **Microsoft Power BI Desktop (x64)** und wählen Sie dann
    **Install** aus.

> ![A screenshot of a computer Description automatically
> generated](./media/image56.png)
>
> ![](./media/image57.png)
>
> Die Anwendung wird ohne Benutzereingabe heruntergeladen und
> installiert. Sie wissen, dass die Installation erfolgreich war, wenn
> die **Power BI Desktop-Verknüpfung** auf dem Desktop angezeigt wird.
>
> ![A screenshot of a computer Description automatically
> generated](./media/image58.png)

12. Schließen Sie das Software-Center.

13. Melden Sie sich von [***SEA-CL1***](urn:gd:lg:a:select-vm) ab.

**Ergebnisse**: Nach Abschluss dieser Übung haben Sie Microsoft Endpoint
Configuration Manager erfolgreich verwendet, um Anwendungen auf
Desktopclientarbeitsstationen bereitzustellen.
