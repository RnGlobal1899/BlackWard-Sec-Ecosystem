                                                    🏗️ BlackWard Security LAB: Architecture Overview 🛡️

Bem-vindo ao centro de documentação técnica do BlackWard Security LAB. Este projeto consiste na implementação de uma infraestrutura corporativa simulada de pequeno porte, distribuída em um ambiente Multi-Cloud Híbrido (Oracle Cloud, Azure, DigitalOcean e Google Cloud). O laboratório visa superar as limitações de hardware local (Athlon 3000G e 8GB de RAM), movendo cargas de trabalho críticas para a nuvem através de uma estratégia de offloading setorial e interconexão de alta disponibilidade.

O laboratório é rigorosamente dividido em quatro módulos interdependentes, permitindo uma abordagem de aprendizado em 360 graus na área de Tecnologia da Informação e Segurança.

🛠️ Módulo 1: Identidade e Infraestrutura de Gestão
Objetivo: Estabelecer a base gerencial estável e a autoridade de identidade do ecossistema.

    • Âncora de Identidade Local (On-Premises): O Windows Server (AD DS) atua como o controlador de domínio raiz, configurado localmente com um nível controlado de RAM para preservar o sistema host.
    • Base Gerencial Permanente (OCI): Utiliza instâncias ARM Ampere da Oracle Cloud (Always Free) para hospedar o MeshCentral (acesso remoto) e o GLPI (inventário de ativos), garantindo disponibilidade 24/7 sem custos.
    • Identidade Híbrida (Azure): Sincronização do diretório local com o Microsoft Entra ID através do Azure for Students, integrando a gestão de usuários com a nuvem.
    • Gestão Administrativa: Uma estação Windows no Azure serve como máquina de gerenciamento para o setor de TI, permitindo administração remota de toda a infraestrutura.

🌐 Módulo 2: Redes Híbridas e Conectividade (Networking)
Objetivo: Garantir a conectividade segura, a segmentação do ambiente e a interoperabilidade entre provedores distintos através de arquiteturas em camadas e SD-WAN.

    • Arquitetura VCN (Cloud): Segmentação de rede na Oracle Cloud (OCI) em subnets públicas (Edge) e privadas (Core), controladas por Security Lists e Network Security Groups (NSG) rigorosos para isolar serviços críticos.
    • Interconexão Site-to-Site (IPsec): Estabelecimento de túneis VPN IPsec entre o perímetro local (FortiGate em Salvador) e o Gateway da Oracle Cloud para redundância e tráfego de alta prioridade.
    • Rede Mesh (Tailscale SD-WAN): Implementação de uma rede privada criptografada que une todas as nuvens (OCI, Azure, DigitalOcean) e o ambiente local, permitindo comunicação transparente via IPs fixos da malha e MagicDNS.
    • Engenharia de Tráfego e DNS: Implementação de DHCP Relay híbrido e resolução de DNS Split-Brain para garantir que a nuvem e o ambiente local operem como uma rede unificada, permitindo a resolução de nomes do AD local em todas as pontas.
    • Segurança de Perímetro: Otimização de regras de firewall e NAT para evitar falhas de conectividade e garantir o tráfego legítimo entre os setores simulados (RH, Vendas e TI).
    • Finalidade Setorial: Esta infraestrutura permite, por exemplo, que estações de trabalho do RH na Azure acessem servidores de arquivos na Oracle de forma segura e transparente.

🛡️ Módulo 3: SOC e Simulação Setorial (Offloading)
Objetivo: Centralizar o monitoramento de segurança e simular departamentos corporativos reais.

    • Wazuh SIEM (OCI): Centralização de logs de todos os setores na Oracle Cloud, aproveitando os 24GB de RAM para o processamento de telemetria e análise de eventos.
    • Distribuição de Ativos por Setor:
        • Setor 1: RH/Adm: Estação Windows na Azure (vítima de phishing) e Servidor de Arquivos Linux na Oracle (alvo de exfiltração).
        • Setor 2: Vendas: Estação Windows na Azure (alvo secundário) e Estações Linux Desktop leves (XFCE) na Oracle.
        • Setor 3: TI/Dev: Servidores de Banco de Dados e Aplicações na Oracle e VM de Gerenciamento Windows na Azure.

☣️ Módulo 4: Red Team e Operações Ofensivas
Objetivo: Simular ameaças externas reais e táticas de pós-exploração.

    • Infraestrutura de Ataque (DigitalOcean): Hospedagem isolada do Sliver C2 e do Gophish utilizando créditos do GitHub Student Pack.
    • Cenário de Compromisso: Simulação de campanhas de engenharia social visando o setor de RH para obter acesso inicial, seguido de movimentação lateral e exfiltração de dados monitorada pelo SIEM.

🚀 Módulo 5: Inovação e Big Data (GCP)
Objetivo: Demonstrar proficiência em tecnologias nativas de nuvem e análise de dados.

    • Orquestração (GKE): Utilização do Google Kubernetes Engine para rodar scanners de vulnerabilidades de forma containerizada.
    • Analytics (BigQuery): Exportação de logs do Wazuh para análise estatística avançada no BigQuery e visualização de inteligência no Looker Studio.

Analista Responsável: Bruno Eduardo  
Status do Ecossistema: Operacional / Em expansão
Última Auditoria: 30/01/2026