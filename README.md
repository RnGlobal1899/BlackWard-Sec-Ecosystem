# **🏗️ BlackWard Security LAB: Architecture Overview 🛡️**

Bem-vindo ao centro de documentação técnica do BlackWard Security LAB. Este projeto consiste na implementação de uma infraestrutura corporativa simulada, distribuída em um ambiente Multi-Cloud Híbrido (Google Cloud Platform, Microsoft Azure e On-Premise). O laboratório foi arquitetado para superar as limitações severas de hardware local (Athlon 3000G e 8GB de RAM), movendo cargas de trabalho pesadas (SIEM, Gestão) para a nuvem através de uma estratégia de Cloud Offloading e interconexão de baixa latência.

O laboratório é rigorosamente dividido em quatro módulos interdependentes, permitindo uma abordagem de aprendizado em 360 graus em Cibersegurança, Redes e Nuvem.

## **🛠️ Módulo 1: Identidade e Infraestrutura de Gestão**
**Objetivo:** Estabelecer a base gerencial estável na GCP e a autoridade de identidade do ecossistema.

    • Âncora de Identidade Local (On-Premises): O Windows Server 2022 (AD DS) virtualizado localmente atua como o controlador de domínio raiz, gerenciando usuários e políticas (GPO) com consumo mínimo de recursos.
    • Base Gerencial Central (GCP): Utilização da instância srv-gcp-mgmt-01 (e2-standard-4, 16GB RAM) na Google Cloud para hospedar o stack de gestão via Docker: MeshCentral (acesso remoto a todos os nós), GLPI (inventário de ativos) e Portainer.
    • Identidade Híbrida (Azure): Sincronização do diretório local com o Microsoft Entra ID através do Azure for Students, integrando a gestão de usuários com a nuvem.
    • Gestão de Endpoints: Administração centralizada de servidores Windows na Azure e Workstations locais através do túnel criptografado, eliminando a necessidade de VPNs legadas ou exposição de portas RDP/SSH.

## **🌐 Módulo 2: Redes Híbridas e Conectividade (Networking)**                                                                                                                               
**Objetivo:** Garantir a conectividade segura, a segmentação do ambiente e a interoperabilidade entre provedores distintos através de arquiteturas em camadas e SD-WAN.

    • Arquitetura VCN (Google Cloud): Configuração de rede na região us-east1 com regras de firewall restritivas (bloqueio total de SSH público), permitindo acesso apenas via IAP (Identity-Aware Proxy) ou malha interna.
    • Rede Mesh (Tailscale SD-WAN): Implementação de uma malha Zero Trust que interconecta todas as nuvens e o ambiente local. A comunicação flui através de túneis criptografados (WireGuard) utilizando IPs fixos e imutáveis (100.x.y.z).
    • Engenharia de Tráfego e DNS: Uso do MagicDNS para resolução de nomes global (ex: ping srv-rh-azure) e configuração de ACLs (Access Control Lists) para segmentação lógica (ex: impedir que o setor de Vendas acesse o segmento de Gestão na GCP).
    • Segurança de Perímetro: Otimização de regras de firewall e NAT para evitar falhas de conectividade e garantir o tráfego legítimo entre os setores simulados (RH, Vendas e TI).
    • Interoperabilidade: O ambiente local atua como um "Spoke" que consome serviços hospedados no "Hub" da Google Cloud com latência otimizada.

obs: A topologia de rede está no caminho /Infrastructure/Network.

## **🛡️ Módulo 3: SOC e Monitoramento Avançado (Blue Team)**
**Objetivo:** Centralizar a inteligência de segurança na nuvem, utilizando hardware de alta performance para detecção de ameaças.

    • Elastic Stack SIEM (GCP): O coração do SOC reside na instância dedicada srv-gcp-soc-01 (16GB RAM, SSD Persistente). Ela processa logs de todo o ecossistema híbrido utilizando Elasticsearch e Kibana Dockerizados.
    • Telemetria Estendida (XDR):
        • Elastic Agent + Sysmon: Implantados nos Servidores de Arquivos da Azure e no Controlador de Domínio Local para enriquecimento de logs (Event IDs 1, 3, 11, etc.).
        • Honeyfiles: Criação de arquivos-armadilha ("folha_pagamento.xlsx") nos servidores da Azure para detecção proativa de acesso não autorizado.

## **☣️ Módulo 4: Red Team e Operações Ofensivas**
**Objetivo:** Simular ataques direcionados à infraestrutura Microsoft (Windows Server e AD).

    • Infraestrutura de Ataque Flexível (C2): A hospedagem dos frameworks de Comando e Controle (Sliver C2, Havoc, Gophish) é descentralizada e resiliente. Prevê-se a utilização futura da Oracle Cloud (Free Tier ARM) para aproveitar o poder computacional gratuito ou instâncias na DigitalOcean (via GitHub Student Pack), garantindo o isolamento total entre a infraestrutura de ataque e a de defesa.
    • Desenvolvimento de Malware: Desenvolvimento de Malware: Criação de artefatos personalizados em C++ utilizando WinAPI (VirtualAlloc, CreateThread) para injetar payloads em memória, focando na evasão de assinaturas estáticas.

**Analista Responsável:** Bruno Eduardo  
**Status do Ecossistema:** Operacional (Migrado para GCP/Híbrido)                                                                                                            
**Última Atualização:** 15/02/2026

