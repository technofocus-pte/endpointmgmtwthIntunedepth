Lab13: Configurare i criteri di protezione delle app per i dispositivi
mobili

**Sommario**

In questo lab si configureranno criteri di protezione delle app per un
dispositivo mobile.

**Scenario**

Tutti gli sviluppatori di Contoso hanno iPhone e iPad che eseguono le
versioni più recenti di iOS/iPadOS. Il dipartimento di sicurezza è
preoccupato per le fughe di dati e vuole evitare che i dati dell'e-mail
aziendale vengano copiati su altre app sui dispositivi mobili. È
necessario fornire una soluzione che risolva i problemi del reparto
sicurezza. È necessario garantire quanto segue:

- I dati di Outlook devono essere limitati dal backup su iTunes o
  iCloud.

- Solo le app gestite dai criteri possono inviare e ricevere dati da
  Outlook.

- Solo le app gestite dai criteri possono tagliare, copiare o incollare
  con Outlook.

- Gli utenti devono fornire le proprie credenziali di account di lavoro
  o scuola per l'accesso a Outlook.

Task 1: Creare un criterio di protezione delle app per i dispositivi
iOS/iPadOS

1.  In SEA-SVR1, se necessario, accedere come Contoso\Administrator con
    la password!\![**Pa55w.rd**](urn:gd:lg:a:send-vm-keys)!!

2.  Sulla barra delle applicazioni, seleziona **Microsoft Edge** e vai
    all'interfaccia di amministrazione di **Microsoft Intune**!!
    https://intune.microsoft.com!! nella barra degli indirizzi, quindi
    premere **Invio**.

3.  Accedere con le credenziali di amministratore tenant di Office 365
    dalla scheda Home.On nella pagina dell'interfaccia di
    **amministrazione di Microsoft Intune**, selezionare **App**.

> ![A screenshot of a computer Description automatically
> generated](./media/image1.png)

4.  Sulle **app** | **Pannello Panoramica,** in Criteri **selezionare**
    Criteri di **protezione delle app.**

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)

5.  Nel riquadro dei dettagli selezionare +**Crea criterio** e quindi
    selezionare **iOS/iPadOS.**

> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)

6.  Nella scheda Informazioni di **base** configurare le opzioni
    seguenti e selezionare **Avanti**:

    - Nome: !\![**Outlook – Developers**](urn:gd:lg:a:send-vm-keys)!!

    - Discrezione: !\![**Policy to prevent cut/copy and paste from
      Outlook**](urn:gd:lg:a:send-vm-keys)!!

> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

7.  Nella scheda **App**, fai clic su + **Seleziona app pubbliche**.

8.  Nel pannello **Seleziona app di destinazione**, nella casella di
    testo, digita !! Prospettiva!! Selezionare **Microsoft Outlook**,
    quindi fare **clic** sul pulsante **Seleziona**, quindi selezionare
    **Avanti**.

> ![Screens screenshot of a computer Description automatically
> generated](./media/image5.png)

9.  Nella scheda **Protezione dei dati** configurare le opzioni seguenti
    e selezionare **Avanti**:

    - Backup dei dati dell'organizzazione su ITunes e backup iCloud:
      **Blocca**

    - Inviare i dati dell'organizzazione ad altre app: **app gestite da
      criteri**

    - Ricevere dati da altre app: **app gestite da criteri**

    - Limita il taglia, copia e incolla tra altre app: **Applicazioni
      gestite da politiche**

> Lascia tutte le altre impostazioni predefinite
>
> ![](./media/image6.png)

10. Nella scheda **Requisiti di accesso** configurare le opzioni
    seguenti e selezionare **Avanti**:

    - PIN per l'accesso: **Non richiesto** Credenziali dell'account
      aziendale o dell'istituto di istruzione per l'accesso:
      **Richiedere**

> ![A screenshot of a computer Description automatically
> generated](./media/image7.png)

11. Nella scheda **Avvio condizionale**, esamina le impostazioni.
    Seleziona **Avanti**.

> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)
>
> **Nota**: qui puoi impostare i requisiti di sicurezza dell'accesso per
> i criteri di protezione dell'accesso. È possibile selezionare
> un'impostazione e immettere il valore che gli utenti devono soddisfare
> per accedere all'app aziendale. Prendi nota delle varie impostazioni
> ma non cambiare nulla.

12. Nella scheda **Assegnazioni** selezionare **Avanti**.

> ![A screenshot of a computer Description automatically
> generated](./media/image9.png)

13. Nella scheda **Rivedi + crea**, esamina le impostazioni e seleziona
    **Crea**.

> ![A screenshot of a computer Description automatically
> generated](./media/image10.png)

14. Sulle app | **Nel pannello Criteri di protezione delle app
    verificare** che Outlook - **Sviluppatori sia elencato.**

> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)

15. Chiudi Microsoft Edge.

**Risultati**: dopo aver completato questo esercizio, sarà stato
configurato correttamente un criterio di protezione delle app per un
dispositivo mobile.
