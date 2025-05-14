**Practice Lab26 : Gestione delle politiche di aggiornamento per iOS e
iPadOS Summary**

In questo lab si configurerà un criterio di aggiornamento da usare per
gestire gli aggiornamenti del sistema operativo per iOS e iPadOS.

**Scenario**

Tutti gli sviluppatori di Contoso hanno iPhone e iPad che eseguono le
versioni più recenti di iOS/iPadOS. Questi dispositivi sono stati
registrati tramite la registrazione automatica dei dispositivi di Apple
ed è necessario configurare un criterio di aggiornamento per il sistema
operativo del dispositivo. È necessario garantire quanto segue:

- Versione da installare: Ultimo aggiornamento.

- Consenti solo gli aggiornamenti automatici tra mercoledì alle 12 e
  giovedì alle 12.

Task 1: Creare un criterio di aggiornamento per i dispositivi iOS/iPadOS

1.  Su [***SEA-SVR1***](urn:gd:lg:a:select-vm), Se necessario, accedi
    come [**Contoso\Administrator**](urn:gd:lg:a:send-vm-keys) con la
    password [**Pa55w.rd**](urn:gd:lg:a:send-vm-keys) e chiudi **Server
    Manager**.

2.  Sulla barra delle applicazioni, seleziona **Microsoft Edge.**

3.  In Microsoft Edge digitare
    [**https://intune.microsoft.com**](https://intune.microsoft.com) nella
    barra degli indirizzi, quindi premere **Invio**.

4.  Accedi come
    [**admin@M365x19242953.onmicrosoft.com**](urn:gd:lg:a:send-vm-keys) con
    la password.

5.  Nella pagina dell'interfaccia di **amministrazione di Microsoft
    Intune** selezionare **Dispositivi**.

6.  Sui **dispositivi** **|** Per pale della **piattaforma**, in
    Politica, selezionare **iOS/iPadOS**.

> ![](./media/image1.png)

7.  Selezionare **Criteri di aggiornamento per iOS/iPadOS**

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)

8.  Nel riquadro dei dettagli selezionare **Crea profilo**.

9.  Nella scheda Informazioni di **base** configurare le opzioni
    seguenti e selezionare **Avanti**:

    - Nome: !\![**iOS/iPadOS update
      policy**](urn:gd:lg:a:send-vm-keys)!!

    - Descrizione: !\![**Policy to manage system updates for iOS and
      iPadOS**](urn:gd:lg:a:send-vm-keys)!!

> ![](./media/image3.png)

10. **Nella scheda Impostazioni** criteri di aggiornamento, configurare
    le opzioni seguenti e selezionare **Avanti**:

    - Seleziona la versione da installare: **Ultimo aggiornamento**

    - Tipo di pianificazione: **Aggiorna durante l'orario pianificato**

    - Fuso orario: **UTC:00**

    - Finestra temporale:

      - Data di inizio: **mercoledì**

      - Ora di inizio: **12 AM**

      - Giorno di fine: **Giovedì**

      - Ora di fine: **12 AM**

> ![](./media/image4.png)

11. Nella scheda **Assegnazioni** selezionare **Avanti**.

> ![A screenshot of a computer Description automatically
> generated](./media/image5.png)

12. Nella scheda **Rivedi + crea**, esamina le impostazioni e seleziona
    **Crea**.

13. Sui dispositivi | **Aggiornare i criteri per il pannello
    iOS/iPadOS**, Nel riquadro dei dettagli verificare che **iOS/iPadOS
    aggiornare la politica** è elencato.

> ![A screenshot of a computer Description automatically
> generated](./media/image6.png)

14. Chiudi Microsoft Edge.

**Risultati:** Dopo aver completato questo esercizio, avrai configurato
correttamente un criterio di aggiornamento per iOS e iPadOS.
