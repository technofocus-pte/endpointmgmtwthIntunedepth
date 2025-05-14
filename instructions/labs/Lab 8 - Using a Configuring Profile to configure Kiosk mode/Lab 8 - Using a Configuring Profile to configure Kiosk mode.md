**Laboratório 8 - Utilizando um Perfil de Configuração para configurar o
Modo Kiosk**

**Resumo**

Neste laboratório, usaremos o Microsoft Intune para criar e aplicar um
perfil de configuração para executar o modo kiosk de aplicativo único em
um dispositivo Windows 11.

**Pré-requisitos**

Os seguintes laboratórios devem ser concluídos antes deste laboratório:

- Laboratório 5 - Gerenciar registro de dispositivos no Microsoft Intune

Observação: você também precisará de um telefone celular que possa
receber mensagens de texto usadas para proteger a autenticação de login
do Windows Hello no Entra ID.

**Exercício 1: Criar e aplicar um perfil de configuração**

**Cenário**

Você foi solicitado a configurar o **SEA-WS2** como um kiosk do Windows
11 para permitir que os visitantes da Contoso naveguem na internet. Você
precisa garantir que o kiosk esteja configurado da seguinte forma:

- Um único aplicativo, kiosk em tela cheia.

- Logon automático.

- Fornece acesso ao navegador Microsoft Edge, que deve ser configurado
  no modo Public Browsing (InPrivate). A página inicial deve ser
  configurada para **http://bing.com.**

**Tarefa 1: Registrar SEA-WS2 no Microsoft Intune**

1.  Entre no
    [*SEA-WS2*](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)
    como **Admin** com a senha !!**Pa55w.rd**!!.

2.  Na barra de tarefas, selecione !!**Pa55w.rd**!! e depois
    **Settings**.

![](./media/image1.png)

3.  Na janela **Settings**, selecione **Accounts**.

![A screenshot of a computer Description automatically
generated](./media/image2.png)

4.  Na página Accounts, selecione **Access work or school**.

![A screenshot of a computer Description automatically
generated](./media/image3.png)

5.  Na página **Access work or school**, selecione **Connect**.

![A screenshot of a computer Description automatically
generated](./media/image4.png)

6.  Na janela **Microsoft account**, selecione **Join this device to
    Microsoft Entra ID**.

![A screenshot of a computer screen Description automatically
generated](./media/image5.png)

7.  Na página **Sign in**, digite
    !!**AllanD@M365xXXXXXX.onmicrosoft.com**!! e então selecione
    **Next**.

![](./media/image6.png)

8.  Na página **Enter password**, digite a senha do locatário:
    !!**P@55w.rd1234**!! e então selecione **Sign in**.

![A screenshot of a computer Description automatically
generated](./media/image7.png)

9.  Na caixa de diálogo **Make sure this is your organization**,
    selecione **Join**.

![A screenshot of a computer error Description automatically
generated](./media/image8.png)

10. Na página **You're all set!,** leia as informações e selecione
    **Done**.

![A screenshot of a computer screen Description automatically
generated](./media/image9.png)

11. Na seção **Access work or school**, verifique se a **Connected to
    Contoso's Azure AD** é exibida.

![A screenshot of a computer Description automatically
generated](./media/image10.png)

12. Selecione **Connected to Contoso's Azure AD** e depois selecione
    **Info**.

![A screenshot of a computer Description automatically
generated](./media/image11.png)

13. Role para baixo e selecione **Sync**. Isso forçará a sincronização
    do dispositivo com o Intune.

![A screenshot of a computer Description automatically
generated](./media/image12.png)

14. Feche a janela **Settings**.

**Tarefa 2: Criar o grupo de dispositivos Contoso Kiosk**

1.  Em
    [*SEA-SVR1*](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10),
    acesse a aba **Microsoft Entra admin center**. Navegue e selecione
    **Grupos** e clique em **All groups**.

![](./media/image13.png)

2.  Na página **Groups | All groups**, selecione **New group**.

![A screenshot of a computer Description automatically
generated](./media/image14.png)

3.  No painel **New Group**, insira as seguintes informações:

- Group type: **Security**

- Group name: !! Contoso Kiosk Devices!!

- Group description: !!All Windows devices configured as a Kiosk!!

- Membership type: **Assigned**

4.  Em **Members**, selecione **No members selected**.

![](./media/image15.png)

5.  No painel **Add members**, na caixa **Search**, digite **Sea.**
    Selecione **SEA-WS2** e, em seguida, escolha **Select**.

![](./media/image16.png)

6.  No painel **New Group**, selecione **Create**.

![A screenshot of a computer Description automatically
generated](./media/image17.png)

7.  No painel **Groups | All groups**, atualize a página e verifique se
    o grupo **Contoso Kiosk Devices** é exibido.

![](./media/image18.png)

**Tarefa 3: Criar um perfil de configuração com base nos requisitos do
cenário**

1.  Volte ao Microsoft Intune admin center e selecione **Devices** na
    barra de navegação.

![A screenshot of a computer Description automatically
generated](./media/image19.png)

2.  Na página **Devices | Overview**, selecione **Windows,** como
    mostrado na imagem abaixo.

![A screenshot of a computer Description automatically
generated](./media/image20.png)

3.  Na página **Windows | Windows devices**, navegue e clique em
    **Configuration profiles**.

![A screenshot of a computer Description automatically
generated](./media/image21.png)

4.  Na página **Windows | Configuration profiles**, na guia
    **Policies**, clique em **+ Create** e selecione **+ New Policy**.

![A screenshot of a computer Description automatically
generated](./media/image22.png)

5.  No painel **Create a profile**, selecione as seguintes opções e, em
    seguida, selecione **Create**:

- Platform: **Windows 10 and later**

- Profile type: **Templates**

- Template name: !!**Kiosk**!!

![A screenshot of a computer Description automatically
generated](./media/image23.png)

6.  No painel **Basics**, insira as seguintes informações e selecione
    **Next**:

- Name: !!Contoso Kiosk Policy!!

- Description: !!Basic settings for Contoso Kiosk Devices.!!

![A screenshot of a computer Description automatically
generated](./media/image24.png)

7.  No painel **Configuration settings**, ao lado de **Select a kiosk
    mode**, selecione **Single app, full-screen kiosk**.

Opções adicionais são exibidas com base no modo selecionado.

8.  No painel **Configuration settings**, selecione as seguintes opções
    e, em seguida, selecione **Next**:

- User logon type: **Auto logon (Windows 10, version 1803 and later, or
  Windows 11)**

- Application type: **Add Microsoft Edge browser**

- Edge Kiosk URL: !! **http://bing.com**!!

- Microsoft Edge kiosk mode type: **Public Browsing (InPrivate)**

- Refresh browser after idle time: **5**

- Specify Maintenance Window for App Restarts: **Not configured**

> ![A screenshot of a computer Description automatically
> generated](./media/image25.png)

9.  No painel **Assignments**, em **Included groups**, selecione **Add
    groups**.

![A screenshot of a computer Description automatically
generated](./media/image26.png)

10. Na janela **Select groups to include**, selecione !!**Contoso Kiosk
    Devices**!! e clique em **Select**.

![A screenshot of a computer Description automatically
generated](./media/image27.png)

11. Na aba **Assignment**, clique no botão **Next**.

![A screenshot of a computer Description automatically
generated](./media/image28.png)

12. Na aba **Applicability Rules**, clique no botão **Next**.

![A screenshot of a computer Description automatically
generated](./media/image29.png)

13. Na aba **Review + create**, clique no botão **Create**.

![A screenshot of a computer Description automatically
generated](./media/image30.png)

14. O perfil de configuração será listado.

![A screenshot of a computer Description automatically
generated](./media/image31.png)

**Tarefa 4: Verifique se o perfil de configuração foi aplicado**

1.  Entre no
    [*SEA-WS2*](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)
    como **Admin** com a senha !!**Pa55w.rd**!!.

2.  Na barra de tarefas, selecione **Start** e depois **Settings**.

![A screenshot of a computer Description automatically
generated](./media/image1.png)

3.  Na janela **Settings**, selecione **Accounts**.

![A screenshot of a computer Description automatically
generated](./media/image2.png)

4.  Na página Accounts, selecione **Access work or school**.

![A screenshot of a computer Description automatically
generated](./media/image3.png)

5.  Selecione **Connected to Contoso's Azure AD** e depois selecione
    **Info**.

![A screenshot of a computer Description automatically
generated](./media/image11.png)

6.  Role para baixo e selecione **Sync**. Isso forçará a sincronização
    do dispositivo com o Intune.

![A screenshot of a computer Description automatically
generated](./media/image12.png)

7.  Feche a janela **Settings**.

> ![](./media/image32.png)

5.  Reinicie o **SEA-WS2**.

Observe que **o SEA-WS2** efetua login automaticamente e cria um perfil.
Após a conclusão do login, o Microsoft Edge é exibido configurado com
navegação InPrivate. Se o SEA-WS2 não efetuar login automaticamente,
repita as etapas de 1 a 7 para garantir que a política tenha sido
atualizada no dispositivo.

![](./media/image33.png)

**Resultados:** Após concluir este exercício, você terá criado e
atribuído com sucesso um perfil de configuração para configurar um
dispositivo Windows 11 como um kiosk de aplicativo único.
