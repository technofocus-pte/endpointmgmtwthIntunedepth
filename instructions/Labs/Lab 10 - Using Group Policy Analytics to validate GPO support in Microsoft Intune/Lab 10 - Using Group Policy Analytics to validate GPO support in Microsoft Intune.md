**Lab 10 - Verwenden der Gruppenrichtlinienanalyse zum Überprüfen der
GPO-Unterstützung in Microsoft Intune**

**Zusammenfassung**

In dieser Übung verwenden Sie die Gruppenrichtlinienanalyse, um ein
Active Directory-Gruppenrichtlinienobjekt (Group Policy Object, GPO) zu
importieren und Einstellungen zu identifizieren, die die entsprechende
Microsoft Intune MDM-Richtlinie unterstützen.

**Szenario**

Contoso hat traditionell Active Directory-Gruppenrichtlinienobjekte
verwendet, um Computer- und Benutzerrichtlinieneinstellungen in der
gesamten Domäne bereitzustellen. Sie planen, alle unterstützten
GPO-Einstellungen in Microsoft Intune-Konfigurationsprofile zu
verschieben. Sie verfügen über ein Gruppenrichtlinienobjekt mit dem
Namen **Windows-Clientrichtlinie**. Sie müssen die
Gruppenrichtlinienanalyse verwenden, um die Einstellungen im
Gruppenrichtlinienobjekt der Windows-Clientrichtlinie zu überprüfen und
zu ermitteln, welche Einstellungen erfolgreich zu Intune migriert werden
können.

**Aufgabe 1: Exportieren des Gruppenrichtlinienobjekts der
Windows-Clientrichtlinie in eine XML-Datei**

1.  Melden Sie sich mit bei an, geben Sie !!**Server-Manager**!! ein und
    wählen Sie es aus.

> ![](./media/image1.png)

2.  In **Server Manager - Dashboard**, wählen Sie **Tools** und wählen
    Sie dann **Group Policy Management**.

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)

3.  In der Group Policy Management Konsole, erweitern Sie
    **Forest:Contoso.com**, dann **Domains**, dann **Contoso.com**, und
    wählen Sie dann **Group Policy Objects** aus.

> Stellen Sie sicher, dass mehrere Gruppenrichtlinienobjekte aufgeführt
> sind.

4.  Wählen Sie im Detailbereich das Symbol **Windows Client Policy** GPO
    aus.

> ![](./media/image3.png)

5.  Klicken Sie mit der rechten Maustaste auf **Windows Client
    Policy** und wählen Sie dann **Save Report** aus.

> ![](./media/image4.png)

6.  Wählen Sie im Dialogfeld GPO-Bericht speichern die Option
    **Documents**, ändern Sie die Option **Save as type** zu **XML
    file**, und wählen Sie dann **Save** aus.

> ![](./media/image5.png)

7.  Schließen Sie die Group Policy Management Konsole.

8.  Schließen Sie den Server Manager.

**Aufgabe 2: Analysieren des Windows-Client-Gruppenrichtlinienobjekts
mithilfe der Gruppenrichtlinienanalyse**

1.  Öffnen Sie Microsoft Edge, geben Sie
    !!**https://intune.microsoft.com**!! in der Adressleiste ein, und
    drücken Sie dann **Enter**.

2.  Melden Sie sich mit den Anmeldeinformationen für den Office
    365-Mandanten an, wenn Sie dazu aufgefordert werden.

3.  In **Microsoft Intune admin center**, navigieren Sie und wählen Sie
    **Devices**.

> ![](./media/image6.png)

4.  Navigieren Sie zum **Manage devices** Bereich und wählen Sie dann
    **Group Policy analytics** aus.

> ![](./media/image7.png)

5.  In **Devices | Group Policy analytics**, wählen Sie **Import** aus.

> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)

6.  In der Schaltfläche **GPO file upload**, klicken Sie auf den Ordner
    neben **Select a file** Suchleiste, wie in der folgenden Abbildung
    gezeigt.

> ![A screenshot of a computer Description automatically
> generated](./media/image9.png)

7.  In der Box **Open**, wählen Sie **Documents** und wählen Sie dann
    **Windows Client Policy.xml**. Klicken Sie dann auf die Schaltfläche
    **Open**.

> ![A screenshot of a computer Description automatically
> generated](./media/image10.png)

8.  Klicken Sie auf die Schaltfläche **Next**.

> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)

9.  In **Scope tags**, klicken Sie auf die Schaltfläche **Next**.

> ![A screenshot of a computer Description automatically
> generated](./media/image12.png)

10. Klicken Sie auf der Registerkarte **Review + create** auf die
    Schaltfläche **Create**.

> ![A screenshot of a computer Description automatically
> generated](./media/image13.png)

11. Das Gruppenrichtlinienobjekt der Windows-Clientrichtlinie wird
    sofort importiert und analysiert. Schließen Sie die Seite **Import
    GPO files**.

12. In **Devices | Group Policy analytics**, überprüfen Sie die
    Information neben **Windows Client Policy**.

> Beachten Sie, dass 89 % der Einstellungen MDM-Unterstützung bieten.
>
> ![A screenshot of a computer Description automatically
> generated](./media/image14.png)

13. Wählen Sie unter MDM-Unterstützung die Option**89%**.

> Beachten Sie **Setting Name**, **MDM-Support**, **CSP-Name**, und die
> **CSP-Mapping** für jede unterstützte Einstellung. Beachten Sie,
> welche Einstellungen nicht über eine entsprechende CSP-Mapping
> verfügen.
>
> ![A screenshot of a computer Description automatically
> generated](./media/image15.png)

14. Schließen Sie das **Windows Client Policy** Fenster.

**Aufgabe 3: Überprüfen des Zusammenfassungsberichts für die
Gruppenrichtlinienanalyse**

1.  Wählen Sie im Navigationsmenü des **Microsoft Intune admin center**
    die Option **Reports**.

> ![](./media/image16.png)

2.  Auf der Seite **Reports**, im Bereich **Device management**, wählen
    Sie **Group Policy analytics** aus.

> ![](./media/image17.png)

3.  Wählen Sie im Detailbereich unter **Summary** die Option **Refresh**
    aus. Möglicherweise müssen Sie einige Male aktualisieren.

> Es kann 5 bis 10 Minuten dauern, den Zusammenfassungsbericht zu
> aktualisieren und zu erstellen.

4.  Überprüfen Sie die Information in **Group policy migration
    readiness**.

> ![A screenshot of a computer Description automatically
> generated](./media/image18.png)
>
> Es sollte eine Reihe von Richtlinien vorhanden sein, die für die
> Migration bereit sind, und eine Reihe von Richtlinien, die nicht
> unterstützt werden.

5.  Wählen Sie die Registerkarte **Reports** aus, und wählen Sie dann
    **Group policy migration readiness** aus.

> ![A screenshot of a group policy migration Description automatically
> generated](./media/image19.png)

6.  Wählen Sie **Generate report** aus.

> ![A screenshot of a computer Description automatically
> generated](./media/image20.png)

7.  Der Bericht zur Group policy migration readiness enthält
    Informationen zu den einzelnen Einstellungen und dem unterstützten
    Profiltyp.

> ![A screenshot of a computer Description automatically
> generated](./media/image21.png)

8.  Schließen Sie das **Group policy migration readiness** Fenster.

**Ergebnisse**: Nach Abschluss dieser Übung haben Sie erfolgreich ein
Gruppenrichtlinienobjekt exportiert und die Gruppenrichtlinienanalyse
verwendet, um entsprechende Richtlinieneinstellungen in Intune zu
überprüfen.
