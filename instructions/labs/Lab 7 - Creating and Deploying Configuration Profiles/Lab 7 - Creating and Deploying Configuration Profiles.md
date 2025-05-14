**Laboratório 7 - Criação e implementação de perfis de configuração**

**Resumo**

Neste laboratório, usaremos o Microsoft Intune para criar e aplicar um
perfil de configuração para um dispositivo Windows 11.

**Pré-requisitos**

Os seguintes laboratórios devem ser concluídos antes deste laboratório:

- Laboratório nº 1 - Gerenciando Identidades no Microsoft Entra ID

- Laboratório nº 2 - Sincronizando Identidades usando o Microsoft Entra
  Connect

- Laboratório nº 5 - Gerenciar registro de dispositivos no Microsoft
  Intune

- Laboratório nº 6 - Registro de dispositivos no Microsoft Intune

Observação: Você também precisará de um telefone celular que possa
receber mensagens de texto, utilizadas para proteger a autenticação do
Windows Hello no ingresso ao Microsoft Entra ID.

**Exercício 1: Criar e aplicar um perfil de configuração.**

**Cenário**

Você precisa usar o Microsoft Entra e o Microsoft Intune para gerenciar
os membros do departamento de Desenvolvedores da Contoso. Você foi
solicitado a avaliar as soluções que permitiriam aos usuários trabalhar
de forma eficaz e segura em dispositivos Windows 11. Cindy White se
ofereceu para ajudar você a testar e avaliar a solução e fornecer
feedback. Ela também forneceu alguns requisitos iniciais que devem ser
incluídos e aplicados aos dispositivos Windows do desenvolvedor:

- A seção Jogos em Configurações não deve estar visível.

- A seção Privacidade em Configurações deve ser restringida o máximo
  possível.

- A pasta **C:\DevProjects** deve ser excluída do Windows Defender.

- O processo devbuild.exe deve ser excluído do Windows Defender.

- Os aplicativos mais usados e adicionados recentemente não devem ser
  exibidos no menu Iniciar.

**Tarefa 1: Verificar as configurações do dispositivo**

1.  Entre no
    [*SEA-WS1*](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)
    como **Cindy** White usando as credenciais dela
    !!**Cindy@M365xXXXXXX.onmicrosoft.com**!! com o PIN !!**102938**!!
    ou Senha !!**P@55w.rd1234**!!

![A screenshot of a computer Description automatically
generated](./media/image1.png)

2.  Na barra de tarefas, selecione **Start** e depois **Settings**.

![A screenshot of a computer Description automatically
generated](./media/image2.png)

3.  Na lista de navegação **Settings**, verifique se você consegue ver a
    configuração **Gaming.**

![A screenshot of a computer Description automatically
generated](./media/image3.png)

4.  Selecione a configuração **Personalization** e, na página
    Personalização, selecione **Start**. Anote as configurações **Show
    recently added apps** e **Show most used apps**.

![](./media/image4.png)

![A screenshot of a computer Description automatically
generated](./media/image5.png)

5.  No aplicativo **Settings**, selecione **Privacy & security**.

6.  Na página **Privacy & security**, observe as opções em
    **Security**, **Windows permissions** e **App permissions**.

![A screenshot of a computer Description automatically
generated](./media/image6.png)

7.  Na página **Privacy & security**, selecione **Windows Security** e
    depois selecione **Open Windows Security**.

![](./media/image7.png)

![A screenshot of a computer security Description automatically
generated](./media/image8.png)

8.  Na página **Windows Security**, selecione **Virus & threat
    protection**.

9.  Na página **Virus & threat protection**, em **Virus & threat
    protection settings**, selecione **Manage settings**.

![A screenshot of a computer Description automatically
generated](./media/image9.png)

10. Role para baixo até **Exclusions** e selecione **Add or remove
    exclusions**. Na caixa de diálogo Controle de Conta de Usuário,
    selecione **Yes**.

![A screenshot of a computer Description automatically
generated](./media/image10.png)

![A screenshot of a computer Description automatically
generated](./media/image11.png)

11. Na página **Exclusions**, verifique se nenhuma exclusão foi
    configurada.

12. Feche a janela **Windows Security**.

![A screenshot of a computer Description automatically
generated](./media/image12.png)

13. Feche a janela **Settings**.

**Tarefa 2: Criar um perfil de configuração com base nos requisitos do
cenário**

1.  Altere para
    [*SEA-SVR1*](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)
    .

2.  Volte para a aba com o **Microsoft Intune admin center** aberto e
    selecione **Devices** na barra de navegação.

![A screenshot of a computer Description automatically
generated](./media/image13.png)

3.  Na página **Devices | Overview**, selecione **Windows,** como
    mostrado na imagem abaixo.

![A screenshot of a computer Description automatically
generated](./media/image14.png)

4.  Na página **Windows | Windows devices**, navegue e clique em
    **Configuration profiles**.

![A screenshot of a computer Description automatically
generated](./media/image15.png)

5.  Na página **Windows | Configuration profiles**, na aba **Policies**,
    clique em **+ Create** e selecione **+ New Policy**.

![A screenshot of a computer Description automatically
generated](./media/image16.png)

6.  No painel **Create a profile** que aparece no lado direito,
    selecione as seguintes opções e, em seguida, selecione **Create**:

- Platform: **Windows 10 and later**

- Profile type: **Templates**

- Template name: !!!!

![A screenshot of a profile Description automatically
generated](./media/image17.png)

7.  No painel **Basics**, insira as seguintes informações e selecione
    **Next**:

- Name: !!Contoso Developer - standard!!

- Description: !!Basic restrictions and configuration for Contoso
  Developers.!!

![](./media/image18.png)

8.  No painel de **Configurations settings**, expanda **Control Panel
    and Settings**.

![A screenshot of a computer Description automatically
generated](./media/image19.png)

9.  Selecione **Block** ao lado das opções de **Gaming** e **Privacy**.

![A screenshot of a computer Description automatically
generated](./media/image20.png)

10. No painel **Device restrictions**, expanda **Start**.

![A screenshot of a computer Description automatically
generated](./media/image21.png)

11. Role para baixo e selecione **Block** ao lado de **Most used
    apps**, **Recently added apps** e **Recently opened items in Jump
    Lists**.

![A screenshot of a computer Description automatically
generated](./media/image22.png)

12. No painel **Device restrictions**, role para baixo e expanda
    **Microsoft Defender Antivirus** .

![A screenshot of a computer Description automatically
generated](./media/image23.png)

13. Em **Microsoft Defender Antivirus,** role para baixo e expanda
    **Microsoft Defender Antivirus Exclusions**.

![](./media/image24.png)

14. Em **Microsoft Defender Antivirus Exclusions,** forneça os detalhes
    abaixo e clique no botão **Next**:

- Files and folders box - !!**C:\DevProjects**!!

- Processes box - !!**DevBuild.exe**!!

![](./media/image25.png)

15. Na aba **Assignments**, clique no botão **Next**.

![A screenshot of a computer Description automatically
generated](./media/image26.png)

16. Na aba **Applicability Rules**, clique no botão **Next**.

![A screenshot of a computer Description automatically
generated](./media/image27.png)

17. No notebook **Review + create**, clique no botão **Create**.

![A screenshot of a computer Description automatically
generated](./media/image28.png)

18. O perfil de configuração deve estar listado agora.

![A screenshot of a computer Description automatically
generated](./media/image29.png)

**Tarefa 3: Criar o grupo de dispositivos do Desenvolvedor Contoso**

1.  No centro de administração do Microsoft Intune, no painel de
    navegação, selecione **Groups**.

![A screenshot of a computer Description automatically
generated](./media/image30.png)

2.  No painel **Groups | All groups**, selecione **New group**.

![A screenshot of a computer Description automatically
generated](./media/image31.png)

3.  No painel **New group**, insira as seguintes informações:

- Group type: **Security**

- Group name: !!Contoso Developer devices!!

- Group description: !!All Windows devices in Contoso Developer
  department!!

- Membership type: **Assigned**

4.  Em **Members**, selecione **No members selected**.

![](./media/image32.png)

5.  No painel **Add members,** em **Search** digite !!Sea!!. Selecione
    **SEA-WS1** e, em seguida, escolha **Select**.

![A screenshot of a computer Description automatically
generated](./media/image33.png)

6.  No painel **New Group**, selecione **Create**.

![](./media/image34.png)

7.  No painel **Groups | All groups,** verifique se o grupo **Contoso
    developer devices** é exibido.

![](./media/image35.png)

**Tarefa 4: Criar um grupo de Dispositivo dinâmico do Azure AD**

1.  No painel **Groups | All Groups**, no painel de detalhes, selecione
    **New group**.

![A screenshot of a computer Description automatically
generated](./media/image36.png)

2.  No painel **Group**, forneça os seguintes valores:

- Group type: **Security**

- Group name: !!Windows Devices!!

- Membership type: **Dynamic Device**

3.  Na seção **Dynamic Device Members**, selecione **Add dynamic
    query**.

![A screenshot of a computer Description automatically
generated](./media/image37.png)

4.  No painel **Dynamic membership rules**, na seção **Rule syntax**,
    selecione **Edit**.

![A screenshot of a computer Description automatically
generated](./media/image38.png)

5.  Na caixa de texto **Edit rule syntax**, adicione a seguinte regra de
    associação simples e selecione **OK** .

!!**(device.deviceOSType -contains "Windows")**!!

![A screenshot of a computer Description automatically
generated](./media/image39.png)

6.  No painel **Dynamic membership rules**, selecione **Save**.

![A screenshot of a computer Description automatically
generated](./media/image40.png)

7.  Na página **New Group**, selecione **Create**.

![A screenshot of a computer Description automatically
generated](./media/image41.png)

**Tarefa 5: Atribuir um perfil de configuração a dispositivos Windows**

1.  Na página do **Microsoft Intune admin center**, selecione
    **Devices** na barra de navegação.

![](./media/image42.png)

2.  Na página **Devices | Overview**, selecione **Windows,** como
    mostrado na imagem abaixo.

![](./media/image43.png)

3.  Na página **Windows | Windows devices**, navegue e clique em
    **Configuration profiles**.

![](./media/image44.png)

4.  No painel **Devices | Configuration profiles**, no painel de
    detalhes, selecione o perfil **Contoso Developer – standard**.

![A screenshot of a computer Description automatically
generated](./media/image45.png)

5.  No painel **Contoso Developer – standard**, role para baixo até a
    seção **Assignments** e selecione **Edit**.

![A screenshot of a computer Description automatically
generated](./media/image46.png)

6.  Na página Tarefas, em **Included groups,** selecione **Add groups**.

![A screenshot of a computer Description automatically
generated](./media/image47.png)

7.  No painel **Select groups to include**, na caixa **Search**, digite
    e selecione !!**Contoso Developer devices**!! e então clique no
    botão **Select**.

![](./media/image48.png)

8.  De volta à lâmina **Device restrictions**, selecione **Review +
    save** e, em seguida, selecione **Save**.

![A screenshot of a computer Description automatically
generated](./media/image49.png)

![](./media/image50.png)

**Tarefa 6: Verifique se o perfil de configuração foi aplicado**

1.  Altere para
    *[SEA-WS1](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10).* Faça
    login usando a conta de Cindy White.

- Username - !!**Cindy@M365xXXXXXXX.onmicrosoft.com**!!

- Password – !!**P@55w.rd1234**!!

2.  Na barra de tarefas, selecione **Start** e depois **Settings**.

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)

3.  Na janela **Settings**, selecione **Accounts**. Na página Contas,
    selecione **Access work or school**.

![A screenshot of a computer Description automatically
generated](./media/image51.png)

4.  Clique no menu suspenso ao lado de **Connected to Contoso’s Azure
    AD** e selecione o botão **Info**.

![](./media/image52.png)

5.  Na página **Managed by Contoso**, role para baixo e, em Status de
    sincronização do dispositivo, selecione **Sync**. Aguarde a
    conclusão da sincronização.

![A screenshot of a computer Description automatically
generated](./media/image53.png)

![A screenshot of a computer Description automatically
generated](./media/image54.png)

6.  Feche o aplicativo **Settings.**

> **Observação**: O andamento da sincronização pode levar até 15 minutos
> para que o perfil seja aplicado ao dispositivo Windows 11. Sair ou
> reiniciar o dispositivo pode acelerar esse processo.

7.  Em
    [*SEA-WS1*](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10),
    selecione **Start** novamente e, em seguida, **Settings**. Verifique
    se a configuração de **Gaming** foi removida.

![A screenshot of a computer Description automatically
generated](./media/image2.png)

![A screenshot of a computer Description automatically
generated](./media/image55.png)

8.  Selecione **Privacy & security** e observe que muitas das
    configurações de privacidade agora estão ocultas.

![](./media/image56.png)

9.  Selecione a configuração **Personalization** e, em seguida,
    **Start**. Verifique se **Show recently added apps** e **Show most
    used apps** estão definidos como **Off** e acinzentados.

![](./media/image57.png)

![A screenshot of a computer Description automatically
generated](./media/image58.png)

10. No aplicativo **Settings**, selecione **Privacy and Security**.

11. Na página **Privacy & Security**, selecione **Windows Security** e
    depois selecione **Open Windows Security**.

![](./media/image59.png)

![A screenshot of a computer security Description automatically
generated](./media/image60.png)

12. Na página **Windows Security**, selecione **Virus & threat
    protection**.

13. Na página **Virus & threat protection**, selecione **Manage
    settings** em **Virus & threat protection settings**.

![A screenshot of a computer Description automatically
generated](./media/image9.png)

14. Role para baixo até **Exclusions** e selecione **Add or remove
    exclusions**. Selecione **Yes** na mensagem do Controle de Conta de
    Usuário.

![A screenshot of a computer Description automatically
generated](./media/image61.png)

![A screenshot of a computer Description automatically
generated](./media/image62.png)

15. Na página **Exclusions**, verifique se **C:\DevProjects** e
    **DevBuild.exe** são exibidos.

![A screenshot of a computer Description automatically
generated](./media/image63.png)

16. Feche a página **Windows Security** e depois feche o aplicativo
    **Settings**.

**Resultados** : Após concluir este exercício, você terá criado e
atribuído com sucesso um perfil de configuração para um dispositivo
Windows 11.

**Exercício 2: Modificar uma política de perfil de configuração
atribuída.**

**Cenário**

Houve uma exceção à política da Contoso que especifica que os membros do
departamento de Desenvolvedores não devem ter as opções de Privacidade
bloqueadas nas Configurações de seus dispositivos. Essa alteração deve
ser implementada e testada.

**Tarefa 1: Alterar definições em um perfil de configuração atribuído**

1.  Altere para **SEA-SVR1**. Volte para a aba do **Microsoft Intune
    admin center** e selecione **Devices** na barra de navegação.

![](./media/image42.png)

2.  Na página **Devices | Overview**, selecione **Windows,** como
    mostrado na imagem abaixo.

![](./media/image43.png)

3.  Na página **Windows | Windows devices**, navegue e clique em
    **Configuration profiles**.

![](./media/image44.png)

4.  No painel **Devices | Configuration profiles**, no painel de
    detalhes, selecione **Contoso Developer - standard**.

![](./media/image64.png)

5.  No painel **Contoso Developer - standard**, role para baixo até a
    seção **Configuration settings** e selecione **Edit**.

![A screenshot of a computer Description automatically
generated](./media/image65.png)

6.  Na página **Device restrictions**, expanda **Control Panel and
    Settings**.

![A screenshot of a computer Description automatically
generated](./media/image66.png)

7.  Ao lado de **Privacy**, certifique-se de que a opção **Not
    configured** esteja selecionada.

![A screenshot of a computer Description automatically
generated](./media/image67.png)

8.  Selecione **Review + save** e depois **Save**.

![](./media/image68.png)

**Tarefa 2: Forçar a sincronização do dispositivo no centro de
administração do Microsoft Intune**

1.  No
    [*SEA-SVR1*](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10),
    em **Microsoft Intune admin center**, selecione **Devices** no
    painel de navegação e, em seguida, selecione **All devices** e
    selecione **SEA-WS1**.

![A screenshot of a computer Description automatically
generated](./media/image69.png)

2.  No painel **SEA-WS1** , selecione **Sync** e, quando solicitado,
    selecione **Yes**.

![](./media/image70.png)

**Observação**: O Intune conectará o dispositivo e sincronizará todas as
políticas. Isso pode levar até 5 minutos.

**Tarefa 3: Verificar alterações no
[*SEA-WS1*](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)**

1.  Altere para
    [*SEA-WS1*](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10).
    Na barra de tarefas, selecione **Start** e, em seguida,
    **Settings**.

![A screenshot of a computer Description automatically
generated](./media/image2.png)

2.  No aplicativo **Settings**, selecione **Privacy & security** e
    verifique se todas as opções de personalização estão de volta.

![A screenshot of a computer Description automatically
generated](./media/image71.png)

3.  Feche todas as janelas abertas e saia do **SEA-WS1**.

**Resultados**: Você terá modificado com sucesso um perfil de
configuração atribuído e verificado as alterações.
