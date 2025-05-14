**Atelier 06 - Inscription d'appareils dans Microsoft Intune**

**Résumé**

Dans cet atelier, vous allez joindre un client Windows à Entra ID et
vérifier que l'appareil s'est automatiquement inscrit dans Microsoft
Intune.

**Conditions préalables**

Le(s) Ateliers suivant(s) doit(vent) être completé(s) avant cet atelier
:

- Atelier \#1-Gestion des identités dans Microsoft Entra ID

- Atelier \#2 : Synchronisation des identités à l'aide de Microsoft
  Entra Connect

- Atelier \#5 : Gérer l'inscription d'un appareil dans Microsoft Intune

Remarque : Vous pouvez également avoir besoin d'un téléphone mobile
capable de recevoir des SMS utilisés pour sécuriser l'authentification
de connexion Windows Hello à Entra ID.

**Scénario**

Vous avez attribué à Cindy White les licences appropriées et vous allez
maintenant tester le processus de jonction d'un appareil Windows à Entra
ID et le faire s'inscrire automatiquement dans Microsoft Intune.

**Tâche 1 : Inscrire automatiquement un appareil Windows à Microsoft
Intune**

1.  Passez à
    [*SEA-WS1*](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)
    et connectez-vous en tant qu**'administrateur** avec le mot de passe
    de !!**Pa55w.rd** !!

![Une capture d'écran d'un ordinateur Description générée
automatiquement avec un niveau de confiance moyen](./media/image1.png)

2.  Dans la barre des tâches, sélectionnez **Démarrer**, puis
    **Paramètres.**

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image2.png)

3.  Dans la fenêtre **Settings**, sélectionnez **Account**.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image3.png)

4.  Sur la page Comptes, sélectionnez **Access work or school**.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image4.png)

5.  Sur la page **Access work or school** , sélectionnez **connect**.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image5.png)

6.  Dans la fenêtre **Microsoft account**  sélectionnez **Join this
    device to Microsoft Entra ID**.

![](./media/image6.png)

7.  Sur la page **Sign in** , tapez
    !\![**Cindy@M365x51282399.onmicrosoft.com**](mailto:Cindy@M365x51282399.onmicrosoft.com) !!
    , puis sélectionnez **Next**.

![](./media/image7.png)

8.  Sur la page **Entrez le mot de passe**, entrez le mot de passe :
    !\![**P@55w.rd1234**](mailto:!!P@55w.rd1234) !! , puis sélectionnez
    **Sign in** .

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image8.png)

9.  **Assurez-vous qu'il s'agit de la** boîte de dialogue de votre
    organisation, puis sélectionnez **join**.

![](./media/image9.png)

10. Sur le site **Vous êtes prêt !** , lisez les informations, puis
    sélectionnez **Done**.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image10.png)

11. Dans la section **Access work or school** , vérifiez que l'option
    **Connected to Contoso's Azure AD s'**affiche.

12. Sélectionnez **Connecté à Azure AD de Contoso**, puis Sélectionnez
    **Info**.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image11.png)

13. Prenez note des informations concernant les zones gérées par
    Contoso, faites défiler l'écran vers le bas, puis sélectionnez
    **Sync**. Cela forcera la synchronisation d'un appareil avec Intune.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image12.png)

14. Fermez la fenêtre **Settings**.

**Tâche 2 : Valider l'inscription de l'appareil dans Microsoft Entra et
Intune**

1.  Dans la barre des tâches **SEA-WS1**, sélectionnez **Start**, tapez
    !!**certlm.msc** !! appuyez sur **Enter**.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image13.png)

2.  Dans la boîte de dialogue Contrôle de compte d'utilisateur,
    sélectionnez le bouton **Yes** .

![](./media/image14.png)

3.  Dans la console **Certificates**, dans le volet de navigation,
    développez **Personnel** et sélectionnez le nœud **Certificate**.
    Vérifiez que les certificats suivants sont répertoriés dans le volet
    de détails :

- Unité de contrôle des appareils MDM Microsoft Intune

- Accès-organisation-MS

- MS-Organization-P2P-Access \[2024\]

Cela indique que l'appareil est inscrit dans Microsoft Entra et Intune.

![](./media/image15.png)

4.  Fermez la fenêtre Certificats.

5.  Cliquez avec le bouton droit de la souris sur le bouton **Start**,
    puis sélectionnez **Windows Terminal (Admin)**.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image16.png)

6.  Dans la boîte de dialogue **User Account Control** cliquez sur le
    bouton **Yes**.

![Une capture d'écran d'une erreur informatique Description générée
automatiquement](./media/image17.png)

7.  Dans la console PowerShell, tapez ce qui suit et appuyez sur
    **Enter** :

!!**dsregcmd /status** !!

8.  Dans la sortie, sous **Device State**,, vérifiez que **AzureAdJoined
    : YES** s'affiche. Cela indique que l'appareil est joint à Azure AD.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image18.png)

9.  Dans la sortie sous **Détails du Tenant**, vérifiez que les trois
    entrées suivantes existent :

- mdmUrl :https :enrollment.manage.microsoft.com/enrollmentserver/discovery.svc

- mdmTouUrl :https :portal.manage.microsoft.com/TermsofUse.aspxmdm

- ComplianceUrl :https :portal.manage.microsoft.com/?portalAction=Compliance

![](./media/image19.png)

*Remarque : Ces entrées indiquent que l'appareil est inscrit dans
Intune.*

**Tâche 3 : Se connecter en tant qu'utilisateur Microsoft Entra ID**

1.  Déconnectez-vous de **SEA-WS1** car vous êtes connecté avec le
    compte d'administrateur local.

2.  Sur l'écran de connexion, sélectionnez Autre utilisateur et
    connectez-vous en tant que
    !!**Cindy@M365xXXXXXXX.onmicrosoft.com** !!  avec le mot de passe :
    !\![**P@55w.rd1234**](mailto:P@55w.rd1234) !!

![](./media/image20.png)

3.  Attendez que le profil soit créé

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image21.png)

**Remarque** - Si vous êtes invité à utiliser **Windows Hello**,
terminez le processus de connexion en conséquence et sur la page **Set
up a PIN**, dans les zones **New PIN** et **Confirm PIN**, tapez
!!**102938** !! , puis sélectionnez **OK**.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image22.png)

4.  Se déconnecter de **SEA-WS1**.

**Tâche 4 : Vérification de l'inscription de l'appareil dans la console
Microsoft Intune**

1.  Passez à
    *[SEA-SVR1](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)*
    et connectez-vous à l'aide des informations d'identification
    fournies.

2.  Dans le navigateur Microsoft Edge, tapez
    !!**https://intune.microsoft.com** !! dans la barre d'adresse, puis
    appuyez sur **Enter** Connectez-vous à l'aide de votre compte
    d'administrateur de locataire Office 365.

3.  Dans le volet de navigation, sélectionnez **Devices**.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image23.png)

4.  Sur les **appareils | Aperçu**, naviguez et cliquez sur **Windows**.

![](./media/image24.png)

5.  Naviguez et cliquez sur **Windows devices**. Vérifiez que
    **SEA-WS1** est répertorié.

Notez que pour SEA-WS1, la colonne **Géré par** affiche **Intune** et la
colonne **wnership** affiche **Corporate**.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image25.png)

**Remarque** : Cette vue répertorie les appareils inscrits à Intune.
N'oubliez pas que vous avez configuré l'inscription automatique entre
Microsoft Entra et Microsoft Intune, et que, pour cette raison, tout
appareil joint ou inscrit à Microsoft Entra est automatiquement inscrit
à Microsoft Intune. Tous les appareils joints avant la configuration de
l'inscription sont uniquement joints ou enregistrés auprès d'Entra, mais
ne sont pas inscrits dans Intune.

6.  Ouvrez un nouvel onglet et accédez **Microsoft Entra admin center**
    !!**https://entra.microsoft.com** !!. Cliquez sur **Devices** , puis
    sélectionnez **All devices**

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image26.png)

7.  Prenez note de **SEA-WS1**. Notez que la colonne **Join Type**
    affiche Microsoft Entra joint et la colonne **MDM** affiche
    Microsoft Intune.

![Une capture d'écran d'un ordinateur Description générée
automatiquement](./media/image27.png)

**Résultats** : Une fois cet exercice terminé, vous aurez joint un
client Windows à Microsoft Entra ID et vérifié que l'appareil s'est
automatiquement inscrit à Microsoft Intune.
