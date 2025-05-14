**Laboratório 6 - Registro de dispositivos no Microsoft Intune**

**Resumo**

Neste laboratório, você conectará um cliente Windows ao Entra ID e
verificará se o dispositivo foi registrado automaticamente no Microsoft
Intune.

**Pré-requisitos**

Os seguintes laboratórios devem ser concluídos antes deste laboratório:

- Laboratório nº 1 - Gerenciando Identidades no Microsoft Entra ID

- Laboratório nº 2 - Sincronizando Identidades usando o Microsoft Entra
  Connect

- Laboratório nº 5 - Gerenciar registro de dispositivos no Microsoft
  Intune

Observação: você também pode precisar de um telefone celular que possa
receber mensagens de texto usadas para autenticar o login com o Windows
Hello no Entra ID.

**Cenário**

Você atribuiu as licenças apropriadas à Cindy White e agora testará o
processo de associação de um dispositivo Windows ao Entra ID e fará com
que ele seja registrado automaticamente no Microsoft Intune.

**Tarefa 1: Registrar automaticamente um dispositivo Windows no
Microsoft Intune**

1.  Altere para
    [*SEA-WS1*](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)
    e faça login como **Admin** com a senha !!**Pa55w.rd**!!

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image1.png)

2.  Na barra de tarefas, selecione **Start** e depois **Settings**.

![A screenshot of a computer Description automatically
generated](./media/image2.png)

3.  Na janela **Settings**, selecione **Accounts**.

![A screenshot of a computer Description automatically
generated](./media/image3.png)

4.  Na página Contas, selecione **Access work or school**.

![A screenshot of a computer Description automatically
generated](./media/image4.png)

5.  Na página **Access work or school**, selecione **Connect**.

![A screenshot of a computer Description automatically
generated](./media/image5.png)

6.  Na janela da **Microsoft account**, selecione **Join this device to
    Microsoft Entra ID**.

![](./media/image6.png)

7.  Na página de **Sign in**, digite
    !\![**Cindy@M365x51282399.onmicrosoft.com**](mailto:Cindy@M365x51282399.onmicrosoft.com)!!
    e selecione **Next**.

![](./media/image7.png)

8.  Na página **Enter password**, digite a senha:
    !\![**P@55w.rd1234**](mailto:!!P@55w.rd1234)!! e selecione **Sign
    in**.

![A screenshot of a computer Description automatically
generated](./media/image8.png)

9.  Aparecerá a caixa de diálogo **Make sure this is your organization**
    e selecione **Join.**

![](./media/image9.png)

10. Na página **You're all set!,** leia as informações e selecione
    **Done**.

![A screenshot of a computer Description automatically
generated](./media/image10.png)

11. Na seção **Access work or school**, verifique se a **Connected to
    Contoso's Azure AD** é exibida.

12. Selecione **Connected to Contoso's Azure AD** e depois selecione
    **Info**.

![A screenshot of a computer Description automatically
generated](./media/image11.png)

13. Anote as informações sobre as áreas gerenciadas pela Contoso, role a
    tela para baixo e selecione **Sync**. Isso forçará a sincronização
    do dispositivo com o Intune.

![A screenshot of a computer Description automatically
generated](./media/image12.png)

14. Feche a janela **Settings**.

**Tarefa 2: Validar o registro do dispositivo no Microsoft Entra e
Intune**

1.  Na barra de tarefas do **SEA-WS1**, selecione **Start**, digite
    !!**certlm.msc**!!!! e pressione **Enter**.

![A screenshot of a computer Description automatically
generated](./media/image13.png)

2.  Na caixa de diálogo Controle de Conta de Usuário, selecione o botão
    **Yes**.

![](./media/image14.png)

3.  No console **Certificates**, no painel de navegação, expanda
    **Personal** e selecione o nó **Certificate.** Verifique se os
    seguintes certificados estão listados no painel de detalhes:

- Microsoft Intune MDM Device CA

- MS-Organization-Access

- MS-Organization-P2P-Access \[2024\]

Isso indica que o dispositivo está registrado no Microsoft Entra e no
Intune.

![](./media/image15.png)

4.  Feche a janela Certificados.

5.  Clique com o botão direito do mouse no botão **Start** e selecione
    **Windows Terminal (Admin)**.

![A screenshot of a computer Description automatically
generated](./media/image16.png)

6.  Na caixa de diálogo **User Account Control**, clique no botão
    **Yes**.

![A screenshot of a computer error Description automatically
generated](./media/image17.png)

7.  No console do PowerShell, digite o seguinte e pressione **Enter**:

!!**dsregcmd /status**!!

8.  Na saída, em **Device State**, verifique se **AzureAdJoined: YES** é
    exibido. Isso indica que o dispositivo está associado ao Azure AD.

![A screenshot of a computer Description automatically
generated](./media/image18.png)

9.  Na saída em **Tenant Details**, verifique se as três entradas a
    seguir existem:

- mdmUrl:https://enrollment.manage.microsoft.com/enrollmentserver/discovery.svc

- mdmTouUrl:https://portal.manage.microsoft.com/TermsofUse.aspxmdm

- ComplianceUrl:https://portal.manage.microsoft.com/?portalAction=Compliance

![](./media/image19.png)

*Observação: essas entradas indicam que o dispositivo está registrado no
Intune.*

**Tarefa 3: Entrar como usuário do Microsoft Entra ID**

1.  Saia do **SEA-WS1,** pois você está conectado com a conta de
    administrador local.

2.  Na tela de login, selecione Other user e entre como
    !!**Cindy@M365xXXXXXXX.onmicrosoft.com**!! com a senha:
    !\![**P@55w.rd1234**](mailto:P@55w.rd1234)!!

![](./media/image20.png)

3.  Aguarde até que o perfil seja criado.

![A screenshot of a computer Description automatically
generated](./media/image21.png)

**Observação** – Se for solicitado o **Windows Hello**, conclua o
processo de login e, na página **Set up a PIN**, nas caixas **New PIN**
e **Confirm PIN,** digite !!**102938**!! e selecione **OK.**

![A screenshot of a computer Description automatically
generated](./media/image22.png)

4.  Saia do **SEA-WS1**.

**Tarefa 4: Verificando o registro do dispositivo no console do
Microsoft Intune**

1.  Mudar para
    [*SEA-SVR1*](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)
    e faça login usando as credenciais fornecidas.

2.  No navegador Microsoft Edge, digite
    !!**https://intune.microsoft.com**!! na barra de endereços e
    pressione **Enter.** Entre com sua conta de administrador de
    locatário do Office 365.

3.  No painel de navegação, selecione **Devices**.

![A screenshot of a computer Description automatically
generated](./media/image23.png)

4.  Na página **Devices | Overview**, navegue e clique em **Windows**.

![](./media/image24.png)

5.  Navegue e clique em **Windows devices**. Verifique se **SEA-WS1**
    está listado.

Observe que, para SEA-WS1, a coluna **Managed by** exibe **Intune**, e a
coluna **Ownership** exibe **Corporate**.

![A screenshot of a computer Description automatically
generated](./media/image25.png)

**Observação:** Esta exibição lista os dispositivos registrados no
Intune. Lembre-se de que você configurou o registro automático entre o
Microsoft Entra e o Microsoft Intune e, por isso, qualquer dispositivo
ingressado ou registrado no Microsoft Entra é automaticamente inscrito
no Microsoft Intune. Todos os dispositivos ingressados antes da
configuração do registro são ingressados ou registrados apenas no Entra,
mas não no Intune.

6.  Abra uma nova aba e navegue até o **Microsoft Entra admin center**
    !!**https://entra.microsoft.com**!!. Clique em **Devices** e depois
    selecione **All devices**.

![A screenshot of a computer Description automatically
generated](./media/image26.png)

7.  Observe o **SEA-WS1**. Observe que a coluna **Join Type** exibe o
    Microsoft Entra joined e a coluna **MDM** exibe o Microsoft Intune.

![A screenshot of a computer Description automatically
generated](./media/image27.png)

**Resultados:** Após concluir este exercício, você terá conectado com
sucesso um cliente Windows ao Microsoft Entra ID e verificado que o
dispositivo foi registrado automaticamente no Microsoft Intune.
