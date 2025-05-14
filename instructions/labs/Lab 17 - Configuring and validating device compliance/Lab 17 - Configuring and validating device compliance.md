Lab17 - Configurazione e convalida della conformità dei dispositivi

**Sommario**

In questo lab viene convalidata la conformità del dispositivo
configurando un criterio di conformità e una regola di accesso
condizionale associata usata per determinare lo stato di un dispositivo
gestito.

**Prerequisiti**

I seguenti laboratori devono essere completati prima di questo
laboratorio:

- Lab \#1- Gestione delle identità nell'ID Microsoft Entra

- Lab \#2- Sincronizzazione delle identità tramite Microsoft Entra
  Connect

- Lab \#5- Gestire la registrazione dei dispositivi in Microsoft Intune

- Lab \#6- Registrazione dei dispositivi in Microsoft Intune

- Lab \#7- Creazione e distribuzione dei profili di configurazione

Exercise 1: Configurazione dei criteri di conformità.

**Scenario**

Contoso vuole assicurarsi che i dispositivi Windows registrati in
Microsoft Intune soddisfino una specifica di configurazione minima. Di
seguito sono richieste le specifiche:

- Versione minima del sistema operativo Windows:10.0.19041.329

- Microsoft Defender Antimalware richiesto.

Se un dispositivo soddisfa questi requisiti, verrà contrassegnato come
conforme. Se il dispositivo non soddisfa questi requisiti, deve essere
contrassegnato come non conforme.

Task 1: Creare e assegnare un criterio di conformità

1.  Accedi a
    [***SEA-SVR1***](urn:gd:lg:a:select-vm) come !!**[Contoso\Administrator](urn:gd:lg:a:send-vm-keys)!!** Con
    la password !!**[Pa55w.rd](urn:gd:lg:a:send-vm-keys)!!** 

2.  Nella barra delle applicazioni, selezionare **Microsoft Edge**. In
    Microsoft Edgetype !!**https://Intune.microsoft.com!!** nella barra
    degli indirizzi, quindi premere **Invio**.

3.  Accedere con le credenziali di **amministratore tenant di Office
    365**.

> ![A screenshot of a computer Description automatically
> generated](./media/image1.png)

4.  Dal riquadro di spostamento selezionare **Dispositivi**, quindi
    selezionare Conformità in **Gestisci dispositivi.**

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)
>
> Sulla **conformità** | Criteri, nel riquadro dei dettagli
> selezionare + **Crea criterio.**
>
> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)

- Nel pannello **Crea un criterio** specificare il valore seguente e
  selezionare **Crea**:

- Piattaforma: **Windows 10 e versioni successive**

> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

5.  Nella scheda Informazioni di **base** specificare il valore seguente
    e selezionare **Avanti**:

    - Nome: !!**[Compliance1](urn:gd:lg:a:send-vm-keys)!!**

> ![](./media/image5.png)

6.  Nella scheda **Impostazioni di conformità** espandere Integrità
    dispositivo ed esaminare le **impostazioni disponibili.**

> ![A screenshot of a computer Description automatically
> generated](./media/image6.png)

7.  Nella scheda **Impostazioni di conformità,** espandere **Proprietà
    dispositivo**. Nel campo Versione **minima del sistema operative**
    tipo!!**[10.0.19041.329](urn:gd:lg:a:send-vm-keys)!!**

> ![A screenshot of a computer Description automatically
> generated](./media/image7.png)

8.  Nella scheda **Impostazioni di conformità**, espandere **Sicurezza
    del sistema**. Impostare **Microsoft Defender Antimalware** su
    Richiedi e quindi selezionare **Avanti**.

> ![](./media/image8.png)

9.  Nella scheda **Azioni per non conformità**, si noti che l'azione per
    **contrassegnare l'impostazione predefinita** del dispositivo non
    conforme è **immediatamente**.

> ![A screenshot of a computer Description automatically
> generated](./media/image9.png)
>
> Esaminare come configurare il numero di giorni dopo i quali il
> dispositivo viene contrassegnato come non conforme e configurare
> azioni aggiuntive.

10. Seleziona **Avanti**. Nella scheda **Assegnazioni**, selezionare
    **Aggiungi gruppi**. Seleziona dispositivi **Windows**, scegliere
    **Seleziona**, quindi selezionare **Avanti**.

> ![A screenshot of a computer Description automatically
> generated](./media/image10.png)
>
> **Nota**: Il gruppo **Dispositivi Windows** è stato creato in
> Creazione e distribuzione dei profili di configurazione - Lab.
>
> Selezionare **Crea**.
>
> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)

11. Nel menu di spostamento selezionare **Dispositivi**, quindi nel
    riquadro di spostamento Dispositivi selezionare **Conformità**.

> ![A screenshot of a computer Description automatically
> generated](./media/image12.png)

12. Nella pagina **Conformità** selezionare **Impostazioni di
    conformità**.

> ![A screenshot of a computer Description automatically
> generated](./media/image13.png)

13. Nella pagina **Impostazioni criteri di conformità,** accanto a
    Contrassegna i **dispositivi a cui non è stato assegnato alcun
    criterio di conformità**, selezionare **Non conforme**, quindi
    selezionare **Salva**.

> ![A screenshot of a computer Description automatically
> generated](./media/image14.png)
>
> Questa impostazione garantisce che tutti i dispositivi a cui non è
> assegnato un criterio di conformità vengano impostati su **Non
> conforme.**

**Risultati**: dopo aver completato questo esercizio, sarà stato
configurato correttamente un criterio di conformità.

Esercizio 2: Creazione di criteri di accesso condizionale per applicare
la conformità.

**Scenario**

Quando un utente utilizza un dispositivo contrassegnato come non
conforme, non dovrebbe essere in grado di accedere alla posta
elettronica. È stato chiesto di configurare un criterio di accesso
condizionale che applica questa regola e di verificare che funzioni come
previsto.

Task 1: Creare un criterio di accesso condizionale

1.  On [***SEA-SVR1***](urn:gd:lg:a:select-vm), nell'interfaccia di
    amministrazione di **Microsoft Intune selezionare Dispositivi**,
    quindi selezionare **Accesso condizionale.**

> ![A screenshot of a computer Description automatically
> generated](./media/image15.png)

2.  Fare clic su **Criteri**, quindi selezionare + **Nuovo criterio**,

> ![A screenshot of a computer Description automatically
> generated](./media/image16.png)

3.  Nel pannello **Nuovo**, nella casella di testo **Nome**, digitare !!
    Condizionale1!! e quindi selezionare **0 utenti o identità del
    carico di lavoro selezionate**.

> ![A screenshot of a computer Description automatically
> generated](./media/image17.png)
>
> Nel pannello **Utenti e gruppi** selezionare il pulsante di opzione
> Tutti gli **utenti**.
>
> ![A screenshot of a computer screen Description automatically
> generated](./media/image18.png)

4.  Sulla **nuova** lama, selezionare **Nessuna risorsa di destinazione
    selezionata**, selezionare il pulsante di opzione **Seleziona app**,
    scegliere!!**Office 365 Exchange Online!!**, e quindi fare clic su
    **Seleziona**

> ![A screenshot of a computer Description automatically
> generated](./media/image19.png)

5.  Nella sezione **Condizioni** del **nuovo** pannello selezionare **0
    condizioni selezionate.**

> ![A screenshot of a computer Description automatically
> generated](./media/image20.png)

6.  Nell'elenco delle condizioni, in **Piattaforme dispositivo**,
    selezionare **Non configurato**. Nella sezione **Configura**
    selezionare **Sì**, selezionare il pulsante di opzione **Seleziona
    piattaforme dispositivo**, selezionare la casella di controllo
    **Windows**, , quindi seleziona **Fine**.

> ![A screenshot of a computer Description automatically
> generated](./media/image21.png)

7.  Nel pannello **Nuovo** in **Controlli di accesso,** nella sezione
    Concedi selezionare **0 controlli selezionati.**

> Selezionare la casella di controllo **Richiedi che il dispositivo sia
> contrassegnato come conforme** e quindi selezionare **Seleziona**.
>
> ![A screenshot of a computer Description automatically
> generated](./media/image22.png)

8.  Nel pannello **Nuovo** selezionare Attivato per l'opzione Abilita
    criteri, quindi selezionare **Crea**.

> ![A screenshot of a computer Description automatically
> generated](./media/image23.png)

9.  Chiudi Microsoft Edge.

Task 2: Verificare che i criteri di accesso condizionale funzionino

1.  Passare a [***SEA-WS3***](urn:gd:lg:a:select-vm) e accedi
    come!!**[Admin](urn:gd:lg:a:send-vm-keys)!!** con la password
    di !!**[Pa55w.rd](urn:gd:lg:a:send-vm-keys)!!**.

2.  Su [***SEA-WS3***](urn:gd:lg:a:select-vm), sulla barra delle
    applicazioni, seleziona Microsoft Edge. In **Microsoft Edge**,
    tipo [**outlook.office.com**](urn:gd:lg:a:send-vm-keys) e quindi
    premere INVIO.

3.  Nella finestra di dialogo Seleziona un conto,
    seleziona!!**Cindy@M365xXXXXXXX.onmicrosoft.com!!**

4.  Nella pagina **Inserisci password**,
    inserisci!!**P@55w.rd12345!!** e seleziona **Accedi**. Se viene
    visualizzata la richiesta di salvataggio della password di Microsoft
    Edge, selezionare **Aggiorna**.

> ![A screenshot of a computer error Description automatically
> generated](./media/image24.png)

5.  Verificare di aver ricevuto il messaggio **"** **Accedi con il tuo
    account di lavoro "**.

> ![A screenshot of a computer Description automatically
> generated](./media/image25.png)

6.  Seleziona **Altri dettagli**. Dovresti vedere altre informazioni sul
    motivo per cui sei bloccato.

> ![A screenshot of a computer error Description automatically
> generated](./media/image26.png)
>
> **Nota**: ciò è dovuto al fatto che SEA-WS3 non è aggiunto all'ID
> Microsoft Entra e non è gestito da Microsoft Intune, quindi non è
> contrassegnato come conforme.

7.  **Chiudi** la finestra del browser.

8.  Passare a [***SEA-WS1***](urn:gd:lg:a:select-vm), e accedi
    come!!**Cindy@M365xXXXXXXX.onmicrosoft.com!!** con
    **password** pagina , entra !!**P@55w.rd12345!!** 

> **Nota**: SEA-WS1 è un dispositivo Windows 11 gestito registrato in
> Intune.

9.  Sulla barra delle applicazioni, seleziona **Microsoft Edge.** In
    Microsoft Edge digitare Outlook.office.com e quindi premere
    **INVIO**.

10. Verifica di poter accedere alla cassetta postale di Cindy.

> ![A screenshot of a computer Description automatically
> generated](./media/image27.png)
>
> **Nota**: ciò è dovuto al fatto che **SEA-WS1** è un dispositivo
> gestito e contrassegnato come conforme.

11. Chiudi Microsoft Edge ed esci da
    [***SEA-WS1***](urn:gd:lg:a:select-vm).

Task 3: Disabilitare i criteri di accesso condizionale

1.  Su [***SEA-SVR1***](urn:gd:lg:a:select-vm), nel centro di
    **amministrazione di Microsoft**
    Intune!\!<https://intune.microsoft.com>!! seleziona **Dispositivi**,
    quindi seleziona **Tutti i dispositivi.**

> ![](./media/image28.png)
>
> Si noti che **SEA-WS1** è conforme, motivo per cui Cindy è stata
> autorizzata ad accedere alla sua cassetta postale.

2.  Nel riquadro di spostamento selezionare **Dispositivi**, quindi
    selezionare **Accesso condizionale**.

> ![](./media/image29.png)
>
> Nella pagina **Accesso condizionale** selezionare **Criteri**, quindi
> fare clic su **Condizionale1**.
>
> ![A screenshot of a computer Description automatically
> generated](./media/image30.png)

3.  Nella pagina **Condizionale1**, nella parte inferiore della pagina,
    selezionare Disattivato e quindi selezionare **Salva**.

> Risultati: dopo aver completato questo esercizio, sarà stato
> configurato correttamente un criterio di accesso condizionale per
> determinare la conformità del dispositivo ![A screenshot of a computer
> Description automatically generated](./media/image31.png)

4.  Chiudi Microsoft Edge.

**Risultati**: dopo aver completato questo esercizio, sarà stato
configurato correttamente un criterio di accesso condizionale per
determinare la conformità del dispositivo
