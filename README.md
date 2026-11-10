# ROTA CLARA — Revisão Humana de Decisões Algorítmicas em Plataformas de Trabalho
 
> **Entrega 2 — Dossiê Consultoria**
> **Disciplina:** Design Profissional · Turma 2N · 2026.2
> **Professor:** Cid Andrade
> **Dossiê selecionado:** 14 — Algoritmos das plataformas de trabalho
 
---
 
## 1. Abertura
 
- **Nome do projeto:** Rota Clara
- **Dossiê:** 14 — Algoritmos das plataformas de trabalho
- **Integrantes:**
  - **Alessandro Tavares Brandão** | RGM: 47995092 | Área: ADS | GitHub: https://github.com/alessandro16014
  - **Júlio Cesar Marques de Sousa** | RGM: 04806969-8 | Área: ADS | GitHub: https://github.com/Juliocesarmarq
  - **Pedro Gonçalves da Mota** | RGM: 47998717 | Área: ADS | GitHub: https://github.com/PedroGMota
### Recorte do projeto e justificativa
 
- **Recorte:** revisão humana de bloqueios indevidos e de decisões algorítmicas.
- **Público-alvo:** entregadores de motocicleta e motoristas de aplicativo autônomos.
- **Região:** Região Metropolitana de São Paulo, com foco em bairros periféricos. O piloto será na Zona Leste da capital.
- **Etapa da solução:** pós-operação, ou seja, o momento em que a plataforma já suspendeu a conta e o trabalhador precisa contestar.

**Justificativa:** nas periferias da Grande São Paulo, a rede de dados móveis oscila e obras desviam rotas. O grupo parte da hipótese de que o algoritmo das plataformas pode ler essa queda de sinal como fraude ou burla de rota e suspender a conta. Essa hipótese não está comprovada por dado oficial e será validada no piloto (seção 7). Como as plataformas não oferecem canal direto com uma pessoa, o trabalhador fica sem renda e sem como se defender.
 
---
 
## 2. Análise do problema
 
### 2.1. O problema e quem é afetado
 
No Brasil, cerca de 1,96 milhão de pessoas trabalharam por aplicativos de transporte e entrega em 2025, das quais 1,2 milhão em transporte de passageiros. Entre os que têm o aplicativo como ocupação principal, 84,4% são homens e 47% têm de 25 a 39 anos. Entre todos os trabalhadores de plataforma, 72,1% estão na informalidade e 34% têm cobertura previdenciária. Para motoristas de transporte e entregadores, o motivo mais citado para trabalhar por aplicativo foi não conseguir outro trabalho. Os dados são nacionais (PNAD Contínua, edição experimental do IBGE, contestada pela Amobitec, associação das plataformas) e não mostram o recorte da periferia de São Paulo.
 
O problema central reside nas desativações automatizadas sumárias: a inteligência artificial da plataforma suspende ou bane o perfil do trabalhador sem aviso prévio fundamentado, omitindo os parâmetros técnicos que motivaram a sanção e negando o acesso a instâncias de recurso com mediação humana. A literatura jurídica contemporânea aponta esse poder unilateral de exclusão digital como uma das expressões mais severas de precarização na gestão algorítmica do trabalho.
 
**Quem é afetado no recorte:** entregadores de moto e motoristas de aplicativo da Zona Leste, de Guarulhos e do ABC. Dois fatores agravam a situação:
 
- **Dependência da renda diária:** Como a maioria desses trabalhadores atua na informalidade, ficar dois ou três dias com a conta bloqueada trava a renda da família na hora. Na prática, falta dinheiro até para o básico, como colocar comida na mesa, abastecer a moto ou fazer a manutenção do veículo.
- **Infraestrutura precária na periferia:** a rede de dados oscila e o GPS falha em vias estreitas ou com obras. Se o algoritmo tratar isso como anomalia, a conta pode ser suspensa por uma falha de infraestrutura, e não por culpa do trabalhador.
### 2.2. Causas tecnológicas
 
- **Algoritmo caixa-preta:** As plataformas usam sistemas de inteligência artificial fechados. Elas bloqueiam o entregador ou motorista, mas nunca explicam exatamente qual dado ou comportamento acionou o alarme de fraude.
- **Falta de contexto local:** O filtro que detecta fraudes não sabe diferenciar uma queda comum de sinal de internet na periferia de uma tentativa real de enganar o GPS.
- **Atendimento por chatbot:** Quem tenta reclamar do bloqueio só consegue falar com chatbots automáticos que mandam respostas prontas, sem nenhuma chance de conversar com uma pessoa de verdade.
- **Direito à revisão sem canal efetivo:** o art. 20 da LGPD garante ao titular o direito de **solicitar revisão** de decisões tomadas unicamente por tratamento automatizado (art. 20 da Lei nº 13.709/2018, a LGPD). A exigência de que essa revisão seja feita por pessoa humana foi vetada em 2019 (Lei nº 13.853/2019), e a ANPD ainda discute como regulamentar o tema: a Nota Técnica nº 12/2025 registrou divergência entre os participantes sobre tornar a revisão humana obrigatória. Na prática, o art. 20 foi o dispositivo da LGPD mais invocado nas decisões judiciais analisadas pelo Painel LGPD nos Tribunais de 2026, inclusive para exigir explicação de bloqueios automatizados e revisão humana. Por isso a revisão humana do Rota Clara é uma escolha de projeto, apoiada em decisões judiciais como a do TJDFT, e não uma obrigação direta da lei. Projetos de lei sobre trabalho em plataformas na América Latina já incluem a transparência algorítmica entre os direitos previstos.
- **Segredo industrial:** o próprio art. 20, 1º, manda informar os critérios da decisão automatizada **respeitando os segredos comercial e industrial**. As plataformas usam esse limite para não detalhar o algoritmo. A solução precisa trazer transparência sem exigir o código-fonte.
### 2.3. O que já existe e por que não basta
 
Hoje o trabalhador só tem o canal da própria plataforma (chatbot, resposta padronizada) ou a via judicial, que é lenta e cara para quem vive de renda diária. No caso julgado pelo TJDFT em 2026, um motorista ficou com a conta suspensa por cerca de 16 semanas, a plataforma não apresentou prova concreta da infração, e a conta só foi reativada depois que ele entrou na Justiça. Não há um intermediário independente que junte as evidências técnicas do caso (telemetria e cobertura de rede), explique o motivo da suspensão e garanta uma análise humana em prazo curto.
 
---
 
## 3. Proposta tecnológica
 
### 3.1. Como funciona para o usuário
 
O Rota Clara é um canal de mediação entre a plataforma e o trabalhador. O fluxo tem quatro passos:
 
1. **Recibo Explicativo:** quando a plataforma sinaliza uma anomalia (ex.: queda de GPS), o trabalhador recebe uma notificação em linguagem simples com o motivo. Exemplo: "Sua conta foi suspensa temporariamente por perda de sinal de GPS por 15 minutos na Zona Leste."
2. **Contestação pelo celular:** o trabalhador anexa uma prova simples (foto da via, comprovante de trânsito ou relato de perda de sinal).
3. **Triagem auditável:** o sistema cruza a telemetria do veículo com os dados de cobertura das antenas da região e separa falha de sinal de possível fraude.
4. **Revisão humana com prazo de 48 horas:** um operador analisa as evidências e decide, com fundamentação, reativar a conta ou manter a suspensão.
### 3.2. Arquitetura e papel de cada área
 
O grupo é formado por três alunos de ADS. As áreas abaixo descrevem o trabalho necessário no projeto, com profundidade maior nas áreas centrais do dossiê (Engenharia de Dados, Ciência de Dados e Gestão).
 
| Área | Papel | Componentes |
|:--|:--|:--|
| **Engenharia de Dados** (central) | Ingerir e guardar os dados | Streaming de telemetria (coordenadas e qualidade do sinal), por exemplo com Kafka. Armazenamento em tabelas versionadas e *append-only* na nuvem (ex.: Delta Lake ou Apache Iceberg), que mantém o histórico sem permitir alteração. |
| **Ciência de Dados** (central) | Classificar e explicar | Modelo de triagem do Rota Clara que separa falha de rede de possível fraude. O **SHAP** explica esse modelo, mostrando o peso de cada variável, e alimenta o Recibo Explicativo. Testes periódicos de equidade verificam se trabalhadores da periferia são penalizados. |
| **Gestão de TI e Produto** (central) | Governança | Regras do fluxo de recurso, SLA de 48 horas e indicadores (seção 7). |
| **Cloud Computing** (apoio) | Infraestrutura | Nuvem (AWS ou Google Cloud) com escala automática para os horários de pico. |
| **Cibersegurança** (apoio) | Segurança e antifraude | Validação do dispositivo para detectar GPS falso (*spoofing*), criptografia da geolocalização e controle de acesso por função (RBAC). |
 
**Onde ficam os dados e quem acessa:** na nuvem do Rota Clara, em tabelas com acesso por função. O trabalhador vê apenas o próprio caso; o operador, apenas os casos da sua fila; a auditoria, os registros de acesso.
 
**Como o motivo da suspensão chega ao Rota Clara:** o SHAP explica o modelo do Rota Clara, não o da plataforma. O motivo do alerta da plataforma (código do motivo e janela de telemetria) vem por API, prevista no contrato B2B. Assim não é preciso acessar o código-fonte da plataforma.
 
### 3.3. O que a tecnologia não resolve
 
- Não obriga a empresa a adotar o sistema se ela não quiser assinar contrato.
- Não muda as regras de negócio da plataforma nem decide a questão do vínculo de emprego, que está no STF (Tema 1291) e, até outubro de 2026, ainda não tinha tese fixada.
- Não conserta a internet ruim da rua nem devolve o dinheiro do dia em que o trabalhador ficou parado.
- Não anula 100% a chance de erro humano, por isso fazemos auditorias constantes.
- Não impede que um fraudador use o canal; a triagem e a validação do dispositivo reduzem esse risco, mas não o zeram.
---
 
## 4. Análise ética
 
### 4.1. Matriz de riscos
 
| ID | Risco | Classificação | Impacto | Controle proposto |
|:--|:--|:--|:--|:--|
| 1 | Bloqueio indevido mantido por decisão automática | Alto | O trabalhador perde acesso à plataforma e à renda | Nenhum bloqueio definitivo sem revisão humana fundamentada em até 48 horas |
| 2 | Viés algorítmico contra trabalhadores de certas regiões | Alto | Tratamento desigual e menos oportunidades de trabalho | Testes de equidade, auditoria periódica e monitoramento dos resultados |
| 3 | Vazamento ou uso indevido de dados de geolocalização | Alto | Exposição da rotina e da localização do trabalhador | Criptografia, controle de acesso por função, registros de acesso e coleta mínima |
| 4 | Revisão humana vira formalidade | Médio | A decisão automática é só carimbada e o erro continua | Auditoria por amostragem e acompanhamento do índice de reversões |
| 5 | Uso do canal para legitimar fraude real (GPS falso) | Médio | Aumenta o risco para as plataformas e para os trabalhadores honestos | Validação do dispositivo e triagem com dados de rede |
| 6 | Conflito de interesse: a plataforma financia o mediador | Médio | Perda de independência e de confiança | Auditoria externa e relatório público com dados agregados |
| 7 | Falta de explicação sobre a decisão | Médio | O trabalhador não consegue contestar com argumentos | IA explicável (SHAP) e Recibo Explicativo em linguagem simples |
 
### 4.2. Decisão do grupo
 
Vamos implantar o sistema em etapas, começando com um piloto focado apenas em entregadores de moto na Zona Leste de São Paulo. Isso permite testar se a IA e o painel de atendimento humano funcionam bem na prática antes de pensar em expandir para outros lugares.
 
### 4.3. Controles nos seis eixos
 
1. **Transparência:** o trabalhador é informado, em linguagem simples, de que houve análise por algoritmo, de qual evento disparou o alerta (ex.: perda de sinal de GPS por 15 minutos em tal região) e de como contestar. A informação chega pelo aplicativo no momento da suspensão.
2. **Revisão humana:** a plataforma pode aplicar a suspensão temporária; nenhum bloqueio definitivo é mantido sem decisão fundamentada de um operador treinado, que vê as evidências e pode reativar, manter ou pedir mais informações. Uma amostra das decisões é auditada e o índice de reversões é monitorado para a revisão não virar formalidade.
3. **Minimização de dados:** coleta de telemetria apenas da janela do evento (alguns minutos antes e depois do alerta), mais cadastro e evidências enviadas pelo trabalhador. Rastreamento contínuo fora do evento e dados sem finalidade definida não são coletados.
4. **Segurança:** criptografia, controle de acesso por função e registros de atividade (logs) para saber quem acessou ou alterou cada dado.
5. **Teste de viés:** comparação periódica das taxas de suspensão por região e por tipo de veículo. Gênero e raça só entram se a plataforma já tiver o dado, de forma agregada e anonimizada (dado sensível, art. 11 da LGPD). Se uma região for desproporcionalmente afetada, o critério é revisado.
6. **Canal de contestação:** a contestação é feita pelo aplicativo, com justificativa e anexos, e analisada por um profissional diferente do que tomou a decisão inicial, em até 48 horas. O trabalhador acompanha o andamento. Se o bloqueio for indevido, o acesso é restabelecido imediatamente.
### 4.4. Conformidade com a LGPD
 
- **Dados tratados:** cadastro do trabalhador, histórico de corridas ou entregas, registros de bloqueios anteriores, localização e qualidade de sinal da janela do evento e evidências enviadas por ele.
- **Dados sensíveis (art. 5º, II):** o sistema não pede nenhum. Se o trabalhador anexar algo sensível por conta própria, o dado é tratado só para o recurso. Dados de gênero e raça para teste de viés só entram agregados e anonimizados.
- **Finalidade:** analisar bloqueios e decisões automatizadas, identificar falhas do sistema, permitir a contestação e garantir a revisão (art. 20).
- **Base legal:** execução de contrato (art. 7º, V) e legítimo interesse em corrigir erros automatizados e garantir a segurança do serviço (art. 7º, IX).
- **Prazo de retenção (proposta do grupo):** telemetria sem contestação, 90 dias; casos contestados, 12 meses após a decisão. Depois disso, os dados são eliminados ou anonimizados. O armazenamento é imutável durante o período de retenção.
- **Menores:** o sistema não trata dados de menores de 18 anos, pois a atividade exige maioridade.
### 4.5. Comunicado público
 
> O Rota Clara ajuda entregadores e motoristas de aplicativo da Grande São Paulo a contestar suspensões automáticas de conta. Quando a suspensão ocorre, o trabalhador recebe uma explicação em linguagem simples, envia a contestação pelo celular e tem o caso analisado por uma pessoa em até 48 horas, com resposta fundamentada. Os dados são usados só para essa análise, protegidos conforme a LGPD e eliminados ou anonimizados depois. A fase inicial é um piloto com motoboys da Zona Leste de São Paulo.
 
---
 
## 5. Acessibilidade e inclusão digital
 
| Quem pode ficar de fora | O que a proposta faz |
|:--|:--|
| Trabalhadores com pouca familiaridade com aplicativos | Linguagem simples e fluxo em três etapas: ver o motivo, enviar a contestação e acompanhar o caso |
| Pessoas com deficiência visual | Compatibilidade com leitores de tela, texto alternativo em imagens, contraste adequado e texto ampliável |
| Pessoas com deficiência auditiva | Sem dependência de áudio; se houver vídeo tutorial, legenda e janela de Libras |
| Pessoas com deficiência motora ou cognitiva | Botões grandes com texto e ícone, navegação simples e previsível, sem prazos curtos para preencher |
| Quem tem celular antigo ou internet limitada | Versão leve, baixo consumo de dados e memória, compatível com Android antigo e com conexão instável |
| Quem não consegue usar o aplicativo | Contestação por telefone ou atendimento presencial, com a mesma análise e o mesmo prazo |
 
**Requisitos:** WCAG 2.2, nível AA (contraste, leitor de tela, texto alternativo, navegação previsível).
 
---
 
## 6. Sustentabilidade
 
**Impacto ambiental:** a Agência Internacional de Energia projeta que o consumo de eletricidade dos data centers no mundo deve mais que dobrar até 2030, para cerca de 945 TWh. Por isso o projeto trata a eficiência como requisito. Os maiores consumos do Rota Clara vêm do armazenamento da telemetria e do processamento em streaming. Para reduzir:
 
- coletar só a janela do evento e eliminar ou anonimizar os dados ao fim da retenção;
- dimensionar a nuvem conforme a demanda, com escala automática;
- preferir região de nuvem com maior uso de energia renovável;
- usar um modelo de triagem leve e armazenamento otimizado.
**Quem mantém e quem paga:** no primeiro ano, o projeto é financiado por investimento inicial, parcerias institucionais ou programas de incentivo à inovação. Depois, a manutenção é custeada por contratos com plataformas e instituições parceiras interessadas em transparência e segurança. Os custos de revisão humana, auditoria e proteção de dados entram no orçamento operacional. Para evitar conflito de interesse, o contrato deve prever auditoria externa e relatório público agregado.
 
---
 
## 7. Impacto esperado
 
### KPIs e metas (piloto, 6 meses)
 
| Indicador | Meta |
|:--|:--|
| **SLA de resolução** | Pelo menos 90% dos recursos decididos por um humano em até 48 horas |
| **Bloqueios indevidos** | Reduzir em 30% os bloqueios indevidos em relação ao 1º mês do piloto |
| **Clareza da explicação** | Pelo menos 80% dos trabalhadores avaliam o Recibo Explicativo como claro, em pesquisa pós-recurso |
| **Adoção regional** | 30% dos motoboys ativos da Zona Leste de São Paulo nos primeiros 6 meses |
| **Reversões** | Acompanhar o percentual de suspensões revertidas após a revisão (sem meta fixa na fase inicial) |
 
### Como ouvir os usuários antes de ampliar
 
- Rodadas quinzenais de feedback com coletivos e associações de entregadores da região piloto.
- Auditoria mensal de viés para checar se rotas ou bairros específicos estão sendo penalizados.
- Critério para ampliar: atingir as metas por dois meses seguidos.
### Contingência: se a solução não pegar
 
O contexto regulatório segue indefinido: o PL 152/2025 foi retirado e o STF ainda não fixou tese no Tema 1291. Em junho de 2026 a OIT aprovou a Convenção nº 193 sobre trabalho em plataformas, enviada ao Congresso, mas sem efeito direto no Brasil por enquanto. Se as plataformas resistirem ao modelo B2B (API), o Rota Clara muda para o modelo **B2C gratuito**. O app emite laudos técnicos de telemetria ao trabalhador, que pode usá-los como prova em tribunais e no Procon, sem depender da adesão das empresas.
 
---
 
## 8. Quadro de decisões
 
| Decisão | Alternativas consideradas | Por que esta |
|:--|:--|:--|
| **1. IA explicável (SHAP) no modelo de triagem** | Modelo caixa-preta ou regressão linear simples | Mostra qual variável do percurso disparou o alerta e gera o Recibo Explicativo. Atende ao direito à explicação previsto no art. 20 da LGPD sem exigir o código-fonte da plataforma. |
| **2. Revisão humana com SLA de 48 horas** | Chatbot ou IA generativa decidindo tudo | O TJDFT (jan/2026) condenou uma plataforma por suspensão de cerca de 16 semanas sem prova da infração. A LGPD garante a revisão, mas não exige que seja humana; por isso o grupo adota a revisão humana como escolha de projeto, com prazo curto. |
| **3. Piloto na Zona Leste de SP** | Lançamento nacional em todas as regiões | Região com muitos trabalhadores e falhas conhecidas de rede. Permite validar o modelo e o painel antes de gastar mais infraestrutura. |
| **4. Armazenamento em nuvem imutável (append-only)** | Banco relacional controlado só pela plataforma | Cria uma trilha de auditoria neutra e sem alteração. Como o Rota Clara é mediador, a integridade da prova importa se o caso for à Justiça. |
| **5. Modelo B2B (API)** | App B2C com mensalidade paga pelo trabalhador | O público já tem renda precária e alta informalidade [1]. Quem paga é a plataforma, que ganha com menos erros, mais conformidade com a LGPD e menos processos. O risco de conflito de interesse é tratado com auditoria externa. |
| **6. App leve com canais alternativos (telefone e presencial)** | Somente SMS ou somente aplicativo | O SMS não permite anexar provas nem explicar o motivo com clareza. O app leve atende a maioria e os canais alternativos cobrem quem não consegue usá-lo. |
 
---
 
## 9. Capítulos individuais
 
### Alessandro Tavares Brandão
 
- **Papel no projeto:** responsável pela escrita das seções 7 (Impacto esperado) e 8 (Quadro de decisões).

**Plano de desenvolvimento SMART (6 a 12 meses)**
 
- **Específico:** Desenvolver meus em Cloud Computing, começando por AWS e Azure; aprofundar banco de dados (desenvolvimento e análise); e chegar do inglês intermediário ao avançado. Hoje, além dos projetos da faculdade, desenvolvo um sistema de fluxo de caixa e estoque para a loja onde trabalho, com um banco de dados simples, como protótipo de aprendizado.
- **Mensurável:** usar o sistema na loja por um dia de testes, com alto volume de vendas e de dados inseridos, e confirmar que, ao finalizar uma venda, ele registra a quantidade e o valor de cada produto de forma correta e sem bugs.
- **Alcançável:** tenho pouco tempo: uma ou duas horas por semana nos dias úteis e quatro a cinco horas nos fins de semana. Em janeiro, com as férias da faculdade, espero me dedicar mais. Materiais de estudo sobre banco de dados já me ajudam no projeto.
- **Relevante:** o projeto une várias áreas do meu interesse e me dá experiência prática com problemas reais, que só aparecem no uso diário do sistema. Isso contribui para minha carreira em TI.
- **Smart:** começar os testes ainda em novembro de 2026 e, até o fim de janeiro de 2027, ter uma versão final, testada e pronta para uso diário na loja.
### Júlio Cesar Marques de Sousa
 
- **Papel no projeto:** responsável por conformidade técnica, ética e governança: Matriz de Riscos (4.1), LGPD (4.4), Acessibilidade e Inclusão Digital (5) e Sustentabilidade (6).
**Plano de desenvolvimento SMART**
 
- **Específico:** reduzir bloqueios indevidos feitos por algoritmos em plataformas de trabalho, com revisão humana obrigatória das contestações antes da decisão definitiva.
- **Mensurável:** reduzir em 30% a taxa de bloqueios indevidos no piloto e responder a pelo menos 90% das contestações em até 48 horas.
- **Alcançável:** alocar uma equipe de análise humana, dar explicações claras sobre as decisões do algoritmo e acompanhar os principais motivos de bloqueio.
- **Relevante:** evitar bloqueios injustos protege a renda dos trabalhadores, aumenta a transparência e fortalece a confiança em soluções automatizadas.
- **Temporal:** consolidar os indicadores em 6 meses após o início do piloto, com avaliação final em até 12 meses.
### Pedro Gonçalves da Mota
 
- **Papel no projeto:** propôs o tema e liderou a organização do trabalho. Responsável pela escrita das seções 1 (Abertura), 2 (Análise do problema) e 3 (Proposta tecnológica).
**Plano de desenvolvimento SMART**
 
- **Competências a desenvolver:** back-end com autenticação, documentação de API, testes automatizados e inglês.
- **Específico:** construir e publicar no GitHub 2 projetos completos de back-end em Python, com autenticação via JWT, documentação automática via Swagger e testes unitários com Pytest.
- **Mensurável:** cobertura de testes acima de 80% nos dois projetos.
- **Alcançável:** conciliar o estudo com a faculdade, usando como base o que já pratico em Python.
- **Relevante:** o objetivo é conquistar uma vaga de desenvolvedor back-end em instituição financeira (Bradesco, Nubank ou Santander).
- **Temporal:** em 6 meses, os dois projetos publicados; em 12 meses, já trabalhando como desenvolvedor back-end, com cursos de back-end e de inglês em andamento para continuar evoluindo.

### Feedback entre os integrantes

- O que o Alessandro diz sobre os parceiros:
Sobre o Pedro: "O Pedro foi o cara que puxou o bonde. Ele trouxe a ideia do trabalho, já deixou o GitHub pronto e organizado para a gente não se perder e sempre mantinha o grupo alinhado nos prazos. A ajuda dele com a parte técnica de backend e o foco dele fizeram toda a diferença para o trabalho andar redondo."

Sobre o Júlio: "O Júlio pegou a parte mais chata e densa do trabalho, que é a parte de leis e regras, e tirou de letra. Ele estudou tudo sobre a LGPD e acessibilidade para garantir que o projeto fosse legal e justo de verdade. 

O que o Júlio diz sobre os parceiros:
Sobre o Pedro: "O Pedro liderou muito bem a organização do grupo. Ele montou a estrutura do repositório de um jeito simples e ajudou a transformar nossa ideia em uma proposta técnica de verdade. Ele conduziu os nossos alinhamentos com muita tranquilidade e foco."

Sobre o Alessandro: "O Alessandro foi super parceiro do início ao fim. Ele conseguiu conciliar a correria do dia a dia dele com os prazos da faculdade e escreveu as partes de impacto e decisões com muita clareza. A vivência prática dele com sistemas ajudou bastante nas nossas discussões."

O que o Pedro diz sobre os parceiros:
Sobre o Alessandro: "O Alessandro foi um parceiro nota dez. Ele se dedicou pra caramba, entregou a parte dele no prazo e com um nível de detalhe muito bom. A visão prática dele ajudou muito a amarrar o nosso quadro de decisões."

Sobre o Júlio: "O Júlio fez um trabalho impecável na parte ética, LGPD e acessibilidade. Ele encarou a leitura pesada das leis e transformou isso em diretrizes práticas para a nossa plataforma. Foi um integrante extremamente focado e pontual, o que deu muita segurança para o nosso projeto."

### Feedback dos colegas (redigido em conjunto)
 
O grupo trabalhou de forma colaborativa. As decisões foram tomadas em conjunto e cada integrante se dedicou à sua parte. O Pedro propôs o tema, deu início ao projeto e organizou o trabalho. O fluxo no GitHub, com branches e pull requests, permitiu que cada um contribuísse e mantivesse o histórico das alterações. As discussões ligaram os conceitos de ADS à realidade social e legal dos trabalhadores de aplicativos.

 
---
 
## 10. Referências
 
1. AGÊNCIA BRASIL. **Brasil tem 2 milhões de pessoas que trabalham por meio de aplicativos.** Brasília: EBC, 4 set. 2026. Disponível em: https://agenciabrasil.ebc.com.br/economia/noticia/2026-09/brasil-tem-2-milhoes-de-pessoas-que-trabalham-por-meio-de-aplicativos.
2. AGÊNCIA DE NOTÍCIAS IBGE. **Trabalhadores de transporte de passageiros por aplicativo chegam a 1,2 milhão de pessoas no país.** Rio de Janeiro: IBGE, 2026. Disponível em: https://agenciadenoticias.ibge.gov.br/agencia-noticias/2012-agencia-de-noticias/noticias/47966-trabalhadores-de-transporte-de-passageiros-por-aplicativo-chegam-a-1-2-milhao-de-pessoas-no-pais.
3. G1 ECONOMIA. **Jornada maior, renda menor: quase 2 milhões trabalham por aplicativos no Brasil, mostra IBGE.** Globo.com, 4 set. 2026. Disponível em: https://g1.globo.com/economia/noticia/2026/09/04/quase-2-milhoes-trabalham-por-aplicativos-no-brasil-mostra-ibge.ghtml.
4. AUTORIDADE NACIONAL DE PROTEÇÃO DE DADOS (ANPD). **Nota Técnica nº 12/2025/CON1/CGN/ANPD:** consolidação das contribuições da Tomada de Subsídios sobre inteligência artificial e revisão de decisões automatizadas. Brasília: ANPD, 15 maio 2025. Disponível em: https://www.ba.gov.br/ssp/sites/site-ssp/files/2026-01/26.%20Nota%20a%20t%C3%A9cnica%20n.%C2%BA%2012%20ANPD%20sobre%20AI%20e%20decis%C3%B5es%20automatizadas.pdf.
5. JUSBRASIL; CEDIS-IDP. **Painel LGPD nos Tribunais:** relatório da 5ª edição. São Paulo, 2026. Disponível em: https://static.jusbr.com/painel-lgpd/edicoes/relatorio-do-painel-lgpd-nos-tribunais-2026.pdf.
6. TRIBUNAL DE JUSTIÇA DO DISTRITO FEDERAL E DOS TERRITÓRIOS (TJDFT). **TJDFT condena plataforma a indenizar motorista por suspensão prolongada sem justa causa.** Brasília: TJDFT, 16 jan. 2026. Processo 0708978-71.2024.8.07.0014. Disponível em: https://www.tjdft.jus.br/institucional/imprensa/noticias/2026/janeiro/tjdft-condena-plataforma-a-indenizar-motorista-por-suspensao-prolongada-sem-justa-causa.
7. SUPREMO TRIBUNAL FEDERAL (STF). **Tema 1291 da repercussão geral (RE 1.446.336):** vínculo empregatício entre motorista de aplicativo e a empresa da plataforma digital; julgamento em andamento. Brasília: STF, 2026. Disponível em: https://portal.stf.jus.br/jurisprudenciarepercussao/tema.asp?num=1291.
8. MACHADO, Sidnei. STF decide trabalho em plataformas diante do fracasso do Congresso. **JOTA**, 1 maio 2026. Disponível em: https://www.jota.info/opiniao-e-analise/artigos/stf-decide-trabalho-em-plataformas-diante-do-fracasso-do-congresso.
9. MOBILE TIME. Matéria sobre a regulamentação dos trabalhadores de aplicativos na América Latina. 20 dez. 2024. Disponível em: https://www.mobiletime.com.br/noticias/20/12/2024/trabalhadores-de-apps/.
10. LIMA NETO, A. M. et al. Gestão algorítmica e o desequilíbrio do meio ambiente de trabalho digital: a uberização como desafio ao trabalho decente no Brasil pós-pandêmico. **Veredas do Direito**, v. 23, n. 10, e237103, 2026. DOI: 10.18623/rvd.v23.7103. Disponível em: https://ojs.veredasjournal.com/index.php/veredas/article/view/7103.
11. INTERNATIONAL ENERGY AGENCY (IEA). **Energy and AI.** Paris: IEA, 10 abr. 2025. Disponível em: https://www.iea.org/reports/energy-and-ai.
12. GAZETA DO POVO. **Lula envia ao Congresso convenção que adiou julgamento no STF sobre trabalho por aplicativo.** 2026. Disponível em: https://www.gazetadopovo.com.br/economia/lula-envia-ao-congresso-convencao-que-adiou-julgamento-no-stf-sobre-trabalho-por-aplicativo/.
 
