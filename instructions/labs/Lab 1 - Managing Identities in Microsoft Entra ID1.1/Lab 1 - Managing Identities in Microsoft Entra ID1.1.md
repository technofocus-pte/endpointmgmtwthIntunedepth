Laboratório 01 - Gerenciando Identidades no Microsoft Entra ID

**Resumo**

Neste laboratório, você usará o Microsoft Entra admin center para criar
e modificar usuários, atribuir funções administrativas, criar e
modificar grupos e gerenciar atribuições de licenças no Microsoft Entra
ID.

Exercício 1: Criando usuários no Microsoft Entra ID

**Cenário**

Você precisa criar contas de usuário no **Microsoft Entra ID** para
alguns novos funcionários que começarão na próxima semana. Os novos
usuários estão listados na tabela a seguir:

[TABLE]

**Observação:** Para localização, use sua região local ou os United
States.

Você também foi informado de que vários outros funcionários serão
contratados nos próximos meses. Você decidiu que usar scripts seria um
método muito mais eficiente para adicionar um grande número de novos
usuários. Você decidiu criar um script em PowerShell e testá-lo ao criar
a conta de Cody Godinez.

Tarefa 1: Criar usuários usando o centro de administração do Microsoft
Entra

1.  Em [***SEA-SVR1***](urn:gd:lg:a:select-vm), faça login como
    [**Contoso\Administrator**](urn:gd:lg:a:send-vm-keys) com a senha
    !\![**Pa55w.rd**](urn:gd:lg:a:send-vm-keys)!!.

> ![Screenshot](./media/image1.png)

2.  Abra o **Microsoft Edge browser** e navegue até

> !\![**https://entra.microsoft.com/#view/Microsoft_AAD_UsersAndTenants/UserManagementMenuBlade/~/AllUsers/menuId/**](https://entra.microsoft.com/#view/Microsoft_AAD_UsersAndTenants/UserManagementMenuBlade/~/AllUsers/menuId/)!!

3.  No prompt de entrada, insira as **Office 365 Tenant credentials** na
    aba Home da interface do Lab.

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)

**Observação** – Se for promovido para o MFA, conclua o processo de
login do MFA.

4.  No **Microsoft Entra admin center**, expanda **Identity** e, no
    painel de navegação, selecione **Users**.

> ![A screenshot of a computer Description automatically
> generated](./media/image3.png)
>
> Anote os usuários que já existem como membros do domínio do ID
> Microsoft Entra. Cada usuário está habilitado conforme indicado na
> coluna **Account enabled**. A coluna **On-premises
> synced** **enabled** indica **No** para todos os usuários atuais. Isso
> indica que cada usuário foi criado diretamente no **Microsoft Entra
> ID** e não sincronizado a partir de um serviço de diretório local.
>
> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

5.  Na página **Users | All users**, selecione **New user** e, em
    seguida, **Create new user**.

> ![](./media/image5.png)

6.  Na página **New User**, certifique-se de que **Create user** esteja
    selecionado e insira o seguinte:

    - User principal name: !\![**ereeve**](urn:gd:lg:a:send-vm-keys)!!

    - Display Name: !\![**Edmund Reeve**](urn:gd:lg:a:send-vm-keys)!!

    - Uncheck **Auto-generate password.**

    - Password **–** !!**P@55w.rd1234**!!

> ![A screenshot of a computer Description automatically
> generated](./media/image6.png)

7.  Na aba **Properties**, forneça as informações abaixo e clique em
    **Next Assignments.**

    - **Job title**, enter !\![**HR Rep**](urn:gd:lg:a:send-vm-keys)!!

    - **Department**, enter  !!**H[R](urn:gd:lg:a:send-vm-keys)**!!

    - **Usage location - United States**

> ![](./media/image7.png)

8.  Na aba Assignments, clique no botão **Review + create**.

> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)

9.  Verifique os detalhes e clique no botão **Create**.

> ![](./media/image9.png)
>
> ![A close-up of a computer screen Description automatically
> generated](./media/image10.png)

10. Da mesma forma, crie a conta de usuário para Miranda Snider com os
    detalhes abaixo.

    - User principal name:  !\![**msnider**](urn:gd:lg:a:send-vm-keys)!!

    - Display Name: !! [**Miranda Snider**](urn:gd:lg:a:send-vm-keys)!!

    - Uncheck **Auto-generate password.**

    - Password **–** !!**P@55w.rd1234**!!

    - Job title - !!**Helpdesk Manager**!!

    - Department **-** !!**Operations**!!

    - Usage location **- United States**

11. Selecione a conta de usuário de **Allan Deyoung** e clique em **Edit
    properties** e atualize as informações do trabalho com os detalhes
    abaixo e, em seguida, clique no botão **Save**.

    - Job title- !\![**IT Admin**](urn:gd:lg:a:send-vm-keys)!!

    -  Department - !\![**IT**](urn:gd:lg:a:send-vm-keys)!!

> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)

12. Selecione a conta de usuário de **Joni Sherman** e clique em **Edit
    properties** e atualize as informações do trabalho com os detalhes
    abaixo e, em seguida, clique no botão **Save.**

    - Job title- !!**ParaLegal**!!

    -  Department - !!**Legal**!!

> ![A screenshot of a computer Description automatically
> generated](./media/image12.png)

13. Selecione a conta de usuário de **Alex Wilber** e clique em **Edit
    properties** e atualize as informações do trabalho com os detalhes
    abaixo e, em seguida, clique no botão **Save.**

    - Job title - !!**Marketing Assistant**!!

    -  Department – !\![**Marketing**](urn:gd:lg:a:send-vm-keys)!!

> ![](./media/image13.png)

Tarefa 2: Criar usuários usando o PowerShell

1.  Em [***SEA-SVR1***](urn:gd:lg:a:select-vm), na barra de tarefas,
    clique com o botão direito do mouse em **Start** e selecione
    **Windows PowerShell (Admin)**.

> ![](./media/image14.png)

2.  Na janela do **Windows PowerShell**, digite o seguinte comando e
    pressione **Enter**. Se solicitado, digite
    !\![**Y**](urn:gd:lg:a:send-vm-keys)!! nas mensagens do NuGet e do
    repositório:

> !!**Install-Module MSOnline**!!
>
> ![](./media/image15.png)

3.  Na janela do **Windows PowerShell**, digite o seguinte comando e
    pressione **Enter**:

> !!**Connect-MsolService**!!
>
> ![A screenshot of a computer Description automatically
> generated](./media/image16.png)

4.  Na caixa de diálogo **Sign in to your account**, entre usando as
    credenciais do Locatário do Office 365 na aba Home.

> **Observação – Se você foi solicitado a alterar a senha das
> credenciais de administrador do locatário, certifique-se de fornecer a
> senha atualizada.**

5.  Na janela do **Windows PowerShell**, digite o seguinte código para
    criar um novo usuário e pressione **Enter**.

> Observação – Cole o comando abaixo no bloco de notas e substitua os
> detalhes do locatário, depois copie e cole o comando no Windows
> PowerShell, se necessário, para garantir que as informações do
> locatário estejam corretas
>
> !!**New-MsolUser -UserPrincipalName
> cgodinez@M365xXXXXXXXX.onmicrosoft.com -DisplayName "Cody Godinez"
> -FirstName "Cody" -LastName "Godinez" -Password ‘P@55w.rd1234’
> -ForceChangePassword $false -UsageLocation "US" -Title "Sales Rep"
> -Department "Sales"**!!
>
> ![A screenshot of a computer screen Description automatically
> generated](./media/image17.png)

6.  Na janela do **Windows PowerShell**, digite o seguinte comando para
    redefinir as senhas de Alew Wilber, Allan Deyoung e Joni Sherman

> !!**Get-MsolUser | Where-Object DisplayName -EQ "Alex Wilber" |
> Set-MsolUserPassword -NewPassword P@55w.rd1234 -ForceChangePassword
> $false**!!
>
> !!**Get-MsolUser | Where-Object DisplayName -EQ “Allan Deyoung” |
> Set-MsolUserPassword -NewPassword P@55w.rd1234 -ForceChangePassword
> $false**!!
>
> !!**Get-MsolUser | Where-Object DisplayName -EQ "Joni Sherman" |
> Set-MsolUserPassword -NewPassword P@55w.rd1234 -ForceChangePassword
> $false**!!
>
> ![A computer screen shot of a program Description automatically
> generated](./media/image18.png)

7.  Na janela do **Windows PowerShell,** digite o seguinte comando e
    pressione **Enter:**

> !!**Get-MsolUser**!!

8.  Verifique se a lista de usuários do seu locatário é exibida.
    Verifique quais usuários têm uma licença atribuída. Qualquer usuário
    com o valor **isLicensed** igual a **False** não recebeu uma
    licença.

> ![A screenshot of a computer Description automatically
> generated](./media/image19.png)

**Resultados:** Após concluir este exercício, você terá criado com
sucesso novas contas de usuário no Microsoft Entra ID.

Exercício 2: Atribuição de funções administrativas no Microsoft Entra ID

**Cenário**

Você precisa revisar e modificar as funções administrativas atuais do
seu locatário.

Você recebeu uma lista de usuários que devem ter funções administrativas
atribuídas, conforme indicado na tabela a seguir.

[TABLE]

Tarefa 1: Revisar e atribuir funções administrativas

1.  Em [***SEA-SVR1***](urn:gd:lg:a:select-vm), mude para o **Microsoft
    Edge.**

2.  No **Microsoft Entra admin center**, no painel de navegação, expanda
    **Roles & admins.**

3.  Selecione **Roles & admin** e pesquise por !!**Global
    administrator**!! e clique na função **Global Administrator**.

> ![A screenshot of a computer Description automatically
> generated](./media/image20.png)

4.  Clique em **Add assignments**.

> ![A screenshot of a computer Description automatically
> generated](./media/image21.png)

5.  Na página Add assignments, selecione **Allan Deyoung** e depois
    selecione **Add**.

> ![A screenshot of a computer Description automatically
> generated](./media/image22.png)

6.  Na parte superior da página, no link de navegação, selecione **Roles
    and administrators**.

> ![A screenshot of a computer Description automatically
> generated](./media/image23.png)

7.  Na página **Roles and administrators**, pesquise e selecione
    !!**User administrator**!!. Certifique-se de que **Assignments**
    esteja selecionada.

> ![A screenshot of a chat Description automatically
> generated](./media/image24.png)
>
> Observe que não há usuários atualmente atribuídos à função
> Administrador de usuários.

8.  Clique em + **Add assignments**.

> ![A screenshot of a computer Description automatically
> generated](./media/image25.png)

9.  Na página Adicionar atribuições, selecione **Edmund Reeve** e depois
    selecione **Add**.

> ![A screenshot of a computer Description automatically
> generated](./media/image26.png)

10. Clique no link **Roles and administrators**, pesquise e selecione
    !!**Helpdesk administrator**!!.

> ![A screenshot of a computer Description automatically
> generated](./media/image27.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image28.png)
>
> Observe que não há usuários atualmente atribuídos à função de
> administrador do Helpdesk.

11. Na página **Helpdesk administrator | Assignments**, selecione **Add
    assignments**.

> ![A screenshot of a computer Description automatically
> generated](./media/image29.png)

12. Na página Adicionar atribuições, selecione **Miranda Snider** e
    depois selecione **Add**.

> ![A screenshot of a computer Description automatically
> generated](./media/image30.png)

13. Na parte superior da página, no link de navegação, selecione **Roles
    and administrators**.

> ![A screenshot of a computer Description automatically
> generated](./media/image31.png)

**Resultados:** Após concluir este exercício, você deverá ter atribuído
com sucesso funções administrativas aos usuários.

Exercício 3: Criação e gerenciamento de grupos e validação de atribuição
de licenças.

**Cenário**

Você precisa adicionar os três novos usuários a um grupo de segurança e
atribuir licenças conforme indicado na tabela a seguir.

[TABLE]

Você também foi solicitado a modificar a marca da empresa para a página
de login.

Tarefa 1: Criar grupos usando o Microsoft Entra admin center

1.  Em [***SEA-SVR1***](urn:gd:lg:a:select-vm), no **Microsoft Entra
    admin center**, no painel de navegação, expanda **Identity**,
    selecione **Groups** e clique em **New group.**

> ![A screenshot of a computer Description automatically
> generated](./media/image32.png)

2.  Na página **New group**, insira o seguinte:

    - Group type: **Security**

    - Group name: !\![**Contoso_Managers**](urn:gd:lg:a:send-vm-keys)!!

    - Membership type: **Assigned**

3.  Em Membros, clique em **No members selected**.

4.  Na página Adicionar membros, adicione **Edmund Reeve**, **Miranda
    Snider** e clique em **Select**.

> ![A screenshot of a computer Description automatically
> generated](./media/image33.png)

5.  Selecione **Create**.

Tarefa 2: Criar grupos usando o PowerShell

1.  Em [***SEA-SVR1***](urn:gd:lg:a:select-vm), alterne para o Windows
    PowerShell.

2.  Na janela do **Windows PowerShell**, digite o seguinte código para
    criar um novo grupo e pressione **Enter:**

> !!**New-MsolGroup -DisplayName "Contoso_Sales" -Description "Contoso
> Sales team users"**!!
>
> ![A screenshot of a computer Description automatically
> generated](./media/image34.png)

3.  Na janela do **Windows PowerShell**, digite o seguinte comando e
    pressione **Enter:**

> !!**Get-MsolGroup**!!
>
> ![A screenshot of a computer screen Description automatically
> generated](./media/image35.png)

4.  Verifique se você obtém a lista de grupos em seu locatário,
    incluindo o grupo **Contoso_Sales** que você acabou de criar.

> ![](./media/image36.png)

5.  Na janela do **Windows PowerShell**, digite o seguinte código para
    definir uma variável como o grupo Contoso_Sales e pressione
    **Enter:**

> !!**$group = Get-MsolGroup | Where-Object {$\_.DisplayName -eq
> "Contoso_Sales"}**!!

6.  Na janela do **Windows PowerShell,** digite o seguinte código para
    definir outra variável como o usuário e pressione **Enter:**

> !!**$user = Get-MsolUser | Where-Object {$\_.DisplayName -eq "Cody
> Godinez"}**!!

7.  Na janela **do Windows PowerShell,** digite o seguinte código para
    adicionar Cody ao Contoso_Sales usando variáveis definidas e
    pressione **Enter:**

> !!**Add-MsolGroupMember -GroupObjectId $group.ObjectId
> -GroupMemberType "User" -GroupMemberObjectId $user.ObjectId**!!

8.  Na janela do **Windows PowerShell**, digite o seguinte código e
    pressione **Enter:**

> !! **Get-MsolGroupMember -GroupObjectId $group.ObjectId**!!

9.  Verifique se você vê **Cody Godinez** no resultado da saída do
    comando.

> ![A screenshot of a computer program Description automatically
> generated](./media/image37.png)

10. Feche o Windows PowerShell.

Tarefa 3: Revisar licenças e modificar a marca da empresa

1.  No Microsoft Entra admin center, no painel Navegação, expanda
    **Identity**, depois expanda **Billing** e selecione **Licenses**.

> https://admin.microsoft.com/Adminportal/Home?referrer=entra#/licenses
>
> ![](./media/image38.png)

2.  Na página **Licenses**, em Subscriptions, verifique todas as
    licenças disponíveis.

> ![](./media/image39.png)
>
> Observação - Observe as licenças atuais disponíveis e atribuídas para
> **Enterprise Mobility + Security E5** e **Office 365 E5 (no Teams)**
>
> ![](./media/image40.png)

3.  No Microsoft 365 admin center, no painel de navegação esquerdo,
    selecione **Usuários** e depois **Usuários ativos.**

> ![](./media/image41.png)

4.  Na lista de usuários, selecione **Cody Godinez.**

> ![A screenshot of a computer Description automatically
> generated](./media/image42.png)

5.  Na página Cody Godinez, selecione **Licenses and apps**

> ![A screenshot of a computer Description automatically
> generated](./media/image43.png)
>
> Observe que Cody ainda não possui nenhuma licença atribuída.

6.  Na página **Licenses and apps**, marque a caixa de seleção ao lado
    de **Enterprise Mobility + Security E5** e **Office 365 E5 (no
    Teams)** e clique em **Save changes**.

> ![A screenshot of a login page Description automatically
> generated](./media/image44.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image45.png)

**Observação:** Repita as etapas 4 a 8 para atribuir licenças Enterprise
Mobility + Security E5 e Office 365 E5 (no Teams) a Joni Sherman, Alex
Wilber e Allan Deyoung, caso eles não tenham recebido as licenças.

7.  No Microsoft Entra admin center, no painel Navegação, expanda
    **Identity** e selecione **Groups**.

> ![](./media/image46.png)

8.  Na página **Groups | All groups**, selecione **Contoso_Managers**.

> ![A screenshot of a computer Description automatically
> generated](./media/image47.png)

9.  Na página **Contoso_Managers**, selecione **Licenses**.

> ![](./media/image48.png)
>
> **Observe que o grupo Contoso_Managers não tem nenhuma atribuição de
> licença atual.**

10. Navegue até o Microsoft 365 admin center e role para baixo até
    licenças, selecione **Enterprise Mobility + Security E5.**

> ![A screenshot of a computer Description automatically
> generated](./media/image49.png)

11. Clique na aba **Groups** e clique em **Assign licenses.**

> ![](./media/image50.png)

12. Selecione Contoso_Mangers na lista e clique em **Assign.**

13. No Microsoft Entra admin center, no painel Navegação, expanda
    **Identity**, depois expanda **Billing** e selecione **Licenses**.

> ![A screenshot of a computer Description automatically
> generated](./media/image51.png)![A screenshot of a computer
> Description automatically generated](./media/image52.png)
>
> ![A screenshot of a computer Description automatically
> generated](./media/image53.png)

14. Na página **Licenses|Overview**, em **Manage**, selecione **All
    products**.

> ![A screenshot of a computer Description automatically
> generated](./media/image54.png)
>
> ![](./media/image53.png)

15. Repita o mesmo processo e atribua a licença do Office 365 E5 (no
    Teams) à equipe Contoso_Managers.

> Observe os usuários que estão atribuídos à licença Office 365 E5 (no
> Teams). Observe a coluna Assignment Paths, que indica como a
> atribuição de licença é configurada para cada usuário. Edmund e
> Miranda recebem a atribuição de licença por serem membros do grupo
> Contoso_Managers. Pode ser necessário selecionar **Refresh** algumas
> vezes para atualizar a coluna Assignment path.
>
> ![](./media/image55.png)

16. Feche o Microsoft Edge.

**Resultados:** Após concluir este exercício, você deverá ter criado e
gerenciado grupos e atribuído licenças com sucesso.
