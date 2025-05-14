Lab 23: Gestione degli aggiornamenti della qualità e delle funzionalità
di Windows

**Sommario**

In questo lab si configureranno le impostazioni di aggiornamento della
qualità e delle funzionalità di Windows usando Intune.

**Prerequisiti**

I seguenti laboratori devono essere completati prima di questo
laboratorio:

- Lab 01- Gestire la registrazione dei dispositivi in Intune

- Lab 06- Registrazione dei dispositivi in Intune

- Lab 07- Creazione e distribuzione dei profili di configurazione

**Nota**: sarà inoltre necessario un telefono cellulare in grado di
ricevere messaggi di testo utilizzati per proteggere l'autenticazione di
accesso a Windows Hello in Azure AD.

**Scenario**

È stato chiesto di configurare un anello di aggiornamento in modo che
influisca solo sui dispositivi membri del gruppo Contoso Developer
Devices. Questo gruppo deve soddisfare i seguenti requisiti:

- Periodo di differimento dell'aggiornamento qualitativo
  (giorni): **15**

- Periodo di differimento dell'aggiornamento delle funzionalità
  (giorni):**45**

- Opzione per mettere in pausa gli aggiornamenti di Windows:
  **Disabilita**

- Opzione per verificare la disponibilità di aggiornamenti di Windows:
  **Abilita**

- Ottimizzazione della consegna: Modalità download: **solo HTTP, no
  peering (0)**

Task 1: Verificare le impostazioni di aggiornamento correnti per un
singolo dispositivo

1.  Passare a [***SEA-WS1***](urn:gd:lg:a:select-vm), accedi come Cindy
    White con il PIN [**102938**](urn:gd:lg:a:select-vm).

2.  Seleziona **Start**, quindi seleziona l'icona **Impostazioni**.

> Si noti che è possibile sospendere gli aggiornamenti per un
> determinato periodo di tempo
>
> ![](./media/image1.png)

3.  In **Impostazioni**, seleziona **Windows Update.**

> Si noti che è possibile sospendere gli aggiornamenti per un
> determinato periodo di tempo.

4.  Nella pagina **Windows Update** selezionare **Opzioni avanzate**.

> ![](./media/image2.png)

5.  Nella pagina **Opzioni avanzate** selezionare **Ottimizzazione
    recapito.**

> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)

6.  Nella pagina **Ottimizzazione recapito**, verifica che l'opzione
    **Consenti download da altri PC** sia abilitata.

7.  Seleziona **Dispositivi su Internet e la mia rete locale**.

> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

8.  In **Impostazioni**, seleziona **Windows Update**.

> ![A screenshot of a computer Description automatically
> generated](./media/image5.png)

9.  Seleziona **Opzioni avanzate**, quindi seleziona **Criteri di
    aggiornamento configurati.**

> ![A screenshot of a computer Description automatically
> generated](./media/image6.png)
>
> Si noti che sul dispositivo non sono impostati criteri di
> aggiornamento.
>
> ![A screenshot of a computer Description automatically
> generated](./media/image7.png)

10. Nel riquadro di navigazione, seleziona **Windows Update**.

Task 2: Rivedere le impostazioni applicate

1.  Nella pagina **Windows Update** selezionare **Cronologia
    aggiornamenti.**

> ![A screenshot of a computer update Description automatically
> generated](./media/image8.png)

2.  Esamina gli aggiornamenti elencati, quindi seleziona **Disinstalla
    aggiornamenti.**

> ![A screenshot of a computer update Description automatically
> generated](./media/image9.png)

3.  Esaminare gli aggiornamenti elencati in **Aggiornamenti
    installati**. Chiudi gli aggiornamenti installati.

> ![A screenshot of a computer Description automatically
> generated](./media/image10.png)

4.  Chiudi l'app **Impostazioni**.

Task 3: Configurare le impostazioni di aggiornamento usando Intune

1.  Passare a [***SEA-SVR1***](urn:gd:lg:a:send-vm-keys) e accedi come
    [**Contoso\Administrator**](urn:gd:lg:a:send-vm-keys) con la
    password di [**Pa55w.rd**](urn:gd:lg:a:send-vm-keys).

2.  Sulla barra delle applicazioni, seleziona **Microsoft Edge.**

3.  In Microsoft Edge digitare
    [**https://intune.microsoft.com**](urn:gd:lg:a:send-vm-keys) nella
    barra degli indirizzi, quindi premere **Invio**.

4.  Accedi come
    [**admin@M365x19242953.onmicrosoft.com**](urn:gd:lg:a:send-vm-keys) con
    la password.

5.  Nel riquadro di spostamento selezionare **Dispositivi**, quindi
    selezionare Aggiornamenti di **Windows 10 e versioni successive**.

> ![](./media/image11.png)

6.  Sui **dispositivi** **| Anelli di aggiornamento per Windows 10 e
    versioni successive** blade selezionare **Crea profile**

> ![](./media/image12.png)

7.  Nel pannello Informazioni di **base** immettere le informazioni
    seguenti e quindi selezionare **Avanti**:

    - Nome: !\![**Contoso Updates -
      standard**](urn:gd:lg:a:send-vm-keys)!!

    - Descrizione: !\![**Standard Windows updates
      configuration**](urn:gd:lg:a:select-vm)!!

> ![](./media/image13.png)

8.  Nel pannello **Aggiorna impostazioni anello** immettere le
    informazioni seguenti e quindi selezionare **Avanti**:

    - Periodo di differimento dell'aggiornamento qualitativo
      (giorni): [**15**](urn:gd:lg:a:send-vm-keys)

    - Periodo di differimento dell'aggiornamento delle funzionalità
      (giorni): [**45**](urn:gd:lg:a:send-vm-keys)

    - Opzione per mettere in pausa gli aggiornamenti di Windows:
      Disabilita

    - Opzione per verificare la disponibilità di aggiornamenti di
      Windows: **Abilita**

> ![](./media/image14.png)

9.  Nel pannello **Assegnazioni**, in **Gruppi inclusi**, selezionare
    **Aggiungi gruppi.**

10. Nel pannello **Seleziona gruppi da includere** nella casella di
    **ricerca**, selezionare **Contoso Developer devices** e quindi
    selezionare **Seleziona**.

> ![A screenshot of a computer Description automatically
> generated](./media/image15.png)
>
> ![](./media/image16.png)

11. Selezionare **Avanti** e nel pannello **Rivedi + crea** selezionare
    **Crea**.

12. Dalla barra di navigazione, selezionare **Profili di
    configurazione**.

13. Sui **dispositivi | Pannello Configurazione**, nel riquadro dei
    dettagli, selezionare **Crea criteri**.

> ![](./media/image17.png)

14. Nel pannello **Crea un profilo** selezionare le opzioni seguenti e
    quindi selezionare **Crea**:

    - Piattaforma: **Windows 10 e versioni successive**

    - Tipo di profilo: **Modelli**

    - Nome del modello: **Delivery Optimization**

> ![](./media/image18.png)

- Nel pannello Informazioni di **base** immettere le informazioni
  seguenti e quindi selezionare **Avanti**:

- Nome: !\![**Contoso Developer - Delivery
  optimization**](urn:gd:lg:a:send-vm-keys)!!

- Descrizione: !\![**Delivery optimization for
  Developer**](urn:gd:lg:a:send-vm-keys)!!

> ![](./media/image19.png)

15. Nel pannello **Impostazioni di configurazione**, immettere le
    informazioni seguenti, quindi selezionare **Avanti**:

    - Modalità di download**: solo HTTP, nessun peering (0)**

> Nel pannello Assegnazioni, in Gruppi inclusi, selezionare Aggiungi
> gruppi ![A screenshot of a computer Description automatically
> generated](./media/image20.png)

16. Nel pannello **Assegnazioni**, in **Gruppi inclusi**, selezionare
    **Aggiungi gruppi.**

17. Nel pannello **Seleziona gruppi da includere**, selezionare
    **Contoso Developer devices** e quindi selezionare **Seleziona**.

> ![A screenshot of a computer Description automatically
> generated](./media/image21.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image22.png)

18. Selezionare **Avanti** due volte e nel pannello **Rivedi + crea**
    selezionare **Crea**.

> ![Screenshot](./media/image23.png)

Task 4: Verificare che le impostazioni di aggiornamento del dispositivo
siano gestite centralmente

1.  Passare a [***SEA-WS1***](https://intune.microsoft.com).

2.  Seleziona **Start**, quindi seleziona l'icona **Impostazioni**.

> ![](./media/image24.png)

3.  Nell'app **Impostazioni** selezionare **Account** e quindi
    selezionare Accedi all'azienda o **all'istituto di istruzione**.

> ![A screenshot of a computer Description automatically
> generated](./media/image25.png)

4.  Nella sezione **Accedi all'azienda o all'istituto** di istruzione,
    selezionare il **collegamento Connesso ad Azure AD** di Contoso e
    quindi selezionare **Informazioni**.

> ![A screenshot of a computer Description automatically
> generated](./media/image26.png)

5.  Nella finestra di dialogo **Aree gestite da Contoso**, seleziona
    **Sincronizza**. Attendi il completamento della sincronizzazione.

> ![A screenshot of a computer Description automatically
> generated](./media/image27.png)

6.  Nell'app **Impostazioni**, seleziona **Windows Update**.

> Si noti che non è possibile sospendere gli aggiornamenti.

7.  Selezionare **le opzioni avanzate**.

> ![](./media/image28.png)

8.  Selezionare **Ottimizzazione della consegna.**

> ![A screenshot of a computer Description automatically
> generated](./media/image29.png)
>
> Si noti che l'opzione **Consenti download da altri PC** non è
> disponibile.

9.  Nell'app **Impostazioni**, seleziona **Windows Update**, selezionare
    **Opzioni avanzate** e quindi selezionare **Criteri di aggiornamento
    configurati**.

> ![](./media/image30.png)
>
> Prendere nota di tutti i criteri impostati sul dispositivo.

10. Chiudi tutte le app e le finestre aperte.

> **Nota**: l'ambiente lab è configurato per impedire l'applicazione di
> Windows Update per evitare ritardi e impatti involontari durante i
> lab.
