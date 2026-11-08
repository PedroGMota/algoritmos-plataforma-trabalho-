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
  * **Júlio Cesar Marques de Sousa** | RGM:  04806969-8 | Área: ADS | GitHub: [@usuario2]
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
1. **Transparência:** [Como a solução garante clareza.]
2. **Revisão humana:** [Como o humano atua nas decisões.]
3. **Minimização de dados:** [Quais dados são descartados/protegidos.]
4. **Segurança:** [Proteção contra acessos indevidos.]
5. **Teste de viés:** [Como o sistema testa discriminação.]
6. **Canal de contestação:** [Como o usuário recorre de uma decisão.]

### 4.4. Conformidade com a LGPD
* **Dados tratados:** [Listar dados de localização, cadastrais e financeiros.]
* **Finalidade e Base Legal:** [Explicar o enquadramento na LGPD.]
* **Prazo de retenção e menores:** [Políticas de descarte.]

### 4.5. Comunicado Público (Até 600 caracteres)
> "[Escreva aqui o comunicado institucional da solução, respeitando rigorosamente o limite de 600 caracteres, incluindo espaços.]"

---

## 5. Acessibilidade e inclusão digital

* **Público excluído:** [Quem pode ficar de fora da tecnologia.]
* **Requisitos WCAG e Dispositivos:** [Como a interface se adapta a smartphones de entrada e atende às diretrizes de acessibilidade.]

---

## 6. Sustentabilidade

* **TI Verde:** [Impacto energético da infraestrutura em nuvem utilizada.]
* **Modelo Financeiro:** [Quem mantém e quem financia o projeto após o primeiro ano de operação.]

---

## 7. Impacto esperado

* **KPIs e Metas:** [Indicadores mensuráveis com metas claras, ex: tempo médio de resposta a contestações em até 48h.]
* **Validação e Contingencia:** [Como ouvir os utilizadores antes de ampliar a escala e o que fazer se a solução não tiver adesão.]

---

## 8. Quadro de decisões

| Decisão Tomada | Alternativas Consideradas | Justificativa Técnica |
|:--|:--|:--|
| 1. [Ex: Uso de Framework XAI (SHAP)] | [Modelos black-box / Regressão simples] | [Garante explicabilidade local sem perder acurácia] |
| 2. | | |
| 3. | | |
| 4. | | |
| 5. | | |

---

## 9. Capítulos individuais

### Capítulo de [Nome do Integrante 1]
* **Papel no Projeto:** [Descrever atribuições confirmadas pelos commits no GitHub]
* **Plano de Desenvolvimento (SMART):** [Metas de competências técnicas e comportamentais para 6 a 12 meses]

### Capítulo de [Nome do Integrante 2]
* **Papel no Projeto:** [...]
* **Plano de Desenvolvimento (SMART):** [...]

### Capítulo de [Nome do Integrante 3]
* **Papel no Projeto:** [...]
* **Plano de Desenvolvimento (SMART):** [...]

### Feedback dos Colegas (Redigido em Conjunto)
* [Breve parágrafo avaliando a dinâmica de colaboração do grupo na Entrega 2.]

---

## 10. Referências

1. [Autor / Instituição]. **[Título da Fonte / Artigo / Relatório]**. [Ano (entre 2024 e 2026)]. Disponível em: <[Link]>. Acesso em: [Data].
2. [Adicionar demais referências seguindo o mesmo padrão].
