Laboratório 22: Configurando a conexão com a nuvem e o cogerenciamento
usando o Configuration Manager

**Resumo**

Neste laboratório, você habilitará a conexão com a nuvem e configurará o
cogerenciamento usando o Microsoft Endpoint Configuration Manager e o
Microsoft Intune.

**Pré-requisitos**

Os seguintes laboratórios devem ser concluídos antes deste laboratório:

- Laboratório 01 - Gerenciando Identidades no Microsoft Entra ID

- Laboratório 02 - Sincronizando Identidades usando o Microsoft Entra
  Connect

- Laboratório 03 - Configurando e gerenciando o Microsoft Entra ID Join

- Laboratório 05 - Gerenciar registro de dispositivos no Microsoft
  Intune

**Cenário**

A Contoso possui uma implementação do Microsoft Endpoint Configuration
Manager e do Microsoft Intune. Você precisa configurar a integração
entre os dois serviços e habilitar o cogerenciamento para seus
dispositivos Windows gerenciados. Você habilitará a conexão com a nuvem,
configurará o cogerenciamento e, em seguida, validará as configurações
usando o SEA-CL1.

Tarefa 1: Preparar o ambiente

1.  Altere para [***SEA-SVR1***](urn:gd:lg:a:select-vm) e faça login
    como
    [**[Contoso\Administrator](urn:gd:lg:a:send-vm-keys)**](urn:gd:lg:a:send-vm-keys)
    com a senha !\![**Pa55w.rd**](urn:gd:lg:a:send-vm-keys)!!.

2.  No Gerenciador do Servidor, selecione **Tools** e, em seguida,
    **Active Directory Users and Computers**.

> ![](./media/image1.png)

3.  No painel de navegação, selecione **Seattle Clients**.

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)

4.  Clique com o botão direito do mouse em **SEA-CL1** e selecione
    **Move**.

> ![A computer screen shot of a computer Description automatically
> generated](./media/image3.png)

5.  Na caixa de diálogo **Move**, selecione **Entra clients** e depois
    selecione **OK.**

> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

6.  Feche **Active Directory Users and Computers**.

7.  Na barra de tarefas, clique com o botão direito do mouse em
    **Start** e selecione **Windows Powershell (Admin).**

> ![A screenshot of a computer Description automatically
> generated](./media/image5.png)

8.  Na janela do **Windows PowerShell**, digite o seguinte comando e
    pressione **Enter**:

> !!**Start**-ADSyncSyncCycle -PolicyType **Initial**!!
>
> ![A screenshot of a computer screen Description automatically
> generated](./media/image6.png)

9.  Feche a janela do PowerShell.

10. Altere para [***SEA-CL1***](urn:gd:lg:a:select-vm).

11. Na barra de tarefas, clique com o botão direito do mouse em
    **Start**, selecione **Shut down or sign out** e depois selecione
    **Restart**.

> ![](./media/image7.png)
>
> **Observação**: A reinicialização acionará a associação híbrida do
> Azure AD no SEA-CL1.

12. Após a reinicialização do [***SEA-CL1***](urn:gd:lg:a:select-vm),
    entre como
    [**[Contoso\Administrator](urn:gd:lg:a:send-vm-keys)**](urn:gd:lg:a:send-vm-keys)
    com a senha [**Pa55w.rd**](urn:gd:lg:a:send-vm-keys) .

13. Na barra de tarefas, clique com o botão direito do mouse em
    **Start** e selecione **Windows Terminal (Admin)**.

> ![](./media/image8.png)

14. Na janela do **Windows PowerShell**, digite o seguinte comando e
    pressione **Enter**:

> !!dsregcmd /**status**!!

15. Na saída em **Device State**, verifique se **AzureAdJoined: YES** e
    **DomainJoined: YES** são exibidos.

> ![](./media/image9.png)
>
> **Observação:** se o dispositivo ainda não estiver conectado ao Azure
> AD, aguarde a conclusão da sincronização do Azure AD Connect e
> reinicie o SEA-CL1 novamente.

16. Feche todas as janelas no [***SEA-CL1***](urn:gd:lg:a:select-vm).

Tarefa 2: Criar uma coleção de dispositivos

1.  Altere para [***SEA-CFG1***](urn:gd:lg:a:select-vm) e faça login
    como
    [**[Contoso\Administrator](urn:gd:lg:a:send-vm-keys)**](urn:gd:lg:a:send-vm-keys)
    com a senha [**Pa55w.rd**](urn:gd:lg:a:send-vm-keys) .

2.  Na barra de tarefas, selecione **Configuration Manager Console**. O
    console do Microsoft Endpoint Configuration Manager será aberto.

> ![A screenshot of a computer Description automatically
> generated](./media/image10.png)

3.  No espaço de trabalho **Assets and Compliance**, selecione **Device
    Collections**.

4.  Clique com o botão direito do mouse em **Device Collections** e
    selecione **Create Device Collection**. O Assistente para Criação de
    Coleção de Dispositivos será aberto.

> ![](./media/image11.png)

5.  Na página **General**, configure o seguinte e selecione **Next**:

    - Name: !\![**Co-managed Devices**](urn:gd:lg:a:send-vm-keys)!!

    - Limiting collection: **All Desktop and Server Clients**

> ![](./media/image12.png)
>
> ![](./media/image13.png)
>
> ![](./media/image14.png)

6.  Na página **Membership Rules**, selecione **Next**.

> ![A screenshot of a computer Description automatically
> generated](./media/image15.png)

7.  No aviso do Gerenciador de Configuração, selecione **OK.** Você
    adicionará um membro direto em uma etapa posterior.

> ![A screenshot of a computer error Description automatically
> generated](./media/image16.png)

8.  Na página **Summary**, selecione **Next** e, na página
    **Completion**, selecione **Close**.

> ![A screenshot of a computer Description automatically
> generated](./media/image17.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image18.png)

Tarefa 3: Atribuir um dispositivo a uma coleção existente

1.  No espaço de trabalho **Assets and Compliance**, selecione
    **Devices**.

> Anote os dispositivos listados. Qualquer dispositivo com um círculo
> verde com uma marca de seleção branca está ativo no momento.

2.  No painel de detalhes, selecione **SEA-CL1**.

3.  Clique com o botão direito do mouse em **SEA-CL1**, aponte para
    **Add Selected Items** e selecione **Add Selected Items to Existing
    Device Collection**.

> ![](./media/image19.png)

4.  Na caixa de diálogo **Select Collection**, selecione **Co-managed
    Devices** e, em seguida, selecione **OK.**

> ![](./media/image20.png)

5.  Para verificar, no espaço de trabalho **Assets and Compliance**,
    selecione **Device Collections** e clique duas vezes em **Co-managed
    Devices**.

> ![](./media/image21.png)
>
> ![](./media/image22.png)
>
> **SEA-CL1** deve ser listado como membro desta coleção.

Tarefa 4: Anexar a nuvem ao Endpoint Configuration Manager

1.  No console do Microsoft Endpoint Configuration Manager, selecione o
    workspace **Administration**.

> ![](./media/image23.png)

2.  No espaço de trabalho **Administration**, expanda **Cloud Services**
    e selecione **Cloud Attach**.

> ![A screenshot of a computer Description automatically
> generated](./media/image24.png)

3.  Na faixa de opções, selecione **Configure Cloud Attach**. O **Cloud
    Attach Configuration Wizard** será aberto.

> ![](./media/image25.png)
>
> ![](./media/image26.png)

4.  Em **Cloud Attach Configuration Wizard**, na página **Cloud
    Attach,** selecione **Sign In**.

5.  Entre como
    [**[admin@M365x19242953.onmicrosoft.com](urn:gd:lg:a:send-vm-keys)**](urn:gd:lg:a:send-vm-keys)
    com a senha [**9whL~;H8ke=D1^95%D**](urn:gd:lg:a:send-vm-keys).

6.  Na página **Cloud attach**, selecione **Customize settings** e
    selecione **Next**.

> ![](./media/image27.png)

7.  No aviso **Create AAD Application**, selecione **Yes**.

> ![A screenshot of a computer Description automatically
> generated](./media/image28.png)

8.  Na página **Configure upload**, aceite o padrão e selecione
    **Next**.

> ![A screenshot of a computer Description automatically
> generated](./media/image29.png)

9.  Na página **Enablement**, ao lado de **Automatic enrollment in
    Intune**, selecione **Pilot**.

10. Na página **Enablement**, ao lado de **Intune Auto Enrollment**,
    selecione **Browse**.

> ![](./media/image30.png)

11. Na caixa de diálogo **Select Collection**, selecione **Co-managed
    Devices** e, em seguida, **OK.** Selecione **Next**.

> ![A screenshot of a computer Description automatically
> generated](./media/image31.png)

12. Na página **Summary**, selecione **Next** e, na página
    **Completion**, selecione **Close**.

> ![A screenshot of a computer Description automatically
> generated](./media/image32.png)

Tarefa 5: Configurar cargas de trabalho

1.  No console do Microsoft Endpoint Configuration Manager, selecione o
    workspace **Administration**.

2.  No espaço de trabalho **Administration**, expanda **Cloud Services**
    e selecione **Cloud Attach**.

3.  No painel de detalhes, selecione **CoMgmtSettingsProd** e, na faixa
    de opções, selecione **Properties**.

> ![A screenshot of a computer Description automatically
> generated](./media/image33.png)
>
> A caixa **CoMgmtSettingsProd Properties** é aberta.

4.  Selecione **Workloads**. Na página **Workloads**, arraste o controle
    deslizante para **Pilot Intune** para as seguintes cargas de
    trabalho:

    - **Compliance policies**

    - **Client apps**

    - **Windows Update policies**

> ![](./media/image34.png)

5.  Selecione a **Staging page**. Na página **Staging**, selecione
    **Browse** ao lado de **Compliance policies**, **Client Apps** e
    **Windows Update Policies** e selecione a coleção **Co-managed
    Devices** para cada carga de trabalho.

6.  Selecione **OK** para fechar a caixa **CoMgmtSettingsProd
    Properties**.

> ![](./media/image35.png)

Tarefa 6: Validar que a SEA-CL1 é co-gerenciada

1.  Altere para [***SEA-SVR1***](urn:gd:lg:a:select-vm).

2.  Na barra de tarefas, selecione **Microsoft Edge**, na barra de
    endereço
    type [**https://entra.microsoft.com**](https://entra.microsoft.com)
    e pressione **Enter.**

3.  Entre como usuário
    [**[admin@M365x19242953.onmicrosoft.com](urn:gd:lg:a:send-vm-keys)**](urn:gd:lg:a:send-vm-keys)
    e use a senha.

4.  Se a mensagem **Stay signed in?** aparecer, selecione **No**.

> O centro de administração do Microsoft Entra será aberto.

5.  No centro de administração do Microsoft Entra, no painel de
    navegação, selecione **Identity.**

> ![](./media/image36.png)

6.  Na página **Devices|All devices**, verifique se **SEA-CL1** está
    listado e se o **Join Type** é **Microsoft Entra hybrid Join**.

> ![](./media/image37.png)

7.  No Microsoft Edge, abra outra aba e digite
    [**https://intune.microsoft.com**](https://intune.microsoft.com) na
    barra de endereço e pressione **Enter.**

8.  No painel de navegação, selecione **Devices** e depois **All
    devices**.

9.  Verifique se **SEA-CL1** está listado com a configuração **Managed
    by** definida como **Co-managed**.

> ![](./media/image38.png)
>
> Pode levar algum tempo para aparecer. Atualize o painel de detalhes
> conforme necessário. A máquina pode aparecer com um nome diferente.
> Clique no dispositivo para confirmar que ele indica **SEA-CL1.**

10. Selecione **SEA-CL1** e, no painel de detalhes, role para baixo para
    exibir informações relacionadas ao estado de cogerenciamento.

11. Feche o Microsoft Edge.

**Resultados:** Após concluir este exercício, você terá habilitado com
sucesso a conexão com a nuvem e configurado o cogerenciamento usando o
Microsoft Endpoint Configuration Manager e o Microsoft Intune.
