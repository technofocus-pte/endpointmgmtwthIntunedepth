**Lab 8 - Utilizzo di un profilo di configurazione per configurare la
modalità tutto schermo**

**Summary**

In questo lab si userà Microsoft Intune per creare e applicare un
profilo di configurazione per eseguire la modalità tutto schermo con una
singola app in un dispositivo Windows 11.

**Prerequisite**

I seguenti laboratori devono essere completati prima di questo
laboratorio:

- Lab 05 - Gestire la registrazione dei dispositivi in Microsoft Intune

Nota: avrai anche bisogno di un telefono cellulare in grado di ricevere
messaggi di testo utilizzati per proteggere l'autenticazione di accesso
a Windows Hello per Entra ID.

**Esercizio 1: Creare e applicare un profilo di configurazione
Scenario**

È stato chiesto di configurare SEA-WS2 come chiosco multimediale di
Windows 11 per consentire ai visitatori di Contoso di esplorare
Internet. È necessario assicurarsi che il chiosco multimediale sia
configurato come segue:

- Un'unica app, chiosco a schermo intero.

- Accesso automatico.

- Consente l'accesso al browser Microsoft Edge, che deve essere
  configurato in modalità di navigazione pubblica (InPrivate). La home
  page deve essere configurata per http://bing.com.

**Task 1: Registrare SEA-WS2 in Microsoft Intune**

1.  Accedere a SEA-WS2 come amministratore con la password
    di!!**Pa55w.rd**!!.

2.  Sulla barra delle applicazioni, seleziona **Start**, quindi
    seleziona **Impostazioni**.

![](./media/image1.png)

3.  Nella finestra **Impostazioni**, seleziona **Account**.

![A screenshot of a computer Description automatically
generated](./media/image2.png)

4.  Nella pagina Account selezionare **Accedi all'azienda o all'istituto
    di istruzione.**

![A screenshot of a computer Description automatically
generated](./media/image3.png)

5.  Nella pagina **Accedi all'azienda o all'istituto** di istruzione
    selezionare **Connetti**.

![A screenshot of a computer Description automatically
generated](./media/image4.png)

6.  Nella finestra **dell'account Microsoft**, seleziona **Aggiungi
    questo dispositivo all'ID Microsoft Entra.**

![A screenshot of a computer screen Description automatically
generated](./media/image5.png)

7.  Nella **pagina di accesso**, digita !!
    AllanD@M365xXXXXXX.onmicrosoft.com!! , quindi seleziona **Avanti**.

![](./media/image6.png)

8.  Nella pagina **Inserisci password** immettere la password del
    tenant: !! P@55w.rd1234!! e quindi **seleziona Accedi.**

![A screenshot of a computer Description automatically
generated](./media/image7.png)

9.  Nella finestra di **dialogo Assicurati che si tratti
    dell'organizzazione** selezionare **Partecipa**.

![A screenshot of a computer error Description automatically
generated](./media/image8.png)

10. Sul pulsante **È tutto pronto!** , leggere le informazioni e quindi
    selezionare **Fine**.

![A screenshot of a computer screen Description automatically
generated](./media/image9.png)

11. Nella sezione **Accedi all'azienda** o all'istituto di istruzione
    verificare che venga visualizzato **Connesso ad Azure AD di
    Contoso.**

![A screenshot of a computer Description automatically
generated](./media/image10.png)

12. Selezionare Connesso ad **Azure AD di Contoso**, quindi selezionare
    **Informazioni**.

![A screenshot of a computer Description automatically
generated](./media/image11.png)

13. Scorri verso il basso, quindi seleziona **Sincronizza**. In questo
    modo verrà forzata la sincronizzazione del dispositivo con Intune.

![A screenshot of a computer Description automatically
generated](./media/image12.png)

14. Chiudi la finestra **Impostazioni**.

**Task 2: Creare il gruppo di dispositivi Contoso Kiosk**

1.  In SEA-SVR1 passare alla scheda Interfaccia di **amministrazione di
    Microsoft Entra.** Naviga e seleziona Gruppi, quindi **fai clic su
    Tutti i gruppi.**

![](./media/image13.png)

2.  Sui **Gruppi** | Pagina **Tutti i gruppi**, seleziona **Nuovo
    gruppo.**

![A screenshot of a computer Description automatically
generated](./media/image14.png)

3.  Nel pannello **Nuovo gruppo** immettere le informazioni seguenti:

- Tipo di gruppo: Sicurezza

- Nome del gruppo: !! Contoso Chiosco dispositivi!!

- Descrizione del gruppo: !! Tutti i dispositivi Windows configurati
  come chiosco!!

- Tipo di adesione: Assegnato

4.  In **Membri**, seleziona **Nessun membro selezionato**.

![](./media/image15.png)

5.  Nel pannello **Aggiungi membri** digitare Mare, nella casella di
    ricerca. Selezionare **SEA-WS2** e quindi selezionare **Seleziona**.

![](./media/image16.png)

6.  Nel pannello **Nuovo gruppo** selezionare **Crea**.

![A screenshot of a computer Description automatically
generated](./media/image17.png)

7.  Sui **Gruppi | Pannello Tutti i gruppi**, aggiornare la pagina e
    verificare che sia visualizzato il gruppo Dispositivi in modalità
    tutto schermo di Contoso.

![](./media/image18.png)

**Task 3: Creare un profilo di configurazione in base ai requisiti dello
scenario**

1.  Tornare all'interfaccia di amministrazione di Microsoft Intune,
    selezionare **Dispositivi** dalla barra di spostamento.

![A screenshot of a computer Description automatically
generated](./media/image19.png)

2.  Sui **dispositivi** | **Pagina di panoramica**, selezionare Windows
    come mostrato **nell'immagine seguente.**

![A screenshot of a computer Description automatically
generated](./media/image20.png)

3.  Su **Windows** | Pagina dei **dispositivi Windows**, navigare e fare
    clic su Profili di **configurazione**.

![A screenshot of a computer Description automatically
generated](./media/image21.png)

4.  Su **Windows** | Pagina Profili di configurazione, nella **scheda
    Criteri, fare clic su** + **Crea e selezionare** + **Nuovo
    criterio.**

![A screenshot of a computer Description automatically
generated](./media/image22.png)

5.  In the **Create a profile** blade, select the following options, and
    then select **Create**:

- Piattaforma: **Windows 10 e versioni successive**

- Tipo di **profilo: Modelli**

- Nome del modello: !!**Kiosk**!!

![A screenshot of a computer Description automatically
generated](./media/image23.png)

6.  Nel pannello Informazioni di **base** immettere le informazioni
    seguenti e quindi selezionare **Avanti**:

- Nome: !!Contoso Kiosk Policy!!

- Descrizione: !!Basic settings for Contoso Kiosk Devices.!!

![A screenshot of a computer Description automatically
generated](./media/image24.png)

7.  Nel pannello **Impostazioni** di configurazione, accanto a
    **Seleziona** una modalità tutto schermo**,** selezionare App
    singola**, tutto schermo**.

Vengono visualizzate opzioni aggiuntive in base alla modalità
selezionata.

8.  Nel pannello Impostazioni di **configurazione selezionare** le
    opzioni seguenti e quindi selezionare **Avanti**:

> Tipo di accesso utente: **accesso automatico (Windows 10, versione
> 1803 e successive, o Windows 11**)
>
> o Tipo di applicazione: Aggiungi **browser Microsoft Edge**
>
> o Edge Kiosk URL: !! http://bing.com!!
>
> o Microsoft Edge kiosk mode type: **Navigazione pubblica (InPrivate)**
>
> o Aggiornare il browser dopo il tempo di inattività: **5**
>
> o Specificare la finestra di manutenzione per il riavv![A screenshot
> of a computer Description automatically
> generated](./media/image25.png)

9.  Nel pannello **Assegnazioni**, in **Gruppi inclusi,** selezionare
    **Aggiungi gruppi.**

![A screenshot of a computer Description automatically
generated](./media/image26.png)

10. Nella **finestra Seleziona gruppi** da includere, selezionare !!
    Contoso Kiosk Devices!, quindi fare clic su **Seleziona**.

![A screenshot of a computer Description automatically
generated](./media/image27.png)

11. Nella scheda **Assegnazione**, fare clic sul pulsante **Avanti**.

![A screenshot of a computer Description automatically
generated](./media/image28.png)

12. Nella scheda **Regole di applicabilità**, fare clic sul pulsante
    **Avanti**.

![A screenshot of a computer Description automatically
generated](./media/image29.png)

13. Nella scheda **Rivedi** + **crea**, fai clic sul pulsante **Crea**.

![A screenshot of a computer Description automatically
generated](./media/image30.png)

14. Verrà elencato il profilo di configurazione.

![A screenshot of a computer Description automatically
generated](./media/image31.png)

**Task 4:** Verificare che il profilo di configurazione sia applicato

Accedere a SEA-WS2 come **amministratore** con la password
di!!**Pa55w.rd**!!.

1.  Sulla barra delle applicazioni, seleziona **Start**, quindi
    seleziona **Impostazioni**.

![A screenshot of a computer Description automatically
generated](./media/image1.png)

2.  Nella finestra **Impostazioni**, seleziona **Account**.

![A screenshot of a computer Description automatically
generated](./media/image2.png)

3.  Nella pagina Account selezionare **Accedi all'azienda o all'istituto
    di istruzione.**

![A screenshot of a computer Description automatically
generated](./media/image3.png)

5.  Selezionare **Connesso ad Azure AD di Contoso**, quindi selezionare
    **Informazioni**.

![A screenshot of a computer Description automatically
generated](./media/image11.png)

6.  Scorri verso il basso, quindi seleziona **Sincronizza**. In questo
    modo verrà forzata la sincronizzazione del dispositivo con Intune.

![A screenshot of a computer Description automatically
generated](./media/image12.png)

7.  Chiudi la finestra **Impostazioni**.

> ![](./media/image32.png)

5.  Riavviare SEA-WS2.

Si noti che **SEA-WS2** accede automaticamente e crea un profilo. Al
termine dell'accesso, viene visualizzato Microsoft Edge configurato con
l'esplorazione InPrivate. Se SEA-WS2 non esegue l'accesso
automaticamente, ripetere i passaggi da 1 a 7 per assicurarsi che il
criterio sia stato aggiornato nel dispositivo.

![](./media/image33.png)

**Risultati**: dopo aver completato questo esercizio, avrai creato e
assegnato correttamente un profilo di configurazione per configurare un
dispositivo Windows 11 come chiosco multimediale con una singola app.
