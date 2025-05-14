Lab13: Konfigurieren von App-Schutzrichtlinien für mobile Geräte

**Zusammenfassung**

In dieser Übung konfigurieren Sie eine App-Schutzrichtlinie für ein
mobiles Gerät.

**Szenario**

Alle Entwickler bei Contoso verfügen über iPhones und iPads, auf denen
die neuesten iOS/iPadOS-Versionen ausgeführt werden. Die
Sicherheitsabteilung beschäftigt sich mit Datenlecks und möchte
verhindern, dass Daten aus der Firmen-E-Mail in andere Apps auf den
mobilen Geräten kopiert werden. Sie müssen eine Lösung bereitstellen,
die die Bedenken der Sicherheitsabteilung ausräumt. Sie müssen Folgendes
sicherstellen:

1.  Outlook-Daten dürfen nicht in iTunes oder iCloud gesichert werden.

2.  Nur richtlinienverwaltete Apps können Daten aus Outlook senden und
    empfangen.

3.  Nur richtlinienverwaltete Apps können mit Outlook ausschneiden,
    kopieren oder einfügen.

- Benutzer müssen die Anmeldeinformationen für ihr Geschäfts-, Schul-
  oder Unikonto angeben, um auf Outlook zugreifen zu können.

Aufgabe 1: Erstellen einer App-Schutzrichtlinie für iOS-/iPadOS-Geräte

1.  Melden Sie sich bei [***SEA-SVR1***](urn:gd:lg:a:select-vm) als
    [**Contoso\Administrator**](urn:gd:lg:a:send-vm-keys) mit dem
    Kennwort!\![**Pa55w.rd**](urn:gd:lg:a:send-vm-keys)!! an.

2.  Wählen Sie in der Taskleiste **Microsoft Edge** aus**,** und
    navigieren Sie zu **Microsoft Intune. Admin Center**
    !!**https://intune.microsoft.com**!! in der Adressleiste und drücken
    Sie dann **Enter**.

3.  Melden Sie sich mit den Anmeldeinformationen des Office
    365-Mandantenadministrators auf der Registerkarte **Home** an.

4.  Auf der **Microsoft Intune admin center** Seite, wählen Sie
    **Apps**.

> ![A screenshot of a computer Description automatically
> generated](./media/image1.png)

5.  In **Apps | Overview**, unter **Policy**, wählen Sie **App
    protection policies** aus.

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)

6.  Wählen Sie im Detailbereich **+Create policy** und wählen Sie dann
    **iOS/iPadOS**.

> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)

7.  Konfigurieren Sie auf der Registerkarte **Basics** die folgenden
    Optionen, und wählen Sie **Next**:

    1.  Name: !\![**Outlook – Developers**](urn:gd:lg:a:send-vm-keys)!!

    2.  Description: !\![**Policy to prevent cut/copy and paste from
        Outlook**](urn:gd:lg:a:send-vm-keys)!!

> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

8.  Klicken Sie auf der Registerkarte **Apps** auf+ **Select public
    apps**.

9.  Auf **Select apps to target**, geben Sie in das Textfeld
    !!**Outlook**!! ein und wählen dann **Microsoft Outlook** und
    klicken Sie dann auf die Schaltfläche **Select** und wählen Sie dann
    **Next**.

> ![Screens screenshot of a computer Description automatically
> generated](./media/image5.png)

10. In **Data protection**, Konfigurieren Sie die folgenden Optionen und
    wählen Sie **Next**:

    1.  Backup Org data to iTunes and iCloud backups: **Block**

    2.  Send Org data to other apps: **Policy managed apps**

    3.  Receive data from other apps: **Policy managed apps**

    4.  Restrict cut, copy, and paste between other apps: **Policy
        managed apps**

> Alle anderen Einstellungen auf Standard belassen
>
> ![](./media/image6.png)

11. In **Access requirements**, konfigurieren Sie die folgenden Optionen
    und wählen Sie **Next**:

    1.  PIN for access: **Not required**

    2.  Work or school account credentials for access: **Require**

> ![A screenshot of a computer Description automatically
> generated](./media/image7.png)

12. Überprüfen Sie auf der Registerkarte **Conditional launch** die
    Einstellungen. Wählen Sie **Next** aus.

> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)
>
> **Hinweis**: Hier können Sie die Sicherheitsanforderungen für die
> Anmeldung für Ihre Zugriffsschutzrichtlinie festlegen. Sie können eine
> Einstellung auswählen und den Wert eingeben, den Benutzer erfüllen
> müssen, um sich bei Ihrer Unternehmens-App anzumelden. Notieren Sie
> sich die verschiedenen Einstellungen, aber ändern Sie nichts.

13. In **Assignments**, wählen Sie **Next** aus.

> ![A screenshot of a computer Description automatically
> generated](./media/image9.png)

14. In **Review + create**, überprüfen Sie die Einstellungen und wählen
    Sie **Create**.

> ![A screenshot of a computer Description automatically
> generated](./media/image10.png)

15. In **Apps | App protection policies**, vergewissern Sie sich, dass
    **Outlook – Developer** im Detailbereich aufgeführt ist.

> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)

16. Schließen Sie Microsoft Edge.

**Ergebnisse**: Nach Abschluss dieser Übung haben Sie erfolgreich eine
App-Schutzrichtlinie für ein mobiles Gerät konfiguriert.
