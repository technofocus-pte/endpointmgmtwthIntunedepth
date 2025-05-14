**Lab 6 - Registrazione dei dispositivi in Microsoft Intune**

**Sommario**

In questo lab si aggiungerà un client Windows all'ID Entra e si
verificherà che il dispositivo sia stato registrato automaticamente in
Microsoft Intune.

**Prerequisite**

I seguenti laboratori devono essere completati prima di questo
laboratorio:

- Lab \#1- Gestione delle identità nell'ID Microsoft Entra

- Lab \#2- Sincronizzazione delle identità tramite Microsoft Entra
  Connect

- Lab \#5- Gestire la registrazione dei dispositivi in Microsoft Intune

Nota: potrebbe essere necessario anche un telefono cellulare in grado di
ricevere messaggi di testo utilizzati per garantire l'autenticazione di
accesso a Windows Hello per Entra ID.

**Scenario**

A Cindy White sono state assegnate le licenze appropriate e ora verrà
testato il processo di aggiunta di un dispositivo Windows all'ID Entra e
verrà registrato automaticamente in Microsoft Intune.

**Task 1: Registrare automaticamente un dispositivo Windows in Microsoft
Intune**

1.  Passare a
    [*SEA-WS1*](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10) e
    accedi come Admin con la password di!!**Pa55w.rd**!!

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image1.png)

2.  Sulla barra delle applicazioni, seleziona **Start**, quindi
    seleziona **Impostazioni**.

![A screenshot of a computer Description automatically
generated](./media/image2.png)

3.  Nella finestra **Impostazioni**, seleziona **Account**.

![A screenshot of a computer Description automatically
generated](./media/image3.png)

4.  Nella pagina Account selezionare **Accedi all'azienda o all'istituto
    di istruzione**.

![A screenshot of a computer Description automatically
generated](./media/image4.png)

5.  Nella pagina **Accedi all'azienda o all'istituto** di istruzione
    selezionare **Connetti**.

![A screenshot of a computer Description automatically
generated](./media/image5.png)

6.  Nella finestra **dell'account Microsoft**, seleziona Aggiungi questo
    **dispositivo all'ID Microsoft Entra.**

![](./media/image6.png)

Nella pagina di accesso digitare!!Cindy@M365x51282399.onmicrosoft.com!!
e quindi selezionare Avanti.![](./media/image7.png)

Nella pagina Inserisci password, inserisci la password: !!
P@55w.rd1234!! e quindi selezionare Accedi.![A screenshot of a computer
Description automatically generated](./media/image8.png)

7.  **Assicurati che venga visualizzata la finestra** di dialogo della
    tua organizzazione, **quindi seleziona Partecipa**.

![](./media/image9.png)

8.  Sul pulsante **È tutto pronto!** , leggere le informazioni e quindi
    selezionare **Fine**.

![A screenshot of a computer Description automatically
generated](./media/image10.png)

9.  Nella sezione **Accedi all'azienda** o all'istituto di istruzione
    **verificare che venga visualizzato Connesso ad Azure AD di
    Contoso**.

10. Selezionare **Connesso ad Azure AD di Contoso**, quindi selezionare
    Informazioni.

![A screenshot of a computer Description automatically
generated](./media/image11.png)

11. Prendere nota delle informazioni relative alle aree gestite da
    Contoso, scorrere verso il basso e quindi selezionare
    **Sincronizza**. In questo modo verrà forzata la sincronizzazione
    del dispositivo con Intune.

![A screenshot of a computer Description automatically
generated](./media/image12.png)

12. Chiudi la finestra **Impostazioni**.

**Task 2: Convalidare la registrazione del dispositivo in Microsoft
Entra e Intune**

1.  Sulla barra delle applicazioni **SEA-WS1**, selezionare **Start**,
    digitare !! certlm.msc!! premere **Invio**.

![A screenshot of a computer Description automatically
generated](./media/image13.png)

2.  Nella finestra di dialogo Controllo account utente selezionare il
    pulsante **Sì**.

![](./media/image14.png)

3.  Nella console **Certificati**, nel riquadro di navigazione,
    espandere **Personale** e selezionare il nodo **Certificato**.
    Verificare che i certificati seguenti siano elencati nel riquadro
    dei dettagli:

- CA del dispositivo MDM di Microsoft Intune

- MS-Organizzazione-Accesso

- MS-Organizzazione-P2P-Accesso \[2024\]

Ciò indica che il dispositivo è registrato in Microsoft Entra e Intune.

![](./media/image15.png)

4.  Chiudere la finestra Certificati.

5.  Fare clic con il pulsante destro del mouse sul pulsante **Start**,
    quindi selezionare **Terminale Windows (Amministratore)**.

![A screenshot of a computer Description automatically
generated](./media/image16.png)

6.  Nella **finestra di dialogo Controllo** account utente, fare clic
    sul pulsante **Sì**.

![A screenshot of a computer error Description automatically
generated](./media/image17.png)

7.  Nella console di PowerShell, digita quanto segue e premi **Invio**:

!!**dsregcmd /status**!!

8.  Nell'output, in **Stato dispositivo**, verificare che sia
    visualizzato **AzureAdJoined**: YES. Ciò indica che il dispositivo è
    aggiunto ad Azure AD.

![A screenshot of a computer Description automatically
generated](./media/image18.png)

9.  Nell'output in **Dettagli tenant** verificare che esistano le tre
    voci seguenti:

- mdmUrl:https://enrollment.manage.microsoft.com/enrollmentserver/discovery.svc

- mdmTouUrl:https://portal.manage.microsoft.com/TermsofUse.aspxmdm

- ComplianceUrl:https://portal.manage.microsoft.com/?portalAction=Compliance

![](./media/image19.png)

*Nota: queste voci indicano che il dispositivo è registrato in Intune.*

**Task 3: Accedi come utente Microsoft Entra ID**

1.  Disconnettersi da **SEA-WS1** dopo aver effettuato l'accesso con
    l'account amministratore locale.

2.  Nella schermata Accedi, seleziona Altro utente e accedi
    come!!**Cindy@M365xXXXXXXX.onmicrosoft.com**!!  con la password
     !\![**P@55w.rd1234**](mailto:P@55w.rd1234)!!

![](./media/image20.png)

Attendi la creazione del profilo ![A screenshot of a computer
Description automatically generated](./media/image21.png)

Nota: se viene richiesto Windows Hello, completare il processo di
accesso di conseguenza e nella pagina **Imposta un PIN**, nelle caselle
**Nuovo PIN** e Conferma PIN, digitare !! 102938!! e quindi selezionare
**OK**.

![A screenshot of a computer Description automatically
generated](./media/image22.png)

3.  Esci da **SEA-WS1**.

**Task 4: Verifica della registrazione del dispositivo nella console di
Microsoft Intune**

1.  Passare a SEA-SVR1 ed effettuare l'accesso utilizzando le
    credenziali fornite.

2.  Nel browser Microsoft Edge, digita !! https://intune.microsoft.com!!
    nella barra degli indirizzi e quindi premere **INVIO**. Accedere con
    l'account amministratore tenant di Office 365.

3.  Nel riquadro di spostamento selezionare **Dispositivi**.

![A screenshot of a computer Description automatically
generated](./media/image23.png)

4.  Sui dispositivi | **Pagina di panoramica**, navigare e fare clic su
    **Windows**.

![](./media/image24.png)

5.  Naviga e fai clic su **dispositivi Windows**. Verificare che
    **SEA-WS1** sia elencato.

Si noti che per SEA-WS1, nella colonna **Gestito** da viene
**visualizzato** Intune e nella colonna Proprietà viene visualizzato
**Corporate**.

![A screenshot of a computer Description automatically
generated](./media/image25.png)

Nota: questa visualizzazione elenca i dispositivi registrati in Intune.
Tenere presente che la registrazione automatica è stata configurata tra
Microsoft Entra e Microsoft Intune e che, a causa di che qualsiasi
dispositivo aggiunto o registrato a Microsoft Entra venga
automaticamente registrato in Microsoft Intune. Tutti i dispositivi
aggiunti prima della configurazione della registrazione vengono aggiunti
o registrati solo a Entra, ma non registrati in Intune.

6.  Apri una nuova scheda e vai all'interfaccia di **amministrazione di
    Microsoft Entra!!** https://entra.microsoft.com!!. Fare clic su
    **Dispositivi**, quindi selezionare Tutti i **dispositivi**.

![A screenshot of a computer Description automatically
generated](./media/image26.png)

7.  Prendere nota di **SEA-WS1**. Si noti che nella colonna **Tipo di
    join** viene visualizzato Microsoft Entra unito e nella colonna MDM
    viene visualizzato Microsoft Intune.

![A screenshot of a computer Description automatically
generated](./media/image27.png)

**Risultati**: dopo aver completato questo esercizio, sarà stato
aggiunto correttamente un client Windows all'ID Microsoft Entra e
verificato che il dispositivo sia stato registrato automaticamente in
Microsoft Intune.
