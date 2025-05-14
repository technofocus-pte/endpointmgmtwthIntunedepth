**Laboratório 10 - Usando o Group Policy Analytics para validar o
suporte ao Group Policy Object (GPO) no Microsoft Intune**

**Resumo**

Neste laboratório, você usará o Group Policy Analytics para importar um
Group Policy Object (GPO) do Active Directory e identificar as
configurações compatíveis com a política equivalente do Microsoft Intune
Mobile Device Management (MDM).

**Cenário**

A Contoso tradicionalmente utiliza Group Policy Objects (GPOs) do Active
Directory para implantar configurações de políticas de computador e
usuário em todo o domínio. Você planeja mover todas as configurações de
GPO suportadas para perfis de configuração do Microsoft Intune. Existe
um GPO chamado **Windows Client Policy**. Você precisa usar o Group
Policy Analytics para validar as configurações no GPO do Windows Client
Policy e identificar quais configurações podem ser migradas com sucesso
para o Intune.

**Tarefa 1: Exportar o Group Policy Object (GPO) do Windows Client
Policy para um arquivo XML**

1.  Efetue login no [***SEA-SVR1***]() com as credenciais fornecidas na
    barra de pesquisa, digite !!**Server Manager**!! e então
    selecione-o.

> ![](./media/image1.png)

2.  Em **Server Manager - Dashboard**, selecione **Tools** e depois
    **Group Policy Management**.

> ![A screenshot of a computer Description automatically
> generated](./media/image2.png)

3.  No console Gerenciamento de Política de Grupo, expanda
    **Forest:Contoso.com**, depois **Domains**, depois **Contoso.com** e
    selecione **Group Policy Objects**.

> Verifique se há vários Group Policy Objects listados.

4.  No painel de detalhes, selecione o GROUP POLICY OBJECT (GPO) do
    **Windows Client Policy.**

> ![](./media/image3.png)

5.  Clique com o botão direito do mouse em **Windows Client Policy** e
    selecione **Save Report**.

> ![](./media/image4.png)

6.  Na caixa de diálogo Salvar relatório de GROUP POLICY OBJECT (GPO),
    selecione **Documents**, altere o **Save as type** para **XML file**
    e selecione **Save**.

> ![](./media/image5.png)

7.  Feche o console de Gerenciamento de Política de Grupo.

8.  Feche o Gerenciador do Servidor.

**Tarefa 2: Analisar o GROUP POLICY OBJECT (GPO) do cliente Windows
usando o Group Policy Analytics**

1.  Abra o Microsoft Edge, digite !!**https://intune.microsoft.com**!!
    na barra de endereço e pressione **Enter**.

2.  Entre com as credenciais de locatário do Office 365, se solicitado.

3.  No **Microsoft Intune admin center**, navegue e selecione
    **Devices**.

> ![](./media/image6.png)

4.  Navegue até a seção **Manage devices** e selecione **Group Policy
    analytics**.

> ![](./media/image7.png)

5.  No painel **Devices | Group Policy analytics**, selecione
    **Import**.

> ![A screenshot of a computer Description automatically
> generated](./media/image8.png)

6.  Na aba **GPO file upload**, clique na pasta ao lado da barra de
    pesquisa **Select a file**, conforme mostrado na imagem abaixo.

> ![A screenshot of a computer Description automatically
> generated](./media/image9.png)

7.  Na caixa **Open**, selecione **Documents** e, em seguida, **Windows
    Client Policy.xml.** Em seguida, clique no botão **Open.**

> ![A screenshot of a computer Description automatically
> generated](./media/image10.png)

8.  Clique no botão **Next**.

> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)

9.  Em **Scope tags**, clique no botão **Next**.

> ![A screenshot of a computer Description automatically
> generated](./media/image12.png)

10. Na aba **Review + create**, clique no botão **Create**.

> ![A screenshot of a computer Description automatically
> generated](./media/image13.png)

11. O GROUP POLICY OBJECT (GPO) do Windows Client Policy é importado e
    analisado imediatamente. Feche a página **Import GPO files**.

12. No painel de **Devices | Group Policy analytics**, revise as
    informações ao lado de **Windows Client Policy.**

> Observe que 89% das configurações têm suporte a MDM.
>
> ![A screenshot of a computer Description automatically
> generated](./media/image14.png)

13. Em Suporte MDM, selecione **89%.**

> Observe cada **Setting Name**, **MDM Support**, **CSP Name** e o **CSP
> Mapping** para cada configuração suportada. Também verifique quais
> configurações não possuem um mapeamento Configuration Service Provider
> (CSP) equivalente.
>
> ![A screenshot of a computer Description automatically
> generated](./media/image15.png)

14. Feche a janela **Windows Client Policy**.

**Tarefa 3: Revisar o Relatório de Resumo da Group Policy Analytics**

1.  No menu de navegação do **Microsoft Intune admin center**, selecione
    **Reports**.

> ![](./media/image16.png)

2.  Na página **Reports**, na seção **Device management**, selecione
    **Group Policy analytics**.

> ![](./media/image17.png)

3.  No painel de detalhes, em **Summary**, selecione **Refresh**. Pode
    ser necessário atualizar algumas vezes.

> Pode levar de 5 a 10 minutos para atualizar e criar o relatório de
> resumo.

4.  Revise as informações **Group policy migration readiness**.

> ![A screenshot of a computer Description automatically
> generated](./media/image18.png)
>
> Deve haver uma série de políticas prontas para migração e uma série de
> políticas não suportadas.

5.  Selecione a aba **Reports** e, em seguida, **Group policy migration
    readiness**.

> ![A screenshot of a group policy migration Description automatically
> generated](./media/image19.png)

6.  Selecione **Generate report**.

> ![A screenshot of a computer Description automatically
> generated](./media/image20.png)

7.  O relatório de prontidão para migração da política de grupo fornece
    informações relacionadas a cada configuração e ao tipo de perfil
    suportado.

> ![A screenshot of a computer Description automatically
> generated](./media/image21.png)

8.  Feche a janela **Group policy migration readiness**.

**Resultados**: Após concluir este exercício, você terá exportado com
sucesso um GROUP POLICY OBJECT (GPO) e usado o Group Policy Analytics
para validar configurações de política equivalentes no Intune.
