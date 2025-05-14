Laboratório 02 - Sincronizando Identidades usando o Microsoft Entra
Connect

**Resumo**

Neste laboratório, você configurará a sincronização dos Active Directory
Domain Services para o Microsoft Entra ID

**Cenário**

Atualmente, a Contoso Corporation gerencia usuários no AD DS e no
Microsoft Entra ID como processos separados. Isso consome tempo e gera
informações inconsistentes. Você foi incumbido de resolver esse problema
conectando os dois diretórios usando a ferramenta de sincronização do
Microsoft Entra Connect.

## Tarefa 0: Habilitar TLS 1.2 usando script do PowerShell

1.  Em **SEA-SVR1**, faça login como **Contoso\Administrator** com a
    senha **Pa55w.rd**

2.  No menu Iniciar, digite **[PowerShell](urn:gd:lg:a:send-vm-keys),**
    clique com o botão direito do mouse em PowerShell e selecione **run
    as administrator**.

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

Tarefa 1: Configurar a sincronização de diretórios com o Microsoft Entra
Connect

1.  Em [***SEA-SVR1***](urn:gd:lg:a:select-vm), se necessário, faça
    login como
    [**[Contoso\Administrator](urn:gd:lg:a:send-vm-keys)**](urn:gd:lg:a:send-vm-keys)
    com a senha !\![**Pa55w.rd**](urn:gd:lg:a:send-vm-keys)!!

2.  Na barra de tarefas, selecione **Microsoft Edge** .

3.  Na barra de endereço, digite
    !\![**http://www.microsoft.com/en-us/download/details.aspx?id=47594**](urn:gd:lg:a:send-vm-keys)!!

4.  Na página Microsoft Entra Connect, selecione **Download**.

> O Microsoft Entra Connect baixa automaticamente para a pasta
> **Downloads** no **SEA-SVR1** .
>
> ![A screenshot of a computer Description automatically
> generated](./media/image4.png)

5.  Clique em **Open file** para o arquivo baixado
    **AzureADConnect.msi**.

> ![A screenshot of a phone Description automatically
> generated](./media/image5.png)

6.  No assistente do **Microsoft Azure Active Directory Connect**, na
    página **Welcome to Azure AD Connect**, marque a caixa de seleção
    **I agree to the license terms and privacy notice** e selecione
    **Continue**.

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image6.png)

7.  Na página **Express Settings**, selecione **Customize**.

> ![](./media/image7.png)

8.  Na página **Install required components**, selecione **Install**.

> ![](./media/image8.png)

9.  Na página **User sign-in**, certifique-se de que **Password Hash
    Synchronization** esteja selecionado e selecione **Next**.

> ![](./media/image9.png)

10. Na página **Connect to Azure AD**, nas caixas **USERNAME** e
    **PASSWORD**, insira suas **Office 365 Tenant credentials** e
    selecione **Next**.

> ![](./media/image10.png)

11. Na página **Connect your directories**, certifique-se de que
    **Contoso.com** esteja listado em **FOREST** e selecione **Add
    Directory**.

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image11.png)

12. Na janela **AD forest account**, selecione a opção **Create New AD
    Account** e, no campo **ENTERPRISE ADMIN USERNAME**, digite
    [**[Contoso\Administrator](urn:gd:lg:a:send-vm-keys)**](urn:gd:lg:a:send-vm-keys)
    e, em seguida, digite !\![**Pa55w.rd**](urn:gd:lg:a:send-vm-keys)!!
    no campo **PASSWORD**. Selecione **OK** e, em seguida **Next**.

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image12.png)
>
> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image13.png)

13. Na página **Azure AD sign-in configuration**, certifique-se de que,
    na lista suspensa **USER PRINCIPAL NAME,** o valor
    **userPrincipalName** esteja selecionado.

> ![](./media/image14.png)

14. Selecione **Continue without matching all UPN suffixes to verified
    domains** e selecione **Next**.

15. Na página **Domain and OU filtering**, selecione **Sync selected
    domains and Ous.**

16. Expanda **Contoso.com** , desmarque a caixa de seleção ao lado de
    **Contoso.com** e certifique-se de que apenas as seguintes caixas de
    seleção estejam selecionadas:
    **IT**, **Managers**, **Marketing**, **Research** e **Sales**.
    Selecione **Next**.

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image15.png)

17. Na página **Uniquely identifying your users**, selecione **Next**.

18. Na página **Filter users and devices**, selecione **Next**.

19. Na página **Optional features**, revise as opções disponíveis, mas
    não faça nenhuma alteração. Certifique-se de que **Password hash
    synchronization** esteja selecionada e, em seguida, selecione
    **Next**.

> ![](./media/image16.png)

20. Na página **Ready to configure**, certifique-se de que **Start the
    synchronization process when configuration completes** esteja
    selecionado e, em seguida, selecione **Install**.

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image17.png)

21. Quando a configuração estiver concluída, selecione **Exit**.

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image18.png)
>
> **Observação**: Neste momento, inicia-se a sincronização dos objetos
> do seu Active Directory Domain Services (AD DS) local com o Microsoft
> Entra ID. Você deve aguardar aproximadamente 3 a 4 minutos para que
> esse processo seja concluído.

22. Feche todas as janelas abertas.

Tarefa 2: Verificar a sincronização no Microsoft Entra ID

1.  No **Microsoft Edge**, abra uma nova aba e navegue até a página de
    usuários do Centro de administração do Microsoft Entra -
    !\![**https://entra.microsoft.com/#view/Microsoft_AAD_UsersAndTenants/UserManagementMenuBlade/~/AllUsers/menuId/**](https://entra.microsoft.com/#view/Microsoft_AAD_UsersAndTenants/UserManagementMenuBlade/~/AllUsers/menuId/)!!
    Se solicitado a entrar, use as credenciais do locatário do Office
    365 na aba Home da interface do Laboratório.

> ![A screenshot of a computer Description automatically
> generated](./media/image19.png)

2.  Verifique se você vê usuários do seu AD DS local. Certifique-se de
    que esses usuários tenham o valor **Yes** na coluna **On-premises
    sync enabled**.

> ![](./media/image20.png)

3.  No painel de navegação, selecione Expandir **Groups** e depois
    selecione **All groups**.

> ![A screenshot of a computer Description automatically
> generated](./media/image21.png)

4.  Verifique se você vê grupos do seu AD DS local ()

> ![A screenshot of a computer Description automatically
> generated](./media/image22.png)

5.  Selecione o grupo **Managers**.

> ![A screenshot of a computer Description automatically
> generated](./media/image23.png)

6.  Na página do grupo **Managers**, selecione **Members** e
    certifique-se de que você vê os usuários.

> ![A screenshot of a computer Description automatically
> generated](./media/image24.png)
>
> ![A screenshot of a group of people Description automatically
> generated](./media/image25.png)
>
> **Observe que você não pode adicionar ou remover membros deste grupo,
> pois ele é originado do AD DS local.**

7.  Feche o Microsoft Edge.

**Resultados** : Após concluir este exercício, você terá configurado com
sucesso o Microsoft Entra Connect para sincronizar a identidade dos
Active Directory Domain Services com o Microsoft Entra ID
