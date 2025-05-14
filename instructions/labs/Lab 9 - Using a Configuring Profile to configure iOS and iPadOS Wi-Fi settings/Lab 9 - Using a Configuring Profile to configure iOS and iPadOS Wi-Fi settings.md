**Lab 9 - Utilizzo di un profilo di configurazione per configurare le
impostazioni Wi-Fi di iOS e iPadOS.**

**Sommario**

In questo lab si userà Microsoft Intune per creare e applicare un
profilo di configurazione per eseguire la configurazione delle
impostazioni Wi-Fi per i dispositivi iOS e iPadOS.

**Esercizio 1: Creazione di un profilo di configurazione.**

**Scenario**

Ti è stato chiesto di creare un profilo di configurazione da utilizzare
per configurare automaticamente le impostazioni Wi-Fi per i dispositivi
iOS e iPadOS registrati. È necessario assicurarsi che le impostazioni
Wi-Fi siano configurate come segue:

- Nome della rete: Contoso Wi-Fi

- SSID: MainOffice

- Connessione automatica: Attiva

- Tipo di sicurezza: WPA/WPA2-Personal

- Chiave pre-condivisa: ContosoWiFi123

- Assegnato a: un nuovo gruppo di sicurezza denominato iOS_iPadOS
  Dispositivi

**Task 1: Creare il gruppo di dispositivi iOS_iPadOS**

1.  Passare a SEA-SVR1. Nella finestra dell'interfaccia di
    **amministrazione di Microsoft Entra**, naviga e seleziona Gruppi,
    quindi fai **clic** su Tutti i **gruppi**.

> ![A screenshot of a computer Description automatically
> generated](./media/image1.png)

2.  Sui Gruppi | **pannello Tutti i gruppi**, selezionare **Nuovo
    gruppo**.

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)

- Nel pannello **Nuovo gruppo** immettere le informazioni seguenti e
  fare clic sul pulsante **Crea** come illustrato nell'immagine
  seguente:Group type: **Security**

- Nome del gruppo: !! iOS_iPadOS Dispositivi!!

- Descrizione del gruppo: !! Tutti i dispositivi iOS e iPadOS!!

- Tipo di adesione: Assegnato

> ![A screenshot of a group Description automatically
> generated](./media/image3.png)

3.  Sui **Gruppi | pannello Tutti i gruppi,** aggiornare la pagina e
    verificare che sia visualizzato il gruppo **iOS_iPadOS
    Dispositivi**.

> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

**Task 2: Creare un profilo di configurazione in base ai requisiti dello
scenario**

1.  Passare alla scheda Interfaccia di **amministrazione di Microsoft
    Intune**, selezionare Dispositivi dalla barra di **spostamento.**

> ![A screenshot of a computer Description automatically
> generated](./media/image5.png)

2.  Sui dispositivi | **Pagina di panoramica**, selezionare
    **iOS/iPadOS** come illustrato nell'immagine seguente.

> ![A screenshot of a computer Description automatically
> generated](./media/image6.png)

3.  Nella **pagina iOS/iPadOS** passare e fare clic su **Profili di
    configurazione**.

4.  Nella schermata **iOS/iPadOS** | Pagina Profili di configurazione,
    nella scheda Criteri, fare **clic su + Crea e selezionare** + Nuovo
    criterio.

> ![](./media/image7.png)

5.  Nel pannello **Crea un profilo** selezionare le opzioni seguenti e
    quindi selezionare **Crea**:

    - Piattaforma: **iOS/iPadOS**

    - o Tipo di profilo: **Modelli**

    - o Nome del modello: **Wi-fi**

> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)

6.  Nel pannello Informazioni di **base** immettere le informazioni
    seguenti e quindi selezionare **Avanti**:

    - Nome: !!**iOS/iPadOS Wi-Fi Policy**!!

    - Descrizione: !!**Wi-Fi settings for iOS/iPadOS Devices**!!

> ![A screenshot of a computer Description automatically
> generated](./media/image9.png)

7.  Nel pannello **Impostazioni di configurazione**, accanto a Tipo di
    **Wi-Fi,** selezionare **Base**.

> Vengono visualizzate opzioni aggiuntive in base al tipo selezionato.

8.  Nel pannello **Impostazioni di configurazione** selezionare le
    opzioni seguenti e quindi selezionare **Avanti**:

    - Nome della rete: !! Contoso Wi-Fi!!

    - SSID: !! MainOffice!

    - Connetti automaticamente: Abilita

    - Tipo di sicurezza: WPA/WPA2-Personal

    - Chiave pre-condivisa: !! ContosoWiFi123!!

> ![A screenshot of a computer Description automatically
> generated](./media/image10.png)

9.  Nel pannello **Assegnazioni**, in **Gruppi inclusi,** selezionare
    **Aggiungi gruppi**.

> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)

10. Nella finestra **Seleziona gruppi** da includere **selezionare
    iOS_iPadOS** Dispositivi e quindi fare clic su **Seleziona**.

> ![](./media/image12.png)

11. Nella scheda **Assegnazioni**, fai clic sul pulsante **Avanti**.

> ![A screenshot of a computer Description automatically
> generated](./media/image13.png)

12. Nella scheda **Rivedi + crea**, fai clic sul pulsante **Crea**.

> ![A screenshot of a computer Description automatically
> generated](./media/image14.png)

13. Verificare che i criteri **Wi-Fi iOS/iPadOS** siano elencati.

> ![A screenshot of a computer Description automatically
> generated](./media/image15.png)
>
> **Risultati**: dopo aver completato questo esercizio, avrai creato e
> assegnato correttamente un profilo di configurazione per configurare
> le impostazioni Wi-Fi per i dispositivi iOS e iPadOS.
