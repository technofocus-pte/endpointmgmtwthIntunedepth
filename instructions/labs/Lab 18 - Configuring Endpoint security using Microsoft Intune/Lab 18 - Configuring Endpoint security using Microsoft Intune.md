Lab 18 - Configurazione della sicurezza degli endpoint con Microsoft
Intune

**Sommario**

In questo lab si creerà un criterio per configurare Microsoft Defender
per i dispositivi gestiti in Microsoft Intune. Registrazione dei
dispositivi in Microsoft Intune

**Prerequisite**

I seguenti laboratori devono essere completati prima di questo
laboratorio:

- Lab \#5- Gestire la registrazione dei dispositivi in Microsoft Intune

- Lab \#6-Enrolling devices into Microsoft Intune

- Lab \#7- Creazione e distribuzione dei profili di configurazione

**Scenario**

È stato chiesto di assicurarsi che il gruppo di sviluppatori Contoso
abbia configurato correttamente Microsoft Defender. È stato richiesto
che:

- La protezione antimanomissione deve essere impedita.

- Nascondi le aree Protezione account, Controllo app e browser,
  Sicurezza del dispositivo, Prestazioni e integrità del dispositivo e
  Opzioni familiari nell'app Sicurezza di Windows

- È necessario aggiungere il nome e il numero di telefono dell'azienda.

- Devono essere configurate anche le impostazioni di protezione in tempo
  reale, correzione e scansione.Settings will be verified by testing on
  an enrolled device, SEA-WS1 and a non-enrolled device, SEA-CL1.

Task 1: Configurare l'esperienza di sicurezza di Windows in Intune

1.  Passare e accedere a
    [***SEA-SVR1***](urn:gd:lg:a:select-vm) as !!**[Contoso\Administrator](urn:gd:lg:a:send-vm-keys)!!** Con
    la password !!**[Pa55w.rd](urn:gd:lg:a:send-vm-keys)!!**

2.  Sulla barra delle applicazioni, seleziona **Microsoft Edge**.

3.  In Microsoft Edge digitare
    !!**https://Intune.microsoft.com!!** nella barra degli indirizzi,
    quindi premere **Invio**.

4.  Accedere come amministratore tenant di Office 365.

> ![A screenshot of a computer Description automatically
> generated](./media/image1.png)

5.  Dal riquadro di navigazione selezionare **Sicurezza degli
    endpoint**, quindi **selezionare Antivirus.**

> ![](./media/image2.png)

6.  Sul sito Sicurezza degli **endpoint |Riquadro Antivirus**,
    selezionare + **Crea criterio.**

> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)

7.  Nel riquadro **Crea un profilo**, per **Piattaforma**, seleziona
    **Windows 10, Windows 11 e Windows Server**.

8.  Nell'elenco **Profilo**, selezionare **Esperienza di sicurezza di
    Windows**. Quindi seleziona Crea.

> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

9.  Nella scheda Informazioni di base, nel campo **Nome**,
    immettere!!**[Windows Security
    Settings](urn:gd:lg:a:send-vm-keys)!!**. seleziona **Avanti**.

> ![A screenshot of a computer Description automatically
> generated](./media/image5.png)

10. In **Defender**, configurare quanto segue settings:

> TamperProtection (dispositivo): Attivato![A screenshot of a computer
> Description automatically generated](./media/image6.png)

- In **Windows Defender Security** Center configurare le impostazioni
  seguenti:Disable protezione dell'account UI: **abilitare**

- Disattiva l'interfaccia utente del browser app: **abilitare**

- Disattiva l'interfaccia utente di sicurezza del
  dispositivo: **abilitare**

- Disattivare la famiglia UI: **abilitare**

- Disattivare lo stato di salute UI: **abilitare**

> ![A screenshot of a computer Description automatically
> generated](./media/image7.png)

11. Accanto a **Abilita avvisi popup personalizzati**, selezionare
    **Abilita**.

12. Nel campo **Nome società** selezionare **Configurato**, quindi
    immettere !!**[Contoso IT](urn:gd:lg:a:send-vm-keys)!!**

13. Per **Telefono**, selezionare **Configurato**, quindi
    immettere!!**[555-1234](urn:gd:lg:a:send-vm-keys)!!** , quindi
    seleziona **Avanti**.

> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)

14. Nella pagina **Tag ambito** selezionare **Avanti**.

> ![A screenshot of a computer Description automatically
> generated](./media/image9.png)

15. Nella scheda **Assegnazioni**, in **Gruppi inclusi**, selezionare
    **Aggiungi gruppi**. Scegliere il gruppo **Dispositivi sviluppatore
    Contoso**, fare clic su **Seleziona** e quindi selezionare
    **Avanti**.

> ![A screenshot of a computer Description automatically
> generated](./media/image10.png)

16. Nella scheda **Rivedi** + **crea**, rivedere le informazioni e
    selezionare **Salva**.

> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)

Task 2: Configurare i criteri antivirus di Microsoft Defender in Intune

Sul sito Sicurezza degli **endpoint |Riquadro Antivirus**, selezionare
**Crea criterio**.

> ![A screenshot of a computer Description automatically
> generated](./media/image12.png)

1.  Nel riquadro **Crea un profilo**, per **Piattaforma**, seleziona
    **Windows 10, Windows 11 e Windows Server.**

2.  Nell'elenco **Profilo** selezionare **Microsoft Defender
    Antivirus**, quindi selezionare **Crea**.

> ![A screenshot of a computer Description automatically
> generated](./media/image13.png)

3.  Nella scheda Informazioni di **base**, nel campo **Nome**, immettere
    !! Impostazioni di Microsoft Defender Antivirus!. Seleziona
    **Avanti**.

> ![A screenshot of a computer Description automatically
> generated](./media/image14.png)

4.  Nella scheda **Impostazioni di configurazione**, configurare le
    seguenti impostazioni:

    - Consenti sistema di prevenzione delle intrusioni: **Consentito**

    - Consenti scansione di tutti i file e gli allegati scaricati:
      **Consentito**

    - Consenti monitoraggio in tempo reale: **Consentito**

> ![](./media/image15.png)

- Verifica firme prima di eseguire Scansione: **Abilitato**

- Giorni per conservare il malware
  pulito: !!**[60](urn:gd:lg:a:send-vm-keys)!!**

> ![A screenshot of a computer Description automatically
> generated](./media/image16.png)
>
> Pianifica il tempo di scansione rapida: !! 60!! (rappresenta l'1:00)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image17.png)
>
> Consenso all'invio di campioni: **invio automatico di campioni
> sicuri** ![A screenshot of a computer Description automatically
> generated](./media/image18.png)

5.  Nella scheda **Impostazioni di configurazione** selezionare
    **Avanti**.

6.  Nella **pagina Tag ambito** selezionare **Avanti**.

> ![A screenshot of a computer Description automatically
> generated](./media/image19.png)

7.  Nella scheda Assegnazioni, in **Gruppi inclusi**, selezionare
    **Aggiungi gruppi**. Choose il gruppo Dispositivi per **sviluppatori
    Contoso**, quindi scegliere **Seleziona** e quindi selezionare
    **Avanti**.

> ![A screenshot of a computer Description automatically
> generated](./media/image20.png)

8.  Nella scheda **Rivedi** + **crea**, esamina le informazioni e
    seleziona **Salva**.

> ![A screenshot of a computer Description automatically
> generated](./media/image21.png)

Task 3: Sincronizzare i dispositivi gestiti

1.  Nell'interfaccia di amministrazione di **Microsoft Intune**
    selezionare **Dispositivi** e quindi selezionare **Tutti i
    dispositivi.**

2.  Sui **dispositivi** | Riquadro **Tutti i dispositivi**, selezionare
    **SEA-WS1** e quindi sul blade **SEA-WS1,** selezionare Sincronizza
    sulla barra degli strumenti, quindi selezionare Sì.

> ![](./media/image22.png)
>
> Attendi 3-4 minuti per il completamento della sincronizzazione.

3.  Chiudi Microsoft Edge.

Task 4: verificare la configurazione

1.  Passare a [***SEA-CL1***](urn:gd:lg:a:select-vm). Se necessario,
    accedere
    come!!**[Contoso\Administrator](urn:gd:lg:a:send-vm-keys)!!** Con la
    password di !!**[Pa55w.rd](urn:gd:lg:a:send-vm-keys)!!**.

2.  Su [***SEA-CL1***](urn:gd:lg:a:select-vm), selezionare, **Start**
    digitare!!**[Windows Security](urn:gd:lg:a:send-vm-keys)!!**, e
    quindi sotto l'icona Sicurezza di Windows selezionare **Apri**.

> Si noti che vengono visualizzate tutte le opzioni di protezione. Ciò è
> dovuto al fatto che SEA-CL1 non è registrato in Intune
>
> ![](./media/image23.png)
>
> Si noti che vengono visualizzate tutte le opzioni di protezione. Ciò è
> dovuto al fatto che SEA-CL1 non è registrato in Intune.
>
> ![A screenshot of a computer security system Description automatically
> generated](./media/image24.png)

3.  Chiudi **Sicurezza di Windows** ed esci da
    [***SEA-CL1***](urn:gd:lg:a:select-vm).

4.  Passare a [***SEA-WS1***](urn:gd:lg:a:select-vm), e accedi come
    **!!Cindy@M365x27131290.onmicrosoft.com!!** con Password
    **!!P@55w.rd12345!!** .

5.  Selezionare **Start**, digitare!!**[Windows
    Security](urn:gd:lg:a:send-vm-keys)!!**, e quindi sotto l'icona
    Sicurezza di Windows selezionare **Apri**.

> ![](./media/image25.png)
>
> Si noti che tutte le aree con restrizioni configurate nei criteri di
> Intune non vengono visualizzate. **SEA-WS1** è registrato in Intune,
> che ha applicato le impostazioni di sicurezza.
>
> ![A screenshot of a computer Description automatically
> generated](./media/image26.png)

6.  Chiudi **Sicurezza di Windows** ed esci da
    [***SEA-WS1***](urn:gd:lg:a:select-vm).

**Risultati:** Dopo aver completato questo esercizio, sarà stato creato
e applicato correttamente un criterio per configurare Microsoft Defender
per i dispositivi gestiti in Intune.
