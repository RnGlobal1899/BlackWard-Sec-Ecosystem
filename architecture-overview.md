                                                    🏗️ BlackWard Security LAB: Architecture Overview

Bem-vindo ao centro de documentação técnica do BlackWard Security LAB. Este projeto representa um ecossistema híbrido (Cloud & On-Premises) projetado para simular cenários reais de infraestrutura corporativa, desenvolvimento ofensivo e operações de defesa cibernética.

O laboratório é rigorosamente dividido em quatro módulos interdependentes, permitindo uma abordagem de aprendizado em 360 graus na área de Tecnologia da Informação e Segurança.

🛠️ Módulo 1: Infraestrutura & Suporte TI
Objetivo: Estabelecer a base corporativa e demonstrar maturidade na gestão de ativos e suporte proativo.

    • Cloud Provisioning (OCI): Utilizo instâncias Ubuntu ARM na Oracle Cloud para centralizar ferramentas gerenciais, priorizando custo-benefício e performance.
    • Active Directory Híbrido: Configuração de Windows Server local com foco em AD DS e DNS, aplicando conceitos de sincronização de identidade e sufixos UPN alternativos.
    • Gestão de Endpoints: Implementação de soluções como MeshCentral para suporte remoto e GLPI (seguindo práticas ITIL) para inventário e gestão de chamados.
    • Troubleshooting de Identidade: Documentação de resoluções de problemas complexos em sincronização híbrida e logs de erros no Entra Connect.

🌐 Módulo 2: Networking
Objetivo: Garantir a conectividade segura e a segmentação do ambiente através de arquiteturas em camadas (Tiered).

    • Arquitetura VCN (Cloud): Segmentação de rede na OCI em subnets públicas (Edge) e privadas (Core), controladas por Security Lists rigorosas.
    • Interconexão Site-to-Site: Estabelecimento de túneis VPN IPsec entre o perímetro local (FortiGate) e o Gateway da Oracle Cloud.
    • Engenharia de Tráfego: Implementação de DHCP Relay híbrido e resolução de DNS Split-Brain para garantir que a nuvem e o ambiente local operem como uma rede unificada.
    • Segurança de Perímetro: Otimização de regras de firewall e NAT para evitar falhas de conectividade e garantir o tráfego legítimo.

☣️ Módulo 3: Offensive Development & Red Team
Objetivo: Desenvolver ferramentas customizadas e simular campanhas de ataque realistas para validar controles defensivos.

    • Comando e Controle (C2): Deploy de infraestruturas como Sliver ou Havoc em nuvem para orquestração de operações remotas.
    • Malware Development (C++): Criação de loaders utilizando a WinAPI (VirtualAlloc, CreateThread) para execução de shellcode diretamente em memória, visando o bypass de soluções EDR.
    • Post-Exploitation: Implementação de técnicas de persistência (chaves de registro/tarefas agendadas) e simulação de exfiltração de dados e movimentação lateral.
    • Engenharia Social: Execução de campanhas simuladas de Phishing (Gophish) para testar o elo humano da segurança.

🛡️ Módulo 4: Blue Team & Incident Response
Objetivo: Monitorar, detectar e responder a ameaças em tempo real utilizando telemetria avançada e automação.

    • SIEM Centralizado: Implementação do Wazuh Manager na nuvem para coleta e correlação de logs de todo o ecossistema híbrido.
    • Visibilidade de Endpoint: Implantação de telemetria avançada via Sysmon (configurado com SwiftOnSecurity) para monitoramento detalhado de processos e rede.
    • Engenharia de Detecção: Criação de regras personalizadas (.xml) para identificar comportamentos específicos das ferramentas desenvolvidas no módulo ofensivo.
    • Resposta a Incidentes: Configuração de Active Response para contenção automática de hosts comprometidos e produção de relatórios Post-Mortem profissionais.

Analista Responsável: Bruno Eduardo  
Status do Ecossistema: Operacional / Em expansão
Última Auditoria: 27/01/2026