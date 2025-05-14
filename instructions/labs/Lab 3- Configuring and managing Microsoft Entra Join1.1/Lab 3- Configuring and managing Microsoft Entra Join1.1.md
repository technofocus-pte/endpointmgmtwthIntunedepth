Laboratório 03: Configurando e gerenciando o Microsoft Entra ID Join

**Resumo**

Neste laboratório, você definirá as configurações do Microsoft Entra ID
Join e executará cenários de associação padrão e híbrida do Microsoft
Entra para dispositivos Windows.

**Pré-requisitos**

Os seguintes laboratórios devem ser concluídos antes deste laboratório:

- Laboratório 02 - Sincronizando Identidades usando o Microsoft Entra
  Connect

**Observação:** você também precisará de um telefone celular que possa
receber mensagens de texto usadas para proteger a autenticação de login
do Windows Hello no Entra ID.

**Exercício 1: Configurando o Microsoft Entra Join**

**Cenário**

Você precisa configurar as definições do dispositivo Entra ID para
garantir que todos os usuários tenham permissão para conectar
dispositivos ao Entra ID. Você também precisa garantir que os usuários
possam conectar no máximo 20 dispositivos e que Allan Deyoung seja
adicionado como administrador local em todos os dispositivos conectados
ao Microsoft Entra ID. Por fim, você verificará se o Microsoft Entra
Join funciona conforme o esperado, solicitando que Joni Sherman conecte
o SEA-WS1 ao locatário.

## Tarefa 0: habilitar o TLS 1.2 usando o script do PowerShell.

1.  No SEA-WS1, faça login como Contoso\Administrator com a senha
    Pa55w.rd

2.  No menu Iniciar, digite **[PowerShell](urn:gd:lg:a:send-vm-keys),**
    clique com o botão direito do mouse em PowerShell e selecione run as
    administrator.

![](./media/image1.png)

3.  Execute o seguinte script no PowerShell.

**If** (-Not (Test-Path
'HKLM:\SOFTWARE\WOW6432Node\Microsoft\\NETFramework\v4.0.30319'))

{

New-Item 'HKLM:\SOFTWARE\WOW6432Node\Microsoft\\NETFramework\v4.0.30319'
-Force | Out-Null

}

New-ItemProperty -Path
'HKLM:\SOFTWARE\WOW6432Node\Microsoft\\NETFramework\v4.0.30319' -Name
'SystemDefaultTlsVersions' -Value '1' -PropertyType 'DWord' -Force |
Out-Null

New-ItemProperty -Path
'HKLM:\SOFTWARE\WOW6432Node\Microsoft\\NETFramework\v4.0.30319' -Name
'SchUseStrongCrypto' -Value '1' -PropertyType 'DWord' -Force | Out-Null

**If** (-Not (Test-Path
'HKLM:\SOFTWARE\Microsoft\\NETFramework\v4.0.30319'))

{

New-Item 'HKLM:\SOFTWARE\Microsoft\\NETFramework\v4.0.30319' -Force |
Out-Null

}

New-ItemProperty -Path
'HKLM:\SOFTWARE\Microsoft\\NETFramework\v4.0.30319' -Name
'SystemDefaultTlsVersions' -Value '1' -PropertyType 'DWord' -Force |
Out-Null

New-ItemProperty -Path
'HKLM:\SOFTWARE\Microsoft\\NETFramework\v4.0.30319' -Name
'SchUseStrongCrypto' -Value '1' -PropertyType 'DWord' -Force | Out-Null

**If** (-Not (Test-Path
'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS
1.2\Server'))

{

New-Item
'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS
1.2\Server' -Force | Out-Null

}

New-ItemProperty -Path
'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS
1.2\Server' -Name 'Enabled' -Value '1' -PropertyType 'DWord' -Force |
Out-Null

New-ItemProperty -Path
'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS
1.2\Server' -Name 'DisabledByDefault' -Value '0' -PropertyType 'DWord'
-Force | Out-Null

**If** (-Not (Test-Path
'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS
1.2\Client'))

{

New-Item
'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS
1.2\Client' -Force | Out-Null

}

New-ItemProperty -Path
'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS
1.2\Client' -Name 'Enabled' -Value '1' -PropertyType 'DWord' -Force |
Out-Null

New-ItemProperty -Path
'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS
1.2\Client' -Name 'DisabledByDefault' -Value '0' -PropertyType 'DWord'
-Force | Out-Null

Write-Host 'TLS 1.2 has been enabled. You must restart the Windows
Server for the changes to take affect.' -ForegroundColor Cyan

![](./media/image2.png)

4.  Reinicie a VM do Windows Server.

![](./media/image3.png)

## Tarefa 1: Configurar as definições do dispositivo do Microsoft Entra ID Join

1.  Altere para **SEA-SVR1**. Na barra de endereços do navegador
    **Microsoft Edge**, digite a seguinte URL:
    !\![**https://entra.microsoft.com**](https://entra.microsoft.com)!!
    e pressione o botão **Enter** .

2.  Faça login com o ID do seu locatário do O365
    !!**admin@M365xXXXXXXXX.onmicrosoft.com**!! e use a senha de
    administrador do locatário.

![A screenshot of a computer Description automatically
generated](./media/image4.png)

![A screenshot of a login box Description automatically
generated](./media/image5.png)

3.  Na caixa de diálogo **Stay signed in?,** selecione o botão **Yes.**

![A screenshot of a computer Description automatically
generated](./media/image6.png)

4.  Na janela do **Microsoft Entra admin center**, navegue e clique em
    **Identity**.

![A screenshot of a computer Description automatically
generated](./media/image7.png)

5.  Na seção **Identity**, selecione **Devices**, navegue e clique em
    **All devices**, conforme mostrado na imagem abaixo.

![A screenshot of a computer Description automatically
generated](./media/image8.png)

Observe que nenhum dispositivo foi encontrado, pois você ainda não
associou nenhum dispositivo.

![](./media/image9.png)

6.  Na página **Devices** | All devices, selecione **Device settings**.

![A screenshot of a computer Description automatically
generated](./media/image10.png)

7.  Na página **Devices | Device settings**, no painel de detalhes, em
    **Users may join devices to Entra**, verifique se **all** está
    selecionado.

Isso indica que todos os usuários do Entra têm permissão para conectar
dispositivos com Windows 10 ou mais recentes ao Microsoft Entra. Observe
que essa configuração não se aplica a dispositivos híbridos conectados
ao Entra ou a dispositivos conectados usando o modo de autoimplementação
do Windows Autopilot.

8.  Na seção **Require Multi-factor Authentication to register or join
    devices with Entra**, verifique se a configuração está definida como
    **No**.

![A screenshot of a computer Description automatically
generated](./media/image11.png)

9.  Na seção **Maximum number of devices per user**, selecione **20
    (Recommended)** .

10. Clique em **Manage** **Additional local administrators on all
    Microsoft Entra Joined devices**. A **página Device Administrators**
    será aberta.

![A screenshot of a computer Description automatically
generated](./media/image12.png)

11. Na página **Device Administrators | Assignments**, selecione **Add
    assignments**.

![A screenshot of a computer Description automatically
generated](./media/image13.png)

12. Na caixa de pesquisar, digite !!**Allan Deyoung**!!, selecione o
    objeto de usuário **Allan Deyoung** e, em seguida, selecione
    **Add**.

![A screenshot of a computer Description automatically
generated](./media/image14.png)

13. Allan Deyoung agora será adicionado como Device Administrator em
    todos os dispositivos Microsoft Entra Joined.

![A screenshot of a computer screen Description automatically
generated](./media/image15.png)

14. Clique no link **Devices | Device settings** abaixo da barra de
    pesquisa do portal do Azure para voltar à página **Device
    Settings**.

![A screenshot of a computer Description automatically
generated](./media/image16.png)

15. Na página **Device settings**, selecione **Save**.

![A screenshot of a computer Description automatically
generated](./media/image17.png)

**Tarefa 2: Executar Microsoft Entra ID Join**

1.  Altere para
    [SEA-WS1](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)
    e faça login como **Admin** com a senha !!**Pa55w.rd**!!.

![](./media/image18.png)

2.  Na barra de tarefas, selecione o ícone **Windows Start button** e
    depois selecione **Settings**.

![](./media/image19.png)

3.  Na janela **Settings**, selecione **Accounts**.

![A screenshot of a computer Description automatically
generated](./media/image20.png)

4.  Na página **Accounts**, selecione **Access work or school**.

![A screenshot of a computer Description automatically
generated](./media/image21.png)

5.  Na página **Access work or school**, selecione **Connect**.

![A screenshot of a computer Description automatically
generated](./media/image22.png)

6.  Na janela **Microsoft account**, selecione **Join this device to
    Microsoft Entra ID**.

![A screenshot of a computer screen Description automatically
generated](./media/image23.png)

7.  Na página **Sign in**, digite !!JoniS@M365xXXXXXXX.onmicrosoft.com!!
    e selecione **Next**.

![Graphical user interface, application, Teams Description automatically
generated](./media/image24.png)

8.  Na página **Enter password**, digite a senha do locatário:
    !\![**P@55w.rd1234**](mailto:P@55w.rd1234)!! e então selecione
    **Sign in**.

![Graphical user interface, application Description automatically
generated](./media/image25.png)

9.  Na caixa de diálogo **Make sure this is your organization**,
    selecione **Join**.

![A screenshot of a computer error Description automatically
generated](./media/image26.png)

10. Na página **You're all set!,** selecione **Done**.

![A screenshot of a computer Description automatically
generated](./media/image27.png)

11. Na página **Access work or school**, verifique se **Connected to
    Contoso's Azure AD** é exibido.

![A screenshot of a computer Description automatically
generated](./media/image28.png)

12. Feche a página **Settings**.

**Tarefa 3: Validar o Microsoft Entra Join**

1.  Em
    [SEA-WS1](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10),
    clique com o botão direito do mouse no ícone **Windows** **Start
    button** e selecione **Windows Terminal (Admin),** conforme mostrado
    na imagem abaixo.

![](./media/image29.png)

2.  Na caixa de diálogo **User Account Control**, selecione **Yes**.

![](./media/image30.png)

3.  No console do PowerShell, digite o seguinte comando e pressione a
    tecla **Enter**:

!!**dsregcmd /status**!!

4.  Na saída, em **Device State**, verifique se **AzureAdJoined: YES** é
    exibido.

Isso indica que o dispositivo está associado ao Microsoft Entra.

![](./media/image31.png)

5.  Feche o PowerShell.

6.  Clique com o botão direito novamente no ícone **Windows**
    **Start** **button** e selecione **Computer Management**.

![A screenshot of a computer Description automatically
generated](./media/image32.png)

7.  Na janela **Computer Management**, expanda **Local Users and
    Groups** e selecione **Groups**.

![](./media/image33.png)

![A screenshot of a computer Description automatically
generated](./media/image34.png)

8.  Clique duas vezes no grupo **Administrators**.

![A screenshot of a computer Description automatically
generated](./media/image35.png)

Observe que Joni Sherman foi adicionado como administrador local no
[SEA-WS1](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10).
Observe também duas entidades de segurança representadas por seus
security identifiers (SID). Esses dois SIDs representam a função de
administrador global do Entra e função de administrador de dispositivos
associados ao Microsoft Entra

![](./media/image36.png)

9.  Feche todas as janelas abertas e saia do SEA-WS1 clicando no **ícone
    do botão Windows Start \> Admin \> Sign out**.

![](./media/image37.png)

10. Altere para **SEA-SVR1** e faça login com as credenciais
    **Contoso\Administrator** e senha !!**Pa55w.rd**!!

![A screenshot of a computer Description automatically
generated](./media/image38.png)

11. Em **Microsoft Entra admin center**, navegue e clique em
    **Identity**.

12. Navegue e selecione **Devices** e clique em **All devices**.

13. Na página **Devices | All devices**, observe que **SEA-WS1** está
    listado.

![](./media/image39.png)

14. Verifique se o **Join Type** está listado como **Microsoft Entra
    Joined** e se o proprietário é **Joni Sherman**.

![](./media/image40.png)

15. Observe também que a coluna MDM mostra **None**. Isso indica que
    dispositivo ainda não é gerenciado pelo Microsoft Intune.

![A screenshot of a computer Description automatically
generated](./media/image41.png)

**Tarefa 4: Entre no Windows como usuário Microsoft Entra**

1.  Altere para **SEA-WS1** e clique em **Other user.**

![](./media/image42.png)

2.  **Entre** como !!**JoniS@M365xXXXXXXX.onmicrosoft.com**!!  com a
    senha do locatário: !!**P@55w.rd1234**!!

**Observação: Aguarde a criação do perfil.**

![](./media/image43.png)

**Observação** – Se for solicitado o **Windows Hello,** conclua o
processo de login conforme indicado e, na página **Set up a PIN**, nas
caixas **New PIN** e **Confirm PIN,** digite !!**102938**!!  e então
selecione **OK.**

![](./media/image44.png)

**Tarefa 5: Remover um dispositivo Windows do Entra**

1.  Em
    [SEA-WS1](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10),
    faça login com Joni Sherman, se solicitado, e se a opção para
    inserir o PIN estiver disponível, digite o !!**102938**!! ou digite
    a senha como !!**P@55w.rd1234**!!

![A screenshot of a computer Description automatically
generated](./media/image45.png)

2.  Na janela **Settings**, selecione **Accounts**.

![A screenshot of a computer Description automatically
generated](./media/image46.png)

3.  No painel de navegação esquerdo, navegue e clique em **Accounts**.
    Na página **Accounts**, selecione **Access work or school**.

![A screenshot of a computer Description automatically
generated](./media/image47.png)

4.  Na página **Access work or school**, selecione a seta ao lado de
    **Connected to Contoso's Azure AD,** conforme mostrado na imagem
    abaixo. Clique em **Disconnect** e selecione **Yes**.

![](./media/image48.png)

![A screenshot of a computer Description automatically
generated](./media/image49.png)

![A screenshot of a computer Description automatically
generated](./media/image50.png)

5.  Na página **Disconnect from the organization**, selecione
    **Disconnect**.

![A blue box with white text Description automatically
generated](./media/image51.png)

6.  Na caixa de diálogo **Windows Security**, no campo **Email
    address**, digite !!Admin!! e, no campo **Password**, digite
    !!Pa55w.rd!!. Selecione **OK.**

![Graphical user interface Description automatically
generated](./media/image52.png)

7.  Na caixa de diálogo **Restart your PC**, selecione **Restart now**.
    O **SEA-WS1** será reiniciado.

![A blue box with white text Description automatically
generated](./media/image53.png)

**Resultados:** Após concluir este exercício, você terá configurado as
definições do dispositivo Microsoft Entra, ingressado um dispositivo no
Entra e removido um dispositivo do Entra.

**Exercício 2: Configurando a junção híbrida do Microsoft Entra**

**Cenário**

Alguns dispositivos Windows da Contoso estão atualmente associados aos
Active Directory Domain Services local. Para permitir que esses
dispositivos acessem perfeitamente os serviços em nuvem, você planeja
habilitar a associação híbrida do Microsoft Entra. Você testará a
associação híbrida do Microsoft Entra reconfigurando o Azure AD Connect
e testando o processo no SEA-CL2.

**Tarefa 1: Preparar o ambiente**

1.  Altere para
    [SEA-SVR1](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)
    .

![A picture containing text Description automatically
generated](./media/image54.png)

2.  Selecione **Windows** ícone **Start**, expanda **Windows
    Administrative Tools** e selecione **Active Directory Users and
    Computers**.

![](./media/image55.png)

3.  Em **Active Directory Users and Computers**, clique com o botão
    direito do mouse em **Contoso.com**, aponte para **New** e selecione
    **Organizational Unit**.

![](./media/image56.png)

4.  Na caixa de diálogo **New-Object - Organizational Unit**, digite
    !!**Entra clients**!! e então selecione **OK**.

![A screenshot of a computer Description automatically
generated](./media/image57.png)

5.  No painel de navegação, selecione **Seattle Clients**. Clique com o
    botão direito do mouse em **SEA-CL2** e selecione **Move**.

![](./media/image58.png)

6.  Na caixa de diálogo **Move**, selecione **Entra clients** e depois
    selecione **OK.**

![A screenshot of a computer Description automatically
generated](./media/image59.png)

7.  Feche **Active Directory Users and Computers**.

![A screenshot of a computer Description automatically
generated](./media/image60.png)

**Tarefa 2: Reconfigurar o Entra Connect**

1.  No
    [SEA-SVR1](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10),
    clique duas vezes em Azure AD Connect em desktop

![A black rectangle with blue lines Description automatically
generated](./media/image61.png)

2.  Na janela **Microsoft Azure Active Directory Connect,** selecione
    **Configure**.

![](./media/image62.png)

3.  Na página **Additional tasks**, selecione **Customize
    synchronization options** e selecione **Next**.

![A screenshot of a computer Description automatically
generated](./media/image63.png)

4.  Na página **Connect to Entra**, nas caixas **USERNAME** e
    **PASSWORD**, insira suas **Office 365 Tenant credentials** e
    selecione **Next.**

![A screenshot of a computer Description automatically
generated](./media/image64.png)

5.  Na página **Connect your directories**, clique no botão Next.

![A screenshot of a computer Description automatically
generated](./media/image65.png)

6.  Na página **Domain and OU filtering**, certifique-se de que **Sync
    selected domains and Ous** esteja selecionado.

7.  Expanda **Contoso.com,** selecione **Entra clients** e clique em
    **Next.**

![A screenshot of a computer Description automatically
generated](./media/image66.png)

8.  Na página **Optional features**, certifique-se de que **Password
    hash synchronization** esteja selecionado e selecione **Next**.

9.  Na página **Ready to configure**, certifique-se de que **Start the
    synchronization process when configuration completes** esteja
    selecionado e, em seguida, selecione **Configure**.

![A screenshot of a computer Description automatically
generated](./media/image67.png)

10. Quando a configuração estiver concluída, selecione **Exit**.

![](./media/image68.png)

Observação: Aguarde aproximadamente 5 minutos para que a sincronização
seja concluída.

**Tarefa 3: Configurar a junção híbrida do Microsoft Entra usando o
Azure AD Connect**

1.  No
    [SEA-SVR1](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)
    VM **Desktop**, clique duas vezes em **Azure AD Connect.**

![Text Description automatically generated with medium
confidence](./media/image69.png)

2.  Na janela **Microsoft Azure Active Directory Connect**, selecione
    **Configure**.

![](./media/image70.png)

3.  Na página **Additional tasks**, selecione **Configure device
    options** e selecione **Next**.

![](./media/image71.png)

4.  Na página **Overview**, selecione **Next**.

![A screenshot of a computer Description automatically
generated](./media/image72.png)

5.  Na página **Connect to Entra**, insira a senha do administrador do
    locatário na caixa **PASSWORD** e selecione **Next**.

![](./media/image73.png)

6.  Na página **Device options**, selecione **Confi Configure Hybrid
    Azure AD Join** e, em seguida, selecione **Next**.

![A screenshot of a computer Description automatically
generated](./media/image74.png)

7.  Na página **Device operating systems**, selecione **Windows 10 or
    later domain-joined devices** e, em seguida, selecione **Next**.

![A screenshot of a computer Description automatically
generated](./media/image75.png)

8.  Na página de **SCP configuration**, marque a caixa de seleção ao
    lado de **Contoso.com**. Selecione **Azure Active Directory** no
    menu suspenso **Authentication Service** e selecione **Add**.

![](./media/image76.png)

9.  Na janela **Enterprise Admin Credentials,** digite
    **Contoso\Administrator** como **Username** e !!**Pa55w.rd**!! como
    **Password**. Selecione **OK** e selecione **Next**.

![A screenshot of a computer security Description automatically
generated](./media/image77.png)

![](./media/image78.png)

10. Na página **Ready to configure**, selecione **Configure** para
    executar a configuração.

![A screenshot of a computer Description automatically
generated](./media/image79.png)

11. Quando a configuração estiver concluída, selecione **Exit**.

![A screenshot of a computer Description automatically
generated](./media/image80.png)

12. Na barra de tarefas, clique com o botão direito do mouse no
    **Windows Start button icon** e selecione **Windows Powershell
    (Admin)**.

![A screenshot of a computer Description automatically
generated](./media/image81.png)

13. Na janela do **Windows PowerShell,** digite o seguinte comando e
    pressione **Enter:**

!!**Start-ADSyncSyncCycle -PolicyType Initial**!!

![A screenshot of a computer Description automatically
generated](./media/image82.png)

14. Feche a janela do PowerShell.

Observação: aguarde aproximadamente 5 minutos para que a sincronização
seja concluída.

**Tarefa 4: Verificar o registro Entra**

1.  Altere para
    [SEA-CL2](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)
    .

2.  Na página de login, selecione o botão **Power** e depois
    **Restart**.

![Graphical user interface, application Description automatically
generated](./media/image83.png)

***Observação:** A reinicialização acionará o Microsoft Entra Join
híbrido no*
[*SEA-CL2*](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)
*.*

3.  Após reiniciar o **SEA-CL2**, faça login como
    **Contoso\Administrator** com a senha !!**Pa55w.rd**!!

![Graphical user interface, application Description automatically
generated](./media/image84.png)

4.  Na barra de tarefas, clique com o botão direito do mouse no **ícone
    Windows Start** e selecione **Windows Terminal (Admin)**.

![A screenshot of a computer Description automatically
generated](./media/image81.png)

5.  Na janela do **Windows PowerShell,** digite o seguinte comando e
    pressione **Enter:**

!!**dsregcmd /status**!!

6.  Na saída em **Device State**, verifique isso.

- **AzureAdJoined: YES** 

- **DomainJoined: YES** are displayed.

![](./media/image85.png)

***Observação: se o dispositivo ainda não estiver conectado ao Entra,
aguarde a conclusão da sincronização do Entra Connect e reinicie o
SEA-CL2. Pode levar de 5 a 10 minutos para que o status seja
atualizado.***

Além disso, você pode fazer login no **SEA-SVR1** e, na janela do
**Windows PowerShell,** digitar o seguinte comando para acelerar a
sincronização.

!!**Start-ADSyncSyncCycle -PolicyType Initial**!!

7.  Feche todas as janelas no
    [SEA-CL2](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)
    e saia.

8.  Altere para
    [SEA-SVR1](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)
    e vá para a janela do **Microsoft Entra admin center**, navegue e
    clique em **Identity**.

![A screenshot of a computer Description automatically
generated](./media/image7.png)

9.  Na seção **Identity**, selecione **Devices**, navegue e clique em
    **All devices**, conforme mostrado na imagem abaixo.

![A screenshot of a computer Description automatically
generated](./media/image8.png)

10. Verifique se o **SEA-CL2** possui o **Microsoft Entra** **hybrid
    joined** como valor para a linha **Join type**. Clique no botão
    **Refresh** se SEA-CL2 não estiver listado.

![A screenshot of a computer Description automatically
generated](./media/image86.png)

11. Feche todas as janelas no
    [SEA-SVR1](https://labclient.labondemand.com/Instructions/e7cc4ae1-e3d9-4c55-accc-696f537e1e17?rc=10)
    .

**Resultados:** Após concluir este exercício, você terá configurado e
validado com sucesso a junção híbrida do Microsoft Entra.
