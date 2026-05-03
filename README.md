# ☁️ AWS Cloud Practitioner CLF-C02 — Guia de Estudos

> Resumo visual e comparativo dos principais serviços AWS para o exame **CLF-C02**.  
> Organizado por domínio, com foco em: o que é, para que serve, quando usar, integrações e comparações.

---

## 📌 Navegação Rápida

| Domínio | Serviços |
|---|---|
| [🤖 AI / ML](#-ai--ml) | Lex, Textract, Polly, Rekognition, Comprehend, SageMaker |
| [📊 Analytics](#-analytics) | QuickSight, Athena, Redshift, Glue, EMR |
| [🔗 Application Integration](#-application-integration) | Step Functions |
| [🧭 CAF — Cloud Adoption Framework](#-caf--cloud-adoption-framework) | Business, People, Governance, Platform, Security, Operations |
| [💻 Compute](#-compute) | EC2, Auto Scaling, Lambda, Beanstalk, ECS, EKS, Fargate, Spot, Hosts |
| [💰 Cost & Pricing](#-cost--pricing) | Budgets, Cost Explorer, Savings Plans, Reserved, On-Demand, CUR, Calculator, Compute Optimizer |
| [🗄️ Database](#️-database) | RDS, DynamoDB, Aurora |
| [🛠️ DevTools / CI-CD](#️-devtools--ci-cd) | CodeCommit, CodeBuild, CodeDeploy, CodePipeline, CLI |
| [🌐 Networking & Content Delivery](#-networking--content-delivery) | VPC, Subnets, Route Tables, IGW, NAT, SG, NACL, ELB, CloudFront, Route53, Peering, Transit GW, Direct Connect, VPN |
| [🏛️ Governance](#️-governance) | Organizations, Control Tower, Config, Marketplace, Tags |
| [⚡ Integration & Messaging](#-integration--messaging) | EventBridge, SQS, SNS, API Gateway |
| [📡 IoT](#-iot) | IoT Core, IoT Greengrass |
| [🔧 Management](#-management) | Systems Manager, CloudFormation, AWS Health |
| [🚚 Migration](#-migration) | Snowball, DMS, Migration Hub, Transfer Family, DataSync, MGN |
| [📈 Monitoring & Observabilidade](#-monitoring--observabilidade) | CloudWatch, CloudTrail, Trusted Advisor, X-Ray |
| [🔒 Security & Identity](#-security--identity) | IAM, WAF, Shield, Artifact, Inspector, GuardDuty, Detective, Secrets Manager, KMS, Macie, Security Hub |
| [💾 Storage](#-storage) | S3 (e classes), EBS, EFS, ECR, Storage Gateway, FSx, Outposts |
| [🎓 Support Plans](#-support-plans) | Basic, Developer, Business, Enterprise |
| [🏗️ Well-Architected Framework](#️-well-architected-framework) | 6 Pilares |

---

## 🤖 AI / ML

| Serviço | O que é | Para que serve | Quando usar | Integra com | Comparação | Infos adicionais |
|---|---|---|---|---|---|---|
| **Lex** | Serviço de criação de chatbots (ex: Alexa) | Construir interfaces de conversa com voz e texto | Chatbot inteligente integrado a apps | Lambda, Connect, Polly | vs **Polly**: Lex = chatbot, Polly = voz | Usa NLP para entender intenções; suporta contact centers |
| **Textract** | OCR inteligente | Extrair texto e dados estruturados de documentos | Digitalizar PDFs, formulários, contratos | S3, Comprehend, Lambda | vs OCR tradicional: Textract entende tabelas e formulários | Reconhece texto impresso e manuscrito |
| **Polly** | Conversão texto-para-fala | Transformar texto em voz natural | Narrar conteúdo ou criar assistentes de voz | Lex, Connect, S3 | vs **Lex**: Polly = voz, Lex = chatbot | Múltiplos idiomas e vozes; ideal para apps acessíveis |
| **Rekognition** | Análise de imagens e vídeos | Detectar objetos, rostos, texto e atividades em escala | Reconhecimento visual em milhões de imagens | S3, Lambda, Kinesis Video Streams | vs **Textract**: Rekognition = imagens, Textract = documentos | Detecção de emoções, moderação de conteúdo, reconhecimento facial |
| **Comprehend** | NLP gerenciado | Extrair insights de texto (sentimento, entidades, tópicos) | Análise de linguagem natural | S3, Textract, Lambda | vs **Lex**: Comprehend = análise de texto, Lex = interação | Múltiplos idiomas; útil para análise de sentimentos e classificação de documentos |
| **SageMaker** | Plataforma gerenciada de ML | Construir, treinar e implantar modelos de ML em escala | Acelerar desenvolvimento de ML sem gerenciar infraestrutura | S3, EC2, ECR, IAM, CloudWatch | vs **EC2**: SageMaker = ML gerenciado, EC2 = infraestrutura manual | Suporta notebooks Jupyter, pipelines de ML, treinamento distribuído e endpoints para inferência |

---

## 📊 Analytics

> **Fluxo típico:** Glue → Athena → QuickSight

| Serviço | O que é | Para que serve | Quando usar | Integra com | Comparação | Infos adicionais |
|---|---|---|---|---|---|---|
| **QuickSight** | BI (Business Intelligence) | Criar dashboards interativos e visualizações | Analisar dados e compartilhar insights rapidamente | S3, Redshift, RDS, Athena, Aurora | vs **Athena**: QuickSight = visualização, Athena = consulta SQL | Serverless; cobra por sessão; suporta ML insights |
| **Athena** | Serviço de consulta interativa (SQL) | Executar queries SQL diretamente em dados no S3 | Analisar dados S3 sem mover para banco | S3, Glue, QuickSight | vs **Redshift**: Athena é serverless, Redshift é DW dedicado | Serverless; paga por consulta; ideal para análise ad-hoc |
| **Redshift** | Data warehouse gerenciado | Analisar grandes volumes de dados estruturados | BI, relatórios e queries complexas | S3, Glue, QuickSight, Kinesis | vs **Athena**: Redshift = DW dedicado, Athena = serverless p/ S3 | Base colunar, otimizado para analytics; paga por nó |
| **Glue** | ETL serverless | Descobrir, preparar e transformar dados para análise | Catalogar e organizar dados antes de consultar | S3, Athena, Redshift, QuickSight | vs **EMR**: Glue = serverless ETL, EMR = cluster Hadoop/Spark | Cria catálogo de dados; suporta jobs em Python/Scala |
| **EMR** | Plataforma gerenciada de Big Data | Processar grandes volumes usando frameworks open-source | Rodar Hadoop, Spark, Hive, Presto em escala | S3, EC2, DynamoDB, Redshift, Glue | vs **Redshift**: EMR = processamento Big Data, Redshift = DW | Escala automática; paga por EC2/S3; ideal para ETL e ML massivo |

---

## 🔗 Application Integration

| Serviço | O que é | Para que serve | Quando usar | Integra com | Comparação | Infos adicionais |
|---|---|---|---|---|---|---|
| **Step Functions** | Orquestrador de workflows serverless | Coordenar múltiplos serviços AWS em fluxos de trabalho visuais | Automatizar processos complexos com estados e dependências | Lambda, ECS, SQS, DynamoDB, Glue | vs **Lambda**: Step Functions = orquestração, Lambda = execução | Coordena centenas de batches; fluxo visual de estados |

---

## 🧭 CAF — Cloud Adoption Framework

| Perspectiva | Foco | Para que serve | Comparação | Detalhes |
|---|---|---|---|---|
| **Business** | Estratégia e financeiro | Alinhar nuvem com objetivos e ROI da empresa | vs **People**: Business = estratégia, People = cultura | Impacto financeiro da adoção; KPIs e benefícios de negócio |
| **People** | Cultura e pessoas | Preparar equipes para adoção da nuvem | vs **Business**: People = cultura, Business = estratégia | Gestão de mudança, capacitação, papéis e responsabilidades |
| **Governance** | Políticas e compliance | Definir políticas, gestão de riscos e conformidade | vs **Security**: Governance = políticas, Security = proteção técnica | Inventário, gestão de portfólio, conformidade regulatória |
| **Platform** | Arquitetura e infraestrutura | Planejar e construir a arquitetura cloud | vs **Operations**: Platform = arquitetura, Operations = execução | CI/CD, rede, compute, storage; arquitetos e engenheiros de plataforma |
| **Security** | Proteção técnica | Proteger dados e cargas de trabalho | vs **Governance**: Security = proteção técnica, Governance = políticas | Identidade, criptografia, resposta a incidentes |
| **Operations** | Operações e monitoramento | Gerenciar e monitorar cargas de trabalho na nuvem | vs **Platform**: Operations = execução, Platform = design | Monitoramento, gestão de incidentes, desempenho e capacidade |

---

## 💻 Compute

| Serviço | O que é | Para que serve | Quando usar | Integra com | Comparação | Infos adicionais |
|---|---|---|---|---|---|---|
| **EC2** | Máquinas virtuais na nuvem | Executar aplicações em instâncias configuráveis | Controle total sobre servidores e SO | EBS, VPC, ELB, Auto Scaling, CloudWatch | vs **Lambda/Beanstalk**: EC2 = controle total | Tipos otimizados para memória, CPU, GPU; suporta Auto Scaling |
| **Auto Scaling** | Escala automática de instâncias | Aumentar/diminuir número de instâncias conforme demanda | Carga variável | EC2, ELB | vs **ELB**: ELB distribui, Auto Scaling adiciona/remove | Garante recursos certos para variações de carga |
| **Lambda** | Computação serverless | Executar código em resposta a eventos sem gerenciar servidores | Funções sob demanda, pagando só pelo uso | S3, DynamoDB, API Gateway, CloudWatch | vs **EC2**: Lambda = serverless, EC2 = VM | Python, Node.js, Java etc.; cobra por invocação e tempo |
| **Elastic Beanstalk** | PaaS gerenciada | Implantar e escalar aplicações sem gerenciar infra | Apps sem se preocupar com servidores | EC2, S3, RDS, Auto Scaling | vs **EC2**: Beanstalk = gerenciado, EC2 = manual | Java, .NET, Node.js, Python, PHP, Go, Ruby |
| **ECS** | Orquestração de containers (Docker) | Gerenciar e escalar containers | Containers sem instalar Kubernetes | EC2, Fargate, ECR | vs **EKS**: ECS = orquestração AWS, EKS = Kubernetes | Simples e integrado; voltado para Docker |
| **EKS** | Kubernetes gerenciado pela AWS | Rodar aplicações em Kubernetes | Compatibilidade com Kubernetes padrão | EC2, Fargate, ECR | vs **ECS**: EKS = Kubernetes upstream, mais flexível | Maior complexidade; mais customizável |
| **Fargate** | Execução serverless de containers | Rodar containers sem gerenciar servidores | Simplicidade, sem gerenciar EC2 | ECS, EKS, ECR | vs **EC2**: Fargate = serverless | Paga por vCPU/memória; sem gestão de instâncias |
| **Spot Instance** | EC2 com desconto usando capacidade ociosa | Usar capacidade ociosa AWS com custo baixo | Cargas tolerantes a interrupção | EC2, Auto Scaling | vs **On-Demand**: Spot é mais barato mas pode ser encerrado | Até 90% mais barato; pode ser interrompida pela AWS |
| **Host Dedicado** | Servidor físico exclusivo | EC2 em hardware dedicado com controle físico | Compliance ou licenciamento específico | EC2, IAM | vs **Instância Dedicada**: Host = controle físico, Instância = lógico | Licenças Oracle, Windows Server; por soquete/núcleo |
| **Instância Dedicada** | EC2 em hardware isolado | Isolamento físico sem controle do host | Isolamento por compliance | EC2 | vs **Host Dedicado**: Instância = isolamento lógico | Mais simples; sem visibilidade do host físico |

---

## 💰 Cost & Pricing

| Serviço | O que é | Para que serve | Quando usar | Comparação | Infos adicionais |
|---|---|---|---|---|---|
| **Budgets** | Orçamento com alertas automáticos | Definir limites e receber alertas de gastos | Controle proativo de custos | vs **Cost Explorer**: Budgets = limite/alerta, Explorer = análise | Envia alertas via SNS ao atingir limites predefinidos |
| **Cost Explorer** | Análise de custos e tendências | Visualizar, entender e gerenciar gastos | Monitorar custos e identificar tendências | vs **Budgets**: Cost Explorer = análise detalhada | Relatórios customizados; histórico e projeções |
| **Savings Plans** | Desconto por compromisso de uso | Reduzir custos em workloads previsíveis | Workloads estáveis | vs **Reserved**: Savings Plans = mais flexível | Compromisso de 1 ou 3 anos; Compute SP (flexível) e EC2 SP (restrito) |
| **On-Demand Instance** | Preço sob demanda sem compromisso | Pagar apenas pelo uso real | Workloads variáveis, testes | vs **Reserved/Savings Plans**: mais caro, sem compromisso | Maior custo unitário; máxima flexibilidade |
| **Reserved Instance** | Reserva com desconto | Reduzir custos em workloads fixos | Workloads estáveis e previsíveis | vs **On-Demand**: menor custo, maior compromisso | Compromisso de 1 ou 3 anos; menos flexível |
| **Cost and Usage Report (CUR)** | Relatório detalhado de uso e custos | Exportar dados granulares de consumo | Análise detalhada (hora/dia/mês), auditoria | vs **Cost Explorer**: CUR é mais detalhado | Exporta para S3; analisável com Athena/QuickSight |
| **Pricing Calculator** | Simulador de custos | Estimar custo antes de criar recursos | Prever gastos antes de provisionar | vs **Budgets**: Calculator = pré, Budgets = pós | Ferramenta web gratuita; baseada em configuração |
| **Compute Optimizer** | Recomendações de instâncias via ML | Sugerir instâncias mais adequadas ao uso real | Otimizar custo e performance | vs **Trusted Advisor**: Optimizer = recomendações detalhadas | Analisa EC2, EBS, ASG e Lambda; usa machine learning |

---

## 🗄️ Database

| Serviço | O que é | Para que serve | Quando usar | Comparação | Infos adicionais |
|---|---|---|---|---|---|
| **RDS** | Banco relacional gerenciado | MySQL, PostgreSQL, MariaDB, Aurora | Dados estruturados, instância reservada | vs **DynamoDB**: RDS = relacional/SQL | OLTP; gerenciado pela AWS; você cuida de acessos e dados |
| **DynamoDB** | NoSQL de alta escala | Alta escala com baixa latência | Milhões de requisições com baixa latência | vs **RDS**: DynamoDB = NoSQL, RDS = relacional | Chave-valor; totalmente gerenciado; suporta JSON |
| **Aurora** | Banco relacional de alta performance | Workloads críticos com MySQL/PostgreSQL | Alta performance e escalabilidade | vs **RDS**: Aurora é mais rápido e escalável | 5x mais rápido que MySQL; storage distribuído e auto-healing; replicação global |

---

## 🛠️ DevTools / CI-CD

| Serviço | O que é | Para que serve | Quando usar | Comparação | Infos adicionais |
|---|---|---|---|---|---|
| **CodeCommit** | Repositório Git gerenciado | Armazenar e versionar código | Repositório privado e seguro na AWS | vs **GitHub**: CodeCommit = nativo AWS | Criptografia automática; integração IAM |
| **CodeBuild** | Serviço de build serverless | Compilar código, rodar testes e gerar artefatos | CI serverless | vs **Jenkins**: CodeBuild = serverless | Paga por minuto de build; múltiplos ambientes |
| **CodeDeploy** | Deploy automatizado | Fazer deploy em EC2, Lambda ou on-premises | Automação de implantação | vs **Elastic Beanstalk**: CodeDeploy é mais granular | Suporta blue/green e rolling updates; reduz downtime |
| **CodePipeline** | Orquestrador de CI/CD | Automatizar fluxo de build, teste e deploy | Pipeline completo end-to-end | vs **Jenkins**: CodePipeline = nativo AWS | Define estágios e ações; totalmente gerenciado |
| **AWS CLI** | Interface de linha de comando | Executar comandos para gerenciar serviços AWS | Automação e scripts | vs **Console**: CLI = scriptável, Console = visual | Acesso programático; ideal para DevOps |

---

## 🌐 Networking & Content Delivery

### Conceitos de VPC

| Serviço | O que é | Para que serve | Comparação | Infos adicionais |
|---|---|---|---|---|
| **VPC** | Rede virtual isolada | Criar ambiente de rede privado e seguro | vs **Subnet**: VPC = rede inteira, Subnet = parte | CIDR, subnets, gateways e regras de segurança |
| **Subnet Pública** | Subnet com acesso à internet | Hospedar recursos acessíveis externamente | vs **Subnet Privada**: Pública = acesso direto | Route table aponta para Internet Gateway; servidores web |
| **Subnet Privada** | Subnet sem acesso direto à internet | Hospedar recursos internos e protegidos | vs **Subnet Pública**: Privada = sem acesso direto | Route table aponta para NAT Gateway; bancos de dados |
| **Route Table** | Regras de roteamento | Define como tráfego é direcionado na VPC | vs **Security Groups**: Route Table = roteamento, SG = firewall | Cada subnet deve ter uma route table |
| **Internet Gateway (IGW)** | Conecta VPC à internet | Comunicação entre VPC e internet pública | vs **NAT Gateway**: IGW = entrada/saída pública | Associado à VPC; usado com route tables públicas |
| **NAT Gateway** | Saída segura para instâncias privadas | Instâncias privadas acessam internet sem exposição | vs **IGW**: NAT = saída privada, IGW = entrada/saída pública | Gerenciado e altamente disponível; updates e downloads |
| **Security Group** | Firewall por instância (stateful) | Controlar tráfego de entrada/saída por instância | vs **NACL**: SG = stateful, NACL = stateless | Resposta permitida automaticamente; somente regras de allow |
| **NACL** | Firewall por subnet (stateless) | Controlar tráfego em nível de subnet | vs **Security Group**: NACL = stateless, SG = stateful | Suporta allow e deny; respostas não são automáticas |

### Conectividade e Distribuição

| Serviço | O que é | Para que serve | Quando usar | Comparação | Infos adicionais |
|---|---|---|---|---|---|
| **CloudFront** | CDN (Rede de distribuição de conteúdo) | Entregar conteúdo com baixa latência globalmente | Distribuir conteúdo de forma rápida e segura | vs **S3**: CloudFront = distribuição, S3 = armazenamento | Mais de 400 edge locations; cache, HTTPS |
| **Route 53** | DNS gerenciado | Roteamento de tráfego e resolução de nomes | Alta disponibilidade | vs **ELB**: Route53 = resolve nomes, ELB = distribui tráfego | Registrar domínios; rotear para endpoints |
| **ELB (Elastic Load Balancer)** | Balanceador de carga | Distribuir tráfego entre múltiplas instâncias | Alta disponibilidade e escalabilidade | vs **Route53**: ELB = distribui tráfego | ALB (camada 7), NLB (camada 4), Gateway LB |
| **VPC Peering** | Conexão direta entre 2 VPCs | Comunicação privada entre VPCs | Ambientes simples, conexões 1:1 | vs **Transit GW**: Peering = par a par, TGW = hub central | A↔B, B↔C, mas A não fala com C automaticamente |
| **Transit Gateway** | Hub central de rede | Conectar múltiplas VPCs e redes on-premises | Conexões em larga escala | vs **VPC Peering**: TGW escala melhor e centraliza | Suporta milhares de VPCs |
| **Direct Connect** | Conexão física dedicada | Link privado entre data center e AWS | Alta largura de banda e baixa latência | vs **VPN**: Direct Connect = dedicado, VPN = internet | Mais estável; ideal para workloads críticos |
| **VPN / Site-to-Site VPN** | Conexão criptografada via internet | Conectar rede on-premises à AWS com segurança | Conexão rápida sem link dedicado | vs **Direct Connect**: VPN = internet, DC = dedicado | Mais barato e rápido de configurar; IPsec |
| **Points of Presence (PoP)** | Local físico de entrada da rede AWS | Aproximar conteúdo e serviços do usuário | Baixa latência e melhor experiência global | vs **Data Center**: PoP = edge, DC = processamento | Mais de 400 PoPs; usados em CDN e DNS |

---

## 🏛️ Governance

| Serviço | O que é | Para que serve | Quando usar | Comparação | Infos adicionais |
|---|---|---|---|---|---|
| **AWS Organizations** | Gerenciamento de múltiplas contas | Agrupar e administrar contas com faturamento consolidado | Multi-conta com políticas centralizadas | vs **Control Tower**: Organizations = estrutura, CT = automação | SCPs (Service Control Policies); Organizational Units (OU) |
| **Control Tower** | Governança multi-conta automatizada | Configurar ambientes multi-conta com boas práticas | Landing zone segura e padronizada | vs **Organizations**: Control Tower = automação, Org = estrutura | Guardrails; provisiona contas automaticamente |
| **AWS Config** | Auditoria e conformidade de recursos | Monitorar e avaliar configurações de recursos | Compliance, auditoria, histórico de mudanças | vs **CloudTrail**: Config = estado atual, CloudTrail = eventos | Não cria recursos; apenas verifica e registra configurações |
| **Marketplace** | Catálogo digital de software | Comprar e implantar soluções de terceiros | Software pronto e validado | vs criar manualmente: Marketplace = curado | Licenciamento simplificado; billing integrado |
| **Tags** | Metadados em pares chave-valor | Organizar, identificar e classificar recursos | Controle de custos, organização, políticas | vs **Resource Groups**: Tags = metadados | Usados para billing, automação, segurança e compliance |

---

## ⚡ Integration & Messaging

| Serviço | O que é | Para que serve | Quando usar | Comparação | Infos adicionais |
|---|---|---|---|---|---|
| **EventBridge** | Barramento de eventos serverless | Conectar aplicações via eventos de forma desacoplada | Reagir a eventos de serviços AWS, SaaS ou apps próprias | vs **SNS/SQS**: EventBridge = roteamento inteligente | Regras avançadas; substitui CloudWatch Events |
| **SQS** | Fila de mensagens | Desacoplar componentes garantindo entrega de mensagens | Garantir entrega entre componentes | vs **SNS**: SQS = fila, SNS = broadcast | Filas padrão (alta taxa) e FIFO (ordem garantida) |
| **SNS** | Publish/Subscribe serverless | Broadcast de notificações para múltiplos destinos | Notificar múltiplos assinantes simultaneamente | vs **SQS**: SNS = fan-out, SQS = fila | HTTP, email, SMS, Lambda, SQS |
| **API Gateway** | Criação e gerenciamento de APIs | Criar, publicar e gerenciar APIs REST/HTTP/WebSocket | Expor serviços de backend de forma segura | vs **ELB**: API Gateway = APIs, ALB = tráfego web | Autenticação, throttling, caching; ideal para serverless |

---

## 📡 IoT

| Serviço | O que é | Para que serve | Quando usar | Comparação | Infos adicionais |
|---|---|---|---|---|---|
| **IoT Core** | Plataforma gerenciada para dispositivos IoT | Conectar e gerenciar dispositivos IoT em escala | Ingestão segura de dados de dispositivos | vs **Greengrass**: IoT Core = nuvem, Greengrass = edge | MQTT, HTTP, WebSockets; autenticação por certificados |
| **IoT Greengrass** | IoT Core para edge computing | Executar aplicações IoT localmente em dispositivos | Processamento local sem depender da nuvem | vs **IoT Core**: Greengrass = edge, Core = nuvem | Roda Lambda offline; sincroniza dados depois |

---

## 🔧 Management

| Serviço | O que é | Para que serve | Quando usar | Comparação | Infos adicionais |
|---|---|---|---|---|---|
| **Systems Manager** | Gerenciamento centralizado de recursos | Administrar e automatizar EC2 e outros recursos | Gerenciar múltiplas instâncias centralizadamente | vs **CloudWatch**: SSM = gestão, CloudWatch = monitoramento | Patching, inventário, Session Manager, Parameter Store |
| **CloudFormation** | Infraestrutura como código (IaC) | Criar recursos AWS via templates declarativos | Padronizar, automatizar e versionar infra | vs **Terraform**: CloudFormation = nativo AWS, Terraform = multi-cloud | YAML/JSON; stacks reutilizáveis; rollback automático |
| **AWS Health** | Status e alertas de saúde dos serviços AWS | Informar sobre eventos que afetam seus recursos | Monitorar disponibilidade e incidentes | vs **CloudWatch**: Health = status da AWS, CloudWatch = métricas | Service Health Dashboard (global) + Personal Health Dashboard (sua conta) |

---

## 🚚 Migration

| Serviço | O que é | Para que serve | Quando usar | Comparação | Infos adicionais |
|---|---|---|---|---|---|
| **Snowball** | Dispositivo físico de transferência | Migrar grandes volumes de dados (TB/PB) para AWS | Mover dados offline | vs **DMS**: Snowball = físico, DMS = lógico | Snowball Edge inclui capacidade de compute |
| **DMS** | Migração de bancos de dados | Migrar dados entre BDs com mínima indisponibilidade | Mover dados para AWS ou entre engines | vs **Snowball**: DMS = migração lógica | Migração homogênea e heterogênea; replicação contínua |
| **Migration Hub** | Gerenciamento centralizado de migração | Acompanhar progresso de migrações | Monitorar múltiplas ferramentas em um painel | vs **DMS**: Migration Hub = gerenciamento, DMS = migração de BD | Não executa migração; apenas coordena e mostra status |
| **Transfer Family** | Transferência via protocolos tradicionais | SFTP, FTPS, FTP para/da AWS | Integrar sistemas legados sem mudar aplicações | vs **Snowball**: Transfer Family = online, Snowball = físico offline | Integra com IAM; sem necessidade de servidores próprios |
| **DataSync** | Transferência automatizada em massa | Mover grandes volumes de dados para AWS de forma rápida | Migração ou sincronização em massa | vs **Transfer Family**: DataSync = massa automatizada, TF = protocolos | Agentes locais; criptografia; migração contínua |
| **Snowball Edge** | Dispositivo físico + compute | Transferir dados e executar workloads localmente | Ambientes desconectados ou remotos | vs **Snowball**: Edge = com compute, Snowball = só transferência | Roda instâncias EC2 e Lambda; locais sem conectividade |
| **Application Migration Service (MGN)** | Migração de servidores e aplicações | Replicar workloads on-premises para EC2 | Migrar servidores sem refatoração | vs **DMS**: MGN = servidores/apps, DMS = bancos de dados | Substitui o antigo SMS; suporta testes antes do cutover |

---

## 📈 Monitoring & Observabilidade

| Serviço | O que é | Para que serve | Quando usar | Comparação | Infos adicionais |
|---|---|---|---|---|---|
| **CloudWatch** | Logs, métricas e alarmes | Monitorar, analisar e visualizar recursos | Observabilidade geral | vs **CloudTrail**: CloudWatch = métricas, CloudTrail = auditoria | Metrics → Logs → Alarms; CPU, memória, rede |
| **CloudTrail** | Auditoria e rastreamento de API | Registrar chamadas de API e atividades na conta | Auditar ações, investigar incidentes, compliance | vs **CloudWatch**: CloudTrail = auditoria de ações | Histórico de eventos; consultas via Athena |
| **Trusted Advisor** | Recomendações e boas práticas | Verificações de quota, segurança, custo e performance | Sempre | vs **Config**: Advisor = recomenda, Config = audita | Custos, segurança, desempenho, tolerância a falhas; completo no Business/Enterprise |
| **X-Ray** | Rastreamento de requisições em apps | Analisar performance e identificar gargalos | Depuração em sistemas distribuídos | vs **CloudWatch**: X-Ray = monitora apps, CloudWatch = recursos | Mapa de chamadas, latência, erros; ideal para microservices |

---

## 🔒 Security & Identity

| Serviço | O que é | Para que serve | Quando usar | Comparação | Infos adicionais |
|---|---|---|---|---|---|
| **IAM** | Gerenciamento de identidade e acesso | Controlar quem acessa quais recursos | Definir usuários, grupos, permissões e políticas | vs **Cognito**: IAM = interno, Cognito = usuários externos | Gratuito; menor privilégio; usuários, grupos, roles, políticas |
| **IAM Roles** | Identidades temporárias com permissões | Conceder acesso a serviços sem credenciais fixas | Serviços ou usuários assumirem permissões temporárias | vs **IAM Users**: Role = temporário, User = credenciais fixas | Sem senha ou chaves permanentes; assumidas por serviços ou contas |
| **WAF** | Firewall de aplicação web | Proteção HTTP/HTTPS contra ataques | Apps web expostas | vs **Shield**: WAF = regras de tráfego, Shield = DDoS | Filtra injeção SQL, bloqueia tráfego malicioso |
| **Shield** | Proteção contra DDoS | Segurança de rede em camadas 3 e 4 | Apps críticas expostas à internet | vs **WAF**: Shield = DDoS, WAF = regras de tráfego | Mitigação automática de ataques de negação de serviço |
| **Artifact** | Portal de compliance | Relatórios de conformidade e certificações AWS | Evidências de auditoria | vs **Config**: Artifact = relatórios, Config = monitoramento | Acordos de conformidade, certificações, relatórios de auditoria |
| **Inspector** | Avaliação de vulnerabilidades | Escanear workloads para falhas de segurança | Identificar CVEs em EC2, containers e Lambda | vs **GuardDuty**: Inspector = vulnerabilidades, GuardDuty = ameaças | Avalia configurações incorretas e exposição de rede |
| **GuardDuty** | Detecção de ameaças com ML | Monitorar atividades suspeitas e maliciosas | Segurança contínua e inteligente | vs **Inspector**: GuardDuty = ameaças, Inspector = vulnerabilidades | Usa ML e feeds de ameaças; comportamento anômalo |
| **Detective** | Investigação de incidentes de segurança | Analisar causa raiz de alertas de segurança | Entender e investigar incidentes | vs **GuardDuty**: Detective = investigação, GuardDuty = detecção | Gráficos de relacionamentos para análise forense |
| **Secrets Manager** | Gerenciamento de segredos | Armazenar e rotacionar credenciais e chaves | Proteger senhas, tokens e segredos | vs **Parameter Store**: Secrets Manager = segredos críticos | Rotação automática de credenciais; criptografia com KMS |
| **KMS** | Gerenciamento de chaves de criptografia | Criar e controlar chaves de criptografia | Proteger dados em repouso e trânsito | vs **Secrets Manager**: KMS = chaves, Secrets Manager = segredos | Integra com quase todos os serviços AWS |
| **Macie** | Proteção de dados sensíveis em S3 | Detectar PII e dados confidenciais | Identificar dados sensíveis em buckets S3 | vs **GuardDuty**: Macie = dados sensíveis, GuardDuty = ameaças | Usa ML para identificar PII e dados financeiros |
| **Security Hub** | Painel central de segurança | Agregar findings de múltiplos serviços | Visão unificada da postura de segurança | vs **GuardDuty**: Security Hub = agregação, GuardDuty = detecção | Consolida GuardDuty, Inspector, Macie, Config; padrões CIS, PCI DSS |

---

## 💾 Storage

### Classes do S3

| Classe | Para que serve | Quando usar | Comparação |
|---|---|---|---|
| **S3 Standard** | Objetos acessados frequentemente | Alta durabilidade e baixa latência | vs Standard-IA: Standard = acesso frequente |
| **S3 Intelligent-Tiering** | Acesso imprevisível | Otimizar custo sem perder performance | vs Standard: Intelligent otimiza custo automaticamente |
| **S3 Standard-IA** | Acesso infrequente mas crítico | Disponibilidade imediata, acesso raro | vs One Zone-IA: Standard-IA = multi-AZ |
| **S3 One Zone-IA** | Objetos pouco acessados com menor custo | Pode tolerar perda de AZ | vs Standard-IA: One Zone = mais barato, menos resiliente |
| **S3 Glacier** | Arquivamento de médio/longo prazo | Dados raramente acessados | vs Deep Archive: Glacier = mais rápido, Deep Archive = mais barato |
| **S3 Glacier Deep Archive** | Arquivamento regulatório de longo prazo | Retenção por anos com custo mínimo | vs Glacier: Deep Archive = mais barato, recuperação até 12h |
| **S3 Express One Zone** | Acesso ultrarrápido de alta performance | Workloads sensíveis à latência | vs Standard: Express = até 10x mais rápido, uma única AZ |

### Outros Serviços de Storage

| Serviço | O que é | Para que serve | Quando usar | Comparação | Infos adicionais |
|---|---|---|---|---|---|
| **EBS** | Armazenamento em blocos persistente | Volumes de disco para EC2 | Armazenamento durável de baixa latência | vs **S3/EFS**: EBS = blocos, S3 = objetos, EFS = arquivos | Um volume por instância; snapshots; bancos de dados |
| **EFS** | Sistema de arquivos elástico compartilhado | Compartilhar arquivos entre múltiplas instâncias | Acesso simultâneo por várias EC2 | vs **S3/EBS**: EFS = arquivos compartilhados | Escala automático; NFS; dados em tempo real |
| **ECR** | Registro de imagens de container | Armazenar e versionar imagens Docker | Repositório seguro para containers | vs **Docker Hub**: ECR = nativo AWS com IAM | Integração nativa com ECS, EKS e Fargate |
| **Storage Gateway** | Armazenamento híbrido on-premises ↔ AWS | Integrar ambientes locais com AWS | Usar AWS como extensão de storage local | vs **Snowball**: Gateway = híbrido contínuo, Snowball = migração pontual | File Gateway, Volume Gateway, Tape Gateway, FSx File Gateway |
| **FSx** | File systems gerenciados | Windows, Lustre, NetApp, OpenZFS | File system compatível e gerenciado | vs **EFS**: FSx = file systems específicos, EFS = NFS genérico | Windows File Server, Lustre (HPC), NetApp ONTAP |
| **Outposts** | Extensão física da AWS no data center | Serviços AWS on-premises com mesmas APIs | Workloads que exigem baixa latência local | vs **Snow Family**: Outposts = rack permanente, Snow = portátil | Rack gerenciado pela AWS; ambientes híbridos |

---

## 🎓 Support Plans

| Plano | Para quem | Suporte | Tempo de resposta | Diferenciais |
|---|---|---|---|---|
| **Basic** | Todo usuário AWS | Documentação, fóruns, billing | — | Trusted Advisor limitado; sem suporte técnico 24/7 |
| **Developer** | Dev/teste | Email em horário comercial | Até 12h | 1 contato; orientação geral |
| **Business** | Workloads de produção | 24/7 por telefone, chat e email | Até 1h para urgências | Trusted Advisor completo; suporte a terceiros; orientação de arquitetura |
| **Enterprise** | Missão crítica | 24/7 com TAM dedicado | Até 15min | TAM dedicado; suporte Concierge; revisão de arquitetura |

---

## 🏗️ Well-Architected Framework

| Pilar | Foco | Serviços Chave | Comparação | Princípios |
|---|---|---|---|---|
| **Excelência Operacional** | Operação e melhoria contínua | CloudWatch, Systems Manager, Config | vs Desempenho: Operacional = processos | Atualizações frequentes; automação; aprendizado com incidentes |
| **Segurança** | Proteção de dados e sistemas | IAM, KMS, Shield, WAF | vs Confiabilidade: Segurança = proteção | IAM, criptografia, monitoramento de atividades |
| **Confiabilidade** | Resiliência e recuperação de falhas | Route53, Auto Scaling, Backup | vs Segurança: Confiabilidade = resiliência | Redundância, failover, backups, disaster recovery |
| **Eficiência de Desempenho** | Uso eficiente de recursos | EC2, RDS, Graviton, Auto Scaling | vs Operacional: Desempenho = tecnologia | Instâncias corretas para compute, storage, BD e rede |
| **Otimização de Custos** | Minimizar gastos mantendo performance | Budgets, Cost Explorer, Savings Plans | vs Desempenho: Custos = gastar menos | On-Demand, Reserved, Spot; análise contínua de uso |
| **Sustentabilidade** | Menor impacto ambiental | Graviton, Data Centers AWS | vs Custos: Sustentabilidade = impacto ambiental | Eficiência energética; otimização de recursos; redução de desperdício |

---

## 📚 Dicas para a Prova

> **Comparações mais cobradas:**
> - **CloudWatch** (métricas) vs **CloudTrail** (auditoria de ações)
> - **SQS** (fila) vs **SNS** (broadcast) vs **EventBridge** (roteamento de eventos)
> - **S3** (objetos) vs **EBS** (blocos) vs **EFS** (arquivos compartilhados)
> - **IAM** (interno) vs **Cognito** (usuários externos)
> - **Inspector** (vulnerabilidades) vs **GuardDuty** (ameaças ativas)
> - **Athena** (serverless query no S3) vs **Redshift** (data warehouse dedicado)
> - **Direct Connect** (link dedicado físico) vs **VPN** (criptografado via internet)
> - **Security Group** (stateful, por instância) vs **NACL** (stateless, por subnet)
> - **DMS** (migração lógica de BD) vs **Snowball** (migração física de dados)

---

*Guia elaborado para estudo do exame AWS Certified Cloud Practitioner CLF-C02.*
