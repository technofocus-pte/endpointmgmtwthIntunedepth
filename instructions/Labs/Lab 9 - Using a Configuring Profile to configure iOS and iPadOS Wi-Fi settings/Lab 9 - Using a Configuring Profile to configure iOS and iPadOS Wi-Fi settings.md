**Lab 9 - Verwenden eines Konfigurationsprofils zum Konfigurieren der
WLAN-Einstellungen für iOS und iPadOS.**

**Zusammenfassung**

In dieser Übung verwenden wir Microsoft Intune, um ein
Konfigurationsprofil zum Ausführen der Konfiguration der
WLAN-Einstellungen für iOS- und iPadOS-Geräte zu erstellen und
anzuwenden.

**Übung 1: Erstellen eines Konfigurationsprofils.**

**Szenario**

Du wurdest aufgefordert, ein Konfigurationsprofil zu erstellen, das zur
automatischen Konfiguration der WLAN-Einstellungen für registrierte iOS-
und iPadOS-Geräte verwendet wird. Sie müssen sicherstellen, dass die
WLAN-Einstellungen wie folgt konfiguriert sind:

- Network name: **Contoso Wi-Fi**

- SSID: **MainOffice**

- Connect automatically: **Enable**

- Security type: **WPA/WPA2-Personal**

- Pre-Shared key: **ContosoWiFi123**

- Assigned to: **A new security group named iOS_iPadOS Devices**

**Aufgabe 1: Erstellen der iOS_iPadOS Gerätegruppe**

1.  Wechseln Sie
    zu *[SEA-SVR1](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10).*
     Im **Microsoft Entra admin center** Fenster, navigieren Sie und
    wählen Sie **Groups**, klicken Sie dann auf **All groups**.

> ![A screenshot of a computer Description automatically
> generated](./media/image1.png)

2.  In **Groups | All groups**, wählen Sie **New group** aus.

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)

3.  In **New Group**, Geben Sie die folgenden Informationen ein und
    klicken Sie auf die **Schaltfläche Create**, wie in der folgenden
    Abbildung gezeigt:

    - Group type: **Security**

    - Group name: !!**iOS_iPadOS Devices**!!

    - Group description: !!**All iOS and iPadOS devices**!!

    - Membership type: **Assigned**

> ![A screenshot of a group Description automatically
> generated](./media/image3.png)

4.  In **Groups | All groups**, aktualisieren Sie die Seite, und stellen
    Sie sicher, dass die Gruppe **iOS_iPadOS Devices** angezeigt wird.

> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

**Aufgabe 2: Erstellen eines Konfigurationsprofils basierend auf den
Szenarioanforderungen**

1.  Wechseln Sie zur Schaltfläche **Microsoft Intune admin center**,
    wählen Sie **Devices** aus der Navigationsleiste.

> ![A screenshot of a computer Description automatically
> generated](./media/image5.png)

2.  Auf der **Devices | Overview** Seite, wählen Sie **iOS/iPadOS** wie
    in der folgenden Abbildung gezeigt.

> ![A screenshot of a computer Description automatically
> generated](./media/image6.png)

3.  Auf der **iOS/iPadOS** Seite, navigieren Sie und klicken Sie auf
    **Configuration profiles**.

4.  Auf der **iOS/iPadOS | Configuration profiles** Seite, auf der
    Schaltfläche **Policies**, klicken Sie auf**+ Create** und wählen
    Sie **+ New Policy** aus.

> ![](./media/image7.png)

5.  In **Create a profile**, wählen Sie die folgenden Optionen aus, und
    wählen Sie dann **Create**:

    - Platform: **iOS/iPadOS**

    - Profile type: **Templates**

    - Template name: **Wi-Fi**

> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)

6.  In **Basics**, geben Sie die folgenden Informationen ein, und wählen
    Sie dann **Next**:

    - Name: !!**iOS/iPadOS Wi-Fi Policy**!!

    - Description: !!**Wi-Fi settings for iOS/iPadOS Devices**!!

> ![A screenshot of a computer Description automatically
> generated](./media/image9.png)

7.  In **Configuration settings**, neben **Wi-Fi type**, wählen Sie
    **Basic** aus.

> Zusätzliche Optionen werden basierend auf dem ausgewählten Typ
> angezeigt.

8.  In **Configuration settings**, wählen Sie die folgenden Optionen
    aus, und wählen Sie dann **Next**:

    - Network name: !!**Contoso Wi-Fi**!!

    - SSID: !! **MainOffice**!!

    - Connect automatically: **Enable**

    - Security type: **WPA/WPA2-Personal**

    - Pre-Shared key: !!**ContosoWiFi123**!!

> ![A screenshot of a computer Description automatically
> generated](./media/image10.png)

9.  In **Assignments**, unter **Included groups**, wählen Sie **Add
    groups** aus.

> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)

10. In Fenster **Select groups to include**, wählen Sie **iOS_iPadOS
    Devices**, und klicken Sie dann auf **Select**.

> ![](./media/image12.png)

11. Auf der Schaltfläche **Assignments**, klicken Sie auf **Next**.

> ![A screenshot of a computer Description automatically
> generated](./media/image13.png)

12. Auf der Schaltfläche **Review + create**, klicken Sie auf die
    Schaltfläche **Create**.

> ![A screenshot of a computer Description automatically
> generated](./media/image14.png)

13. Stellen Sie sicher, dass die **iOS/iPadOS Wi-Fi Policy** aufgeführt
    ist.

> ![A screenshot of a computer Description automatically
> generated](./media/image15.png)
>
> **Ergebnisse**: Nach Abschluss dieser Übung haben Sie erfolgreich ein
> Konfigurationsprofil erstellt und zugewiesen, um die
> WLAN-Einstellungen für iOS- und iPadOS-Geräte zu konfigurieren.
