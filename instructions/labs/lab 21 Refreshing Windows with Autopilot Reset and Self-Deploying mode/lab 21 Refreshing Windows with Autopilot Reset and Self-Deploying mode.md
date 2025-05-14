Lab 21: Aggiornamento di Windows con la reimpostazione di Autopilot e la
modalità di distribuzione automatica.

**Sommario**

In questo laboratorio imparerai come eseguire un reset remoto
dell'Autopilot.

**Prerequisiti**

I seguenti laboratori devono essere completati prima di questo
laboratorio:

- Lab 01- Gestione delle identità nell'ID Microsoft Entra

- Lab 02- Sincronizzazione delle identità tramite Azure AD Connect

- Lab 21- Distribuzione di Windows 11 tramite Microsoft Deployment
  Toolkit

- Lab 20- Distribuzione di Windows 11 con Autopilot

**Scenario**

SEA-WS4 è stato distribuito utilizzando Windows Autopilot. È necessario
testare un altro scenario di provisioning che prevede la reimpostazione
di Autopilot. Verrà creato un nuovo profilo di distribuzione configurato
con la modalità di distribuzione automatica di Windows Autopilot.

Task 1: Configurare un profilo di distribuzione di Windows Autopilot con
distribuzione automatica

1.  Passare a [***SEA-SVR1***](urn:gd:lg:a:select-vm).

> ![](./media/image1.png)

2.  In **Microsoft Edge**, apri una nuova scheda e vai a
    [**https://intune.microsoft.com**](https://intune.microsoft.com). Se
    richiesto, accedi
    con [**admin@M365xXXXXXXXX.onmicrosoft.com**](mailto:admin@M365xXXXXXXXX.onmicrosoft.com) e paswword.

3.  Nell'interfaccia di **amministrazione di Microsoft Intune**
    selezionare **Dispositivi**.

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)
>
> Nella sezione **Onboarding del dispositivo** selezionare
> **Registrazione**.
>
> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)

4.  Nel pannello Registrazione di Windows, nel riquadro dei dettagli,
    selezionare **Profili di distribuzione.**

> ![](./media/image4.png)

5.  Nel pannello **Profili di distribuzione di Windows** AutoPilot,
    selezionare **Contoso Profile 1** e quindi selezionare
    **Proprietà**.![](./media/image5.png)

> ![A screenshot of a computer Description automatically
> generated](./media/image6.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image7.png)

6.  Scorri verso il basso fino a **Assegnazioni**, quindi seleziona
    **Modifica**.

> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)

7.  Accanto a **Dispositivi IT**, seleziona **Rimuovi**.

> ![](./media/image9.png)

8.  Seleziona **Rivedi e salva**, quindi seleziona **Salva**.

> ![A screenshot of a computer Description automatically
> generated](./media/image10.png)

9.  Chiudere il **profilo Contoso 1|Pagina Proprietà.**

10. Nel pannello **Profili di distribuzione di Windows AutoPilot**,
    seleziona **Crea profilo** e quindi seleziona **PC Windows**.![A
    screenshot of a computer Description automatically
    generated](./media/image11.png)

11. Nella casella di testo **Nome** della scheda Informazioni di
    **base** type [**Contoso profile 2**](urn:gd:lg:a:send-vm-keys).

12. Per **Converti tutti i dispositivi di destinazione in Autopilot**,
    selezionare **No** e quindi selezionare **Avanti**.

> ![](./media/image12.png)

13. Nella scheda **Configurazione guidata (Out-of-box experience),**
    assicurarsi che la modalità di **distribuzione sia impostata** su
    **Distribuzione automatica.**

> ![](./media/image13.png)

14. Assicurarsi che siano impostate le seguenti opzioni:

    - Lingua (Regione): **Impostazione predefinita del sistema
      operativo**

    - Configura automaticamente la tastiera: **Sì**

    - Applica il modello di nome del dispositivo: **Sì**

    - Inserire un nome [**Contoso-%RAND:2%**](urn:gd:lg:a:send-vm-keys)

> ![A screenshot of a computer Description automatically
> generated](./media/image14.png)

15. Selezionare **Avanti**.

16. Nella scheda **Assegnazioni**, in **Gruppi inclusi**, selezionare
    **Aggiungi gruppi.**

> ![A screenshot of a computer Description automatically
> generated](./media/image15.png)

17. Selezionare il gruppo **Dispositivi IT** e fare clic su
    **Seleziona**. Seleziona **Avanti**.

> ![](./media/image16.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image17.png)

18. Nel pannello **Rivedi** + **crea**, esaminare le informazioni e
    quindi selezionare **Crea**.

> ![A screenshot of a computer Description automatically
> generated](./media/image18.png)

Task 2: Eseguire un ripristino dell'Autopilot

1.  Nell'interfaccia di amministrazione di Microsoft Intune selezionare
    **Dispositivi** e quindi selezionare **Tutti i dispositivi.**

> Selezionare l'Autopilot PC (inizia con il nome DESKTOP).
>
> ![A screenshot of a computer Description automatically
> generated](./media/image19.png)

2.  Nella barra dei menu selezionare l'ellisse e quindi selezionare
    **Reimpostazione Autopilot.**

> ![A screenshot of a computer Description automatically
> generated](./media/image20.png)

3.  Al prompt dei messaggi, selezionare **Sì**.

> ![A screenshot of a computer Description automatically
> generated](./media/image21.png)

4.  Passare a  [***SEA-SVR2***](urn:gd:lg:a:select-vm) e massimizzare la
    finestra **SEA-WS4.**

> **Nota:** SEA-WS4 dovrebbe essere ancora in esecuzione dal laboratorio
> precedente

5.  **Nota:** aggiorna il dispositivo all'ultima versione e quindi fai
    clic su Riavvia.

6.  Riavvio **SEA-WS4**.

> ![A screenshot of a computer Description automatically
> generated](./media/image22.png)
>
> **Nota**: questo processo può richiedere 30 minuti e si riavvia più
> volte durante il processo. L'istruttore può continuare con il modulo
> successivo mentre questa attività viene completata. Assicurati di
> tornare per completare l'attività 3 durante la prossima sessione di
> laboratorio.

Task 3: Verificare l'installazione del pilota automatico

1.  Nella pagina di accesso, inserisci
    [**Cindy@M365x19242953.onmicrosoft.com**](mailto:Cindy@M365x19242953.onmicrosoft.com) con
    la Password di  [**P@55w.rd1234**](mailto:P@55w.rd1234).

2.  In **Usa Windows Hello con il tuo account**, seleziona **OK**.

> ![A screenshot of a computer Description automatically
> generated](./media/image23.png)

3.  Nella pagina **Verifica la tua identità**, seleziona il metodo di
    verifica del testo.

4.  Nella pagina **Inserisci codice**, inserisci il codice che è stato
    inviato al tuo dispositivo mobile, quindi seleziona **Verifica**.

> ![A screenshot of a computer Description automatically
> generated](./media/image24.png)

5.  Nella finestra di dialogo **Configura un PIN**, nei campi **Nuovo
    PIN** e **Conferma PIN**, entrare
    [**102938**](urn:gd:lg:a:send-vm-keys), e quindi selezionare **OK**.

> ![](./media/image25.png)

6.  Sul **set Tutti**! , selezionare **OK**.

7.  Seleziona **Start** e seleziona **Impostazioni**.

> ![](./media/image26.png)

8.  Selezionare **Account** e quindi **Accedi all'azienda o all'istituto
    di istruzione**. Verificare che il dispositivo sia connesso ad Azure
    AD di Contoso.

> ![](./media/image27.png)

9.  Selezionare **Connesso ad Azure AD di Contoso** e selezionare
    **Informazioni**.

> ![](./media/image28.png)
>
> Nella pagina **Gestito da Contoso** scorrere verso il basso e quindi
> selezionare **Sincronizza**.
>
> ![](./media/image29.png)

10. Su **SEA-WS4**, chiudere la finestra **Impostazioni**.

11. Arrestare **SEA-WS4** e chiudere la finestra **SEA-WS4**.

12. Su [***SEA-SVR2***](urn:gd:lg:a:select-vm), chiudere la console di
    gestione di Hyper-V.

**Risultat**i: dopo aver completato questo esercizio, sarà stato
effettuato il provisioning di un dispositivo Windows 11 con la
reimpostazione di Autopilot utilizzando la modalità di distribuzione
automatica.
