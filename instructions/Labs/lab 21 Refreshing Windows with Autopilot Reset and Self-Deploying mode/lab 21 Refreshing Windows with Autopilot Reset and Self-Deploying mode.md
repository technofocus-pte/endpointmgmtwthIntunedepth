Lab 21: Aktualisieren von Windows mit dem Autopilot-Reset- und
Self-Deploying-Modus.

**Zusammenfassung**

In diesem Lab erfahren Sie, wie Sie einen Remote-Autopilot-Reset
durchführen.

**Voraussetzungen**

Die folgenden Übungen müssen vor diesem Labor abgeschlossen werden:

1.  Lab 01 – Verwalten von Identitäten in Microsoft Entra ID

2.  Lab 02 – Synchronisieren von Identitäten mithilfe von Azure AD
    Connect

3.  Lab 21 – Bereitstellen von Windows 11 mit dem Microsoft Deployment
    Toolkit

4.  Lab 20 – Bereitstellen von Windows 11 mit Autopilot

**Szenario**

SEA-WS4 wurde unter Verwendung von Windows Autopilot bereitgestellt. Sie
müssen ein anderes Bereitstellungsszenario testen, das das Zurücksetzen
des Autopiloten umfasst. Sie erstellen ein neues Bereitstellungsprofil,
das mit dem Selbstbereitstellungsmodus von Windows Autopilot
konfiguriert ist.

Aufgabe 1: Konfigurieren eines selbstbereitstellenden Windows
Autopilot-Bereitstellungsprofils

1.  Wechseln Sie zu [***SEA-SVR1***](urn:gd:lg:a:select-vm).

> ![](./media/image1.png)

2.  In **Microsoft Edge**, öffnen Sie einen neuen Tab und navigieren Sie
    zu [**https://intune.microsoft.com**](https://intune.microsoft.com).
    Wenn Sie dazu aufgefordert werden, melden Sie sich mit
    [**admin@M365xXXXXXXXX.onmicrosoft.com**](mailto:admin@M365xXXXXXXXX.onmicrosoft.com) und
    dem Password an.

3.  In **Microsoft Intune admin center**, wählen Sie **Devices** aus.

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)

4.  Im Bereich **Device onboarding**, wählen Sie **Enrollment** aus.

> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)

5.  Wählen Sie auf dem Blatt Windows-Registrierung im Detailbereich die
    Option **Deployment Profiles**.

> ![](./media/image4.png)

6.  Wählen Sie auf dem Blatt **Windows AutoPilot deployment
    profiles** die Option **Contoso-Profil 1 aus,** und wählen Sie dann
    **Properties**.

> ![](./media/image5.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image6.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image7.png)

7.  Scrollen Sie nach unten zu **Assignments**, und wählen Sie dann
    **Edit**.

> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)

8.  Wählen Sie neben **IT Devices** die Option **Remove**.

> ![](./media/image9.png)

9.  Wählen Sie **Review and save** und wählen Sie dann **Save**.

> ![A screenshot of a computer Description automatically
> generated](./media/image10.png)

10. Schließen Sie die **Contoso Profile 1|Properties** Seite.

11. Auf dem Blatt **Windows AutoPilot deployment profiles**, wählen Sie
    **Create profile** und wählen Sie dann **Windows PC**.

> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)

12. Geben Sie auf der Registerkarte **Basics** im Textfeld **Name** den
    Namen [**Contoso-Profil 2** ein](urn:gd:lg:a:send-vm-keys).

13. Wählen Sie für **Convert all targeted devices to Autopilot** die
    Option **No** und dann **Next**.

> ![](./media/image12.png)

14. Stellen Sie auf der Registerkarte **Out-of-Box Experience (OOBE)**
    sicher, dass der **Deployment Mode** auf **Self-Deploying**
    eingeschaltet ist.

> ![](./media/image13.png)

15. Stellen Sie sicher, dass die folgenden Optionen festgelegt sind:

    - Language (Region): **Operating system default**

    - Automatically configure keyboard: **Yes**

    - Apply device name template: **Yes**

    - Enter a name: [**Contoso-%RAND:2%**](urn:gd:lg:a:send-vm-keys)

> ![A screenshot of a computer Description automatically
> generated](./media/image14.png)

16. Wählen Sie **Next** aus.

17. Wählen Sie auf der Registerkarte **Assignments** unter **Included
    groups** die Option **Add groups**.

> ![A screenshot of a computer Description automatically
> generated](./media/image15.png)

18. Wählen Sie die Schaltfläche **IT Devices** group und klicken sie auf
    **Select**. Wählen Sie **Next** aus.

> ![](./media/image16.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image17.png)

19. Überprüfen Sie auf dem Blatt **Review + create** die Informationen,
    und wählen Sie dann **Create**.

> ![A screenshot of a computer Description automatically
> generated](./media/image18.png)

Aufgabe 2: Durchführen eines Autopilot-Zurücksetzens

1.  Wählen Sie im **Microsoft Intune admin center \>Devices** und dann
    **All devices**.

2.  Wählen Sie den Autopilot-PC aus (Beginnt mit dem Namen DESKTOP).

> ![A screenshot of a computer Description automatically
> generated](./media/image19.png)

3.  Wählen Sie in der Menüleiste die Auslassungspunkte aus, und wählen
    Sie dann **Autopilot Reset**.

> ![A screenshot of a computer Description automatically
> generated](./media/image20.png)

4.  Wählen Sie an der Eingabeaufforderung **Yes**.

> ![A screenshot of a computer Description automatically
> generated](./media/image21.png)

5.  Wechseln Sie zu [***SEA-SVR2***](urn:gd:lg:a:select-vm) und
    maximieren Sie das **SEA-WS4-**Fenster.

> **Hinweis**: SEA-WS4 sollte weiterhin aus dem vorherigen Lab
> ausgeführt werden
>
> **Hinweis**: Aktualisieren Sie das Gerät auf die neueste Version und
> klicken Sie dann auf Neustart.

6.  Starte Sie **SEA-WS4** neu.

> ![A screenshot of a computer Description automatically
> generated](./media/image22.png)
>
> **Hinweis**: Dieser Vorgang kann 30 Minuten dauern und wird während
> des Vorgangs mehrmals neu gestartet. Ihr Kursleiter kann mit dem
> nächsten Modul fortfahren, während diese Aufgabe abgeschlossen ist.
> Stellen Sie sicher, dass Sie in Ihrer nächsten Lab-Sitzung
> wiederkommen, um Aufgabe 3 abzuschließen.

Aufgabe 3: Überprüfen der Autopilot-Bereitstellung

1.  Geben Sie auf der Anmeldeseite Folgendes
    ein:[**Cindy@M365x19242953.onmicrosoft.com**](mailto:Cindy@M365x19242953.onmicrosoft.com) und
    nutzen Sie das Passwort [**P@55w.rd1234**](mailto:P@55w.rd1234).

2.  Wählen Sie unter **Use Windows Hello with your account** die Option
    **OK**.

> ![A screenshot of a computer Description automatically
> generated](./media/image23.png)

3.  Wählen Sie auf der Seite **Verify your identity** die Option Text
    verification method aus.

4.  Geben Sie auf der Seite **Enter Code** den Code ein, der per SMS an
    Ihr Mobilgerät gesendet wurde, und wählen Sie dann **Verify**.

> ![A screenshot of a computer Description automatically
> generated](./media/image24.png)

5.  Geben Sie im Dialogfeld **Set up Pin** in den Feldern **New PIN**
    und **Confirm** **PIN** 102938 ein, und wählen Sie dann **OK**.

> ![](./media/image25.png)

6.  Auf der Seite **All set!** wählen Sie **OK** aus.

7.  Wählen Sie **Start** und wählen Sie **Settings** aus.

> ![](./media/image26.png)

8.  Wählen Sie **Accounts** und dann **Access work or school** aus.
    Stellen Sie sicher, dass das Gerät mit dem Azure AD von Contoso
    verbunden ist.

> ![](./media/image27.png)

9.  Wählen Sie **Connected to Contoso's Azure AD** und dann **Info**
    aus.

> ![](./media/image28.png)

10. Scrollen Sie auf der Seite **Managed by Contoso** nach unten, und
    wählen Sie dann **Sync**.

> ![](./media/image29.png)

11. Auf der **SEA-WS4 Seite**, schließen Sie das **Settings** Fenster.

12. Fahren Sie **SEA-WS4 herunter** und schließen Sie das
    **SEA-WS4-**Fenster.

13. Schließen Sie auf [***SEA-SVR2***](urn:gd:lg:a:select-vm) den
    Hyper-V-Manager.

**Ergebnisse**: Nach Abschluss dieser Übung haben Sie ein Windows
11-Gerät mit Autopilot-Zurücksetzen im Self-Deploying-Modus
bereitgestellt.
