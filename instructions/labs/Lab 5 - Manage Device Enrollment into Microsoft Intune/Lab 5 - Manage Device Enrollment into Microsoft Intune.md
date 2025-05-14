**Laboratório 5 - Gerenciar registro de dispositivos no Microsoft
Intune**

**Resumo**

Neste laboratório, você se preparará para o gerenciamento de
dispositivos usando o Microsoft Intune, revisando e atribuindo licenças,
configurando o registro automático do Windows e configurando restrições
de registro.

**Pré-requisitos**

Os seguintes laboratórios devem ser concluídos antes deste laboratório:

- Laboratório 01 - Gerenciando Identidades no Microsoft Entra ID

- Laboratório 02 - Sincronizando Identidades usando o Microsoft Entra
  Connect

**Observação** : você também precisará de um telefone celular que possa
receber mensagens de texto usadas para proteger a autenticação de login
do Windows Hello no Entra ID.

**Cenário**

Você precisa se preparar para o gerenciamento de dispositivos usando o
Microsoft Intune. Primeiro, você precisa garantir que os usuários tenham
as licenças apropriadas para o gerenciamento de dispositivos. Como um
teste de verificação, você atribuirá as licenças necessárias a Aaron
Nicholls. Você também precisa garantir que qualquer dispositivo Windows
que esteja associado ou registrado no Microsoft Entra ID seja
automaticamente inscrito no Intune. Você também foi solicitado a
garantir que os membros do grupo de vendas estejam impedidos de
registrar dispositivos Android e iOS pessoais no Intune e que o Limite
de Dispositivos de Registro seja aumentado para 10 dispositivos. Por
fim, você precisa configurar Allan Deyoung como um gerente de registro
de dispositivos para permitir que ele registre 1.000 dispositivos.

**Tarefa 1: Revisar e atribuir licenças para gerenciamento de
dispositivos**

1.  Em
    [*SEA-SVR1*](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)
    , navegue até a janela **Microsoft 365 admin center**.

![](./media/image1.png)

2.  Navegue e selecione **Billing** e clique em **Licenses**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image2.png)

3.  Na página **Licenses**, anote as licenças que estão disponíveis no
    locatário.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image3.png)

4.  Selecione e clique em **Enterprise Mobility + Security E5**. Observe
    todos os usuários aos quais esta licença foi atribuída. Você pode
    atribuir e remover licenças deste local.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image4.png)

![](./media/image5.png)

5.  Selecione um usuário para ver as licenças atribuídas a ele. Observe
    os serviços incluídos na licença Enterprise Mobility + Security E5.
    O Microsoft Intune é um dos serviços suportados por esta licença.

![](./media/image6.png)

6.  No painel de navegação do **Microsoft 365 admin center**, selecione
    **Active users**.

![](./media/image7.png)

7.  Pesquise e selecione !!**Cindy White**!!

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image8.png)

8.  Na página **Cindy White user**, clique em **Licenses and apps**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image9.png)

9.  Em **Settings**, no campo **Usage location**, selecione **United
    States** e clique na caixa de seleção **Enterprise Mobility +
    Security E5 and Office 365 E5 (no teams)** e clique em **Save
    changes**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image10.png)

***Observação** : antes de atribuir uma licença a um usuário, o usuário
deve ter um local de uso definido.*

![](./media/image11.png)

**Tarefa 2: Definindo a senha do usuário utilizando o PowerShell**

1.  No [***SEA-SVR1***](urn:gd:lg:a:select-vm), clique com o botão
    direito do mouse no **botão Start** e selecione **Windows PowerShell
    (Admin)**.

![](./media/image12.png)

2.  Na caixa de diálogo **User Account Control**, selecione **Yes**.

![](./media/image13.png)

3.  Na janela do **Windows PowerShell,** digite o seguinte comando e
    pressione **Enter** :

!!**Connect-MsolService**!!

![A computer screen with white text Description automatically
generated](./media/image14.png)

4.  Na caixa de diálogo **Sign in to your account**, entre usando as
    credenciais do Locatário do Office 365 na aba Home.

**Observação – se você foi solicitado a alterar a senha das credenciais
de administrador do locatário, certifique-se de fornecer a senha
atualizada.**

![A screenshot of a computer Description automatically
generated](./media/image15.png)

![A screenshot of a computer screen Description automatically
generated](./media/image16.png)

5.  Na janela **Windows PowerShell**, digite o seguinte comando para
    redefinir as senhas da **Cindy White**

!!**Get-MsolUser | Where-Object DisplayName -EQ "Cindy White" |
Set-MsolUserPassword -NewPassword P@55w.rd1234 -ForceChangePassword
$false**!!

![A computer screen shot of a program Description automatically
generated](./media/image17.png)

**Tarefa 3: Habilitar o registro automático do Windows no Microsoft
Intune**

1.  Em **SEA-SVR1**, abra uma nova aba no **Microsoft Edge** e então na
    barra de endereço digite !!**https://Endpoint.microsoft.com**!! e
    pressione **Enter**. Se for solicitado a entrar, informe a
    credencial do **Office 365 Tenant Admin**.

2.  No Microsoft Intune admin center, selecione **Devices**.

![A screenshot of a computer Description automatically
generated](./media/image18.png)

3.  Navegue e clique em **Enrollment**. Certifique-se de que a aba
    **Windows** esteja selecionada, navegue até a seção **Enrollment
    options** e clique em **Automatic Enrollment**.

![](./media/image19.png)

4.  Na linha **MDM user scope**, selecione o botão de opção **All** e
    depois selecione **Save.**

![](./media/image20.png)

5.  Clique no link **Devices | Enrollment**, como mostrado na imagem
    abaixo.

![](./media/image21.png)

**Observação**: Ao executar esta etapa, você habilitou o registro
automático no Intune para qualquer usuário que realizar uma associação
ao Azure AD com um dispositivo Windows.

**Tarefa 4: Configurar Restrições de Inscrição**

1.  Acesse a seção **Devices onboarding** e clique em **Enrollment**. Em
    seguida, clique na aba **Android**, conforme mostrado na imagem
    abaixo.

![](./media/image22.png)

2.  Role para baixo até a seção **Enrollment options** e clique em
    **Device platform restriction**.

![](./media/image23.png)

3.  Selecione a aba **Android restrictions** e depois selecione +
    **Create restriction**.

![](./media/image24.png)

![](./media/image25.png)

4.  Na página **Create restriction**, na caixa **Name**, digite
    !!**Android Personal Device Restriction**!! Selecione **Next**.

![](./media/image26.png)

5.  Na página Platform settings, em **Personally owned**, selecione
    **Block** para os seguintes tipos de dispositivos e clique no botão
    **Next**:

    - Android Enterprise (work profile)

    - Android device administrator

![](./media/image27.png)

6.  Na página **Scope tags**, selecione **Next**.

![A screenshot of a computer Description automatically
generated](./media/image28.png)

7.  Na página **Assignments**, em **Included groups**, selecione **Add
    groups**.

![A screenshot of a computer Description automatically
generated](./media/image29.png)

8.  No painel **Select groups to include** na **barra de pesquisa,**
    digite e selecione **Sales** e clique no botão **Select**.

![A screenshot of a computer Description automatically
generated](./media/image30.png)

9.  Na aba **Assignments**, clique no botão **Next**.

![A screenshot of a computer Description automatically
generated](./media/image31.png)

10. Na página **Review + create**, selecione **Create**.

![A screenshot of a computer Description automatically
generated](./media/image32.png)

Observe que a Restrição de Dispositivo Pessoal com Android foi atribuída
com prioridade 1.

![A screenshot of a computer Description automatically
generated](./media/image33.png)

11. Na página **Devices | Enrollment**, na aba **Windows,** navegue até
    a seção **Enrollment options** e clique na **Device limit
    restriction**.

![A screenshot of a computer Description automatically
generated](./media/image34.png)

Observe que há uma restrição de limite de dispositivos padrão atribuída
a Todos os Usuários. Essa restrição padrão define um limite de registro
de dispositivos para 5 dispositivos por usuário.

12. Nas **Enrollment device limit restrictions**, selecione + **Create
    restriction**.

![A screenshot of a computer Description automatically
generated](./media/image35.png)

13. Na página Create restriction, na caixa **Name**, insira !!**Sales
    Device Enrollment Limit**!! Selecione **Next**.

![A screenshot of a computer Description automatically
generated](./media/image36.png)

14. Na página **Device limit**, selecione **10** e depois **Next**.

![A screenshot of a computer Description automatically
generated](./media/image37.png)

15. Na página **Scope tags**, selecione **Next**.

![A screenshot of a computer Description automatically
generated](./media/image38.png)

16. Na página **Assignments**, em **Included groups**, selecione **Add
    groups**.

![A screenshot of a computer Description automatically
generated](./media/image39.png)

17. Na caixa de pesquisa da página **Select groups to include**, digite
    e selecione **Sales** e depois clique no botão **Select**.

![](./media/image40.png)

18. Clique no botão **Next**.

![A screenshot of a computer Description automatically
generated](./media/image41.png)

19. Na página **Review + create**, selecione **Create**.

![A screenshot of a computer Description automatically
generated](./media/image42.png)

20. Recarregue a página. Observe o Limite de Inscrição de Dispositivos
    de Vendas, configurado com um limite de 10 dispositivos e atribuído
    com prioridade 1.

![A screenshot of a computer Description automatically
generated](./media/image43.png)

**Tarefa 5: Configurar um gerenciador de registro de dispositivos**

1.  No **Microsoft Intune admin center,** selecione **Devices**.

![](./media/image44.png)

2.  Navegue até a seção **Device onboarding** e clique em
    **Enrollment**, depois clique na aba **Device enrolment managers**.

![](./media/image45.png)

3.  No painel **Enroll devices**, selecione **Device enrollment
    managers.**

Observe que, por padrão, não há gerenciadores de registro de
dispositivos configurados.

4.  Na **Enroll devices|Device enrollment managers**, selecione **Add**.

![A screenshot of a computer Description automatically
generated](./media/image46.png)

5.  Na página **Add user**, em Nome de usuário, insira o endereço de
    e-mail de Allan **Add user** (substitua **XXXXXX** pelo nome do seu
    locatário ) e selecione **Add**.

![A screenshot of a computer Description automatically
generated](./media/image47.png)

**Agora Allan tem permissão para registrar até 1.000 dispositivos.**

6.  No Microsoft Intune admin center, no painel de navegação, selecione
    **Home**.

![A screenshot of a computer Description automatically
generated](./media/image48.png)

7.  Feche o Microsoft Edge.

**Resultados**: Após concluir este exercício, você terá revisado e
atribuído licenças com sucesso, configurado o registro automático do
Windows, habilitado e atribuído restrições de registro e configurado um
gerenciador de registro de dispositivos.
