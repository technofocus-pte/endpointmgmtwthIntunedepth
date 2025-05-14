Laboratório12 - Implementando aplicativos em nuvem usando o Microsoft
Intune

**Resumo**

Neste laboratório, você criará e implementará aplicativos baseados em
nuvem usando o Intune e o site Company Portal.

**Pré-requisitos**

Os seguintes laboratórios devem ser concluídos antes deste laboratório:

- Laboratório nº 1 - Gerenciando Identidades no Microsoft Entra ID

- Laboratório nº 2 - Sincronizando Identidades usando o Microsoft Entra
  Connect

- Laboratório nº 5 - Gerenciar registro de dispositivos no Microsoft
  Intune

- Laboratório nº 6 - Registro de dispositivos no Microsoft Intune

- Laboratório nº 7 - Criação e implementação de perfis de configuração

**Observação:** você também precisará de um telefone celular que possa
receber mensagens de texto usadas para proteger a autenticação de login
do Windows Hello no Microsoft Entra ID.

Exercício 1: Adicionar um aplicativo da Microsoft Store ao Microsoft
Intune

**Cenário**

Você usa o Microsoft Intune para gerenciar o desktop e aplicativos para
a Contoso Corporation. O departamento de Pesquisa frequentemente se
conecta a vários servidores para executar tarefas e solicitou que o
aplicativo Microsoft Remote Desktop estivesse disponível para os membros
da Pesquisa instalarem conforme necessário. O Microsoft Remote Desktop
está disponível na Microsoft Store, mas você decide adicionar o
aplicativo ao Intune para que os usuários possam acessá-lo pelo site
Company Portal. Um membro da Pesquisa chamado Aaron Nicholls concordou
em testar o processo de instalação após você publicar o aplicativo no
portal.

Tarefa 1: Adicionar o Microsoft Remote Desktop ao Microsoft Intune

1.  Em
    [***SEA-SVR1***](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17),
    se necessário, faça login como
    [**[Contoso\Administrator](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17)**](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17)
    com a senha !\![**Pa55w.rd**](urn:gd:lg:a:select-vm)!! e feche o
    **Server Manager**.

2.  Na barra de tarefas, selecione **Microsoft Edge.**

3.  No Microsoft Edge, digite !!
    [**https://Intune.microsoft.com**](urn:gd:lg:a:select-vm) !! na
    barra de endereço e pressione **Enter**.

4.  Entre usando as credenciais do locatário do Office 365 na aba
    Início.

5.  Na página do **Microsoft Intune admin center**, selecione **Apps**.

> ![A screenshot of a computer Description automatically
> generated](./media/image1.png)

6.  Na página **Apps**, no painel de navegação, selecione **All apps**.

7.  No painel de detalhes, selecione **+Add**.

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)

8.  Na página **Select app type**, clique no menu suspenso e selecione
    **Microsoft store app (new)**.

> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)
>
> Leia as informações sobre o aplicativo da Microsoft Store e clique em
> **Select**. A página **Add App** será aberta.

9.  Na página de **App information**, clique no Link **Search the**
    **Microsoft Store app (new)**.

> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

10. Na aba de pesquisa **Search the** **Microsoft Store app (new)** e
    selecione !\![**Microsoft Remote
    Desktop**](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17)!!
    e clique no botão Select.

> ![A screenshot of a computer Description automatically
> generated](./media/image5.png)

11. De volta à aba Add App, insira as seguintes informações e selecione
    **Next**:

    - Category: **Business**

    - Show this as a featured app in the Company Portal: **Yes**

> ![A screenshot of a computer Description automatically
> generated](./media/image6.png)

12. Na aba **Assignments**, clique em **+ Add group**

> ![A screenshot of a computer Description automatically
> generated](./media/image7.png)

13. Na página **Select groups**, selecione o grupo **Research, Sales** e
    clique em **Select**.

> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)

14. Clique no botão **Next**.

> ![A screenshot of a computer Description automatically
> generated](./media/image9.png)

15. Na aba Review + create, clique no botão **Create**.

> ![](./media/image10.png)

16. A página da Microsoft Remote Desktop é aberta.

> Tome nota dos nós de Propriedades, Device install status e User
> install status.
>
> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)

Tarefa 2: Forçar a sincronização de políticas do console do Microsoft
Intune

1.  No **Microsoft Intune admin center**, selecione **Devices** e depois
    **All devices**.

2.  No painel de details, selecione **SEA-WS1.**

> ![A screenshot of a computer Description automatically
> generated](./media/image12.png)

3.  No painel **SEA-WS1**, selecione **Sync** e, quando solicitado,
    selecione **Yes**.

> ![A screenshot of a computer Description automatically
> generated](./media/image13.png)
>
> O Microsoft Intune entrará em contato com o dispositivo e sincronizará
> todas as políticas. Isso pode levar até 5 minutos.

Tarefa 3: Instalar um aplicativo do site Company Portal

1.  Entre no [*SEA-WS1*]() como **Cindy White** usando as credenciais
    dela !! !!**Cindy@M365xXXXXXX.onmicrosoft.com**!! com Senha
    !!**P@55w.rd1234**!! ou com o PIN !!**102938**!!

2.  Na barra de tarefas, selecione **Microsoft Edge.**

3.  Se necessário, na página **Welcome to Microsoft Edge**, selecione
    **Confirm and continue**. Feche a página Welcome.

4.  Na barra de endereço, navegue até
    !\![**https://portal.manage.microsoft.com**](urn:gd:lg:a:send-vm-keys)!!

5.  Entre como !!**Cindy@M365xXXXXXX.onmicrosoft.com**!!

> ![](./media/image14.png)

6.  No portal da web da Contoso, selecione **Devices.**.

> ![A screenshot of a computer Description automatically
> generated](./media/image15.png)

7.  Na página Devices, selecione **Tap here to tell us which device
    you're using or add a new device**.

> ![](./media/image16.png)

8.  Na caixa de diálogo **Which device are you using**, selecione a
    opção ao lado de **SEA-WS1** e clique no botão **Select**.

> ![A screenshot of a computer Description automatically
> generated](./media/image17.png)
>
> Observe que a mensagem agora muda para Apps will be installed onto:
> **SEA-WS1**
>
> ![](./media/image18.png)

9.  No canto superior esquerdo, selecione o botão de navegação e depois
    selecione **Downloads & updates**.

> ![A screenshot of a computer Description automatically
> generated](./media/image19.png)

10. Nos resultados listados, verifique o status, o aplicativo
    **Microsoft Remote Desktop** deve aparecer como Instalado.

> Observação: pode levar de 10 a 20 minutos para o aplicativo aparecer.
>
> ![A screenshot of a computer Description automatically
> generated](./media/image20.png)

11. Clique em **Start** **Menu** e verifique se a **Remote Desktop** é
    exibida no menu Iniciar.

> ![A screenshot of a computer Description automatically
> generated](./media/image21.png)

**Resultados:** Após concluir este exercício, você terá adicionado e
instalado com sucesso um aplicativo da Microsoft Store do Microsoft
Intune.

Exercício 2: Configurar e implementar Microsoft 365 Apps a partir do
Microsoft Intune

**Cenário**

Todos os usuários do departamento de Pesquisa da Contoso precisam dos
Microsoft 365 Apps. Você foi solicitado a implementar as versões de 64
bits do Microsoft Excel, Outlook, PowerPoint e Word em seus dispositivos
Windows. Você também precisa garantir que eles estejam configurados para
o canal atual para atualizações.

Tarefa 1: Verificar aplicativos instalados no SEA-WS1

1.  Em [***SEA-WS1***](urn:gd:lg:a:send-vm-keys), na barra de tarefas,
    selecione **Start** e depois selecione o aplicativo **Settings**.

> ![A screenshot of a computer Description automatically
> generated](./media/image22.png)

2.  No aplicativo **Settings**, selecione **Apps** e, em seguida, **Apps
    & features**.

> ![A screenshot of a computer Description automatically
> generated](./media/image23.png)
>
> Verifique se o **Microsoft 365 Apps for enterprise - en-us** não está
> listado.
>
> ![A screenshot of a computer Description automatically
> generated](./media/image24.png)

3.  Feche todas as janelas abertas.

Tarefa 2: Adicionar Microsoft 365 Apps ao Microsoft Intune

1.  Altere para [***SEA-SVR1***](urn:gd:lg:a:send-vm-keys) e, no
    **Microsoft Intune admin center**, selecione **Apps**.

2.  Na aba **Apps | Overview**, selecione **All Apps**. No painel de
    detalhes, selecione **+ Add**.

> ![A screenshot of a computer Description automatically
> generated](./media/image25.png)

3.  No painel **Select app type**, em **Microsoft 365 Apps**, selecione
    **Windows 10 and later** e clique em **Select**.

> ![A screenshot of a computer Description automatically
> generated](./media/image26.png)

4.  No painel **Add Microsoft 365 Apps**, configure as seguintes opções
    e selecione **next**:

    - Suite Name: !\![**Microsoft 365 Apps
      (Research)**](urn:gd:lg:a:select-vm)!!

    - Suite Description: !\![**Microsoft 365 Apps for the Research
      department at Contoso**](urn:gd:lg:a:select-vm) !! (Selecione
      **Edit Description** para inserir essas informações.)

> ![A screenshot of a computer Description automatically
> generated](./media/image27.png)

5.  Na guia **Configure app suite**, expanda o menu suspenso **Select
    Office apps** e selecione os seguintes aplicativos do Office:

    - Excel

    - Outlook

    - PowerPoint

    - Word

> ![A screenshot of a computer Description automatically
> generated](./media/image28.png)

6.  Na aba **Configure app suite**, configure as seguintes opções e
    selecione **Next**:

    - Architecture: **64-bit**

    - Default file format: **Office Open XML Format**

    - Update channel: **Current Channel**

    - Accept the Microsoft Software License Terms on behalf of
      users: **Yes**

> ![A screenshot of a computer Description automatically
> generated](./media/image29.png)

7.  Na aba **Assignments**, na seção **Required**, selecione **Add
    group.**

> ![A screenshot of a computer Description automatically
> generated](./media/image30.png)

8.  No painel **Select groups**, selecione **Research** e, em seguida,
    escolha **Select**.

> ![A screenshot of a group Description automatically
> generated](./media/image31.png)

9.  Selecione **Next**.

> ![A screenshot of a computer Description automatically
> generated](./media/image32.png)

10. Na aba **Review + Create**, selecione **Create**.

> ![A screenshot of a computer Description automatically
> generated](./media/image33.png)

11. Na página **Microsoft 365 Apps (Research)**, selecione
    **Properties**.

> ![A screenshot of a computer Description automatically
> generated](./media/image34.png)

12. No painel de detalhes, verifique se **Research** está listada em
    **Required** na seção **Assignments**.

> ![A screenshot of a computer Description automatically
> generated](./media/image35.png)

Tarefa 3: Forçar a sincronização de políticas do console do Microsoft
Intune

1.  No **Microsoft Intune admin center**, selecione **Devices** e depois
    **All devices**.

2.  No painel de details, selecione **SEA-WS1**.

> ![A screenshot of a computer Description automatically
> generated](./media/image36.png)

3.  No painel **SEA-WS1**, selecione **Sync** e, quando solicitado,
    selecione **Yes**.

> ![A screenshot of a computer Description automatically
> generated](./media/image37.png)
>
> O Microsoft Intune entrará em contato com o dispositivo e sincronizará
> todas as políticas. Isso pode levar até 5 minutos.

Tarefa 4: Verificar se os Microsoft 365 Apps estão instalados

1.  Se você já estiver conectado no
    [*SEA-WS1*](urn:gd:lg:a:send-vm-keys?rc=10) como **Cindy White.**

> **Observação** – Pode ser necessário aguardar aproximadamente 10 a 15
> minutos para que o Microsoft 365 Suite seja instalado no dispositivo.

2.  Saia e entre novamente no [*SEA-WS1*]() como **Cindy White** usando
    as credenciais dela !!**Cindy@M365xXXXXXX.onmicrosoft.com**!! com
    Senha !!**P@55w.rd1234**!!

3.  No ***[SEA-WS1](urn:gd:lg:a:send-vm-keys),*** na barra de tarefas,
    selecione **Start** e depois selecione o aplicativo **Settings**.

> ![A screenshot of a computer Description automatically
> generated](./media/image38.png)

4.  No aplicativo **Settings**, selecione **Apps** e na página **Apps &
    features**.

> ![A screenshot of a computer Description automatically
> generated](./media/image23.png)

5.  Pesquise por !!**Microsoft 365**!! e verifique se **Microsoft 365
    Apps for enterprise - en-us** está listado.

> ![A screenshot of a computer Description automatically
> generated](./media/image39.png)

6.  Feche o aplicativo **Settings** e selecione o botão **Start**.

7.  Na seção **Recommended,** você poderá ver os aplicativos
    recém-instalados que foram selecionados nos Microsoft 365 Apps no
    Microsoft Intune.

> ![A screenshot of a computer Description automatically
> generated](./media/image40.png)

Tarefa 5: Monitorar o status da instalação do aplicativo no Microsoft
Intune

1.  Altere para **[*SEA-SVR1*](urn:gd:lg:a:select-vm)** e no **Microsoft
    Intune admin center**, selecione **Apps**.

> ![](./media/image41.png)

2.  No painel **Apps | Overview**, selecione **Monitor** e depois **App
    install status**.

> ![A screenshot of a computer Description automatically
> generated](./media/image42.png)

3.  No painel de detalhes, selecione **Microsoft 365 Apps (Research)**.

> ![A screenshot of a computer Description automatically
> generated](./media/image43.png)

4.  No painel de detalhes, em **Device status** e em **User status**,
    verifique se **1** é exibido em Instalado.

> ![A screenshot of a computer Description automatically
> generated](./media/image44.png)
>
> **Observação:** Isso indica que o aplicativo está instalado em um
> dispositivo e para um usuário. Observe que pode levar algum tempo para
> que as informações sejam exibidas e apareçam como **Install Pending**.
>
> **Observação:** você pode iniciar o **Laboratório 13** e verificar
> novamente após **30 a 45** minutos.

![A screenshot of a computer Description automatically
generated](./media/image45.png)

5.  Selecione **Device install status**.

> No painel de details, você pode ver os dispositivos nos quais o
> aplicativo está instalado e também o nome do usuário. A coluna
> **Device Name** deve listar **SEA-WS1,** e a coluna **Status**. Isso
> significa que o aplicativo está instalado em **SEA-WS1.**
>
> ![A screenshot of a computer Description automatically
> generated](./media/image46.png)

6.  No **Microsoft Intune admin center**, selecione **Devices**.

7.  No painel **Devices | Overview**, selecione **All devices** e, em
    seguida, no painel de detalhes, selecione **SEA-WS1**.

> ![A screenshot of a computer Description automatically
> generated](./media/image47.png)

8.  No painel **SEA-WS1**, selecione **Managed Apps**.

9.  No painel **SEA-WS1 | Managed Apps**, no painel de detalhes,
    selecione **Microsoft 365 Apps (Research)**.

> ![A screenshot of a computer Description automatically
> generated](./media/image48.png)
>
> Na janela **Microsoft 365 Apps (Research) - Installation details**,
> você pode ver todo o ciclo de vida do aplicativo, ou seja, quando ele
> foi criado, atribuído, hora e status da instalação e a última vez que
> o dispositivo fez check-in (sincronizado com o Microsoft Intune).
>
> ![A screenshot of a computer Description automatically
> generated](./media/image49.png)

10. Feche todas as janelas abertas.

**Resultados:** Após concluir este exercício, você terá configurado e
implementado com sucesso os Microsoft 365 Apps do Microsoft Intune.
