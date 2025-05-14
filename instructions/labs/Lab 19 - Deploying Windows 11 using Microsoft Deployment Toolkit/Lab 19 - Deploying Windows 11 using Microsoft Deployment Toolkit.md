# **Lab 19 - Distribuzione di Windows 11 tramite Microsoft Deployment Toolkit**

**Sommario**

In questo lab si userà Microsoft Deployment Toolkit per creare e
distribuire un'immagine del sistema operativo Windows 11.

**Scenario**

È necessario distribuire una nuova macchina virtuale Windows 11
denominata SEA-WS4. Si decide di utilizzare Microsoft Deployment Toolkit
per distribuire il sistema operativo in una macchina virtuale creata in
Hyper-V. Si configurerà una nuova condivisione di distribuzione in MDT e
quindi si configurerà la sequenza di attività che eseguirà i passaggi
per distribuire SEA-WS4.

### **Task 1:** Creare una nuova condivisione di distribuzione

1.  Passare a [**SEA-SVR2**](urn:gd:lg:a:select-vm), Accedi come
    !!**[Contoso\Administrator](urn:gd:lg:a:send-vm-keys)!!** Con la
    password !!**[Pa55w.rd](urn:gd:lg:a:send-vm-keys)!!**

> ![Screenshot](./media/image1.png)

2.  Sulla barra delle applicazioni, seleziona **Esplora file**, quindi
    vai a!!**[E:\Labfiles\ISOs](urn:gd:lg:a:send-vm-keys)!!**

> ![Screenshot](./media/image2.png)

3.  Fare clic con il pulsante destro del **mouse**
    **Win11_21H2_Eval.iso** e quindi selezionare Monta. L'ISO si monta
    come unità DVD **D**.

> ![Screenshot](./media/image3.png)
>
> ![Screenshot](./media/image4.png)

4.  Chiudi l'esploratore di file.

5.  Selezionare **il menu Start**, espandere **Microsoft Deployment
    Toolkit** e quindi **selezionare Deployment Workbench.**

> ![Screenshot](./media/image5.png)

6.  In **Deployment Workbench** fare clic con il pulsante destro del
    mouse su **Condivisioni di distribuzione** e quindi scegliere Nuova
    **condivisione** di distribuzione.

> ![Screenshot](./media/image6.png)
>
> Verrà visualizzata la Creazione **guidata nuova condivisione
> distribuzione**.

7.  Nella **pagina** Percorso, in Percorso **condivisione distribuzione,
    modificare** il valore
    a !!**[E:\DeploymentShare](urn:gd:lg:a:send-vm-keys)!!** e quindi
    selezionare **Avanti**.

> ![Screenshot](./media/image7.png)

8.  Nella pagina **Condividi**, prendere nota del **nome della
    condivisione**, ma non modificarlo. Seleziona **Avanti**.

> ![Screenshot](./media/image8.png)

9.  Nella pagina **Nome descrittivo**, accettare il valore predefinito e
    selezionare **Avanti**.

> Nella pagina Opzioni configurare quanto segue, quindi selezionare
> Avanti
>
> ![Screenshot](./media/image9.png)

10. Nella pagina **Opzioni** configurare quanto segue, quindi
    selezionare **Avanti**:

    - Chiedi di impostare la password dell'amministratore locale:
      **Abilitata**

> Tutte le altre caselle di controllo: **Disabilitato**
>
> ![Screenshot](./media/image10.png)

11. Nella pagina **Riepilogo** esaminare le informazioni e quindi
    selezionare Avanti.

> ![Screenshot](./media/image11.png)

12. Nella pagina **Conferma**, assicurati che il processo sia stato
    completato correttamente, quindi seleziona **Fine**.

> ![Screenshot](./media/image12.png)

13. In Condivisioni di **distribuzione** espandere la cartella
    **Condivisione di distribuzione MDT.**

> Prendere nota dei vari nodi che possono essere configurati per la
> condivisione di distribuzione.

### **Task 2:** Aggiungere i file del sistema operativo alla condivisione di distribuzione

1.  In Deployment Workbench espandere **Condivisioni di distribuzione**,
    **Condivisione di distribuzione MDT** e quindi selezionare **Sistemi
    operativi**.

> ![Screenshot](./media/image13.png)

2.  Fare clic con il pulsante destro del mouse su **Sistemi operativi**,
    quindi selezionare **Importa sistema operativo.** Viene visualizzata
    l'Importazione guidata sistema operativo.

> ![Screenshot](./media/image14.png)

3.  Nella procedura **guidata Importa sistema operativo**, nella pagina
    Tipo di **sistema operativo**, selezionare Set **completo di file di
    origine** e quindi selezionare **Avanti**.

> ![Screenshot](./media/image15.png)

4.  Nella pagina **Origine**, in **Directory di origine**, immettere !!
    D:\\! , quindi seleziona **Avanti**.

> ![Screenshot](./media/image16.png)

5.  Nella pagina **Destinazione**, Modificare il nome della directory di
    destinazione predefinito in!!**[Windows 11 Enterprise
    x64](urn:gd:lg:a:send-vm-keys)!!** , quindi seleziona **Avanti**.

> ![Screenshot](./media/image17.png)

6.  Nella pagina **Riepilogo** esaminare le informazioni e quindi
    selezionare **Avanti**.

> ![Screenshot](./media/image18.png)
>
> I file di origine del sistema operativo vengono copiati nella
> condivisione di distribuzione.

7.  Nella pagina **Conferma**, assicurati che il processo sia stato
    completato correttamente, quindi seleziona **Fine**.

> ![Screenshot](./media/image19.png)

8.  In **Deployment Workbench**, con l'opzione **Sistemi operativi
    selezionata**, verificare che il sistema operativo visualizzi.

### **Task 3: Aggiunta di applicazioni alla condivisione di distribuzione**

1.  In Deployment Workbench espandere Condivisioni di distribuzione,
    **Condivisione di distribuzione MDT** e quindi selezionare
    **Applicazioni**.

2.  Fare clic con il pulsante destro del mouse su **Applicazioni** e
    quindi selezionare Nuova applicazione. Viene visualizzata la
    Creazione guidata **nuova applicazione.**

> ![Screenshot](./media/image20.png)

3.  Nella Creazione guidata **nuova applicazione**, nella pagina **Tipo
    di applicazione** selezionare **Applicazione** con file di origine e
    quindi selezionare **Avanti**.

> ![Screenshot](./media/image21.png)

4.  Nella pagina **Dettagli** configurare quanto segue, quindi
    selezionare **Avanti**:

    - Editore: !!**[Microsoft](urn:gd:lg:a:send-vm-keys)!!**

    - Nome del l'applicazione: !!**[XML
      Notepad](urn:gd:lg:a:send-vm-keys)!!**

> ![Screenshot](./media/image22.png)

5.  Nella pagina **Origine**, in **Directory di origine**, inserisci
    !!**[E:\Labfiles\Apps](urn:gd:lg:a:send-vm-keys)!!** e quindi
    selezionare **Avanti**.

> ![Screenshot](./media/image23.png)

6.  Nella pagina **Destinazione** accettare il nome della directory di
    destinazione predefinito e quindi selezionare **Avanti**.

> ![Screenshot](./media/image24.png)
>
> Nella pagina **Dettagli comando**, in Riga di **comando, immettere**
> !! XmlNotepadSetup.msi /q!! e quindi selezionare **Avanti**.
>
> ![Screenshot](./media/image25.png)

7.  Nella pagina **Riepilogo** esaminare le informazioni e quindi
    selezionare **Avanti**.

> ![Screenshot](./media/image26.png)

8.  Nella pagina **Conferma**, assicurati che il processo sia stato
    completato correttamente, quindi seleziona **Fine**.

### **Task 4: Creare una sequenza di attività MDT**

1.  In Deployment Workbench espandere **Condivisioni di distribuzione,**
    **Condivisione di distribuzione MDT** e quindi selezionare Sequenze
    di **attività**.

2.  Fare clic con il pulsante destro del mouse su **Sequenze di**
    attività e quindi **scegliere Nuova sequenza** di attività. Verrà
    visualizzata la Creazione guidata **nuova sequenza** di attività.

> ![Screenshot](./media/image27.png)

- Nella pagina **Impostazioni generali** configurare quanto segue e
  quindi selezionare **Avanti**:Task sequence
  ID: !!**[001](urn:gd:lg:a:send-vm-keys)!!**

- Nome della sequenza di attività: !!**[Deploy Windows 11
  Enterprise](urn:gd:lg:a:send-vm-keys)!!**

> ![Screenshot](./media/image28.png)

3.  Nella pagina **Seleziona modello**, selezionare **Sequenza di
    attività client standard** e quindi selezionare **Avanti**.

> ![Screenshot](./media/image29.png)

4.  Nella pagina **Seleziona sistema operativo**, selezionare **Windows
    10 Enterprise Evaluation** e quindi selezionare **Avanti**.

> ![Screenshot](./media/image30.png)

5.  Nella pagina **Specifica codice Product Key**, selezionare **Non
    specificare un codice Product Key** in questo momento, quindi
    selezionare **Avanti**.

> ![Screenshot](./media/image31.png)

6.  Nella pagina **Impostazioni del sistema operativo,** configurare
    quanto segue e quindi selezionare **Avanti**:

    - Nome completo: !!**[User](urn:gd:lg:a:send-vm-keys)!!**

    - Organizzazione: !!**[Contoso
      Corporation](urn:gd:lg:a:send-vm-keys)!!**

    - Internet Explorer Home
      Page: !!**[about:blank](urn:gd:lg:a:send-vm-keys)!!**

> ![Screenshot](./media/image32.png)

7.  Nella pagina **Password amministratore,** selezionare **Usa la
    password dell'amministratore locale specificata**, quindi
    immettere !!**[Pa55w.rd](urn:gd:lg:a:send-vm-keys)!!** in entrambe
    le caselle di testo. Seleziona **Avanti**.

> ![Screenshot](./media/image33.png)

8.  Nella pagina **Riepilogo** esaminare le informazioni e quindi
    selezionare **Avanti**.

> ![Screenshot](./media/image34.png)

9.  Nella pagina **Conferma**, assicurarsi che il processo sia stato
    completato correttamente, quindi selezionare **Fine**.

> ![Screenshot](./media/image35.png)

10. **Nell'ambiente Distribuzione**, con l'opzione **Sequenze di
    attività** selezionata, verificare che **venga visualizzata** la
    sequenza di attività Distribuisci **Windows 11 Enterprise**.

> ![Screenshot](./media/image36.png)

11. Fare clic con il pulsante destro del mouse sulla sequenza di
    attività Distribuisci **Windows 11 Enterprise** e quindi scegliere
    **Proprietà**.

> ![Screenshot](./media/image37.png)

12. Selezionare la scheda **Sequenza di attività**.

13. Espandere il nodo **Convalida** e quindi selezionare **Convalida**.

14. Nella pagina **Proprietà** rimuovere i segni di spunta accanto a
    **Verifica memoria minima** e Verifica velocità **minima del
    processore.**

> Non apportare altre modifiche.

15. Nella finestra **Distribuisci proprietà di Windows 11 Enterprise**
    selezionare **OK**.

> ![Screenshot](./media/image38.png)

### **Task 5: Configurare le proprietà della condivisione di distribuzione e le impostazioni di Windows PE**

1.  In Deployment Workbench espandere **Condivisioni di distribuzione**
    e selezionare **Condivisione di distribuzione MDT.**

2.  Fare clic con il pulsante destro del mouse su **Condivisione
    distribuzione MDT** e quindi scegliere **Proprietà**.

> Nella finestra Proprietà condivisione di distribuzione MDT, nella
> scheda Generale
>
> ![Screenshot](./media/image39.png)

3.  Nella finestra **Proprietà condivisione di distribuzione MDT**,
    nella scheda **Generale**, Prendere nota delle informazioni fornite
    al momento della creazione della condivisione di distribuzione.

> ![Screenshot](./media/image40.png)

4.  Seleziona la scheda **Regole**.

> Nella scheda Regole viene visualizzato il contenuto del file
> CustomSettings.ini. Questi valori sono stati forniti anche durante la
> creazione della condivisione di distribuzione.
>
> ![Screenshot](./media/image41.png)

5.  Seleziona la scheda **Windows PE.**

> La scheda Windows PE fornisce opzioni per la creazione di un disco di
> avvio di Windows PE.

6.  Nella scheda **Windows PE,** accanto a **Piattaforma**, selezionare
    **x64.**

7.  Nella sezione **Personalizzazioni di Windows PE,** accanto a
    Dimensioni **spazio di lavoro virtuale**, seleziona **64**.

> ![Screenshot](./media/image42.png)

8.  Selezionare la scheda **Funzionalità**, quindi selezionare la
    casella di controllo accanto ai seguenti Feature Pack:

    - DISM Cmdlets

    - Windows PowerShell

> Supporto dei componenti di accesso ai dati Microsoft
> (MDAC/ADO)![Screenshot](./media/image43.png)
>
> ![Screenshot](./media/image44.png)

9.  Seleziona la scheda **Monitoraggio**.

10. Nella scheda **Monitoraggio** selezionare la casella di controllo
    accanto a **Abilita monitoraggio per questa condivisione di
    distribuzione**.

11. Nella finestra **Proprietà condivisione di distribuzione MDT**
    selezionare **OK**.

> ![Screenshot](./media/image45.png)

12. Fare clic con il pulsante destro del mouse su **Condivisione di
    distribuzione MDT** e quindi scegliere Aggiorna condivisione di
    distribuzione. Verrà visualizzata la procedura guidata **Aggiorna
    condivisione distribuzione**.

> ![Screenshot](./media/image46.png)

13. Nella pagina **Opzioni** selezionare **Ottimizza il processo di
    aggiornamento dell'immagine** di avvio e quindi selezionare
    **Avanti**.

> ![Screenshot](./media/image47.png)

14. Nella pagina **Riepilogo** selezionare **Avanti**.

> ![Screenshot](./media/image48.png)
>
> La condivisione di distribuzione avvia l'aggiornamento e la creazione
> dei file di Windows PE. Il completamento dell'operazione richiederà
> alcuni minuti.

15. Nella pagina **Conferma**, assicurati che il processo sia stato
    completato correttamente, quindi seleziona **Fine**.

> ![Screenshot](./media/image49.png)

### **Task 6:** Distribuisci Windows 11 usando MDT

1.  Su [**SEA-SVR2**](urn:gd:lg:a:select-vm), Sulla barra delle
    applicazioni, seleziona **Hyper-V Manager**.

> ![Screenshot](./media/image50.png)
>
> Nella console di gestione di Hyper-V selezionare **Gestione
> commutatori virtuali**.
>
> ![Screenshot](./media/image51.png)
>
> Selezionare **Esterno** nell'elenco, quindi fare clic su **Crea
> commutatore virtuale**.
>
> ![Screenshot](./media/image52.png)

2.  Nella pagina **Proprietà commutatore virtuale,** sotto il **nome**,
    inserire [**External network**](urn:gd:lg:a:send-vm-keys),
    selezionare **OK**, quindi selezionare **Sì**.

> ![Screenshot](./media/image53.png)
>
> ![Screenshot](./media/image54.png)

3.  Nella console di gestione di Hyper-V selezionare **SEA-SVR2** e
    quindi nel riquadro Azioni selezionare **Nuovo**, quindi selezionare
    **Macchina virtuale**.

> ![Screenshot](./media/image55.png)
>
> Nella pagina **Prima di iniziare** selezionare **Avanti**.
>
> ![Screenshot](./media/image56.png)

4.  Nella casella **Nome** della pagina **Specifica nome e percorso
    digitare**!!**[SEA-WS4](urn:gd:lg:a:send-vm-keys)!!**.

5.  Selezionare la casella di controllo successivo a **Archiviare la
    macchina virtuale in una posizione** diversa e quindi accanto a Tipo
    di **posizione**
    !!**[E:\Labfiles\VirtualMachines](urn:gd:lg:a:send-vm-keys)!!**.
    selezionare **Avanti**.

> ![Screenshot](./media/image57.png)

6.  Nella pagina **Specifica generazione**, assicurarsi che sia
    selezionata l'opzione **Generazione 2**, quindi selezionare
    **Avanti**.

> ![Screenshot](./media/image58.png)

7.  Nella pagina **Assegna memoria**, accanto a Tipo di **memoria di
    avvio** !!**[8192](urn:gd:lg:a:send-vm-keys)!!** , quindi seleziona
    **Avanti**.

> ![Screenshot](./media/image59.png)

8.  Nella pagina **Configura rete**, accanto a **Connessione**,
    selezionare **Rete esterna**, quindi selezionare **Avanti**.

> ![Screenshot](./media/image60.png)

9.  Nella pagina **Connetti disco rigido virtuale**, selezionare **Crea
    un disco rigido virtuale** e immettere quanto segue, quindi fare
    clic su **Avanti**:

    - Nome: !!**[SEA-WS4.vhdx](urn:gd:lg:a:send-vm-keys)!!**

    - Locazione: !!**[E:\Labfiles\VirtualMachines](urn:gd:lg:a:send-vm-keys)!!**

    - Dimensioni: !!**[60](urn:gd:lg:a:send-vm-keys)!!**

> ![Screenshot](./media/image61.png)

10. Nella pagina Opzioni di installazione, sceglio **Installare un
    sistema operativo da un file immagine avviabile** e configurare
    quanto segue:

    - File immagine
      (.iso): !!**[E:\DeploymentShare\Boot\LiteTouchPE_x64.iso](urn:gd:lg:a:send-vm-keys)!!**

> ![Screenshot](./media/image62.png)

11. Seleziona **Avanti**, quindi **Fine**.

> ![Screenshot](./media/image63.png)

12. Nella console di gestione di Hyper-V fare clic con il pulsante
    destro del mouse su **SEA-WS4** e quindi scegliere **Impostazioni**.

> ![Screenshot](./media/image64.png)

13. Selezionare **Sicurezza**, quindi selezionare la casella di
    controllo accanto ad **Abilita Trusted Platform Module.**

> ![Screenshot](./media/image65.png)

14. Selezionare **Processore**, quindi modificare il numero di
    processori virtuali in!!**[2](urn:gd:lg:a:send-vm-keys)!!**.

15. Selezionare **OK** per chiudere la finestra di dialogo Impostazioni.

> ![Screenshot](./media/image66.png)

16. Nella console di gestione di Hyper-V selezionare **SEA-WS4**,
    selezionare **Connetti** e quindi selezionare **Avvia**.

> ![Screenshot](./media/image67.png)
>
> ![Screenshot](./media/image68.png)

17. All'avvio del computer, premere un tasto qualsiasi della tastiera
    per richiamare la distribuzione guidata di MDT. Ingrandisci la
    finestra secondo necessità.

> ![Screenshot](./media/image69.png)

18. Nella pagina di **benvenuto**, select **Eseguire la Distribuzione
    guidata per installare un nuovo sistema
    operativo**.![Screenshot](./media/image70.png)

19. Nella finestra **Specificare le credenziali per la connessione alle
    condivisioni** di rete immettere quanto segue e quindi selezionare
    **OK**:

    - Nome utente!!**[Administrator](urn:gd:lg:a:send-vm-keys)!!**

    - Password: !!**[Pa55w.rd](urn:gd:lg:a:send-vm-keys)!!**

    - Domain: !!**[Contoso](urn:gd:lg:a:send-vm-keys)!!**

> ![Screenshot](./media/image71.png)

20. Nella pagina **Sequenza di attività** selezionare **Distribuisci
    Windows 11** Enterprise e quindi selezionare **Avanti**.

> ![Screenshot](./media/image72.png)

21. Nella pagina **Dettagli computer,** accanto a **Nome computer**
    inserisci !! MARE-WS4!! , quindi seleziona **Avanti**.

> ![Screenshot](./media/image73.png)

22. Nella pagina **Sposta dati e impostazioni** selezionare **Avanti**.

> ![Screenshot](./media/image74.png)

23. Nella pagina **Dati utente (ripristino)** selezionare **Avanti**.

> ![Screenshot](./media/image75.png)

24. Nella pagina **Impostazioni locali e ora** selezionare **Avanti**.

> ![Screenshot](./media/image76.png)

25. Nella pagina **Applicazioni** selezionare **Avanti**.

> ![Screenshot](./media/image77.png)

26. Nella pagina **Password amministratore**, immettere !! Pa55w.rd!! in
    entrambe le caselle di testo, quindi selezionare **Avanti**.

> ![Screenshot](./media/image78.png)

27. Nella pagina **Pronto** selezionare **Inizia**.

> L'installazione ha inizio. Il completamento richiederà un po' di tempo
> e riavvierà SEA-WS4 durante l'installazione, se necessario
> ![Screenshot](./media/image79.png)
>
> L'installazione ha inizio. Il completamento richiederà un po' di tempo
> e riavvierà **SEA-WS4** durante l'installazione, se necessario.

28. Passare a **Deployment Workbench.**

29. In Deployment Workbench espandere **Condivisioni di distribuzione**
    ed espandere **Condivisione di distribuzione MDT.**

30. Selezionare **Monitoraggio**, quindi nel riquadro dei dettagli fare
    doppio clic su **SEA-WS4**.

> ![Screenshot](./media/image80.png)
>
> Esaminare lo stato di monitoraggio durante la distribuzione.
>
> ![A screenshot of a computer Description automatically
> generated](./media/image81.png)

31. Passa a **SEA-WS4.**

32. Al termine dell'installazione, il desktop si aprirà e finalizzerà la
    distribuzione. Nel riepilogo della distribuzione selezionare
    **Fine**.

> ![Screenshot](./media/image82.png)

33. Arrestare **SEA-WS4** e chiudere la finestra Connessione macchina
    virtuale.

> ![Screenshot](./media/image83.png)

34. Nella console di gestione di Hyper-V, fare clic con il pulsante
    destro del mouse su **SEA-WS4** e quindi selezionare
    **Impostazioni**.

> Nel riquadro dei dettagli, in File multimediali, selezionare Nessuno e
> quindi selezionare OK
>
> ![Screenshot](./media/image84.png)

35. Nelle **Impostazioni per SEA-WS4**, espandere **Controller SCSI,**
    quindi selezionare Unità **DVD.**

36. Nel riquadro dei dettagli, in File **multimediali**, selezionare
    **Nessuno** e quindi selezionare **OK**.

> ![Screenshot](./media/image85.png)

37. Fare clic con il pulsante destro del mouse su **SEA-WS4**, quindi
    selezionare **Checkpoint** per creare un checkpoint dello stato
    corrente di SEA-WS4.

> ![Screenshot](./media/image86.png)
>
> ![Screenshot](./media/image87.png)

38. On [**SEA-SVR2**](urn:gd:lg:a:select-vm), chiudere la console di
    gestione di **Hyper-V** e chiudere **Deployment Workbench.**

39. Apri **l'esploratore di file,** fare clic con il tasto destro del
    mouse su **DVD Drive D** e quindi **selezionare**.

> ![Screenshot](./media/image88.png)
>
> ![Screenshot](./media/image89.png)

40. Chiudere **Esplora file** e disconnettersi da **SEA-SVR2**.

**Risultati**: dopo aver completato questo esercizio, Microsoft
Deployment Toolkit sarà stato utilizzato correttamente per creare e
distribuire una workstation Windows 11.
