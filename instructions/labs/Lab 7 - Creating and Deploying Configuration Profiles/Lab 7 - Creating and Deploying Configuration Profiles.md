**Lab 7 - Creazione e distribuzione dei profili di configurazione**

**Sommario**

In questo lab si userà Microsoft Intune per creare e applicare un
profilo di configurazione per un dispositivo Windows 11.

**Prerequisite**

I seguenti laboratori devono essere completati prima di questo
laboratorio:

- Lab \#1- Gestione delle identità nell'ID Microsoft Entra

- o Lab \#2-Sincronizzazione delle identità utilizzando Microsoft Entra
  Connect

- o Lab \#5-Gestire la registrazione del dispositivo in Microsoft Intune

- o Laboratorio \#6-Registrazione dispositivi in Microsoft Intune

Nota: avrai anche bisogno di un telefono cellulare in grado di ricevere
messaggi di testo utilizzati per proteggere l'autenticazione di accesso
a Windows Hello per l'ID Microsoft Entra.

**Esercizio 1: Creare e applicare un profilo di configurazione.**

**Scenario**

È necessario usare Microsoft Entra e Microsoft Intune per gestire i
membri del reparto Sviluppatori di Contoso. Ti è stato chiesto di
valutare le soluzioni che consentirebbero agli utenti di lavorare in
modo efficace e sicuro sui dispositivi Windows 11. Cindy White si è
offerta volontaria per aiutarti a testare e valutare la soluzione e
fornire un feedback. Ti ha anche fornito alcuni requisiti iniziali che
devono essere inclusi e applicati ai dispositivi Windows dello
sviluppatore:

- o La sezione Giochi nelle impostazioni non dovrebbe essere visibile.

- o La sezione Privacy nelle impostazioni dovrebbe essere ristretta il
  più possibile.

- o La cartella C: DevProjects deve essere esclusa da Windows Defender.

- o Il processo devbuild.exe deve essere escluso da Windows Defender.

- o Le app più utilizzate e le app aggiunte di recente non devono essere
  visualizzate nel menu Start.

1.  **Task 1: Verifica delle impostazioni del dispositivo**

2.  Accedi a SEA-WS1 come **Cindy** White utilizzando le sue
    credenziali!!**Cindy@M365xXXXXXX.onmicrosoft.com**!! con il
    PIN!!**102938**!! o Password !!**P@55w.rd1234**!!

![A screenshot of a computer Description automatically
generated](./media/image1.png)

3.  Sulla barra delle applicazioni, seleziona **Start**, quindi
    seleziona **Impostazioni**.

![A screenshot of a computer Description automatically
generated](./media/image2.png)

4.  Nell'elenco di navigazione **Impostazioni**, verifica di
    visualizzare l'impostazione **Gioco**.

![A screenshot of a computer Description automatically
generated](./media/image3.png)

5.  Seleziona l'impostazione Personalizzazione, quindi nella pagina
    **Personalizzazione** seleziona Avvia. Prendi nota delle
    impostazioni **Mostra app** aggiunte di recente e Mostra **app più
    utilizzate**.

![](./media/image4.png)

![A screenshot of a computer Description automatically
generated](./media/image5.png)

6.  Nell'app **Impostazioni**, seleziona **Privacy e sicurezza**.

7.  Nella pagina **Privacy e sicurezza**, prendi nota delle opzioni in
    **Sicurezza, Autorizzazio**ni di Windows e **Autorizzazioni app**.

![A screenshot of a computer Description automatically
generated](./media/image6.png)

8.  Nella **pagina Privacy** e **sicurezza selezionare** **Sicurezza di
    Windows** e quindi selezionare Apri **sicurezza di Windows**.

![](./media/image7.png)

![A screenshot of a computer security Description automatically
generated](./media/image8.png)

9.  Nella pagina **Sicurezza di Windows**, seleziona **Protezione da
    virus e minacce**.

10. **Nella pagina Protezione da virus** e minacce, in **Impostazioni di
    protezione** da virus e minacce, **selezionare Gestisci
    impostazioni.**

![A screenshot of a computer Description automatically
generated](./media/image9.png)

11. Scorri verso il basso fino a **Esclusioni** e seleziona **Aggiungi o
    rimuovi esclusioni**. Nella finestra di dialogo Controllo account
    utente selezionare **Sì**.

![A screenshot of a computer Description automatically
generated](./media/image10.png)

![A screenshot of a computer Description automatically
generated](./media/image11.png)

12. Nella pagina **Esclusioni**, verificare che non siano state
    configurate esclusioni.

13. Chiudere la finestra **Sicurezza di Windows**.

![A screenshot of a computer Description automatically
generated](./media/image12.png)

14. Chiudi la finestra **Impostazioni**.

**Task 2: Creare un profilo di configurazione in base ai requisiti dello
scenario**

1.  Passare a
    [*SEA-SVR1*](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10).

2.  Torna alla scheda con l'interfaccia di **amministrazione di
    Microsoft Intune aperta,** seleziona **Dispositivi** dalla barra di
    spostamento.

![A screenshot of a computer Description automatically
generated](./media/image13.png)

3.  Sui dispositivi | **Pagina di** **panoramica**, selezionare
    **Windows** come mostrato nell'immagine seguente.

![A screenshot of a computer Description automatically
generated](./media/image14.png)

4.  Su Windows | **Pagina dei dispositivi Windows**, navigare e fare
    clic su **Profili di configurazione.**

![A screenshot of a computer Description automatically
generated](./media/image15.png)

5.  Su Windows | **Pagina Profili di configurazione**, nella scheda
    Criteri, fare **clic su + Crea e selezionare + Nuovo criterio.**

![A screenshot of a computer Description automatically
generated](./media/image16.png)

6.  Nel riquadro **Crea un profilo** visualizzato sul lato destro
    selezionare le opzioni seguenti e quindi selezionare Crea**:**

- Piattaforma: Windows 10 e versioni successive

- Tipo di profilo: Modelli

- Nome del modello: !!!!

![A screenshot of a profile Description automatically
generated](./media/image17.png)

7.  Nel pannello Informazioni di **base** immettere le informazioni
    seguenti e quindi selezionare **Avanti**:

- o Nome: !! Contoso sviluppatore - standard!!

- o Descrizione: !! Restrizioni di base e configurazione per gli
  sviluppatori Contoso.!!

![](./media/image18.png)

8.  Nel pannello **Impostazioni configurazioni** espandere Pannello **di
    controllo e Impostazioni.**

![A screenshot of a computer Description automatically
generated](./media/image19.png)

9.  Seleziona **Blocca** accanto alle opzioni **Gioco e Privacy.**

![A screenshot of a computer Description automatically
generated](./media/image20.png)

10. Nel pannello **Restrizioni dispositivo** espandere **Start**.

![A screenshot of a computer Description automatically
generated](./media/image21.png)

11. Scorri verso il basso e seleziona **Blocca accanto** a App più
    utilizzate**,** App aggiunte di recente ed **Elementi aperti di
    recente nelle Jump List.**

![A screenshot of a computer Description automatically
generated](./media/image22.png)

12. Nel pannello **Restrizioni dispositivo** scorrere verso il basso ed
    espandere **Microsoft Defender Antivirus.**

![A screenshot of a computer Description automatically
generated](./media/image23.png)

13. In **Microsoft Defender Antivirus** scorrere verso il basso ed
    espandere **Esclusioni di Microsoft Defender Antivirus.**

![](./media/image24.png)

14. In Esclusioni antivirus di **Microsoft Defender fornisci** i
    dettagli seguenti e fai clic sul pulsante **Avanti**:

- Casella dei file e delle cartelle - !!**C:\DevProjects**!!

- Box dei processi - !!**DevBuild.exe**!!

![](./media/image25.png)

15. Nella scheda **Assegnazioni**, fare clic sul pulsante **Avanti**.

![A screenshot of a computer Description automatically
generated](./media/image26.png)

Nella scheda **Regole di applicabilità**, fare clic sul pulsante
**Avanti**.

![A screenshot of a computer Description automatically
generated](./media/image27.png)

16. Nella scheda **Rivedi** + **crea**, fai clic sul pulsante **Crea**.

![A screenshot of a computer Description automatically
generated](./media/image28.png)

17. Il profilo di configurazione dovrebbe essere elencato ora.

![A screenshot of a computer Description automatically
generated](./media/image29.png)

**Task 3: Creare il gruppo di dispositivi Contoso Developer**

1.  **Nell'interfaccia di amministrazione di Microsoft Intune, nel
    riquadro di spostamento, selezionare gruppi**.

![A screenshot of a computer Description automatically
generated](./media/image30.png)

Sui **Gruppi** | Pannello **Tutti i gruppi**, selezionare **Nuovo
gruppo.**![A screenshot of a computer Description automatically
generated](./media/image31.png)

2.  Nel pannello **Nuovo gruppo** immettere le informazioni seguenti:

- o Tipo di gruppo: **Sicurezza**

- o Nome del gruppo: !! Contoso Sviluppatore dispositivi!!

- o Descrizione del gruppo: !! Tutti i dispositivi Windows nel reparto
  sviluppatore di Contoso!!

- o Tipo di adesione: **Assegnato**

3.  In **Membri**, seleziona **Nessun membro selezionato**.

![](./media/image32.png)

4.  Nel pannello **Aggiungi membri**, nella casella di ricerca digitare
    !! Mare!! . Selezionare **SEA-WS1,** quindi **scegliere** Seleziona.

![A screenshot of a computer Description automatically
generated](./media/image33.png)

5.  Nel pannello **Nuovo gruppo** selezionare **Crea**.

![](./media/image34.png)

6.  Sui **Gruppi** | Pannello Tutti i gruppi, verificare che sia
    visualizzato il gruppo di dispositivi per **sviluppatori Contoso.**

![](./media/image35.png)

1.  Attività 4: Creare un gruppo di dispositivi Azure AD dinamico

2.  Sui Gruppi | Nel pannello Tutti i gruppi selezionare **Nuovo
    gruppo** nel riquadro dei **dettagli**.

![A screenshot of a computer Description automatically
generated](./media/image36.png)

3.  Nel pannello **Gruppo** specificare i valori seguenti:

- Tipo di gruppo: **Sicurezza**

- Nome del gruppo: !! Dispositivi Windows!!

- Tipo di appartenenza: Dispositivo dinamico

4.  Nella **sezione Membri dispositivo dinamici** selezionare **Aggiungi
    query dinamica.**

![A screenshot of a computer Description automatically
generated](./media/image37.png)

5.  Nel pannello **Regole di appartenenza dinamica,** nella sezione
    **Sintassi regola**, selezionare **Modifica**.

![A screenshot of a computer Description automatically
generated](./media/image38.png)

6.  Nella casella di testo **Modifica sintassi regola** aggiungere la
    seguente regola di appartenenza semplice e selezionare **OK**.

!!**(device.deviceOSType -contains "Windows")**!!

![A screenshot of a computer Description automatically
generated](./media/image39.png)

7.  Nel pannello Regole di **appartenenza dinamica selezionare**
    **Salva**.

![A screenshot of a computer Description automatically
generated](./media/image40.png)

8.  Nella pagina **Nuovo gruppo**, seleziona **Crea**.

![A screenshot of a computer Description automatically
generated](./media/image41.png)

**Task 5: Assegnare un profilo di configurazione ai dispositivi
Windows**

1.  Nella pagina dell'interfaccia di **amministrazione di Microsoft
    Intune** selezionare Dispositivi dalla barra di **spostamento.**

![](./media/image42.png)

2.  Sui dispositivi | **Pagina di panoramica**, selezionare **Windows**
    come mostrato nell'immagine seguente.

![](./media/image43.png)

3.  Su **Windows** | Pagina dei dispositivi **Windows**, navigare e fare
    clic su **Profili di configurazione.**

![](./media/image44.png)

4.  Sui dispositivi | Nel pannello **Profili di configurazione**
    selezionare il profilo **Contoso Developer - Standard.**

![A screenshot of a computer Description automatically
generated](./media/image45.png)

5.  Nel pannello **Sviluppatore Contoso - standard** scorrere verso il
    basso fino alla **sezione Assegnazioni** e selezionare **Modifica**.

![A screenshot of a computer Description automatically
generated](./media/image46.png)

6.  Nella pagina Assegnazioni, in **Gruppi inclusi**, selezionare
    **Aggiungi gruppi**.

![A screenshot of a computer Description automatically
generated](./media/image47.png)

7.  Nel pannello **Seleziona gruppi da includere**, nella casella di
    **ricerca**, digitare e selezionare !! Dispositivi per sviluppatori
    Contoso!! e quindi fare clic sul pulsante **Seleziona**.

![](./media/image48.png)

15. Torna al pannello **Restrizioni dispositivo**, seleziona
    **Rivedi** + **Salva**, quindi seleziona **Salva**.

![A screenshot of a computer Description automatically
generated](./media/image49.png)

![](./media/image50.png)

**Task 6: Verificare che il profilo di configurazione sia applicato**

1.  Passare a SEA-WS1. Accedi utilizzando l'account di Cindy White.

- Nome utente - !!**Cindy@M365xXXXXXXX.onmicrosoft.com**!!

- Password – !!**P@55w.rd1234**!!

> Sulla barra delle applicazioni, seleziona **Start**, quindi seleziona
> **Impostazioni**.![A screenshot of a computer Description
> automatically generated](./media/image2.png)

2.  Nella finestra **Impostazioni**, **seleziona Account**. Nella pagina
    Account selezionare **Accedi all'azienda o all'istituto di
    istruzione.**

![A screenshot of a computer Description automatically
generated](./media/image51.png)

3.  Fare clic sull'elenco a discesa accanto a **Connesso ad Azure AD di
    Contoso** e selezionare il pulsante **Informazioni**.

![](./media/image52.png)

4.  Nella pagina **Gestito da Contoso** scorrere verso il basso e quindi
    in Stato **sincronizzazione** dispositivo selezionare Sincronizza.
    Attendi il completamento della sincronizzazione.

5.  ![A screenshot of a computer Description automatically
    generated](./media/image53.png)

![A screenshot of a computer Description automatically
generated](./media/image54.png)

6.  Chiudi l'app **Impostazioni**.

> **Nota**: l'avanzamento della sincronizzazione potrebbe richiedere
> fino a 15 minuti prima che il profilo venga applicato al dispositivo
> Windows 11. La disconnessione o il riavvio del dispositivo può
> accelerare questo processo.

Su SEA-WS1, **selezionare** Riavvia, quindi selezionare
**Impostazioni**. Verifica che l'impostazione **Gioco sia stata
rimossa.**![A screenshot of a computer Description automatically
generated](./media/image2.png)

![A screenshot of a computer Description automatically
generated](./media/image55.png)

7.  Seleziona **Privacy e sicurezza** e nota che molte delle
    impostazioni sulla privacy sono ora nascoste.

![](./media/image56.png)

8.  Seleziona l'impostazione **Personalizzazione**, quindi seleziona
    **Avvia**. **Verifica** che Mostra app aggiunte di recente e Mostra
    app più utilizzate siano disattivate e disattivate.

![](./media/image57.png)

![A screenshot of a computer Description automatically
generated](./media/image58.png)

9.  Nell'app **Impostazioni**, seleziona **Privacy e sicurezza.**

10. Nella pagina **Privacy e sicurezza** selezionare **Sicurezza di
    Windows** e quindi selezionare Apri **sicurezza di Windows**.

![](./media/image59.png)

![A screenshot of a computer security Description automatically
generated](./media/image60.png)

11. Nella pagina **Sicurezza di Windows**, selezionare **Protezione da
    virus e minacce.**

12. Nella pagina **Protezione da virus** e minacce selezionare
    **Gestisci impostazioni** in Impostazioni di protezione **da virus e
    minacce**.

![A screenshot of a computer Description automatically
generated](./media/image9.png)

13. Scorri verso il basso fino a **Esclusioni** e seleziona **Aggiungi o
    rimuovi esclusioni**. Selezionare Sì nel messaggio Controllo account
    utente.

![A screenshot of a computer Description automatically
generated](./media/image61.png)

![A screenshot of a computer Description automatically
generated](./media/image62.png)

14. Nella pagina **Esclusioni** verificare che siano visualizzati
    C:\DevProjects e DevBuild.exe.

![A screenshot of a computer Description automatically
generated](./media/image63.png)

15. Chiudi la pagina **Sicurezza di Windows**, quindi chiudi l'app
    **Impostazioni**.

**Risultati:** dopo aver completato questo esercizio, avrai creato e
assegnato correttamente un profilo di configurazione per un dispositivo
Windows 11.

**Esercizio 2: Modificare un criterio del profilo di configurazione
assegnato.**

**Scenario**

È stata introdotta un'eccezione ai criteri di Contoso che specifica che
le opzioni di privacy dei membri del reparto sviluppatori non devono
essere bloccate in Impostazioni nei dispositivi. Questa modifica deve
essere implementata e testata.

**Task 1: Modificare le impostazioni in un profilo di configurazione
assegnato**

1.  Passare a **SEA-SVR1**. Torna alla scheda Interfaccia di
    **amministrazione di Microsoft** Intune, seleziona Dispositivi dalla
    barra di spostamento.

![](./media/image42.png)

2.  Sui dispositivi | **Pagina di panoramica**, selezionare **Windows**
    come mostrato nell'immagine seguente.

![](./media/image43.png)

3.  Su Windows | Pagina dei dispositivi **Windows**, navigare e fare
    clic su **Profili di configurazione.**

![](./media/image44.png)

4.  Sui dispositivi | **Pannello Profili di configurazione,** nel
    riquadro dei dettagli selezionare **Contoso Developer - standard.**

![](./media/image64.png)

5.  Nel pannello **Contoso Developer** - Standard scorrere verso il
    basso fino alla sezione **Impostazioni di configurazione** e quindi
    selezionare **Modifica**.

![A screenshot of a computer Description automatically
generated](./media/image65.png)

6.  Nella pagina **Restrizioni del dispositivo**, espandere Pannello di
    **controllo e Impostazioni.**

![A screenshot of a computer Description automatically
generated](./media/image66.png)

7.  Accanto a **Privacy**, assicurati che sia selezionata l'opzione
    **Non configurata**.

![A screenshot of a computer Description automatically
generated](./media/image67.png)

8.  Seleziona **Rivedi + salva,** quindi seleziona **Salva**.

![](./media/image68.png)

**Task 2: Forzare la sincronizzazione dei dispositivi dall'interfaccia
di amministrazione di Microsoft Intune**

1.  In SEA-SVR1, nell'interfaccia di **amministrazione di Microsoft
    Intune,** selezionare Dispositivi nel riquadro di spostamento,
    quindi selezionare Tutti i dispositivi e selezionare **SEA-WS1.**

![A screenshot of a computer Description automatically
generated](./media/image69.png)

Nel pannello **SEA-WS1** selezionare **Sincronizza** e, quando
richiesto, selezionare **Sì**.![](./media/image70.png)

**Nota**: Intune connetterà il dispositivo e sincronizzerà tutti i
criteri. Questa operazione può richiedere fino a 5 minuti.

1.  Attività 3: Verificare le modifiche su SEA-WS1

2.  Passare a SEA-WS1. Sulla barra delle applicazioni, seleziona
    **Start**, quindi seleziona **Impostazioni**.

![A screenshot of a computer Description automatically
generated](./media/image2.png)

3.  Nell'app **Impostazioni**, seleziona **Privacy e sicurezza** e
    verifica che tutte le opzioni di personalizzazione siano tornate.

![A screenshot of a computer Description automatically
generated](./media/image71.png)

4.  Chiudi tutte le finestre aperte e disconnettiti da SEA-WS1.

**Risultati**: dopo aver completato questo esercizio, sarà stato
modificato un profilo di configurazione assegnato, modificato un profilo
di configurazione e verificate le modifiche.
