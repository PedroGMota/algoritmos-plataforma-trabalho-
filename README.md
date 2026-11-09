# ALGORITMOS DAS PLATAFORMAS DE TRABALHO

> **Entrega 2 — Dossiê Consultoria**  
> **Disciplina:** Design Profissional · Turma 2N · 2026.2  
> **Professor:** Cid Andrade  
> **Dossiê Selecionado:** 14 — Algoritmos das plataformas de trabalho  

---

## 1. Abertura

* **Nome do Projeto:** Rota Clara
* **Recorte Escolhido:** Revisão Humana de Bloqueios Indevidos e Decisões Algorítmicas.
* ### Recorte do Projeto e Justificativa
* **Público-Alvo:** Entregadores de motocicletas e motoristas de aplicativo autônomos.
* **Região:** Região Metropolitana de São Paulo (com foco em bairros periféricos).
* **Etapa da Solução:** Fase pós-operação (momento da suspensão da conta e triagem do recurso).

**Justificativa Técnica e Social:**
A escolha deste recorte é justificada pela alta frequência de desativações automatizadas geradas por falhas da infraestrutura. Em regiões periféricas da Grande São Paulo, as oscilações na rede de dados móveis e desvios por obras fazem o algoritmo interpretar a queda de sinal como sinalização de fraude ou burla de rota. Como as plataformas não oferecem canal direto com operadores humanos, o trabalhador é suspenso temporariamente.
  * **Alessandro Tavares Brandão** | RGM: 47995092 | Área: ADS | GitHub: https://github.com/alessandro16014
  * **Júlio Cesar Marques de Sousa** | RGM:  04806969-8 | Área: ADS | GitHub: https://github.com/Juliocesarmarq
  * **Pedro Gonçalves da Mota** | RGM: 47998717 | Área: ADS | GitHub: https://github.com/PedroGMota
  

---

## 2. Análise do Problema

### 2.1. O Problema e Quem é Afetado
* No Brasil, cerca de 1,96 milhão de pessoas trabalham por meio de aplicativos de transporte de passageiros e entregas de produtos. A imensa maioria desse contingente é composta por homens (84,4%), com idade entre 25 e 39 anos (47%), que têm o aplicativo como sua ocupação principal e única fonte de renda.   O problema central abordado neste projeto são as desativações automatizadas e os bloqueios sumários de contas. Ou seja, o momento em que o algoritmo da plataforma decide, sozinho, banir ou suspender o trabalhador sem dar aviso prévio, sem explicar o motivo real e sem oferecer uma forma justa de defesa.

## Quem é afetado no nosso recorte?
* No recorte da Região Metropolitana de São Paulo (RMSP), os mais prejudicados são os entregadores de motocicletas e motoristas de aplicativo que operam em bairros periféricos (como a Zona Leste da capital, Guarulhos e a região do ABC).Esses trabalhadores enfrentam dois grandes gargalos no dia a dia:Dependência Financeira Extrema: Cerca de 72,1% desses trabalhadores estão na informalidade e dependem do ganho diário do aplicativo para colocar comida na mesa. Ficar bloqueado por 2 ou 3 dias significa zerar o orçamento familiar.   Infraestrutura Deficiente nas Periferias: Em bairros periféricos, as redes de dados móveis sofrem com constante oscilação de sinal. Além disso, desvios por obras ou vias estreitas fazem o sinal de GPS falhar.Quando o sinal cai ou oscila, o algoritmo da plataforma interpreta essa perda de conexão como uma "anomalia" ou "tentativa de fraude" (como o uso de aplicativos de GPS falso). O resultado é a suspensão automática da conta por uma falha na infraestrutura de internet da cidade, e não por culpa do trabalhador.   

### 2.2. Causas Tecnológicas e Insuficiência das Soluções Atuais
* As causas técnicas desse problema e as falhas dos sistemas atuais das plataformas incluem:
* Algoritmos "Caixa-Preta" (Black-Box): Os modelos de Inteligência Artificial das plataformas tomam decisões baseadas em padrões complexos de dados sem gerar um histórico explicável para quem é afetado. O sistema bloqueia a conta, mas não diz qual dado específico gerou o bloqueio.
* Falta de Sensibilidade ao Contexto Local: O filtro de detecção de fraudes não diferencia uma perda de sinal causada por uma "sombra de cobertura de rede" na periferia de uma tentativa real de burlar o GPS.
* Atendimento Automatizado Ineficiente Chatbots: Quando o trabalhador tenta contestar o bloqueio, ele é atendido por robôs com respostas prontas e genéricas ex: Sua conta foi suspensa por violar os Termos de Uso. Não existe a opção de conversar com um ser humano.
* Violação da LGPD e das Diretrizes da ANPD: O Artigo 20 da Lei Geral de Proteção de Dados (LGPD) e a Nota Técnica nº 20/2026 da ANPD exigem que qualquer decisão tomada 100% por algoritmos possa ser revisada por uma pessoa humana. As plataformas descumprem essa regra ao usar respostas robóticas genéricas.
* O Impasse do Segredo Industrial: As plataformas recusam-se a mostrar como o algoritmo funciona alegando proteção ao segredo comercial. Decisões do Tribunal Superior do Trabalho (TST) já impediram a perícia direta no código-fonte das empresas para proteger suas patentes. Isso exige uma solução técnica que traga transparência sem precisar violar o segredo industrial da empresa.   

---

## 3. Proposta tecnológica

### 3.1. Experiência do Utilizador (Passo a Passo)
1. A solução Rota Clara funciona como um canal de governança e mediação entre a plataforma de trabalho e o profissional. O fluxo do utilizador funciona em 4 passos simples:

2. Notificação de Suspensão com "Recibo Explicativo": Quando o sistema da plataforma sinaliza uma anomalia (ex.: queda de GPS), o Rota Clara envia uma notificação ao trabalhador com um relatório simples explicando o motivo exato do alerta (ex.: "Sua conta foi suspensa temporariamente devido a uma perda de sinal de GPS na Zona Leste por 15 minutos").

3. Envio Rápido de Contestação: Direto pelo celular, o trabalhador pode anexar uma prova simples do seu contexto (como uma foto da via, comprovante de trânsito ou relato de perda de sinal de rede).

4. Triagem Inteligente e Auditável: O Rota Clara cruza os dados do histórico de telemetria do veículo com a localização das antenas de telefonia da região, separando os casos de falha de sinal real das tentativas de fraude.

5. Revisão Humana Obrigatória (SLA de 48h): O recurso é enviado para um painel de atendimento onde um operador humano analisa as evidências técnicas e toma a decisão final de reativar a conta ou manter o bloqueio de forma fundamentada, tudo em até 48 horas.

### 3.2. Arquitetura da Solução e Papel de Cada Área
* Para colocar essa proposta em prática, cada área de TI do nosso grupo atua de forma complementar:
  
1. Engenharia de Dados (Área Central) Ingestão em Tempo Real: Conecta a transmissão de dados de telemetria do aplicativo (coordenadas de GPS e sinal de rede) usando ferramentas de streaming. Armazenamento Auditável e Imutável: Utiliza um formato de tabela moderna em nuvem com funcionalidade de viagens no tempo. Isso garante que o histórico de corridas e quedas de sinal fique gravado de forma imutável, impedindo que a empresa ou o usuário alterem dados antigos.
2. Ciência de Dados (Área Central) Inteligência Artificial Explicável (XAI): Aplica métodos de IA Explicável, como o SHAP (Shapley Additive exPlanations). Essa tecnologia calcula o peso de cada variável na decisão sem precisar expor o código-fonte proprietário da empresa, permitindo gerar o "Recibo Explicativo" para o trabalhador.mTeste e Mitigação de Vieses: Roda testes estatísticos contínuos de equidade (Fairness) para garantir que o algoritmo não penalize sistematicamente motoristas de áreas periféricas.
3. Gestão de TI e Produto (Área Central) Desenho da Governança Algorítmica: Define as regras de negócio do fluxo de recurso e estabelece o SLA (Acordo de Nível de Serviço) de resposta humana em até 48 horas. Métricas de Sucesso (KPIs): Acompanha indicadores do sistema, como o índice de falsos positivos revertidos, tempo médio de resposta ao trabalhador e nível de satisfação com a clareza das explicações.
4. Cloud Computing (Área de Apoio) Infraestrutura em Nuvem Escalável: Mantém o sistema rodando em ambiente de nuvem flexível (AWS ou Google Cloud) para suportar picos de solicitações nos horários de alta demanda da cidade sem travar ou ficar fora do ar.
5. Cibersegurança (Área de Apoio)Prevenção Real contra Fraudes: Implementa rotinas de segurança que validam se o dispositivo móvel do motorista é autêntico, diferenciando uma queda de rede genuína de um uso deliberado de programas de adulteração de localização (GPS Spoofing).Proteção de Dados e LGPD: Aplica criptografia nos dados de geolocalização e controla quem pode acessar os históricos dos trabalhadores através de controle de acesso por funções (RBAC).   

---

## 4. Análise ética

### 4.1. Matriz de Riscos (Mínimo de 5 Riscos)
| ID | Risco Identificado | Classificação (Alto/Médio/Baixo) | Impacto | Controlo Proposto |
|:--|:--|:--|:--|:--|
| 1 | Bloqueios automáticos indevidos realizados pelo algoritmo  | Alto | Trabalhador perde acesso à plataforma e pode perder sua renda  | Criar revisão humana antes do bloqueio definitivo |
| 2 | Viés algorítmico causando decisões discriminatórias contra trabalhadores | Alto | Tratamento desigual e redução de oportunidades de trabalho | Realizar testes de viés, auditorias periódicas e monitoramento dos resultados do algoritmo |
| 3 | Controle excessivo do trabalhador por decisões automatizadas | Médio | Redução da autonomia e aumento da dependência da plataforma  | Criar regras de governança e supervisão humana |
| 4 | Pressão causada pelo monitoramento constante do algoritmo | Médio | Prejuízos ao bem-estar e qualidade de trabalho | Avaliar impactos do sistema e criar limites de monitoramento |
| 5 | Falta de explicação sobre decisões tomadas pelo algoritmo | Médio | Dificuldade de contestação e perda de confiança na plataforma  | Utilizar IA explicável e informar os motivos da decisão |

### 4.2. Decisão do Grupo
* [Insira aqui, em até 10 linhas, a decisão fundamentada do grupo sobre a implantação do sistema.]

### 4.3. Controles nos Seis Eixos
1. Transparência: 
 O RevisaAI informa ao motorista, em linguagem simples, que a análise é feita por algoritmo, quais critérios foram considerados (ex.: denúncias, avaliações, inconsistência de documentos) e o motivo específico do bloqueio ou da sinalização. A notificação é enviada no app antes ou no momento da medida, com indicação de como contestar. 
2. Revisão humana: 
 Nenhum bloqueio é aplicado apenas por decisão do algoritmo. Um funcionário treinado analisa o caso antes da medida, com acesso às evidências que levaram à sinalização, e tem autonomia para confirmar, revogar ou pedir mais informações. Para evitar que a revisão vire mera formalidade, uma amostra das decisões é auditada, e o índice de reversões é monitorado. 
3. Minimização de dados: 
 São coletados apenas os dados necessários para avaliar a conduta do motorista (cadastro, avaliações, denúncias e registros da corrida). Dados sensíveis ou sem finalidade definida, como trajetos detalhados fora das corridas, localização contínua e informações pessoais não relacionadas à análise, são descartados ou anonimizados, conforme os princípios da LGPD (finalidade, adequação e necessidade). 
4. Segurança: 
 O RevisaAI utiliza criptografia de dados, controle de acesso por níveis de permissão e registro de atividades (logs) para rastrear quem acessou ou alterou informações. Essas medidas reduzem riscos de vazamento e uso indevido dos dados dos trabalhadores. 
5. Teste de Viés: 
 O sistema realiza avaliações periódicas dos resultados do algoritmo, comparando taxas de bloqueio por região, gênero, raça e tipo de veículo. Se um grupo ou região for desproporcionalmente afetado, o critério é revisado antes de continuar em uso. 
6. Canal de Contestação: 
 O motorista pode contestar qualquer bloqueio ou decisão algorítmica diretamente pelo app, com envio de justificativas e documentos. A contestação é analisada por um profissional diferente do que tomou a decisão inicial, com resposta fundamentada em prazo definido (ex.: até 5 dias úteis). Durante a análise, o motorista é informado do andamento. Se o bloqueio for considerado indevido, o acesso é restabelecido imediatamente. 

### 4.4. Conformidade com a LGPD
* **Dados tratados: Serão tratados apenas os dados necessários à análise das decisões algorítmicas: dados cadastrais do trabalhador, dados de habilitação (quando aplicável), histórico de corridas ou entregas, registros de bloqueios anteriores, informações de localização vinculadas à atividade profissional e evidências apresentadas pelo próprio usuário na contestação, como documentos e registros de comunicação.
* **Finalidade e Base Legal: Finalidade: os dados serão utilizados para analisar bloqueios e decisões automatizadas, identificar possíveis falhas do sistema, viabilizar a contestação pelo trabalhador e assegurar decisões mais justas por meio da revisão humana, conforme o art. 20 da LGPD. 
 Base legal: O tratamento fundamenta-se na execução de contrato entre a plataforma e o trabalhador (art. 7º, V) e no legítimo interesse da organização em garantir a segurança, corrigir erros automatizados e aprimorar a confiabilidade do serviço (art. 7º, IX).
* **Prazo de retenção e menores: Os dados serão conservados apenas pelo período necessário à conclusão da análise e a eventuais auditorias, sendo posteriormente eliminados ou anonimizados. O sistema não realizará coleta de dados de menores de 18 anos.

### 4.5. Comunicado Público (Até 600 caracteres)
> O RevisaAI é uma solução criada para tornar as decisões algorítmicas das plataformas de trabalho mais transparentes e justas. Nenhum bloqueio ou penalização é aplicado apenas por algoritmo: uma equipe humana revisa cada caso. O trabalhador é informado do motivo da medida, pode contestá-la pelo aplicativo e acompanhar a análise, com resposta em até 5 dias úteis. A solução busca reduzir erros, proteger dados pessoais conforme a LGPD e promover uma relação mais equilibrada entre tecnologia e trabalho.

---

## 5. Acessibilidade e inclusão digital

* **Público excluído:  O RevisaAI considera os usuários que podem encontrar dificuldades de acesso à tecnologia, como trabalhadores com pouca familiaridade com aplicativos, pessoas com deficiência visual, auditiva, motora ou cognitiva, e usuários com dispositivos antigos ou acesso limitado à internet.
* **Requisitos WCAG e Dispositivos:  A interface será desenvolvida com linguagem simples e sem termos técnicos, organizando o processo em três etapas: visualizar o motivo do bloqueio, enviar a contestação e acompanhar o andamento do caso. As informações terão fonte legível, possibilidade de ampliação do texto e botões identificados por texto e ícones. 

O sistema será otimizado para smartphones de entrada, com versão leve, baixo consumo de dados e memória, compatibilidade com versões antigas do Android e funcionamento em conexões instáveis. Como alternativa, a contestação poderá ser realizada por outros canais de atendimento, como telefone e atendimento presencial. 

A solução seguirá as diretrizes da WCAG 2.2, nível AA, incluindo contraste adequado, compatibilidade com leitores de tela, textos alternativos para imagens, legendas em conteúdos audiovisuais e navegação simples e previsível. 

---

## 6. Sustentabilidade

* **TI Verde: TI Verde: 

O RevisaAI utilizará infraestrutura em nuvem, priorizando provedores que adotem práticas de eficiência energética e sustentabilidade. Os recursos computacionais serão dimensionados conforme a demanda, evitando consumo desnecessário de energia. A solução utilizará processos leves, armazenamento otimizado e políticas de eliminação ou anonimização de dados após o período de retenção definido, reduzindo o uso de recursos computacionais e o impacto ambiental. 
* **Modelo Financeiro:
* No primeiro ano, o projeto será financiado por investimento inicial, parcerias institucionais ou programas de incentivo à inovação. Após esse período, a manutenção poderá ser realizada por meio de contratos com plataformas de trabalho e instituições parceiras interessadas em melhorar a transparência e a segurança de seus sistemas. Os custos de revisão humana, auditorias e proteção de dados serão considerados no orçamento operacional para garantir a continuidade da solução. 

---

## 7. Impacto esperado

- **KPIs e Metas:**
  - **SLA de Resolução:** Tempo máximo de 48 horas para a análise humana e decisão final sobre a contestação do trabalhador.
  - **Taxa de Falsos-Positivos:** Redução de pelo menos 80% nos bloqueios definitivos indevidos causados exclusivamente por falhas de infraestrutura de rede e GPS.
  - **Mitigação de Passivo Judicial:** Diminuir drasticamente as condenações das plataformas parceiras por "suspensão prolongada sem justa causa e violação da ampla defesa", alinhando a operação à jurisprudência atual.
  - **Adoção Regional:** Atingir a adesão de 30% dos motoboys ativos na Zona Leste de São Paulo nos primeiros 6 meses do projeto piloto.

- **Validação e Contingência:**
  - **Validação:** Realização de rodadas quinzenais de feedback junto a coletivos e associações de entregadores na região piloto, além de auditorias mensais de viés para garantir que a IA não esteja penalizando rotas específicas.
  - **Contingência:** Caso o modelo de licenciamento B2B (API) sofra resistência inicial das plataformas devido aos recentes impasses regulatórios e falhas de avanço legislativo (como visto ao longo de 2025 e 2026), a Rota Clara adotará a contingência de atuar como uma "LegalTech B2C". O aplicativo emitirá laudos técnicos gratuitos de telemetria aos motoristas, servindo como base probatória material para que eles possam buscar seus direitos nos tribunais e Procons, forçando indiretamente a adesão das empresas pela via jurídica.

 
---

## 8. Quadro de decisões

| Decisão Tomada | Alternativas Consideradas | Justificativa Técnica |
|:--|:--|:--|
| 1. **Uso de Framework XAI (SHAP)** | Modelos *black-box* (caixa-preta) ou Regressão Linear simples | Garante a **explicabilidade local**, permitindo identificar exatamente qual variável do percurso ativou o gatilho de fraude. Atende ao Art. 20 da LGPD, que exige revisão, sem necessidade de quebrar o segredo industrial das plataformas parceiras. |
| 2. **Revisão Humana com SLA de 48h** | Automação total via Chatbot com IA Generativa | Mitiga os crescentes riscos jurídicos e atende decisões recentes dos tribunais (2025/2026) que proíbem o bloqueio sumário sem que um humano avalie a defesa do trabalhador. A automação integral manteria a infração regulatória. |
| 3. **Piloto Regional (Zona Leste SP)** | Lançamento Nacional "Big Bang" (todas as regiões simultâneas) | Reduz riscos operacionais ao focar em um ambiente hiper-segmentado conhecido por instabilidades crônicas de rede. Permite validar a acurácia do modelo SHAP antes do consumo massivo de infraestrutura em nuvem. |
| 4. **Armazenamento em Nuvem Imutável** | Bancos de dados relacionais tradicionais sob controle exclusivo da plataforma | Garante uma **trilha de auditoria** neutra e inviolável (Logs seguros). Como a Rota Clara atua como mediadora, a integridade da prova é fundamental caso a contestação evolua para a esfera jurídica. |
| 5. **Modelo de Negócios B2B (API as a Service)** | Aplicativo B2C com mensalidade paga pelo entregador/motorista | O público-alvo já sofre com precarização de renda e alta informalidade. Monetizar através das empresas (que pagam pela mitigação de risco, compliance de ESG e redução de processos judiciais) viabiliza o projeto de forma ética. |

---

## 9. Capítulos individuais

### Capítulo de Alessandro Tavares Brandão
* **Papel no Projeto: Responsavel pela escrita das sessões 7 e 8 **
* **# Plano de Desenvolvimento SMART para os próximos 6 a 12 meses

##  Específico (S)
**O que você vai fazer de forma clara e exata?**

Quero ampliar meus conhecimentos em Cloud Computing, começando com AWS da Amazon e também com o Azure da Microsoft, me aprofundar um pouco mais no desenvolvimento e análise de banco de dados, e alcançar o nível do intermediário ao avançado no Inglês. 

*Contexto Atual:* Atualmente, além dos projetos da faculdade, estou desenvolvendo um sistema de fluxo de caixa e estoque para a loja na qual trabalho, junto com um banco de dados, ainda simples, apenas um protótipo para aprendizado.

---

##  Mensurável (M)
**Como você vai comprovar que alcançou o objetivo?**

Quero utilizar o sistema na loja por um dia para fins de testes, para verificar como ele se comporta em um número elevado de vendas, ou de dados sendo inseridos. O objetivo é garantir que, ao finalizar uma venda, o sistema adicione a quantidade e o valor de cada produto vendido de forma correta e sem bugs.

---

## Alcançável (A)
**Quais recursos você possui e como vai encaixar isso na rotina?**

Atualmente tenho pouca disponibilidade para desenvolver este projeto. Ao final do dia me sobram apenas uma ou duas horas na semana, e aos finais de semana cerca de quatro ou cinco horas — um tempo a mais no qual eu consigo pensar e desenvolver este projeto. 

Espero que em janeiro, por conta das férias da faculdade, eu consiga desenvolver este projeto de uma forma melhor e também focar mais nos estudos fora da faculdade. Alguns materiais de estudos sobre bancos de dados estão me auxiliando no desenvolvimento deste projeto.

---

## Relevante (R)
**Por que isso é estrategicamente importante para o seu futuro profissional?**

Porque este projeto une várias áreas de estudos do meu interesse. Durante o período de desenvolvimento, vou adquirir um conhecimento não só técnico de programação e criação de bancos de dados, mas também do mercado de trabalho real, entendendo problemas reais que são descobertos apenas na utilização do sistema no dia a dia. São problemas cujas soluções vêm da experiência prática. 

Por estes motivos, acredito que este projeto é muito relevante para o meu desenvolvimento pessoal e para o futuro da minha carreira em TI.

---

## Temporal (T)
**Qual é o prazo final definitivo?**

Quero começar a fazer alguns testes ainda neste mês de **Novembro de 2026**, e pretendo ir atualizando aos poucos e aumentando a quantidade de testes. 

Até o final de **Janeiro de 2027**, o projeto ganhará uma versão final e oficial, devidamente testada e pronta para o uso diário dentro da loja.** 

### Capítulo de Júlio César Marques de Sousa
Entendido, aqui está o conteúdo organizado, sem alterar o que você escreveu.

## Atuação: conformidade técnica, ética e governança do projeto

- Pesquisa e análise sobre gestão algorítmica
- Estudo e mapeamento de discriminação algorítmica
- Construção da Matriz de Riscos da solução
- Desenvolvimento e adequação à LGPD (Privacidade e Proteção de Dados)
- Definição de requisitos de Acessibilidade e Inclusão Digital
- Levantamento de diretrizes de Sustentabilidade (TI Verde)
- Discussão e planejamento da estratégia de implantação via MVP (Produto Mínimo Viável)

## Plano de Desenvolvimento Individual (SMART)

**S (Específica)**\
&#x20;Reduzir bloqueios indevidos realizados por algoritmos em plataformas de trabalho, implementando um fluxo de revisão humana obrigatório para contestações antes da tomada de decisão definitiva.
**M (Mensurável)**
- Diminuir em 30% a taxa de bloqueios indevidos identificados durante a fase piloto.
- Responder a pelo menos 90% das contestações dos usuários no prazo máximo de 48 horas.
**A (Atingível)**\
&#x20;A meta será viabilizada por:
- Alocação de equipe para análise humana dedicada
- Fornecimento de explicações claras sobre as decisões do algoritmo
- Acompanhamento contínuo dos principais motivos de bloqueio
**R (Relevante)**\
&#x20;A eliminação de bloqueios injustos:
- Protege a renda dos trabalhadores
- Aumenta a transparência do sistema
- Fortalece a confiança da comunidade no uso de soluções automatizadas
**T (Temporal)**\
&#x20;Atingir e consolidar os indicadores no período de 6 meses após o lançamento do projeto piloto, com avaliação final em até 12 meses.

Se quiser, posso gerar isso em Word ou PDF. (o que tu achou???)

### Capítulo de Pedro Gonçalves da Mota
* **Papel no Projeto:** Responsável pela escrita da Abertura (Seção 1), Análise do Problema (Seção 2), Proposta Tecnológica (Seção 3), Quadro de Decisões. 
* **Plano de Desenvolvimento (SMART):** Dentro dos 6 meses eu pretendo construir e publicar 2 projetos completos de backend no GitHub com autenticação via JWT, documentação automática via Swagger e cobertura de testes unitários com Pytest superior a 80%, visando a conquista de uma vaga em instituições financeiras (como Bradesco, Nubank ou Santander). Nós próximos 12 meses já vou estar trabalhando dentro de algum desses bancos, na área de desenvolvedor back-end, contribuindo ao máximo que posso, e sempre procurando me aperfeiçoar através de cursos de desenvolvedor back-end, fazer curso de inglês, pra impulsionar meu currículo e minha vida profissional.   

### Feedback dos Colegas (Redigido em Conjunto)
* A nossa equipe operou com excelente nível de colaboração ao longo da Entrega 2. O fluxo de trabalho estruturado no GitHub por meio de branches e Pull Requests garantiu que cada integrante contribuísse de tal maneira. As discussões integraram os conceitos de ADS à realidade social e legal dos trabalhadores de aplicativos, gerando um dossiê técnico coerente, viável e eticamente responsável.

---

## 10. Referências

1. AGÊNCIA BRASIL. Brasil tem 2 milhões de pessoas que trabalham por meio de aplicativos. EBC, 2026. Disponível em: https://agenciabrasil.ebc.com.br/economia/noticia/2026-09/brasil-tem-2-milhoes-de-pessoas-que-trabalham-por-meio-de-aplicativos.

2. AGÊNCIA DE NOTÍCIAS IBGE. Trabalhadores de transporte de passageiros por aplicativo chegam a 1,2 milhão de pessoas no país. IBGE, 2026. Disponível em: https://agenciadenoticias.ibge.gov.br/agencia-noticias/2012-agencia-de-noticias/noticias/47966-trabalhadores-de-transporte-de-passageiros-por-aplicativo-chegam-a-1-2-milhao-de-pessoas-no-pais.

3. G1 ECONOMIA. Jornada maior, renda menor: quase 2 milhões trabalham por aplicativos no Brasil, mostra IBGE. Globo.com, 2026. Disponível em: https://g1.globo.com/economia/noticia/2026/09/04/quase-2-milhoes-trabalham-por-aplicativos-no-brasil-mostra-ibge.ghtml

4. AUTORIDADE NACIONAL DE PROTEÇÃO DE DADOS (ANPD). Nota Técnica nº 20/2026: Tratamento de dados pessoais em sistemas de tomada de decisão automatizada e inteligência artificial. Brasília: ANPD, 2026. Disponível em: https://www.gov.br/anpd/pt-br/acesso-a-informacao/participacao-social/outras-acoes/ts-04-2026-nota-tecnica-no-20-2026.pdf/@@display-file/file.

5. TRIBUNAL SUPERIOR DO TRABALHO (TST). TST suspende perícia técnica no algoritmo de plataforma de táxis. Brasília: TST, 2024. Disponível em: https://www.tst.jus.br/-/tst-suspende-per%C3%ADcia-t%C3%A9cnica-no-algoritmo-de-plataforma-de-t%C3%A1xis.

6. SUPREMO TRIBUNAL FEDERAL (STF). Tema 1291: Reconhecimento de vínculo empregatício entre motorista de aplicativo de prestação de serviços de transporte e a empresa administradora de plataforma digital. Brasília: STF, 2024. Disponível em: https://portal.stf.jus.br/jurisprudenciarepercussao/tema.asp?num=1291.

7. Portal JOTA (Maio de 2026):** Artigo *"STF decide trabalho em plataformas diante do fracasso do Congresso"*, abordando o bloqueio estrutural do legislativo perante pautas como o PL 152/2025 e outros PLPs, além da nova fronteira do controle algorítmico nas relações de trabalho.
       [Link de referência (JOTA)](https://www.jota.info/opiniao-e-analise/artigos/stf-decide-trabalho-em-plataformas-diante-do-fracasso-do-congresso)
   
8. TJDFT - Tribunal de Justiça do Distrito Federal e dos Territórios (Janeiro de 2026):** Decisão jurisprudencial unânime onde a plataforma de mobilidade foi condenada a indenizar um motorista por lucros cessantes devido a uma *"suspensão prolongada sem justa causa e sem demonstração concreta de infração"*. O caso fundamenta a necessidade da revisão humana em 48h proposta pelo Rota Clara.
       [Link de referência (TJDFT Oficial)](https://www.tjdft.jus.br/institucional/imprensa/noticias/2026/janeiro/tjdft-condena-plataforma-a-indenizar-motorista-por-suspensao-prolongada-sem-justa-causa)

9. Painel LGPD nos Tribunais / Cedis-IDP (Junho de 2025):** Relatório analítico ressaltando os direitos dos entregadores sobre decisões automatizadas, especificamente a necessidade de uma explicação das razões de bloqueio e do direito assegurado à revisão humana baseada no Art. 20 da LGPD.
       [Link de referência (Relatório LGPD)](https://static.jusbr.com/painel-lgpd/edicoes/relatorio-do-painel-lgpd-nos-tribunais-2026.pdf)

10. Mobile Time (Dezembro de 2024):** Cobertura jornalística sobre os modelos de regulamentação do trabalho autônomo por plataformas em toda a América Latina e os  desafios impostos pelas decisões automatizadas opacas sobre a jornada do trabalhador.
https://www.mobiletime.com.br/noticias/20/12/2024/trabalhadores-de-apps/

11. https://ojs.veredasjournal.com/index.php/veredas/article/view/7103

12. https://seer.sis.puc-campinas.edu.br/direitoshumanos/article/view/5201

13. https://www.scielo.br/j/read/a/8KzGRQSrSPnDWRfWpcqbgFy/?lang=pt

14. https://ctbdigital.com.br/artigo/art162/


 
