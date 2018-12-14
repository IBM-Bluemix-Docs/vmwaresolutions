---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-05"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Pedindo e excluindo instâncias do Single-node Trial for VMware vCenter Server on IBM Cloud

O Single-node Trial for VMware vCenter Server on {{site.data.keyword.cloud}} é uma nuvem privada hospedada em um único locatário que entrega a pilha do VMware vSphere como um serviço. Embora o ambiente gerenciado pelo cliente seja geralmente implementado com um mínimo de três nós, essa avaliação de nó único fornece um caminho de baixo custo para obter benefícios de uma implementação de nuvem híbrida.

Essa avaliação é ideal para uma prova de conceito que demonstra a velocidade da automação avançada da IBM para a implementação inicial e a facilidade de mover cargas de trabalho de não produção simples para a nuvem. Usando o VMware Hybrid Cloud Extension (HCX), é possível ampliar com segurança sua rede de data center no local para o {{site.data.keyword.CloudDataCent_notm}} enquanto reduz a complexidade de rede de configuração da interconexão. O HCX abstrai os recursos de rede subjacentes para o túnel por meio da Internet pública para que seja possível mover de forma contínua as cargas de trabalho bidirecionalmente sem a necessidade de redefinir o IP das máquinas virtuais (VMs). Com o HCX, não há necessidade de ter o VMware NSX instalado no local e é compatível com versões mais antigas do vSphere.  

A avaliação de nó único destina-se somente à prova de conceitos. Não execute cargas de trabalho de trabalho de produção nesse ambiente. As funções de gerenciamento, como a inclusão e a remoção de hosts e clusters, o pedido de serviços de complemento adicionais e a aplicação de atualizações, não são suportadas.
{:important}

Essa avaliação é destinada ao uso de até 90 dias. Quando tiver concluído a avaliação, você poderá excluir esse ambiente e, em seguida, provisionar um ambiente altamente disponível que atenda às suas necessidades de capacidade. Para obter mais informações, veja [Pedindo instâncias do vCenter Server with Hybridity Bundle](vc_hybrid_orderinginstance.html).

## Especificações técnicas para instâncias do Single-node Trial for vCenter Server

Os componentes a seguir são incluídos em sua instância do Single-node Trial for vCenter Server:

A disponibilidade e a precificação de configurações padronizadas de hardware podem variar com base no {{site.data.keyword.CloudDataCent_notm}} que é selecionado para implementação.
{:note}

### Bare Metal Server

Um processador Dual Intel Xeon Gold 5120 (28 Núcleos, 2.20 GHz) com 384 GB de RAM.

### Rede

Os componentes de rede a seguir são pedidos:
*  Uplinks duais de rede pública e privada de 10 Gbps
*  Três VLANs (Virtual LANs): uma VLAN pública e duas VLANs privadas
*  Uma VXLAN (Virtual eXtensible LAN) com DLR (Distributed Logical Router) para comunicação leste-oeste potencial entre cargas de trabalho locais conectadas a redes de camada 2 (L2). A VXLAN é implementada como uma topologia de roteamento de amostra, que pode ser modificada, usada para construção ou ser removida. Também é possível incluir zonas de segurança anexando VXLANs adicionais em novas interfaces lógicas no DLR.
*  Dois VMware NSX Edge Services Gateways:
  * Um serviço de gerenciamento seguro VMware NSX Edge Services Gateway (ESG) para tráfego de gerenciamento de saída HTTPS, que é implementado pela IBM como parte da tipologia de rede de gerenciamento. Esse ESG é usado pelas VMs de gerenciamento da IBM para se comunicar com componentes de gerenciamento externo específicos da IBM relacionados à automação. Para obter mais informações, veja [Configurando sua rede para usar o ESG gerenciado pelo cliente](../vcenter/vc_esg_config.html#configuring-your-network-to-use-the-customer-managed-nsx-esg-with-your-vms).

    Este ESG não está acessível a você e não pode ser usado. Caso seja modificado, talvez não seja possível gerenciar a instância do Single-node Trial for vCenter Server por meio do console do {{site.data.keyword.vmwaresolutions_short}}. Além disso, observe que usar um firewall ou desativar as comunicações ESG para os componentes de gerenciamento externo da IBM fará com que o {{site.data.keyword.vmwaresolutions_short}} se torne inutilizável.
    {:important}
  * Um VMware NSX Edge Services Gateway seguro e gerenciado pelo cliente para tráfego de carga de trabalho de entrada e saída HTTPS, que é implementado pela IBM como um modelo que pode ser modificado por você para fornecer acesso VPN ou acesso público. Para obter mais informações, veja [O NSX Edge gerenciado pelo cliente representa um risco de segurança?](../vmonic/faq.html#does-the-customer-managed-nsx-edge-pose-a-security-risk-)

Para obter mais informações sobre os componentes de rede pedidos ao implementar o serviço HCX on {{site.data.keyword.cloud_notm}}, veja [Visão geral do HCX on {{site.data.keyword.cloud_notm}}](../services/hcx_considerations.html).

### Virtual Server Instances

Os virtual server instances (VSIs) a seguir são pedidos:

* Um VSI for IBM CloudBuilder, que será encerrado depois que a implementação da instância for concluída.
* Um VSI do Microsoft Windows Server para o Microsoft Active Directory (AD) é implementado e pode ser consultado. O VSI funciona como o DNS para a instância em que os hosts e as VMs são registrados.

### Licenças e taxas fornecidas pela IBM

As licenças a seguir são incluídas com a sua ordem de instância do Single-node Trial for vCenter Server.

* VMware vSphere Enterprise Plus 6.5u1
* VMware vCenter Server 6.5
* VMware NSX Service Providers Advanced Edition 6.4

As instâncias do Single-node Trial for vCenter Server não suportam o Bring Your Own License.
{:note}

Suporte adicional e taxas de serviços podem se aplicar.

## Especificações técnicas para o VMware HCX on IBM Cloud

O Single-node Trial for vCenter Server inclui o HCX on {{site.data.keyword.cloud_notm}}. Para obter informações sobre especificações técnicas e considerações para o HCX on {{site.data.keyword.cloud_notm}}, veja [Visão geral do VMware HCX on IBM Cloud](../services/hcx_considerations.html).

## Requisitos e planejamento para pedir instâncias do Single-node Trial for vCenter Server

Assegure-se de confirmar os requisitos a seguir e conclua as tarefas a seguir:
* Pré-requisitos para instâncias do HCX no local:
 * Requer o VMware vSphere e o vCenter 5.5 ou superior.
 * O ambiente do vSphere deve ter comutadores distribuídos para o VMx que será migrado para o {{site.data.keyword.cloud_notm}}.
 * O HCX Manager Virtual Appliance deve estar apto a ser implementado em uma rede privada no ambiente local e deve ter permissão para acessar a Internet pública.
* A conta do {{site.data.keyword.cloud_notm}} que você está usando deve atender a determinados requisitos. Para obter mais informações, veja [Requisitos para a conta do {{site.data.keyword.cloud_notm}}](../vmonic/slaccountrequirement.html).
*  Configure as credenciais de infraestrutura do {{site.data.keyword.cloud_notm}} na página **Configurações**. Para obter mais informações, veja [Gerenciando contas de usuários e configurações](../vmonic/useraccount.html).
* Revise os requisitos de nome da instância:  
 * Apenas caracteres alfanuméricos e o traço (-) são permitidos.
 * O nome da instância deve iniciar e terminar com um caractere alfanumérico.
 * O comprimento máximo do nome da instância é de 10 caracteres.
 * O nome da instância deve ser exclusivo dentro de sua conta.
* Revise os {{site.data.keyword.CloudDataCents_notm}} que atendem aos requisitos para a infraestrutura física. Para obter mais informações, veja a seção *Disponibilidade do {{site.data.keyword.CloudDataCent_notm}}* em [Requisitos e planejamento para instâncias do vCenter Server with Hybridity Bundle](../vcenter/vc_hybrid_planning.html#ibm-cloud-data-center-availability).

## Procedimento para pedir instâncias do Single-node Trial for vCenter Server

1. Na página **Single-node Trial for VMware vCenter Server on {{site.data.keyword.cloud_notm}}**, clique no cartão **vCenter Server** e clique em **Continuar**.
2. Na página **Single-node Trial for VMware vCenter Server**, conclua as etapas para solicitar uma conta de infraestrutura do {{site.data.keyword.cloud_notm}} ou forneça seu **Nome do usuário** e **Chave API** existentes e clique em **Recuperar**.

 Esta seção estará oculta se a chave API já existir.
 {:note}
3. Insira o nome da instância.
4. Selecione o {{site.data.keyword.CloudDataCent_notm}} para hospedar a instância.  

 O  {{site.data.keyword.CloudDataCent_notm}}  é pré-selecionado. Selecione um local do  {{site.data.keyword.CloudDataCent_notm}}  diferente, se necessário.
 {:note}
5. Na área de janela **Resumo do pedido**, verifique a configuração da instância antes de fazer o pedido.
   1. Revise as configurações para a instância.
   2. Revise o custo estimado da instância. Clique em **Detalhes da precificação** para gerar um PDF de resumo. Para salvar ou imprimir o resumo de seu pedido, clique no ícone **Imprimir** ou **Fazer download** no canto superior direito da janela PDF.
   3. Clique no link ou nos links dos termos que se aplicam ao seu pedido e confirme que concorda com esses termos antes de pedir a instância.
   4. Clique em **Provisão**.

### Resultados

A implementação da instância é iniciada automaticamente e o HCX no local na chave de ativação de serviço do {{site.data.keyword.cloud_notm}} é pedido.

#### Processo de implementação para HCX no IBM Cloud

A implementação do HCX no {{site.data.keyword.cloud_notm}} é automatizada. As etapas a seguir são concluídas pelo processo de automação do {{site.data.keyword.vmwaresolutions_short}}:
1. Três sub-redes são pedidas para o HCX por meio da infraestrutura do {{site.data.keyword.cloud_notm}}:
   * Duas sub-redes móveis privadas para gerenciamento HCX.
   * Uma sub-rede portátil pública para ativação e manutenção com o VMware. Essa sub-rede também é usada para interconexões de HCX.

   Os endereços IP nas sub-redes que são pedidos para o HCX são destinados a serem gerenciados pela automação do VMware on {{site.data.keyword.cloud_notm}}. Esses endereços IP não podem ser designados a recursos do VMware, como VMs e NSX Edges, que são criados por você. Se você precisar de endereços IP adicionais para seus artefatos do VMware, deverá pedir suas próprias sub-redes do {{site.data.keyword.cloud_notm}}.
   {:important}
3. Três conjuntos de recursos e pastas da VM para o HCX são criados, os quais são necessários para as interconexões do
HCX, os componentes do HCX local e os componentes do HCX remoto.
4. Um par de VMware NSX Edge Services Gateways (ESGs) para o tráfego de gerenciamento do HCX é implementado e configurado:
   * As interfaces de uplink públicas e privadas são configuradas usando as sub-redes pedidas.
   * Os ESGs são configurados como um par de dispositivos de borda extragrandes com a Alta Disponibilidade (HA) ativada.
   * As regras de firewall e as regras de conversão de endereço de rede (NAT) são configuradas para permitir o tráfego HTTPS de entrada e de saída para/do HCX Manager.
   * As regras do balanceador de carga e os conjuntos de recursos são configurados. Essas regras são conjuntos de recursos usados para encaminhar o tráfego de entrada relacionado ao HCX para os dispositivos virtuais apropriados do HCX Manager, vCenter Server e Platform Services Controller (PSC).
   * Um certificado SSL para criptografar o tráfego HTTPS de entrada relacionado ao HCX que está chegando por meio de ESGs é aplicado.

   A borda de gerenciamento do HCX é dedicada ao tráfego de gerenciamento do HCX entre os componentes do HCX no local e os componentes do HCX do lado da nuvem. Não modifique o limite de gerenciamento do HCX ou use-o para extensões de rede do HCX. Em vez disso, crie limites separados para extensões de rede. Além disso, usar um firewall ou desativar as comunicações de borda de gerenciamento do HCX para os componentes de gerenciamento privados da IBM ou para a Internet pública pode impactar negativamente a funcionalidade do HCX.
   {:important}

5. O HCX Manager on {{site.data.keyword.cloud_notm}} é implementado, ativado e configurado:
   * O HCX Manager é registrado com o vCenter Server.
   * O HCX Manager, vCenter Server, PSC e NSX Manager são configurados.
   * A frota do HCX está configurado.
   * Os contêineres de implementação do HCX locais e remotos são configurados.
6. O nome do host e o endereço IP do HCX Manager está registrado com o servidor DNS do VMware vCenter Server on {{site.data.keyword.cloud_notm}}.

#### Visualizando detalhes da instância

É possível verificar o status da implementação visualizando os detalhes da instância. Para obter informações sobre a visualização de detalhes da instância, veja:

* [Visualizando instâncias do vCenter Server](vc_viewinginstances.html)
* [Visualizando instâncias do VMware HCX on IBM Cloud no local](../services/standalone_viewingserviceinstances.html)

Quando a instância é implementada com êxito, os componentes que são descritos nas seções *Especificações técnicas* deste tópico são instalados em sua plataforma virtual VMware e a chave de ativação de serviço do HCX on {{site.data.keyword.cloud_notm}} no local está disponível na página de detalhes do HCX on {{site.data.keyword.cloud_notm}} no local.

O status da instância muda para **Pronto para uso** e você recebe uma notificação por e-mail.

### O que fazer a seguir

Instale o HCX Enterprise Manager local e configure a conexão com a instância do HCX on {{site.data.keyword.cloud_notm}}.

1. Localize a chave de ativação no local na página **Instâncias implementadas**.
  1. No console do {{site.data.keyword.vmwaresolutions_short}}, clique em **Instâncias implementadas** na área de janela de navegação esquerda.
  2. Na tabela **Instâncias do vCenter Server**, revise a coluna **Tipo** para localizar a instância de avaliação de nó único e anote o nome da instância.
  3. Role para a tabela **Instâncias do HCX no local** e revise a coluna **Nome** para localizar a instância que tem o mesmo nome que a instância de nó único. O nome da instância é anexado com *-OnPrem*.
  4. Anote a chave no campo **Chave de ativação**.
2. Obtenha o HCX Enterprise Manager Open Virtual Appliance (OVA) local por meio do console do HCX on {{site.data.keyword.cloud_notm}} HCX Manager.
  1. Conecte-se ao HCX Cloud Console.
    1. Na tabela **Instâncias do vCenter Server**, clique na instância de avaliação de nó único para visualizar os detalhes da instância.
    2. Em **Informações de acesso**, localize e anote as credenciais do vCenter.
    3. Clique em **Serviços** na área de janela de navegação esquerda.
    4. Na página **Serviços**, clique em **HCX on IBM Cloud**.
    5. Na página de detalhes **HCX on IBM Cloud**, localize e anote o **IP do HCX Cloud**.
    6. Assegure-se de que esteja conectado à VPN para acessar sua rede privada do {{site.data.keyword.cloud_notm}}.
    7. Clique em **Visualizar HCX Cloud Console**.
  2. Em **Console em Nuvem do HCX**, conclua as etapas a seguir:
      1. Clique na guia **Administração**.
      2. Na guia **Atualizações do Sistema**, clique em **SOLICITAR LINK DE DOWNLOAD**.
      3. Clique em **COPIAR LINK** e, em seguida, use esse link para fazer download do HCX Enterprise Client para um ambiente local com acesso ao ambiente do vSphere local.
3. No VMware vSphere Web Client, implemente o HCX Enterprise Client como um dispositivo virtual do HCX Manager (HCX Manager) em seu ambiente local. Para obter mais informações, consulte [Instalando o HCX Enterprise Manager OVA](https://docs.vmware.com/en/VMware-NSX-Hybrid-Connect/3.5.1/user-guide/GUID-C61E107C-1F5F-4615-9BA9-351900CDB69E.html).

    Deve-se implementar o HCX Manager local em uma rede privada e permitir que ele acesse a rede pública. É possível usar um NSX Edge, Vyatta ou gateways semelhantes para permitir acesso à Internet ao HCX Manager local. Se os gateways usados para acesso à rede privada e acesso à rede pública forem diferentes, recomenda-se que você use o gateway padrão para permitir o acesso à rede pública e permitir que o **Console do Administrador do HCX Manager** crie uma rota estática para o acesso à rede privada.  
    {:note}
4. Use a chave de ativação no local anotada na etapa 1 para ativar a VM do HCX Enterprise Manager local.
  1. Efetue login na VM do HCX Enterprise Manager local usando as credenciais especificadas ao implementar o OVA.
  2. Insira a chave de ativação quando solicitada.

  Para obter mais informações, consulte [Ativação e configuração inicial do HCX](https://docs.vmware.com/en/VMware-NSX-Hybrid-Connect/3.5.1/user-guide/GUID-6A4740C1-2225-444C-8ADC-CBE54F181536.html).
  {:note}
5. Um certificado SSL autoassinado foi gerado pelo serviço HCX on {{site.data.keyword.cloud_notm}}. Deve-se importar o certificado para o HCX Manager local concluindo as etapas a seguir:
    1. No **Console do Administrador do HCX Manager** local, clique na guia **Administração**.
    2. Na área de janela de navegação esquerda, clique em **Certificado CA confiável** e, em seguida, clique em **IMPORTAR** à direita.
    3. Clique em **URL** e, em seguida, insira a URL do certificado que deseja aplicar, que é o **HCX Cloud IP** (``https://<cloud-side public IP>``), que pode ser localizado no HCX na página de detalhes do serviço {{site.data.keyword.cloud_notm}} no console do {{site.data.keyword.vmwaresolutions_short}}.
    4. Clique em **APLICAR**.
6. Continue a configuração inicial e construa a interconexão. Para obter mais informações, consulte [Instalando e configurando o VMware HCX Enterprise](https://docs.vmware.com/en/VMware-NSX-Hybrid-Connect/3.5.1/user-guide/GUID-A26BFB16-FA94-426F-8E18-15BAD4BF840E.html).
7. Amplie as redes no VMware HCX do local para o {{site.data.keyword.cloud_notm}}. Para obter mais informações, consulte [Ampliando redes com o VMware HCX](https://docs.vmware.com/en/VMware-NSX-Hybrid-Connect/3.5.1/user-guide/GUID-DD9C3316-D01C-4088-B3EA-84ADB9FED573.html?hWord=N4IghgNiBcIKIA8AuBTAdgEwJZoOYAI0UkB3AewCcBrAZxAF8g).
8. Migre as VMs entre o local e o {{site.data.keyword.cloud_notm}}. Para obter mais informações, consulte [Migrando máquinas virtuais com o VMware HCX](https://docs.vmware.com/en/VMware-NSX-Hybrid-Connect/3.5.1/user-guide/GUID-D0CD0CC6-3802-42C9-9718-6DA5FEC246C6.html?hWord=N4IghgNiBcILIEsDmAnMAXBA7JACAagiugK6S5xgDGAFtgKYDOuA7gujQXC2CvbgAkAwgA0QAXyA).

Deve-se gerenciar os componentes de infraestrutura do {{site.data.keyword.vmwaresolutions_short}} que são criados em sua conta do {{site.data.keyword.cloud_notm}} somente por meio do console do {{site.data.keyword.vmwaresolutions_short}}, não do {{site.data.keyword.slportal}} ou de qualquer outro meio fora do console.
Se você mudar esses componentes fora do console do {{site.data.keyword.vmwaresolutions_short}}, as mudanças não serão sincronizadas com o console e poderão tornar seu ambiente instável.
{:important}

## Procedimento para excluir as instâncias do Single-node Trial for vCenter Server

Para liberar os componentes que você pediu em uma instância do Single-node Trial for vCenter Server, exclua a instância.

Para obter mais informações, veja [Excluindo instâncias do vCenter Server](vc_deletinginstance.html).

### Links relacionados

* [Inscrevendo-se para uma conta do {{site.data.keyword.cloud_notm}}](../vmonic/signing_softlayer_account.html)
* [Glossário de termos do HCX](../services/hcx_glossary.html)
* [Documentação do VMware Hybrid Cloud Extension](https://hcx.vmware.com/#/vm-documentation)
* [Obtendo o HCX OVA](https://docs.vmware.com/en/VMware-NSX-Hybrid-Connect/3.5.1/user-guide/GUID-B0471D10-6EB0-4587-9205-11BF0C78EC1C.html)
* [Pedindo instâncias do vCenter Server with Hybridity Bundle](vc_hybrid_orderinginstance.html)