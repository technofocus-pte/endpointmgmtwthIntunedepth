# **Laboratório 19 - Implementação do Windows 11 usando o Microsoft Deployment Toolkit**

**Resumo**

Neste laboratório, você usará o Microsoft Deployment Toolkit para criar
e Implementar uma imagem do sistema operacional Windows 11.

**Cenário**

Você precisa Implementar uma nova máquina virtual do Windows 11 chamada
SEA-WS4. Você decide usar o Microsoft Deployment Toolkit para
Implementar o sistema operacional em uma máquina virtual criada no
Hyper-V. Você configurará um novo Compartilhamento de Implementação no
MDT e, em seguida, configurará a sequência de tarefas que executará as
etapas de Implementação do SEA-WS4.

### **Tarefa 1: Criar um novo compartilhamento de Implementação**

1.  Altere para [**SEA-SVR2**](urn:gd:lg:a:select-vm), faça login como
    !!**[Contoso\Administrator](urn:gd:lg:a:send-vm-keys)!!** com a
    senha !!**[Pa55w.rd](urn:gd:lg:a:send-vm-keys)!!**

> ![Screenshot](./media/image1.png)

2.  Na barra de tarefas, selecione **File Explorer** e navegue até
    !!**[E:\Labfiles\ISOs](urn:gd:lg:a:send-vm-keys)!!**

> ![Screenshot](./media/image2.png)

3.  Clique com o botão direito do mouse em **Win11_21H2_Eval.iso** e
    selecione **Mount**. O ISO será montado como DVD Drive **D.**

> ![Screenshot](./media/image3.png)
>
> ![Screenshot](./media/image4.png)

4.  Feche o **File Explorer**.

5.  Selecione o **Start menu**, expanda **Microsoft Deployment Toolkit**
    e selecione **Deployment Workbench.**

> ![Screenshot](./media/image5.png)

6.  Em **Deployment Workbench**, clique com o botão direito do mouse em
    **Deployment Shares** e selecione **New Deployment Share** .

> ![Screenshot](./media/image6.png)
>
> O **New Deployment Share Wizard** é aberto.

7.  Na página **Path**, em **Deployment share path**, altere o valor
    para !!**[E:\DeploymentShare](urn:gd:lg:a:send-vm-keys)!!** e
    selecione **Next**.

> ![Screenshot](./media/image7.png)

8.  Na página **Share**, anote o **Share name**, mas não o altere.
    Selecione **Next**.

> ![Screenshot](./media/image8.png)

9.  Na página **Descriptive Name**, aceite o valor padrão e selecione
    **Next**.

> ![Screenshot](./media/image9.png)

10. Na página **Options**, configure o seguinte e selecione **Next**:

    - Solicitar a definição da senha do administrador local: **Enabled**

    - Todas as outras caixas de seleção: **Disabled**

> ![Screenshot](./media/image10.png)

11. Na página **Summary**, revise as informações e selecione **Next**.

> ![Screenshot](./media/image11.png)

12. Na página **Confirmation**, certifique-se de que o processo foi
    concluído com sucesso e selecione **Finish**.

> ![Screenshot](./media/image12.png)

13. Em **Deployment Shares**, expanda a pasta **MDT Deployment Share**.

> Anote os vários nós que podem ser configurados para o compartilhamento
> de Implementação.

### **Tarefa 2: Adicionar arquivos do sistema operacional ao compartilhamento de Implementação**

1.  No Deployment Workbench, expanda **Deployment Shares**, expanda
    **MDT Deployment Share** e selecione **Operating Systems**.

> ![Screenshot](./media/image13.png)

2.  Clique com o botão direito do mouse em **Operating Systems** e
    selecione **Import Operating System**. O Assistente para Importação
    do Sistema Operacional será aberto.

> ![Screenshot](./media/image14.png)

3.  No **Import Operating System Wizard**, na página **OS Type**,
    selecione **Full set of source files** e, em seguida, selecione
    **Next**.

> ![Screenshot](./media/image15.png)

4.  Na página **Source**, em **Source Directory**, digite !!
    [**D:\\**](urn:gd:lg:a:send-vm-keys) **!!** e selecione **Next**.

> ![Screenshot](./media/image16.png)

5.  Na página **Destination**, altere o nome do diretório de destino
    padrão para !!**[Windows 11 Enterprise
    x64](urn:gd:lg:a:send-vm-keys)!!** e selecione **Next**.

> ![Screenshot](./media/image17.png)

6.  Na página **Summary**, revise as informações e selecione **Next**.

> ![Screenshot](./media/image18.png)
>
> Os arquivos de origem do sistema operacional são copiados para o
> compartilhamento de Implementação.

7.  Na página **Confirmation**, certifique-se de que o processo foi
    concluído com sucesso e selecione **Finish**.

> ![Screenshot](./media/image19.png)

8.  Em **Deployment Workbench**, com **Operating Systems** selecionados,
    verifique se o sistema operacional é exibido.

### **Tarefa 3: Adicionar aplicações ao compartilhamento de Implementação**

1.  No Deployment Workbench, expanda **Deployment Shares**, expanda
    **MDT Deployment Share** e selecione **Applications**.

2.  Clique com o botão direito do mouse **em Applications** e selecione
    **New Application**. O Assistente para Novo Aplicativo será aberto.

> ![Screenshot](./media/image20.png)

3.  Em **New Application Wizard**, na página **Application Type**,
    selecione **Application with source files** e, em seguida, selecione
    **Next**.

> ![Screenshot](./media/image21.png)

4.  Na página **Details**, configure o seguinte e selecione **Next**:

    - Publisher: !!**[Microsoft](urn:gd:lg:a:send-vm-keys)!!**

    - Application Name: !!**[XML Notepad](urn:gd:lg:a:send-vm-keys)!!**

> ![Screenshot](./media/image22.png)

5.  Na página **Source**, em **Source directory**, digite
    !!**[E:\Labfiles\Apps](urn:gd:lg:a:send-vm-keys)!!** e selecione
    **Next**.

> ![Screenshot](./media/image23.png)

6.  Na página **Destination**, aceite o nome do diretório de destino
    padrão e selecione **Next**.

> ![Screenshot](./media/image24.png)

7.  Na página **Command Details**, em **Command line,** digite
    !!**[XmlNotepadSetup.msi /q](urn:gd:lg:a:send-vm-keys)!!** e
    selecione **Next**.

> ![Screenshot](./media/image25.png)

8.  Na página **Summary**, revise as informações e selecione **Next**.

> ![Screenshot](./media/image26.png)

9.  Na página **Confirmation**, certifique-se de que o processo foi
    concluído com sucesso e selecione **Finish**.

### **Tarefa 4: Criar uma sequência de tarefas MDT**

1.  No Deployment Workbench, expanda **Deployment Shares**, expanda
    **MDT Deployment Share** e selecione **Task Sequences**.

2.  Clique com o botão direito do mouse em **Task Sequences** e
    selecione **New Task Sequence Wizard**. O **New Task Sequence
    Wizard** será aberto.

> ![Screenshot](./media/image27.png)

3.  Na página **General Settings**, configure o seguinte e selecione
    **Next**:

    - Task sequence ID: !!**[001](urn:gd:lg:a:send-vm-keys)!!**

    - Task sequence name: !!**[Deploy Windows 11
      Enterprise](urn:gd:lg:a:send-vm-keys)!!**

> ![Screenshot](./media/image28.png)

4.  Na página **Select Template**, selecione **Standard Client Task
    Sequence** e, em seguida, **Next**.

> ![Screenshot](./media/image29.png)

5.  Na página **Select OS**, selecione **Windows 10 Enterprise
    Evaluation** e depois selecione **Next**.

> ![Screenshot](./media/image30.png)

6.  Na página **Specify Product Key**, selecione **Do not specify a
    product key at this time** e, em seguida, selecione **Next**.

> ![Screenshot](./media/image31.png)

7.  Na página **OS Settings**, configure o seguinte e selecione
    **Next**:

    - Full Name: !!**[User](urn:gd:lg:a:send-vm-keys)!!**

    - Organization: !!**[Contoso
      Corporation](urn:gd:lg:a:send-vm-keys)!!**

    - Internet Explorer Home
      Page: !!**[about:blank](urn:gd:lg:a:send-vm-keys)!!**

> ![Screenshot](./media/image32.png)

8.  Na página **Admin Password**, selecione **Use the specified local
    Administrator password** e digite
    !!**[Pa55w.rd](urn:gd:lg:a:send-vm-keys)!!** em ambas as caixas de
    texto. Selecione Next.

> ![Screenshot](./media/image33.png)

9.  Na página **Summary**, revise as informações e selecione **Next**.

> ![Screenshot](./media/image34.png)

10. Na página **Confirmation**, certifique-se de que o processo foi
    concluído com sucesso e selecione **Finish**.

> ![Screenshot](./media/image35.png)

11. Em **Deployment Workbench**, com **Task Sequences** selecionado,
    verifique se a sequência de tarefas **Deploy Windows 11 Enterprise**
    é exibida.

> ![Screenshot](./media/image36.png)

12. Clique com o botão direito do mouse na sequência de tarefas **Deploy
    Windows 11 Enterprise** e selecione **Properties**.

> ![Screenshot](./media/image37.png)

13. Selecione a aba **Task Sequence**.

14. Expanda o nó **Validation** e selecione **Validate**.

15. Na página **Properties**, desmarque as opções **Ensure minimum
    memory**.

> Não faça nenhuma outra alteração.

16. Na janela **Deploy Windows 11 Enterprise Properties**, selecione
    **OK** .

> ![Screenshot](./media/image38.png)

### **Tarefa 5: Configurar propriedades de compartilhamento de Implementação e configurações do Windows PE**

1.  No Deployment Workbench, expanda **Deployment Shares** e selecione
    **MDT Deployment Share**.

2.  Clique com o botão direito do mouse em **MDT Deployment Share** e
    selecione **Properties**.

> ![Screenshot](./media/image39.png)

3.  Na janela **MDT Deployment Share Properties**, na aba **General**,
    anote as informações que foram fornecidas quando o compartilhamento
    de Implementação foi criado.

> ![Screenshot](./media/image40.png)

4.  Selecione a aba **Rules**.

> A aba Regras exibe o conteúdo do arquivo CustomSettings.ini. Esses
> valores foram fornecidos durante a criação do compartilhamento de
> implementação.
>
> ![Screenshot](./media/image41.png)

5.  Selecione a aba **Windows PE.**

> A aba Windows PE fornece opções para criar um disco de inicialização
> do Windows PE.

6.  Na aba **Windows PE**, ao lado de **Platform**, selecione **x64.**

7.  Na seção **Windows PE Customizations**, ao lado de **Scratch space
    size**, selecione **64**.

> ![Screenshot](./media/image42.png)

8.  Selecione a aba **Features** e então marque a caixa de seleção ao
    lado dos seguintes Pacotes de Recursos:

    - DISM Cmdlets

    - Windows PowerShell

    - Microsoft Data Access Components (MDAC/ADO) support

> ![Screenshot](./media/image43.png)
>
> ![Screenshot](./media/image44.png)

9.  Selecione a aba **Monitoring**.

10. Na aba **Monitoring**, marque a caixa de seleção ao lado de **Enable
    monitoring for this deployment share**.

11. Na janela **MDT Deployment Share Properties**, selecione **OK.**

> ![Screenshot](./media/image45.png)

12. Clique com o botão direito do **MDT Deployment Share** e selecione
    **Update Deployment Share**. O Assistente para Atualizar
    Compartilhamento de Implementação será aberto.

> ![Screenshot](./media/image46.png)

13. Na página **Options**, selecione **Optimize the boot image updating
    process** e selecione **Next**.

> ![Screenshot](./media/image47.png)

14. Na página **Summary**, selecione **Next**.

> ![Screenshot](./media/image48.png)
>
> O Compartilhamento de Implementação começa a atualizar e criar os
> arquivos do Windows PE. Isso levará alguns minutos para ser concluído.

15. Na página **Confirmation**, certifique-se de que o processo foi
    concluído com sucesso e selecione **Finish**.

> ![Screenshot](./media/image49.png)

### **Tarefa 6: Implementar o Windows 11 usando o MDT**

1.  Em [**SEA-SVR2**](urn:gd:lg:a:select-vm), na barra de tarefas,
    selecione **Hyper-V Manager**.

> ![Screenshot](./media/image50.png)

2.  No Gerenciador do Hyper-V, selecione **Virtual Switch Manager**.

> ![Screenshot](./media/image51.png)

3.  Selecione **External** na lista e clique em **Create Virtual
    Switch**.

> ![Screenshot](./media/image52.png)

4.  Na página **Virtual Switch Properties**, em **Name**, insira
    [**External network**](urn:gd:lg:a:send-vm-keys), selecione **OK**
    e, em seguida, selecione **Yes**.

> ![Screenshot](./media/image53.png)
>
> ![Screenshot](./media/image54.png)

5.  No Gerenciador do Hyper-V, selecione **SEA-SVR2** e, no painel
    Actions, selecione **New** e, em seguida, **Virtual Machine**.

> ![Screenshot](./media/image55.png)

6.  Na página **Before you Begin**, selecione **Next**.

> ![Screenshot](./media/image56.png)

7.  Na página **Specify Name and Location**, na caixa **Name**, digite
    !!**[SEA-WS4](urn:gd:lg:a:send-vm-keys)!!**.

8.  Marque a caixa de seleção ao lado de **Store the virtual machine in
    a different location** e, em seguida, ao lado de **Location**,
    digite
    !!**[E:\Labfiles\VirtualMachines](urn:gd:lg:a:send-vm-keys)!!**.
    Selecione **Next**.

> ![Screenshot](./media/image57.png)

9.  Na página **Specify Generation**, certifique-se de que **Generation
    2** esteja selecionada e selecione **Next**.

> ![Screenshot](./media/image58.png)

10. Na página **Assign Memory**, ao lado de **Startup memory,** digite
    !!**[8192](urn:gd:lg:a:send-vm-keys)!!** e selecione **Next**.

> ![Screenshot](./media/image59.png)

11. Na página **Configure Networking**, ao lado de **Connection**,
    selecione **External Network** e depois **Next**.

> ![Screenshot](./media/image60.png)

12. Na página **Connect Virtual Hard Disk**, selecione **Create a
    virtual hard disk**, digite o seguinte e clique em **Next**:

    - Name: !!**[SEA-WS4.vhdx](urn:gd:lg:a:send-vm-keys)!!**

    - Location: !!**[E:\Labfiles\VirtualMachines](urn:gd:lg:a:send-vm-keys)!!**

    - Size: !!**[60](urn:gd:lg:a:send-vm-keys)!!**

> ![Screenshot](./media/image61.png)

13. Na página **Installation Options**, selecione **Install an operating
    system from a bootable image file** e configure o seguinte:

    - Image file
      (.iso): !!**[E:\DeploymentShare\Boot\LiteTouchPE_x64.iso](urn:gd:lg:a:send-vm-keys)!!**

> ![Screenshot](./media/image62.png)

14. Selecione **Next** e depois **Finish**.

> ![Screenshot](./media/image63.png)

15. No Gerenciador do Hyper-V, clique com o botão direito do mouse em
    **SEA-WS4** e selecione **Settings**.

> ![Screenshot](./media/image64.png)

16. Selecione **Security** e marque a caixa de seleção ao lado de
    **Enable Trusted Platform Module**.

> ![Screenshot](./media/image65.png)

17. Selecione **Processor** e altere o número de processadores virtuais
    para !!**[2](urn:gd:lg:a:send-vm-keys)!!**.

18. Selecione **OK** para fechar a caixa de diálogo Configurações.

> ![Screenshot](./media/image66.png)

19. No Gerenciador do Hyper-V, selecione **SEA-WS4**, selecione
    **Connect** e, em seguida, selecione **Start**.

> ![Screenshot](./media/image67.png)
>
> ![Screenshot](./media/image68.png)

20. Quando o computador iniciar, pressione qualquer tecla do teclado
    para abrir o Assistente de Implementação do MDT. Maximize a janela
    conforme necessário.

> ![Screenshot](./media/image69.png)

21. Na página **Welcome**, selecione **Run the Deployment Wizard to
    install a new Operating System**.

> ![Screenshot](./media/image70.png)

22. Na janela **Specify credentials for connecting to network shares**,
    digite o seguinte e selecione **OK:**

    - User Name: !!**[Administrator](urn:gd:lg:a:send-vm-keys)!!**

    - Password: !!**[Pa55w.rd](urn:gd:lg:a:send-vm-keys)!!**

    - Domain: !!**[Contoso](urn:gd:lg:a:send-vm-keys)!!**

> ![Screenshot](./media/image71.png)

23. Na página **Task Sequence**, selecione **Deploy Windows 11
    Enterprise** e, em seguida, selecione **Next**.

> ![Screenshot](./media/image72.png)

24. Na página **Computer Details**, ao lado de **Computer name,** digite
    !!**[SEA-WS4](urn:gd:lg:a:send-vm-keys)!!** e selecione **Next**.

> ![Screenshot](./media/image73.png)

25. Na página **Move Data and Settings**, selecione **Next**.

> ![Screenshot](./media/image74.png)

26. Na página **User Data (Restore)**, selecione **Next**.

> ![Screenshot](./media/image75.png)

27. Na página **Locale and Time**, selecione **Next**.

> ![Screenshot](./media/image76.png)

28. Na página **Applications**, selecione **Next**.

> ![Screenshot](./media/image77.png)

29. Na página **Administrator Password**, digite
    !!**[Pa55w.rd](urn:gd:lg:a:send-vm-keys)!!** em ambas as caixas de
    texto e selecione **Next**.

> ![Screenshot](./media/image78.png)

30. Na página **Ready**, selecione **Begin**.

> ![Screenshot](./media/image79.png)
>
> A instalação será iniciada. Levará algum tempo para ser concluída e o
> **SEA-WS4** será reinicializado durante a instalação, conforme
> necessário.

31. Altere para o **Deployment Workbench.**

32. No Deployment Workbench, expanda **Deployment Shares** e expanda
    **MDT Deployment Share**.

33. Selecione **Monitoring** e, no painel de detalhes, clique duas vezes
    em **SEA-WS4**.

> ![Screenshot](./media/image80.png)
>
> Revise o status do monitoramento durante a Implementação.
>
> ![A screenshot of a computer Description automatically
> generated](./media/image81.png)

34. Altere para **SEA-WS4.**

35. Após a conclusão da instalação, a área de trabalho será aberta e
    finalizará a Implementação. No resumo da Implementação, selecione
    **Concluir.**

> ![Screenshot](./media/image82.png)

36. Desligue o **SEA-WS4** e feche a janela Conexão da Máquina Virtual.

> ![Screenshot](./media/image83.png)

37. No Gerenciador do Hyper-V, clique com o botão direito do mouse em
    **SEA-WS4** e selecione **Settings**.

> ![Screenshot](./media/image84.png)

38. Em **Settings for SEA-WS4**, expanda **SCSI Controller** e selecione
    **DVD Drive**.

39. No painel de detalhes, em **Media**, selecione **None** e depois
    selecione **OK.**

> ![Screenshot](./media/image85.png)

40. Clique com o botão direito do mouse em **SEA-WS4** e selecione
    **Checkpoint** para criar um ponto de verificação do estado atual do
    SEA-WS4.

> ![Screenshot](./media/image86.png)
>
> ![Screenshot](./media/image87.png)

41. Em [**SEA-SVR2**](urn:gd:lg:a:select-vm), feche o **Hyper-V
    Manager** e o **Deployment Workbench.**

42. Abra o **File Explorer**, clique com o botão direito do mouse na
    **DVD Drive D** e selecione **Eject**.

> ![Screenshot](./media/image88.png)
>
> ![Screenshot](./media/image89.png)

43. Feche o **File Explorer** e saia do **SEA-SVR2**.

**Resultados:** Após concluir este exercício, você terá usado com
sucesso o Microsoft Deployment Toolkit para criar e Implementar uma
estação de trabalho do Windows 11.
