Lab 20: Distribuzione di Windows 11 con Autopilot

**Summary**

In questo lab si apprenderà come effettuare il provisioning di un
dispositivo Windows 11 con Autopilot usando la modalità guidata
dall'utente.

**Prerequisiti**

I seguenti laboratori devono essere completati prima di questo
laboratorio:

- Lab 01- Gestione delle identità nell'ID Microsoft Entra

- Lab 02- Sincronizzazione delle identità tramite Azure AD Connect

- Lab 11- Distribuzione di Windows 11 tramite Microsoft Deployment
  Toolkit

**Scenario**

Contoso IT sta pianificando di implementare una distribuzione di nuovi
dispositivi Windows 11 usando Autopilot. I dispositivi hanno
un'installazione predefinita di Windows 11. Gli utenti devono essere in
grado di connettere il dispositivo, accenderlo e rispondere a domande
minime durante la configurazione guidata, usando le credenziali dell'ID
Microsoft Entra per accedere. Il processo dovrebbe registrare e unirsi
automaticamente al dominio Entra ID. È stato chiesto di configurare e
testare l'esperienza utilizzando SEA-WS4, che è stato installato e
configurato di recente utilizzando Hyper-V.

Task 1: Creare un gruppo nell'interfaccia di amministrazione di
Microsoft Entra.

1.  Passa e accedi a [***SEA-SVR1***](urn:gd:lg:a:select-vm) come
    !!  con la password [**Pa55w.rd**](urn:gd:lg:a:send-vm-keys) e
    chiudere il **server** **Manager**.**Contoso\Administrator**!! Con
    la password !!!!  e chiudi **Server Manager**.

2.  Sulla barra delle applicazioni, seleziona **Microsoft Edge.**

3.  In Microsoft Edge, nella barra degli indirizzi, digita!!﷟HYPERLINK
    "https://entra.microsoft.com"**ttps://entra.microsoft.com**!!, e
    quindi premere INVIO. Se richiesto, accedi con la tua e la
    password.[**admin@M365xXXXXXXXX.onmicrosoft.com**](mailto:admin@M365xXXXXXXXX.onmicrosoft.com)!!
     e la password.

4.  ![](./media/image1.png)

5.  Nel riquadro di spostamento selezionare **Identità**.

> In **Identità**, seleziona **Gruppi**.
>
> ![](./media/image2.png)

6.  Nei **Gruppi** | pannello **Tutti i gruppi**, selezionare **Nuovo
    gruppo**.

> ![](./media/image3.png)

7.  Nel pannello **Nuovo gruppo**, nell'elenco **Tipo di gruppo**,
    selezionare **Sicurezza**.

8.  Nella casella **Nome gruppo** digitare!!﷟HYPERLINK
    "http://urn:gd:lg:a:send-vm-keys"**IT Devices**!!.

9.  Nella casella **Descrizione gruppo** digitare!!﷟HYPERLINK
    "http://urn:gd:lg:a:send-vm-keys"**IT Department Devices**!!.

10. Nell'elenco Tipo di appartenenza selezionare **Dispositivo
    dinamico**.

> Selezionare **Aggiungi query dinamica**.
>
> ![](./media/image4.png)

11. Nel pannello Regole di **appartenenza dinamica selezionare**
    **Modifica** sopra la casella **Sintassi regola.**

> ![](./media/image5.png)

12. Nella casella di testo Modifica sintassi regola aggiungere la
    seguente regola di appartenenza semplice e selezionare OK.

13. !!(device.devicePhysicalIDs -any (\_ -contains "\[ZTDId\]"))!!

> ![](./media/image6.png)

14. Seleziona **Salva** per chiudere **le regole di appartenenza
    dinamiche**, quindi seleziona Crea per **creare** il gruppo.

> ![A screenshot of a computer Description automatically
> generated](./media/image7.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)
>
> ![](./media/image9.png)

Task 2: Generare un file CSV (comma-separated value) specifico del
dispositivo

Passare a SEA-SVR2 ed effettuare l'accesso come
[**Contoso\Administrator**](urn:gd:lg:a:send-vm-keys) con la password
di !!﷟HYPERLINK "http://urn:gd:lg:a:send-vm-keys"**Pa55w.rd**!!.

> ![A screenshot of a computer Description automatically
> generated](./media/image10.png)

1.  Seleziona **Hyper-V Manager** nella barra delle applicazioni.

> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)

2.  In Macchine virtuali fare clic con il pulsante destro del mouse su
    **SEA-WS4** e selezionare **Connetti**.

> ![](./media/image12.png)

3.  Nella finestra **SEA-WS4**, selezionare **Avvia**. All'avvio del
    computer, ingrandire la finestra.

> ![A screenshot of a computer Description automatically
> generated](./media/image13.png)

4.  Accedere a **SEA-WS4** come amministratore con la password
    di!!﷟HYPERLINK "http://urn:gd:lg:a:send-vm-keys"**Pa55w.rd**!!.

> ![A screenshot of a computer Description automatically
> generated](./media/image14.png)

5.  Fare clic con il pulsante destro del mouse su **Start**, selezionare
    **Terminale Windows (amministratore),** , quindi selezionare Sì al
    **prompt** di **Controllo dell'account utente.**

> ![](./media/image15.png)
>
> ![A screenshot of a computer error Description automatically
> generated](./media/image16.png)

6.  Al prompt della riga di comando di Windows PowerShell digitare il
    cmdlet seguente e quindi premere **INVIO**:

> !! Install-Script -Name Get-WindowsAutoPilotInfo!!

![A screenshot of a computer Description automatically
generated](./media/image17.png)

7.  Riceverai tre richieste. Ogni volta, digitare Y e quindi premere
    **INVIO**.

> ![](./media/image18.png)

8.  Al prompt della riga di comando di Windows PowerShell digitare il
    cmdlet seguente e quindi premere **INVIO**:

> !!**Set**-ExecutionPolicy *RemoteSigned*!!

9.  Quando richiesto, digitare Y e quindi premere INVIO.

10. Al prompt della riga di comando di Windows PowerShell digitare il
    cmdlet seguente e quindi premere **INVIO**:

> !!Get-WindowsAutoPilotInfo.ps1 -OutputFile C:\Computer.csv!!
>
> ![](./media/image19.png)

11. Al prompt della riga di comando di Windows PowerShell digitare il
    comando seguente, premere **INVIO** e quindi esaminare il contenuto
    del file:

12. **type** !!C:\Computer.csv!!

> ![](./media/image20.png)

13. Al prompt della riga di comando di Windows PowerShell digitare il
    comando seguente, quindi premere **INVIO**. In questo modo il file
    verrà copiato in **SEA-SVR2**:

14. copy !!c:\computer.csv \\sea-svr2\labfiles!!

> ![A screenshot of a computer screen Description automatically
> generated](./media/image21.png)

15. Chiudere il prompt dei comandi di Windows PowerShell.

Task 3: Usare un profilo di distribuzione di Windows Autopilot

1.  Passare a [***SEA-SVR1***](urn:gd:lg:a:select-vm).

> ![](./media/image22.png)

2.  In **Microsoft Edge**, apri una nuova scheda e naviga
    to !!﷟HYPERLINK
    "https://intune.microsoft.com"**https://intune.microsoft.com**!! Se
    richiesto, accedi con una
    password.[**admin@M365xXXXXXXX.onmicrosoft.com**](mailto:admin@M365xXXXXXXX.onmicrosoft.com)!!
    e password.

3.  Nell'interfaccia di amministrazione di **Microsoft Intune
    selezionare Dispositivi**.

4.  Nella sezione **Registrazione dispositivi** selezionare **Registra
    dispositivi**.

5.  Nel riquadro dei dettagli scorrere verso il basso fino a Programma
    di **distribuzione di Windows Autopilot,** quindi selezionare
    **Dispositivi**.

> ![A screenshot of a computer Description automatically
> generated](./media/image23.png)

6.  Nel pannello **Dispositivi di Windows Autopilot** sulla barra dei
    menu, selezionare **Importa**, selezionare **l'icona della**
    **cartella** e quindi navigare su !!﷟HYPERLINK
    "http://urn:gd:lg:a:send-vm-keys"**\\SEA-SVR2\Labfiles**!!,
    sceglie **Computer.csv**, seleziona **Apri**, quindi seleziona
    **Importa**.

> ![](./media/image24.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image25.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image26.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image27.png)
>
> **Nota**: il processo di importazione può richiedere fino a 15 minuti,
> ma normalmente richiede circa 5 minuti.

7.  **Importante**: al termine del processo, il dispositivo potrebbe non
    essere visualizzato. In questo caso, selezionare il pulsante
    Sincronizza, attendere alcuni minuti, quindi selezionare
    **Aggiorna**.

8.  **Selezionare** X per chiudere il pannello dei **dispositivi Windows
    Autopilot**.

> ![](./media/image28.png)

9.  Nel pannello Registrazione di Windows, nel riquadro dei dettagli,
    **selezionare Profili di distribuzione.**

> Nel pannello Profili di distribuzione di Windows Autopilot selezionare
> Crea profilo e quindi selezionare PC Windows ![](./media/image29.png)
>
> **Nel pannello Profili di distribuzione di Windows** AutoPilot
> selezionare **Crea profilo** e quindi **selezionare PC
> Windows**.![](./media/image30.png)

10. Nella casella di testo **Nome** della scheda Informazioni di
    **base** digitare !!﷟HYPERLINK
    "http://urn:gd:lg:a:send-vm-keys"**Contoso profile1**!!.

> Per **Converti tutti i dispositivi di destinazione in Autopilot,**
> selezionare **No** e quindi selezionare **Avanti**.![A screenshot of a
> computer Description automatically generated](./media/image31.png)

11. Nella scheda **Configurazione guidata (Out-of-box experience)**
    assicurarsi che la modalità di **distribuzione sia impostata** su
    **Guidata dall'utente.**

12. Assicurarsi che l'opzione **Partecipa all'ID Microsoft Entra come**
    sia impostata su **Aggiunto a Microsoft Entra. Ensure that the
    following options are set**:

    - Condizioni di licenza software Microsoft: **Nascondi**

    - Impostazioni privacy: **Nascondi**

    - Nascondi le opzioni di modifica dell'account: **Nascondi**

    - Tipo di account utente: **Amministratore**.

    - Consenti distribuzione con provisioning anticipato: **No**

    - Lingua (Regione): **Impostazione predefinita del sistema
      operativo**

    - Configura automaticamente la tastiera: **Sì**

13. Applica il modello di nome del dispositivo: **No**

14. Selezionare **Avanti**

> ![](./media/image32.png)

15. Nella scheda **Assegnazioni**, in **Gruppi inclusi**, selezionare
    **Aggiungi gruppi.**

16. Selezionare **il gruppo Dispositivi** IT e fare **clic su
    Seleziona**. Seleziona **Avanti**.

> ![](./media/image33.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image34.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image35.png)

17. Nel pannello **Rivedi** + **crea** esaminare le informazioni e
    quindi selezionare **Crea**.

> ![A screenshot of a computer Description automatically
> generated](./media/image36.png)
>
> ![](./media/image37.png)

Task 4: Ripristinare il PC

1.  Passare a [***SEA-SVR2***](urn:gd:lg:a:select-vm). Il computer
    SEA-WS4 dovrebbe essere ancora ingrandito.

> ![](./media/image38.png)

2.  Su **SEA-WS4,** selezionare **Start**, digitare !!﷟HYPERLINK
    "http://urn:gd:lg:a:send-vm-keys"**reset**!!  e seleziona
    **Reimposta questo PC.**

> ![](./media/image39.png)

3.  Nella sezione **Reimposta questo PC**, seleziona **Reimposta PC.**

> ![A screenshot of a computer Description automatically
> generated](./media/image40.png)

4.  Seleziona **Rimuovi tutto,** quindi seleziona **Reinstallazione
    locale.**

> ![A blue screen with white text Description automatically
> generated](./media/image41.png)
>
> ![A blue screen with white text Description automatically
> generated](./media/image42.png)
>
> Seleziona **Avanti**, quindi seleziona **Reimposta**.![A screenshot of
> a computer Description automatically generated](./media/image43.png)
>
> ![A blue screen with white text Description automatically
> generated](./media/image44.png)
>
> **Nota**: in genere questa attività non è necessaria per la nuova
> distribuzione di dispositivi fisici. Le informazioni sull'autopilota
> del dispositivo vengono fornite dal produttore o possono essere
> ottenute dal dispositivo prima della configurazione guidata. Ai fini
> di questo laboratorio, è necessario avviare un reset per simulare una
> nuova configurazione guidata del dispositivo.

**Nota**: questo processo può richiedere 45-60 minuti e si riavvierà più
volte durante il processo. L'istruttore può continuare con il modulo
successivo mentre questa attività viene completata. Assicurati di
tornare per completare l'attività 5 durante la prossima sessione di
laboratorio.Task 5: Verify Autopilot deployment

1.  Nella pagina di **accesso di Contoso Corp**., enter  !!﷟HYPERLINK
    "mailto:Cindy@M365x19242953.onmicrosoft.com"**Cindy@M365x19242953.onmicrosoft.com**!!
    e selezionare **Avanti**.

2.  Nella pagina Password, inserisci !!﷟HYPERLINK
    "mailto:P@55w.rd1234"**P@55w.rd1234**!! and selezionare **Accedi**.

3.  In **Usa Windows Hello con il tuo account**, seleziona **OK**.

> ![A screenshot of a computer Description automatically
> generated](./media/image45.png)

4.  Nella pagina **Verifica la tua identità**, seleziona il metodo di
    verifica del testo.

> ![A screenshot of a computer Description automatically
> generated](./media/image46.png)

5.  Nella pagina **Inserisci codice**, inserisci il codice che è stato
    inviato al tuo dispositivo mobile, quindi seleziona **Verifica**.

> ![A screenshot of a computer Description automatically
> generated](./media/image47.png)

6.  Nella finestra di **dialogo Configura un PIN**, nei campi **Nuovo
    PIN** e **Conferma PIN** immettere 102938 e quindi selezionare
    **OK**.

> Seleziona Start e seleziona Impostazioni.![A screenshot of a computer
> Description automatically generated](./media/image48.png)

7.  Sul **set Tutti**! , selezionare **OK**.

8.  Seleziona **Start** e seleziona **Impostazioni**.

> ![A screenshot of a computer Description automatically
> generated](./media/image49.png)

9.  Selezionare **Account** e quindi **Accedi all'azienda o
    all'istituto** di istruzione. Verificare che il dispositivo sia
    connesso ad Azure AD di Contoso.

> ![A screenshot of a computer Description automatically
> generated](./media/image50.png)

10. Selezionare **Connesso ad Azure AD di Contoso** e selezionare
    **Informazioni**.

> ![A screenshot of a computer Description automatically
> generated](./media/image51.png)

11. Nella pagina **Gestito da Contoso** scorrere verso il basso e quindi
    selezionare **Sincronizza**.

> ![A screenshot of a computer Description automatically
> generated](./media/image52.png)
>
> ![](./media/image53.png)

12. Su **SEA-WS4**, chiudere la finestra **Impostazioni**.

13. Passare a  [***SEA-SVR1***](urn:gd:lg:a:select-vm).

14. Nell'interfaccia di amministrazione di Microsoft Entra, selezionare
    **Identità**, selezionare **Dispositivi**, quindi selezionare
    **Tutti i dispositivi.**

> ![](./media/image54.png)
>
> Si noti che il nuovo dispositivo viene visualizzato con un nome che
> inizia con "**DESKTOP-**". Si noti inoltre che il tipo di join è
> **l'ID Microsoft Entra** unito a Cindy White come proprietario.
>
> Selezionare il dispositivo Autopilot. Esamina le opzioni di gestione
> lungo la barra dei menu in alto.
>
> Si noti che è possibile **ritirare**, **cancellare**,
> **sincronizzare** e **riavviare** il dispositivo.

15. Seleziona l'ellisse alla fine della barra dei menu e prendi nota
    delle funzionalità di gestione aggiuntive.

> ![A screenshot of a computer Description automatically
> generated](./media/image55.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image56.png)
>
> Le funzionalità aggiuntive includono Fresh Start, Autopilot Reset,
> Scansione rapida, Scansione completa e altre.

Chiudere Microsoft Edge

**Risultati:** dopo aver completato questo esercizio, sarà stato
effettuato il provisioning di un dispositivo Windows 11 con Autopilot
utilizzando la modalità guidata dall'utente.
