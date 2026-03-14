# Trabalho de Conclusao - ARQUITETURA DE SOFTWARE, CIÊNCIA DE DADOS E CYBERSECURITY

Dupla Certificação da PUC-Campinas e PUC-PR
- https://duplapos.puc-campinas.edu.br/cursos-pos-graduacao/arquitetura-de-software

**Sobre**

Ser capaz de arquitetar diferentes soluções tecnológicas para “resolver” os problemas do mundo é uma missão grandiosa. Desenvolva sua capacidade de desenhar soluções sistêmicas, escolher componentes, direcionar estratégias, fazer migrações e implementar práticas de segurança em um curso inovador.

---


- [Trabalho de Conclusao - ARQUITETURA DE SOFTWARE, CIÊNCIA DE DADOS E CYBERSECURITY](#trabalho-de-conclusao---arquitetura-de-software-ciência-de-dados-e-cybersecurity)
    - [SUMÁRIO EXECUTIVO](#sumário-executivo)
    - [PROBLEMATIZAÇÃO](#problematização)
    - [JUSTIFICATIVA E OBJETIVO GERAL](#justificativa-e-objetivo-geral)
    - [FUNDAMENTAÇÃO TEÓRICA](#fundamentação-teórica)
    - [PERCURSO METODOLÓGICO DA INTERVENÇÃO](#percurso-metodológico-da-intervenção)
    - [RESULTADOS ESPERADOS](#resultados-esperados)
    - [REFERÊNCIAS](#referências)

&nbsp;

---

&nbsp;

**IMPLEMENTAÇÃO DE INTERNAL DEVELOPER PLATFORM PARA GOVERNANÇA EM AMBIENTE ENTERPRISE**

*Eduardo Doval Zenardi Filho*

### SUMÁRIO EXECUTIVO

O presente projeto propõe a arquitetura e implementação de uma Internal Developer Platform (IDP) para uma organização multinacional de grande porte. Do ponto de vista dos usuários – compostos por desenvolvedores de software, engenheiros de dados e profissionais de segurança corporativa – o sistema atua como um portal centralizado de *self-service* para o provisionamento automatizado de infraestrutura e serviços em nuvem. O sistema funcionará em um ambiente de nuvem distribuído globalmente (Microsoft Azure), servindo como a camada de abstração principal entre o código-fonte e a infraestrutura subjacente, como clusters Kubernetes (AKS) e bancos de dados. A principal função da plataforma é reduzir a carga cognitiva dos times de engenharia, oferecendo *templates* de arquitetura padronizados, ou *Golden Paths* (SKELTON; PAIS, 2019), que já contêm as melhores práticas de Infraestrutura como Código (IaC), CI/CD, monitoramento e governança de segurança embutidas.

### PROBLEMATIZAÇÃO

Em ambientes corporativos de escala global, a proliferação de microsserviços e a adoção de múltiplas soluções em nuvem geram uma complexidade operacional insustentável (BEYER *et al.*, 2016). Atualmente, os times de desenvolvimento gastam uma parcela significativa de seu tempo configurando infraestrutura, gerenciando permissões de acesso e lidando com armazenamento de dados distribuídos, em vez de focar na entrega de valor de negócio.

Além da ineficiência e do gargalo operacional, essa falta de padronização arquitetural resulta em graves riscos de Segurança da Informação. Sem uma governança centralizada, aplicações são frequentemente implantadas com configurações de rede inadequadas, falta de rastreabilidade de logs e violações do princípio de privilégio mínimo. A ausência de um fluxo automatizado e validado dificulta a auditoria, a aplicação de *patches* de segurança em escala e a manutenção de uma postura de nuvem resiliente contra ameaças cibernéticas.

### JUSTIFICATIVA E OBJETIVO GERAL

**Justificativa**

Uma Internal Developer Platform (IDP) é, fundamentalmente, uma camada de autoatendimento (*self-service*) construída para abstrair a complexidade operacional da infraestrutura de nuvem (CNCF, 2026). Para uma organização *enterprise*, sua relevância é inestimável: ela atua como o motor central que traduz as intenções dos desenvolvedores em infraestrutura provisionada, permitindo que as equipes foquem na escrita de código de negócio em vez de gerenciar configurações de servidores, redes e permissões.

A implementação dessa plataforma justifica-se pela necessidade crítica de otimizar a entrega de software e garantir a padronização em um cenário corporativo globalizado e de alta complexidade. Atualmente, a fragmentação de ferramentas e a configuração manual geram uma alta carga cognitiva para as equipes, resultando em atrasos no *time-to-market* de novos produtos e na elevação dos custos operacionais.

Para o negócio, o impacto desta intervenção é estratégico e transformador. O IDP centraliza a governança corporativa, assegurando que todas as aplicações sigam padrões rigorosos de arquitetura e segurança desde o início do desenvolvimento (*security by design*). Além de automatizar o provisionamento em nuvem, a plataforma estabelece diretrizes claras para os ambientes de trabalho — padronizando, inclusive, o uso de assistentes de codificação baseados em inteligência artificial. Dessa forma, o IDP mitiga falhas humanas, reduz vulnerabilidades sistêmicas e permite que as equipes foquem exclusivamente na inovação, impulsionando a competitividade da organização.

**Objetivo Geral**

Propor a arquitetura e o modelo de implementação de uma Internal Developer Platform (IDP) escalável e segura para o contexto de uma corporação multinacional, visando automatizar o provisionamento de infraestrutura *on demand*, centralizar a governança e reduzir a carga cognitiva dos times, garantindo segurança na entrega contínua de software.

### FUNDAMENTAÇÃO TEÓRICA

A construção de um IDP de nível *enterprise* requer a orquestração de tecnologias nativas de nuvem e ferramentas consolidadas para garantir escalabilidade, segurança e resiliência (CNCF, 2026). A arquitetura proposta fundamenta-se nos seguintes pilares:

**Portal do Desenvolvedor, Catálogo de Serviços e *Golden Paths***

O Backstage (SPOTIFY, 2026) atua como a interface central da plataforma. Ele unifica o catálogo de software corporativo e fornece os *Golden Paths*. Um *Golden Path* (caminho pavimentado) é um conjunto de práticas, *templates* e ferramentas pré-configuradas e suportadas oficialmente pela organização para o desenvolvimento de software (SKELTON; PAIS, 2019). Sua importância reside em reduzir a fadiga de decisão técnica. Para estabelecer esses caminhos, a engenharia de plataforma deve tratar o IDP como um produto (*Platform as a Product*), colaborando continuamente com os desenvolvedores para criar *templates* que resolvam dores reais.

**Nuvem Enterprise e Orquestração de Infraestrutura**

O Microsoft Azure servirá como provedor base, com o AKS (*Azure Kubernetes Service*) como motor de orquestração de contêineres (MICROSOFT, 2026a). O Crossplane é adotado como o motor de Infraestrutura como Código (IaC). Ao invés de fluxos imperativos externos, o Crossplane estende a API do Kubernetes, permitindo provisionar recursos complexos do Azure nativamente (CROSSPLANE, 2026).

**Automação, GitOps e Governança de IA**

O Azure Pipelines atua como motor de CI, compilando o código, rodando testes automatizados, escaneando vulnerabilidades e publicando as imagens no *Azure Container Registry* (ACR). O ArgoCD atua como motor de CD (GitOps), garantindo que o estado da infraestrutura no AKS seja idêntico ao declarado nos repositórios. A automação também injeta nativamente arquivos de instrução (como o padrão `AGENT.md`) na raiz de cada projeto, governando o uso de IA local pelos engenheiros.

**Ciclo DevSecOps e Segurança (Cybersecurity)**

A adoção do IDP e dos *Golden Paths* é o alicerce para materializar o ciclo DevSecOps. Ao invés de a segurança ser um gargalo no final do desenvolvimento, ela é injetada na origem (*Shift-Left*). O uso obrigatório de imagens de contêiner *distroless* da Chainguard é um exemplo prático dessa governança: os projetos já nascem livres de vulnerabilidades conhecidas e sem *shells* (CHAINGUARD, 2026). Complementarmente, o Kyverno atua como motor de *Policy as Code*, bloqueando implantações fora do padrão (KYVERNO, 2026), e o *Azure Key Vault* gerencia segredos de forma segura via *CSI Driver* (MICROSOFT, 2026b).

### PERCURSO METODOLÓGICO DA INTERVENÇÃO

**Nota Metodológica sobre o uso de Inteligência Artificial**

Em conformidade com as diretrizes e boas práticas acadêmicas atuais, declara-se que a elaboração deste projeto contou com o apoio da ferramenta de inteligência artificial generativa Google Gemini. A IA foi utilizada exclusivamente como assistente para estruturação do escopo, *brainstorming* de soluções arquiteturais e organização textual das ideias. A autoria, as decisões arquiteturais da *stack* tecnológica (Azure, Crossplane, Kyverno), a curadoria do conteúdo e a validação teórica são de inteira responsabilidade do autor deste documento.

**Arquitetura Lógica da Solução**

Para tornar o IDP confiável e resiliente a mudanças, a arquitetura foi desenhada com forte separação de responsabilidades (SKELTON; PAIS, 2019). O sistema é modular o suficiente para que cada pedaço de código tenha um escopo único, garantindo alta coesão e baixo acoplamento.

A plataforma será dividida em quatro camadas principais:

![arquitetura](./arquitetura.png)

1. **Camada de Interação (*Developer Portal*):** Interface unificada onde os desenvolvedores solicitam o provisionamento de recursos por meio de *Golden Paths*.
2. **Camada de Automação e CI/CD:** Responsável pela execução (pipelines no Azure Pipelines e sincronização via ArgoCD).
3. **Camada de Orquestração (*Control Plane*):** A decisão de hospedar o IDP de forma nativa no Kubernetes (AKS) garante escalabilidade ímpar, adicionando automaticamente novos *pods* e réplicas dos serviços nos horários de pico comercial (MICROSOFT, 2026a). Recebe as requisições via estrutura RESTful e traduz em comandos baseados em manifestos do Crossplane.
4. **Camada de Infraestrutura e Nuvem (*On Demand*):** Onde os recursos reais são provisionados dinamicamente via código.

**Análise e Mitigação de Riscos**

* **Risco 1: Rejeição dos desenvolvedores.** *Mitigação:* Tratar o IDP como um produto, envolvendo os usuários finais no desenho dos *templates* para garantir a redução do tempo de *setup* local.
* **Risco 2: Falha na Padronização de Imagens Seguras.** Utiliza-se o Kyverno para garantir que o princípio de *Security by Default* seja respeitado (KYVERNO, 2026). Abaixo, o manifesto declarativo utilizado para bloquear implantações que não utilizem as imagens *distroless* padronizadas da Chainguard:

```yaml
apiVersion: kyverno.io/v1
kind: ClusterPolicy
metadata:
  name: require-chainguard-distroless
  annotations:
    policies.kyverno.io/title: "Exigir Imagens Distroless (Chainguard)"
    policies.kyverno.io/category: "Pod Security / Supply Chain"
spec:
  validationFailureAction: Enforce
  background: true
  rules:
    - name: check-image-registry
      match:
        any:
        - resources:
            kinds:
              - Pod
      validate:
        message: "Deploy bloqueado pelo IDP: Apenas imagens distroless aprovadas (cgr.dev/chainguard/*) são permitidas."
        pattern:
          spec:
            containers:
              - image: "cgr.dev/chainguard/*"
            =(initContainers):
              - image: "cgr.dev/chainguard/*"

```

A diretiva `Enforce` impede ativamente que a API do Kubernetes aceite a criação de *Pods* fora do padrão corporativo.

### RESULTADOS ESPERADOS

A implementação do IDP deverá promover uma transformação na cultura de engenharia, na postura de segurança e na eficiência financeira da organização. Espera-se alcançar os seguintes resultados:

* **Métricas de Aceleração de Entrega:** Com a adoção dos *Golden Paths*, estima-se um ganho operacional sistêmico. Projeta-se que a implementação resulte em uma aceleração de até 30% no *lead time* para a entrega de novos projetos, eliminando as esperas tradicionais associadas à abertura de chamados para operações (BEYER *et al.*, 2016).
* **Catálogo Unificado e Economia Financeira:** O catálogo fornecerá uma visibilidade arquitetural centralizada, evitando que times desenvolvam o mesmo software e compitam internamente. A mitigação desse retrabalho traduz-se em economia expressiva de orçamento de TI.
* **Governança Financeira (FinOps):** Através do tagueamento automatizado, a empresa terá uma noção exata de seus gastos (*cloud spend* e *workforce*), permitindo ajustes proativos (BEYER *et al.*, 2016).
* **Maximização da Segurança com Imagens *Distroless*:** A padronização das esteiras de CI/CD garantirá aplicações *secure by default* (CHAINGUARD, 2026). Espera-se uma redução drástica na superfície de ataque e otimização do tráfego de rede.

### REFERÊNCIAS

BEYER, B. *et al*. **Site Reliability Engineering**: How Google Runs Production Systems. Sebastopol: O'Reilly Media, 2016.

CHAINGUARD. **What are Distroless Images?**: Securing the Software Supply Chain. [S. l.]: Chainguard, 2026. Disponível em: [https://www.chainguard.dev/unchained/what-are-distroless-images](https://www.chainguard.dev/unchained/what-are-distroless-images). Acesso em: 14 mar. 2026.

CNCF. **Cloud Native Landscape**. San Francisco: Cloud Native Computing Foundation, 2026. Disponível em: [https://landscape.cncf.io/](https://landscape.cncf.io/). Acesso em: 14 mar. 2026.

CROSSPLANE. **The Cloud Native Control Plane**. [S. l.]: Crossplane, 2026. Disponível em: [https://crossplane.io/docs/](https://crossplane.io/docs/). Acesso em: 14 mar. 2026.

KYVERNO. **Kubernetes Native Policy Management**. [S. l.]: Kyverno, 2026. Disponível em: [https://kyverno.io/docs/](https://kyverno.io/docs/). Acesso em: 14 mar. 2026.

MICROSOFT. **Arquitetura do Azure Kubernetes Service (AKS)**. Redmond: Microsoft Learn, 2026a. Disponível em: [https://learn.microsoft.com/pt-br/azure/aks/concepts-clusters-workloads](https://learn.microsoft.com/pt-br/azure/aks/concepts-clusters-workloads). Acesso em: 14 mar. 2026.

MICROSOFT. **Integração do Azure Key Vault com o AKS via Secrets Store CSI Driver**. Redmond: Microsoft Learn, 2026b. Disponível em: [https://learn.microsoft.com/pt-br/azure/aks/csi-secrets-store-driver](https://learn.microsoft.com/pt-br/azure/aks/csi-secrets-store-driver). Acesso em: 14 mar. 2026.

SKELTON, M.; PAIS, M. **Team Topologies**: Organizing Business and Technology Teams for Fast Flow. Portland: IT Revolution Press, 2019.

SPOTIFY. **Backstage**: An open platform for building developer portals. Estocolmo: Spotify, 2026. Disponível em: [https://backstage.io/docs/overview/what-is-backstage](https://backstage.io/docs/overview/what-is-backstage). Acesso em: 14 mar. 2026.
 

