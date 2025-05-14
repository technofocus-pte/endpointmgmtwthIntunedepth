# **Lab 19 - Bereitstellen von Windows 11 mit dem Microsoft Deployment Toolkit**

**Zusammenfassung**

In dieser Übung verwenden Sie das Microsoft Deployment Toolkit, um ein
Windows 11-Betriebssystemabbild zu erstellen und bereitzustellen.

**Szenario**

Sie müssen eine neue virtuelle Windows 11-Maschine mit dem Namen SEA-WS4
bereitstellen. Sie entscheiden sich für die Verwendung des Microsoft
Deployment Toolkit, um das Betriebssystem auf einem virtuellen Computer
bereitzustellen, der in Hyper-V erstellt wurde. Sie konfigurieren eine
neue Bereitstellungsfreigabe in MDT und konfigurieren dann die
Tasksequenz, die die Schritte zum Bereitstellen von SEA-WS4 ausführt.

### **Aufgabe 1: Erstellen einer neuen Bereitstellungsfreigabe**

1.  Wechseln Sie zu [**SEA-SVR2**](urn:gd:lg:a:select-vm), melden Sie
    sich an als
    !!**[Contoso\Administrator](urn:gd:lg:a:send-vm-keys)!!** mit dem
    Passwort !!**[Pa55w.rd](urn:gd:lg:a:send-vm-keys)!!** an.

> ![Screenshot](./media/image1.png)

2.  Wählen Sie auf der Taskleiste File Explorer aus**,** und navigieren
    Sie dann zu !!**[E:\Labfiles\ISOs](urn:gd:lg:a:send-vm-keys)!!**

> ![Screenshot](./media/image2.png)

3.  Klicken Sie mit der rechten Maustaste **Win11_21H2_Eval.iso** und
    wählen Sie dann **Mount**. Die ISO-Datei wird als DVD-Laufwerk **D**
    gemountet.

> ![Screenshot](./media/image3.png)
>
> ![Screenshot](./media/image4.png)

4.  Schließen Sie **File Explorer**.

5.  Wählen Sie **Start menu**, erweitern Sie **Microsoft Deployment
    Toolkit**, und wählen Sie dann **Deployment Workbench**.

> ![Screenshot](./media/image5.png)

6.  Im **Deployment Workbench**, klicken Sie mit der rechten Maustaste
    auf **Deployment Shares** und wählen Sie dann **New Deployment
    Share** aus.

> ![Screenshot](./media/image6.png)
>
> Der **New Deployment Share Wizard** öffnet sich.

7.  Auf der Seite **Path**, unter **Deployment share path**, ändern Sie
    den Wert
    in!!**[E:\DeploymentShare](urn:gd:lg:a:send-vm-keys)!!** Und wählen
    Sie dann **Next** aus.

> ![Screenshot](./media/image7.png)

8.  Notieren Sie sich auf der Seite **Share** den **Share Name,** aber
    ändern Sie ihn nicht. Wählen Sie **Next**.

> ![Screenshot](./media/image8.png)

9.  Übernehmen Sie auf der Seite **Descriptive Name** den Standardwert,
    und wählen Sie **Next**.

> ![Screenshot](./media/image9.png)

10. Konfigurieren Sie auf der Seite **Option** folgendes, und wählen Sie
    dann **Next**:

    - Ask to set the local Administrator password: **Enabled**

    - All other check boxes: **Disabled**

> ![Screenshot](./media/image10.png)

11. Überprüfen Sie auf der Seite **Summary** die Informationen, und
    wählen Sie dann **Next**.

> ![Screenshot](./media/image11.png)

12. Stellen Sie auf der Seite **Confirmation** sicher, dass der Vorgang
    erfolgreich abgeschlossen wurde, und wählen Sie dann **Finish**.

> ![Screenshot](./media/image12.png)

13. Unter **Deployment Shares**, erweitern Sie den Ordner **MDT
    Deployment Share**.

> Notieren Sie sich die verschiedenen Knoten, die für die
> Bereitstellungsfreigabe konfiguriert werden können.

### **Aufgabe 2: Hinzufügen von Betriebssystemdateien zur Bereitstellungsfreigabe**

1.  Erweitern Sie in Deployment Workbench, **Deployment Shares**,
    erweitern Sie **MDT Deployment Share**, und wählen Sie dann
    **Operating Systems**.

> ![Screenshot](./media/image13.png)

2.  Klicken Sie mit der rechten Maustaste auf **Operating Systems**, und
    wählen Sie dann **Import Operating System** aus. Der Assistent zum
    Importieren von Betriebssystemen wird geöffnet.

> ![Screenshot](./media/image14.png)

3.  Im **Import Operating System Wizard**, auf der Seite **OS Type**,
    wählen Sie **Full set of source files** und wählen Sie dann **Next**
    aus.

> ![Screenshot](./media/image15.png)

4.  Auf der Seite **Source**, unter **Source Directory**, geben Sie
    !!**[D:\\](urn:gd:lg:a:send-vm-keys)!!**  ein und wählen Sie dann
    **Next** aus.

> ![Screenshot](./media/image16.png)

5.  Auf der Seite **Destination**, ändern Sie den Namen des
    Standardzielverzeichnisses in!!**[Windows 11 Enterprise
    x64](urn:gd:lg:a:send-vm-keys)!!** und wählen Sie dann **Next** aus.

> ![Screenshot](./media/image17.png)

6.  Auf der Seite **Summary**, überprüfen Sie die Informationen, und
    wählen Sie dann **Next**.

> ![Screenshot](./media/image18.png)
>
> Die Quelldateien des Betriebssystems werden in die
> Bereitstellungsfreigabe kopiert.

7.  Auf der Seite **Confirmation**, stellen Sie sicher, dass der Vorgang
    erfolgreich abgeschlossen wurde, und wählen Sie dann **Finish**.

> ![Screenshot](./media/image19.png)

### **Aufgabe 3: Hinzufügen von Anwendungen zur Bereitstellungsfreigabe**

1.  Erweitern Sie in Deployment Workbench, **Deployment Shares**,
    erweitern Sie **MDT Deployment Share**, und wählen Sie dann
    **Application** aus.

2.  Klicken Sie mit der rechten Maustaste auf **Applications** und
    wählen Sie dann **New Application**. Der Assistent für neue
    Anwendungen wird geöffnet.

> ![Screenshot](./media/image20.png)

3.  Im **New Application Wizard**, auf der **Application Type** Seite,
    wählen Sie **Application with source files** und wählen Sie dann
    **Next** aus.

> ![Screenshot](./media/image21.png)

4.  Konfigurieren Sie auf der Seite **Details** Folgendes, und wählen
    Sie dann **Next**:

    - Publisher: !!**[Microsoft](urn:gd:lg:a:send-vm-keys)!!**

    - Application Name: !!**[XML Notepad](urn:gd:lg:a:send-vm-keys)!!**

> ![Screenshot](./media/image22.png)

5.  Auf der **Source** Seite, unter **Source directory**, geben Sie
    !!**[E:\Labfiles\Apps](urn:gd:lg:a:send-vm-keys)!!** Ein und wählen
    Sie dann **Next** aus.

> ![Screenshot](./media/image23.png)

6.  Auf der **Destination** Seite, übernehmen Sie den Standardnamen des
    Zielverzeichnisses, und wählen Sie dann **Next**.

> ![Screenshot](./media/image24.png)

7.  Geben Sie auf der Seite **Command Details** unter **Command**
    **line** !! ein.**[XmlNotepadSetup.msi
    /q](urn:gd:lg:a:send-vm-keys)!!** und wählen Sie dann **Next**
    aus**.**

> ![Screenshot](./media/image25.png)

8.  Überprüfen Sie auf der Seite **Summary** die Informationen, und
    wählen Sie dann **Next**.

> ![Screenshot](./media/image26.png)

9.  Stellen Sie auf der Seite **Confirmation** sicher, dass der Vorgang
    erfolgreich abgeschlossen wurde, und wählen Sie dann **Finish**.

### **Aufgabe 4: Erstellen einer MDT-Tasksequenz**

1.  Erweitern Sie in Deployment Workbench, **Deployment Shares**,
    erweitern Sie **MDT Deployment Share**, und wählen Sie dann **Task
    Sequences** aus.

2.  Klicken Sie mit der rechten Maustaste auf **Task Sequences**, und
    wählen Sie dann **New Task Sequence** aus. Der **New Task Sequence
    Wizard** wird geöffnet.

> ![Screenshot](./media/image27.png)

3.  Konfigurieren Sie auf der Seite **General Settings** folgendes, und
    wählen Sie dann **Next**:

    - Task sequence ID: !!**[001](urn:gd:lg:a:send-vm-keys)!!**

    - Task sequence name: !!**[Deploy Windows 11
      Enterprise](urn:gd:lg:a:send-vm-keys)!!**

> ![Screenshot](./media/image28.png)

4.  Auf der Seite **Select Template**, wählen Sie **Standard Client Task
    Sequence**, und wählen Sie dann **Next**.

> ![Screenshot](./media/image29.png)

5.  Auf der **Select OS** Seite, wählen Sie **Windows 10 Enterprise
    Evaluation** und wählen Sie dann **Next** aus.

> ![Screenshot](./media/image30.png)

6.  Auf der Seite **Specify Product Key**, wählen Sie **Do not specify a
    product key at this time**, und wählen Sie dann **Next**.

> ![Screenshot](./media/image31.png)

7.  Auf der Seite **OS Settings**, konfiguren Sie die untenstehen
    Anweisungen und wählen Sie dann **Next** aus:

    - Full Name: !!**[User](urn:gd:lg:a:send-vm-keys)!!**

    - Organization: !!**[Contoso
      Corporation](urn:gd:lg:a:send-vm-keys)!!**

    - Internet Explorer Home
      Page: !!**[about:blank](urn:gd:lg:a:send-vm-keys)!!**

> ![Screenshot](./media/image32.png)

8.  Auf der Seite **Admin Password**, wählen Sie **Use the specified
    local Administrator password** und geben Sie dann
    !!**[Pa55w.rd](urn:gd:lg:a:send-vm-keys)!!** in beide Boxen ein.
    Wählen Sie dann **Next** aus.

> ![Screenshot](./media/image33.png)

9.  Überprüfen Sie auf der Seite **Summary** die Informationen, und
    wählen Sie dann **Next**.

> ![Screenshot](./media/image34.png)

10. Stellen Sie auf der Seite **Confirmation** sicher, dass der Vorgang
    erfolgreich abgeschlossen wurde, und wählen Sie dann **Finish**.

> ![Screenshot](./media/image35.png)

11. Vergewissern Sie sich, dass in der **Deployment Workbench** bei
    ausgewählten **Task Sequences** die Tasksequenz **Deploy Windows 11
    Enterprise** angezeigt wird.

> ![Screenshot](./media/image36.png)

12. Klicken Sie mit der rechten Maustaste auf die **Deploy Windows 11
    Enterprise**, und wählen Sie dann **Properties**.

> ![Screenshot](./media/image37.png)

13. Wählen Sie die Registerkarte **Task Sequence** aus.

14. Erweitern Sie den Knoten **Validation**, und wählen Sie dann
    **Validate**.

15. Entfernen Sie auf der Seite **Properties** die Häkchen neben
    **Ensure minimum memory** und **Ensure minimum processor speed**.

> Nehmen Sie keine weiteren Änderungen vor.

16. Wählen Sie im Fenster **Deploy Windows 11 Enterprise
    Properties** die Option **OK**.

> ![Screenshot](./media/image38.png)

### **Aufgabe 5: Konfigurieren der Eigenschaften von Bereitstellungsfreigaben und Windows PE-Einstellungen**

1.  Erweitern Sie in Deployment Workbench, **Deployment Shares**, und
    wählen Sie **MDT Deployment Share**.

2.  Klicken Sie mit der rechten Maustaste auf **MDT Deployment
    Share** und wählen Sie dann **Properties**.

> ![Screenshot](./media/image39.png)

3.  Notieren Sie sich im Fenster **MDT Deployment Share Properties** auf
    der Registerkarte **General** die Informationen, die beim Erstellen
    der Bereitstellungsfreigabe bereitgestellt wurden.

> ![Screenshot](./media/image40.png)

4.  Wählen Sie die Registerkarte Rules aus.

> Auf der Registerkarte Rules wird der Inhalt der CustomSettings.ini
> Datei angezeigt. Diese Werte wurden auch während der Erstellung der
> Bereitstellungsfreigabe angegeben.
>
> ![Screenshot](./media/image41.png)

5.  Wählen Sie die **Registerkarte** Windows PE aus.

> Die Registerkarte Windows PE enthält Optionen zum Erstellen einer
> Windows PE-Startdiskette.

6.  Wählen Sie auf der Registerkarte **Windows PE** neben **Plattform**
    die Option **x64**.

7.  Wählen Sie im Abschnitt **Windows PE-Anpassungen** neben **Scratch
    space size** die Option **64**.

> ![Screenshot](./media/image42.png)

8.  Wählen Sie die Registerkarte **Features** und dann das
    Kontrollkästchen neben den folgenden Feature Packs aus:

    - DISM Cmdlets

    - Windows PowerShell

    - Microsoft Data Access Components (MDAC/ADO) support

> ![Screenshot](./media/image43.png)
>
> ![Screenshot](./media/image44.png)

9.  Wählen Sie die Registerkarte **Monitoring** aus.

10. Aktivieren Sie auf der Registerkarte **Monitoring** das
    Kontrollkästchen neben **Enable monitoring for this deployment
    share**.

11. Im **MDT Deployment Share Properties** Fenster, wählen Sie **OK**.

> ![Screenshot](./media/image45.png)

12. Klicken Sie mit der rechten Maustaste **MDT Deployment Share** und
    wählen Sie dann **Update Deployment Share**. Der Assistent zum
    Aktualisieren von Bereitstellungsfreigaben wird geöffnet.

> ![Screenshot](./media/image46.png)

13. Auf der Seite **Options**, wählen Sie **Optimize the boot image
    updating process** und wählen Sie dann **Next** aus.

> ![Screenshot](./media/image47.png)

14. Auf der Seite **Summary,** wählen Sie **Next**.

> ![Screenshot](./media/image48.png)
>
> Die Bereitstellungsfreigabe beginnt mit der Aktualisierung und
> Erstellung der Windows PE-Dateien. Dies dauert einige Minuten.

15. Stellen Sie auf der Seite **Confirmation** sicher, dass der Vorgang
    erfolgreich abgeschlossen wurde, und wählen Sie dann **Finish**.

> ![Screenshot](./media/image49.png)

### **Aufgabe 6: Bereitstellen von Windows 11 mithilfe von MDT**

1.  Wählen Sie auf [**SEA-SVR2**](urn:gd:lg:a:select-vm) in der
    Taskleiste **Hyper-V Manager**.

> ![Screenshot](./media/image50.png)

2.  Wählen Sie im Hyper-V-Manager **Virtual Switch Manager**.

> ![Screenshot](./media/image51.png)

3.  Wählen Sie in der Liste **External** aus und klicken Sie dann auf
    **Create Virtual Switch**.

> ![Screenshot](./media/image52.png)

4.  Auf der Seite **Virtual Switch Properties**, unter Namen, geben Sie
    [**External network**](urn:gd:lg:a:send-vm-keys), wählen Sie dann
    **OK**, und wählen Sie dann **Yes**.

> ![Screenshot](./media/image53.png)
>
> ![Screenshot](./media/image54.png)

5.  Wählen Sie im Hyper-V-Manager **SEA-SVR2** aus**,** und wählen Sie
    dann im Bereich Aktionen die Option **New** und dann **Virtual
    Machine**.

> ![Screenshot](./media/image55.png)

6.  Auf der Seite **Before you Begin**, wählen Sie **Next**.

> ![Screenshot](./media/image56.png)

7.  Auf der Seite **Specify Name and Location**, geben Sie im Feld
    **Name**!!**[SEA-WS4](urn:gd:lg:a:send-vm-keys)!!** ein.

8.  Aktivieren Sie das Kontrollkästchen neben **Store the virtual
    machine in a different location** und wählen Sie dann
    **Location** geben Sie
    !!**[E:\Labfiles\VirtualMachines](urn:gd:lg:a:send-vm-keys)!!** ein.
    Wählen Sie dann **Next** aus.

> ![Screenshot](./media/image57.png)

9.  Auf der Seite **Specify Generation**, stellen Sie sicher das
    **Generation 2** ausgewählt ist und wählen Sie dann **Next** aus.

> ![Screenshot](./media/image58.png)

10. Auf der Seite **Assign Memory**, neben **Startup memory** geben Sie
    !!**[8192](urn:gd:lg:a:send-vm-keys)!!** ein und wählen Sie dann
    **Next**.

> ![Screenshot](./media/image59.png)

11. Auf der Seite **Configure Networking**, neben **Connection**, wählen
    Sie **External Network** und dann wählen Sie **Next** aus**.**

> ![Screenshot](./media/image60.png)

12. Auf der Seite **Connect Virtual Hard Disk**, wählen Sie **Create a
    virtual hard disk** und geben Sie Folgendes ein und klicken Sie dann
    auf **Next**:

    - Name: !!**[SEA-WS4.vhdx](urn:gd:lg:a:send-vm-keys)!!**

    - Location: !!**[E:\Labfiles\VirtualMachines](urn:gd:lg:a:send-vm-keys)!!**

    - Size: !!**[60](urn:gd:lg:a:send-vm-keys)!!**

> ![Screenshot](./media/image61.png)

13. Auf der Seite **Installation Options**, wählen Sie **Install an
    operating system from a bootable image file** und konfigurieren Sie
    Folgendes:

    - Image file
      (.iso): !!**[E:\DeploymentShare\Boot\LiteTouchPE_x64.iso](urn:gd:lg:a:send-vm-keys)!!**

> ![Screenshot](./media/image62.png)

14. Wählen Sie **Next** und wählen Sie dann **Finish**.

> ![Screenshot](./media/image63.png)

15. Klicken Sie im Hyper-V-Manager mit der rechten Maustaste auf
    **SEA-WS4**, und wählen Sie dann **Settings**.

> ![Screenshot](./media/image64.png)

16. Wählen Sie **Security** aus, und aktivieren Sie dann das
    Kontrollkästchen neben **Enable Trusted Platform Module**.

> ![Screenshot](./media/image65.png)

17. Wählen Sie **Processor** aus, und ändern Sie dann die Anzahl der
    virtuellen Prozessoren in !!**[2](urn:gd:lg:a:send-vm-keys)!!**.

18. Wählen Sie **OK** aus, um das Dialogfeld Einstellungen zu schließen.

> ![Screenshot](./media/image66.png)

19. Wählen Sie im Hyper-V-Manager **SEA-WS4 aus**, wählen Sie
    **Connect** aus, und wählen Sie dann **Start**.

> ![Screenshot](./media/image67.png)
>
> ![Screenshot](./media/image68.png)

20. Drücken Sie beim Starten des Computers eine beliebige Taste auf der
    Tastatur, um den MDT-Bereitstellungs-Assistenten aufzurufen.
    Maximieren Sie das Fenster nach Bedarf.

> ![Screenshot](./media/image69.png)

21. Auf der **Welcome** Seite, wählen Sie **Run the Deployment Wizard to
    install a new Operating System** aus.

> ![Screenshot](./media/image70.png)

22. Im Fenster **Specify credentials for connecting to network shares**,
    geben Sie Folgendes ein und wählen Sie dann **OK**:

    - User Name: !!**[Administrator](urn:gd:lg:a:send-vm-keys)!!**

    - Password: !!**[Pa55w.rd](urn:gd:lg:a:send-vm-keys)!!**

    - Domain: !!**[Contoso](urn:gd:lg:a:send-vm-keys)!!**

> ![Screenshot](./media/image71.png)

23. Auf der Seite **Task Sequence**, wählen Sie **Deploy Windows 11
    Enterprise** und wählen Sie dann **Next**.

> ![Screenshot](./media/image72.png)

24. Auf der **Computer Details** Seite, neben **Computer name** geben
    Sie !!**[SEA-WS4](urn:gd:lg:a:send-vm-keys)!!** ein und wählen Sie
    **Next**.

> ![Screenshot](./media/image73.png)

25. Auf der Seite **Move Data and Settings**, wählen Sie **Next** aus.

> ![Screenshot](./media/image74.png)

26. Auf der Seite **User Data (Restore)**, wählen Sie **Next** aus.

> ![Screenshot](./media/image75.png)

27. Auf der Seite **Locale and Time**, wählen Sie **Next** aus.

> ![Screenshot](./media/image76.png)

28. Auf der Seite **Applications**, wählen Sie **Next** aus.

> ![Screenshot](./media/image77.png)

29. Auf der Seite **Administrator Password**, geben
    Sie!!**[Pa55w.rd](urn:gd:lg:a:send-vm-keys)!!** in beiden
    Textfeldern ein und wählen Sie dann **Next**.

> ![Screenshot](./media/image78.png)

30. Auf der Seite **Ready**, wählen Sie **Begin** aus.

> ![Screenshot](./media/image79.png)
>
> Die Installation beginnt. Es wird einige Zeit dauern, bis der Vorgang
> abgeschlossen ist, und **SEA-WS4** wird während der Installation bei
> Bedarf neu gestartet.

31. Wechseln Sie zu **Deployment Workbench**.

32. Erweitern Sie in Deployment Workbench, **Deployment Shares**, und
    erweitern Sie **MDT Deployment Share**.

33. Wählen Sie **Monitoring** aus und doppelklicken Sie dann im
    Detailbereich auf **SEA-WS4**.

> ![Screenshot](./media/image80.png)
>
> Überprüfen des Überwachungsstatus während der Bereitstellung.
>
> ![A screenshot of a computer Description automatically
> generated](./media/image81.png)

34. Wechseln Sie zu **SEA-WS4**.

35. Nachdem die Installation abgeschlossen ist, wird der Desktop
    geöffnet und die Bereitstellung abgeschlossen. Wählen Sie in der
    Bereitstellungszusammenfassung **Finish**.

> ![Screenshot](./media/image82.png)

36. Fahren Sie **SEA-WS4** herunter und schließen Sie das Fenster
    Virtual Machine Connection.

> ![Screenshot](./media/image83.png)

37. Klicken Sie im Hyper-V-Manager mit der rechten Maustaste auf
    **SEA-WS4**, und wählen Sie dann **Settings**.

> ![Screenshot](./media/image84.png)

38. Im **Settings for SEA-WS4**, erweitern Sie **SCSI Controller** und
    wählen Sie dann **DVD Drive**.

39. Wählen Sie im Detailbereich unter **Media** die Option **None** aus,
    und wählen Sie dann **OK**.

> ![Screenshot](./media/image85.png)

40. Klicken Sie mit der rechten Maustaste auf **SEA-WS4**, und wählen
    Sie dann **Checkpoint** aus, um einen Prüfpunkt mit dem aktuellen
    Status von SEA-WS4 zu erstellen.

> ![Screenshot](./media/image86.png)
>
> ![Screenshot](./media/image87.png)

41. Schließen Sie [auf](urn:gd:lg:a:select-vm) **SEA-SVR2** den
    **Hyper-V-Manager,** und schließen Sie dann **Deployment
    Workbench**.

42. Öffnen Sie den **File Explorer**, klicken Sie mit der rechten
    Maustaste auf **DVD Drive D** und wählen Sie dann **Eject**.

> ![Screenshot](./media/image88.png)
>
> ![Screenshot](./media/image89.png)

43. Schließen Sie **File Explorer** und melden Sie sich bei **SEA-SVR2**
    ab.

**Ergebnisse**: Nach Abschluss dieser Übung haben Sie das Microsoft
Deployment Toolkit erfolgreich verwendet, um eine Windows
11-Arbeitsstation zu erstellen und bereitzustellen.
