Übungs-Lab26: Verwalten von Updaterichtlinien für iOS und iPadOS

**Zusammenfassung**

In dieser Übung konfigurieren Sie eine Updaterichtlinie, die zum
Verwalten von Betriebssystemupdates für iOS und iPadOS verwendet werden
soll.

**Szenario**

Alle Entwickler bei Contoso verfügen über iPhones und iPads, auf denen
die neuesten iOS/iPadOS-Versionen ausgeführt werden. Sie haben diese
Geräte über die automatische Geräteregistrierung von Apple registriert
und müssen eine Updaterichtlinie für das Gerätebetriebssystem
konfigurieren. Sie müssen Folgendes sicherstellen:

- Zu installierende Version: Neuestes Update.

- Automatische Updates dürfen nur zwischen Mittwoch um 12 Uhr und
  Donnerstag um 12 Uhr durchgeführt werden.

Aufgabe 1: Erstellen einer Updaterichtlinie für iOS-/iPadOS-Geräte

1.  Melden Sie sich auf [***SEA-SVR1***](urn:gd:lg:a:select-vm) bei
    Bedarf als [**Contoso\Administrator**](urn:gd:lg:a:send-vm-keys) mit
    dem Kennwort [**Pa55w.rd**](urn:gd:lg:a:send-vm-keys) an, und
    schließen Sie **Server Manager**.

2.  Wählen Sie in der Taskleiste **Microsoft Edge**.

3.  Geben Sie in Microsoft Edge
    [**https://intune.microsoft.com**](https://intune.microsoft.com) in
    die Adressleiste ein, und drücken Sie dann **Enter**.

4.  Melden Sie sich als
    [**admin@M365x19242953.onmicrosoft.com**](urn:gd:lg:a:send-vm-keys)
    mit dem Passwort an.

5.  Wählen Sie auf der Seite **Microsoft Intune Admin Center** die
    Option **Devices**.

6.  Auf **Devices|By platform**, unter **Policy**, wählen Sie
    **iOS/iPadOS** aus.

> ![](./media/image1.png)

7.  Wählen Sie **Update Policies for iOS/iPadOS** aus.

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)

8.  Wählen Sie im Detailbereich **Create profile**.

9.  Konfigurieren Sie auf der Registerkarte **Basics** die folgenden
    Optionen, und wählen Sie **Next**:

    - Name: !\![**iOS/iPadOS update
      policy**](urn:gd:lg:a:send-vm-keys)!!

    - Description: !\![**Policy to manage system updates for iOS and
      iPadOS**](urn:gd:lg:a:send-vm-keys)!!

> ![](./media/image3.png)

10. Konfigurieren Sie auf der Registerkarte **Update policy
    settings** die folgenden Optionen, und wählen Sie **Next**:

    - Select version to install: **Latest update**

    - Schedule type: **Update during scheduled time**

    - Time zone: **UTC:00**

    - Time window:

    - Start day: **Wednesday**

      - Start time: **12 AM**

      - End day: **Thursday**

      - End time: **12 AM**

> ![](./media/image4.png)

11. Wählen Sie auf der Registerkarte **Assignments** die Option
    **Next**.

> ![A screenshot of a computer Description automatically
> generated](./media/image5.png)

12. Überprüfen Sie auf der Registerkarte **Review + create** die
    Einstellungen, und wählen Sie **Create**.

13. Auf **Devices | Update policies for iOS/iPadOS**, überprüfen Sie im
    Detailbereich, ob **iOS/iPadOS update policy** aufgeführt ist.

> ![A screenshot of a computer Description automatically
> generated](./media/image6.png)

14. Schließen Sie Microsoft Edge.

**Ergebnisse**: Nach Abschluss dieser Übung haben Sie erfolgreich eine
Updaterichtlinie für iOS und iPadOS konfiguriert.
