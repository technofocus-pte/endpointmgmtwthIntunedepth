# Lab 4 - Gestire la registrazione del dispositivo Microsoft Entra.

**Sommario**

In questo laboratorio verrà eseguita la registrazione di Microsoft Entra
utilizzando un dispositivo Windows.

**Esercizio 1: Configurazione della registrazione del dispositivo
Microsoft Entra**

**Scenario**

Diversi utenti hanno chiesto di usare i propri dispositivi iOS, Android
e Windows personali per accedere alle risorse cloud di Contoso. Poiché
Contoso non è proprietario dei dispositivi, non si desidera che gli
utenti eseguano un join Entra per la gestione completa dei dispositivi.
È invece necessario assicurarsi che gli utenti siano in grado di
registrare i propri dispositivi con Microsoft Entra, che consente
comunque di applicare i criteri aziendali alle app in base alle esigenze
e di consentire agli utenti di accedere alle risorse di Contoso. Verrà
eseguita la verifica della registrazione del dispositivo Microsoft Entra
utilizzando un dispositivo Windows 11.

**Task 1: Configurare la registrazione del dispositivo Azure AD**

1.  Sul SEA-SVR1, aprire una nuova scheda nel browser Edge e inserire il
    seguente URL, !! https://entra.microsoft.com!!, quindi premere il
    pulsante **Invio**.

2.  Accedere con l'ID tenant di Office 365

3.  !!**admin@M365xXXXXXXXX.onmicrosoft.com**!! e utilizzare la password
    dell'amministratore del tenant.

> ![A screenshot of a computer Description automatically
> generated](./media/image1.png)
>
> ![A screenshot of a login box Description automatically
> generated](./media/image2.png)

4.  **Se rimani connesso**? , selezionare il pulsante **Sì**.

> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)

5.  **Nella finestra dell'interfaccia di** **amministrazione** di
    Microsoft Entra, naviga e fai clic su **Identità**.

![A screenshot of a computer Description automatically
generated](./media/image4.png)

6.  Seleziona Dispositivi, quindi Pagina Impostazioni dispositivo, nel
    riquadro dei dettagli verifica che gli utenti possano registrare i
    propri dispositivi con Microsoft Entra sia impostato su Tutti e sia
    disattivato.

> Questa opzione è disattivata e impostata su **Tutti** per impostazione
> predefinita quando Microsoft Intune è abilitato nel tenant. In questo
> modo tutti gli utenti sono in grado di registrare dispositivi
> personali, iOS, Android e macOS Windows 10 o versioni successive con
> Azure AD.
>
> ![](./media/image5.png)

**Task 2: Eseguire la registrazione a Microsoft Entra**

1.  Passare a SEA-WS1 e accedere come **amministratore** con la password
    di !!**Pa55w.rd**!!.

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image6.png)

2.  Sulla barra delle applicazioni, seleziona **Start**, quindi
    seleziona **Impostazioni**.

![A screenshot of a computer Description automatically
generated](./media/image7.png)

3.  Nella finestra **Impostazioni**, seleziona **Account**.

![A screenshot of a computer Description automatically
generated](./media/image8.png)

4.  Nella pagina **Account** selezionare Accedi all'azienda o
    all'istituto di istruzione.

![A screenshot of a computer Description automatically
generated](./media/image9.png)

5.  Nella pagina **Accedi all'azienda o all'istituto** di istruzione
    selezionare **Connetti**.

![A screenshot of a computer Description automatically
generated](./media/image10.png)

6.  Nella pagina di accesso,
    tipo!!**JoniS@M365xXXXXXXX.onmicrosoft.com**!!  , quindi seleziona
    **Avanti**.

![](./media/image11.png)

7.  Nella pagina Immetti password immettere la password del tenant:
    !\![**P@55w.rd1234**](mailto:P@55w.rd1234)!! e quindi seleziona
    **Accedi**

![A screenshot of a computer Description automatically
generated](./media/image12.png)

8.  Sul pulsante **È tutto pronto**! , selezionare **Fine**.

![A screenshot of a computer Description automatically
generated](./media/image13.png)

9.  Nella pagina **Accedi al lavoro o all'istituto di istruzione**,
    verifica che sia visualizzato **l'account di lavoro o
    dell'istituto** di istruzione di Joni.

![A screenshot of a computer Description automatically
generated](./media/image14.png)

10. Chiudi la pagina **Impostazioni**.

**Task 3: Convalidare la registrazione a Microsoft Entra**

1.  Su SEA-WS1, fare **clic** con il pulsante destro del mouse sul
    pulsante Start, quindi selezionare Terminale Windows
    (**amministratore**).

> ![A screenshot of a computer Description automatically
> generated](./media/image15.png)

2.  Nella finestra di dialogo Controllo **account utente** selezionare
    **Sì**.

> ![A screenshot of a computer error Description automatically
> generated](./media/image16.png)

3.  Nella console di PowerShell, digita quanto segue e premi **Invio**:

> !!**dsregcmd /status**!!

4.  Nell'output in Stato **utente verificare** che sia visualizzato
    **WorkplaceJoined**: YES. Ciò indica che l'utente ha eseguito una
    registrazione del dispositivo in Microsoft Entra.

> ![A screenshot of a computer Description automatically
> generated](./media/image17.png)

5.  Chiudere PowerShell e quindi disconnettersi da **SEA-WS1**.

6.  Passare a SEA-SVR1. Vai alla finestra dell'interfaccia di
    **amministrazione di Microsoft Entra**, naviga e fai clic su
    **Identità**.

> ![A screenshot of a computer Description automatically
> generated](./media/image18.png)
>
> 7\. Nella sezione **Identità**, seleziona Dispositivi, quindi naviga e
> fai clic su **Tutti i dispositivi** come mostrato nell'immagine
> **sottostante**.
>
> ![A screenshot of a computer Description automatically
> generated](./media/image19.png)

8.  Verificare che il **tipo di join** sia elencato come Microsoft Entra
    registrato e che il proprietario sia **Joni Sherman.**

> ![](./media/image20.png)
>
> Si noti che il dispositivo è registrato a Microsoft Entra, NON a
> Microsoft Entra. I dispositivi registrati Entra sono in genere
> dispositivi a cui non è possibile aggiungere Entra o dispositivi che
> sono di proprietà personale dell'utente. La registrazione di un
> dispositivo fornirà l'accesso alle risorse basate su cloud.

9.  Chiudi Microsoft Edge.

**Task 4: Accedere a Windows e disconnettersi dall'organizzazione**

1.  Passare a SEA-WS1. Sulla barra delle applicazioni, **seleziona il
    pulsante dell'icona** **Start di Windows,** quindi seleziona
    **Impostazioni**.

![A screenshot of a computer Description automatically
generated](./media/image7.png)

2.  Nella finestra **Impostazioni**, seleziona **Account**.

> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)

3.  Nella pagina **Account** selezionare Accedi all'azienda o
    **all'istituto di istruzione**.

> ![A screenshot of a computer Description automatically
> generated](./media/image9.png)

4.  Nella pagina **Accedi all'azienda o all'istituto di istruzione**,
    fai clic sull'elenco a discesa accanto JoniS@M3654xXXXXXXXX account
    aziendale o dell'istituto di istruzione, come mostrato nell'immagine
    seguente.

> ![](./media/image21.png)

5.  Fare clic sul pulsante **Disconnetti**.

> ![A screenshot of a computer Description automatically
> generated](./media/image22.png)

6.  Fare clic sul pulsante **Sì** per confermare la rimozione
    dell'account.

> ![A screenshot of a computer Description automatically
> generated](./media/image23.png)
>
> Si noti che non è necessario riavviare per disconnettere un
> dispositivo registrato a Microsoft Entra.

7.  Esci da **SEA-WS1**.

![A screenshot of a computer Description automatically
generated](./media/image24.png)

**Risultati:** dopo aver completato questo esercizio, sarà stata
configurata la registrazione del dispositivo Microsoft Entra.
