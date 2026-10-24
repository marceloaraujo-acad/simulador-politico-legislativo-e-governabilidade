# Simulador de Congresso: Legislativo & Poderes (Inspirado em Lawgivers II)

![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)
![TailwindCSS](https://img.shields.io/badge/Tailwind_CSS-38B2AC?style=for-the-badge&logo=tailwind-css&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)
![Status](https://img.shields.io/badge/Status-Funcional-success?style=for-the-badge)
![License](https://img.shields.io/badge/Licença-MIT-blue?style=for-the-badge)

Um simulador e jogo de estratégia política de página única (*Single-File Web Application*), fortemente inspirado na franquia **Lawgivers** e adaptado para a engenharia institucional do **Presidencialismo de Coalizão brasileiro**. 

O projeto permite visualizar, inspecionar, editar e adicionar membro a membro parlamentares na **Câmara dos Deputados (513 cadeiras padrão ou expansível)** e no **Senado Federal (81 cadeiras padrão ou expansível)**, criar e editar **Partidos Políticos e suas ideologias**, operar o filtro prévio das **Comissões Permanentes (CCJ, Finanças e Mérito)**, gerenciar a governabilidade do **Poder Executivo**, simular o controle de constitucionalidade no **Supremo Tribunal (STF)** e conduzir votações nominais em tempo real respeitando os quóruns e ritos regimentais.

---

## Visão Geral

Neste simulador, o jogador assume o controle da articulação política e do desenho institucional do país. Cada um dos **594 parlamentares iniciais** (com possibilidade de criar novos mandatos ou alterar o total de cadeiras) possui atributos próprios e editáveis de **espectro ideológico**, **disciplina partidária**, **fisiologismo (sensibilidade a emendas)**, **satisfação governamental** e **histórico de votações**, reagindo dinamicamente às orientações de bancada, aos pareceres de comissão, à pressão popular e às negociações com o Palácio do Planalto.

---

## Funcionalidades Principais

### 1. Plenário em Hemiciclo, Inspeção & Edição Individual de Parlamentares
- **Renderização Interativa:** Visualização completa dos Deputados Federais e Senadores dispostos em hemiciclo dinâmico.
- **Camadas de Visualização (*Layers*):** Alterne a coloração do plenário entre **Partidos Políticos**, **Bloco de Coalizão** (Governo, Centrão/Independentes, Oposição), **Espectro Ideológico** (Esquerda $\leftrightarrow$ Direita) e **Mapa do Último Voto** (`SIM`, `NÃO`, `ABSTENÇÃO`, `OBSTRUÇÃO`).
- **Ficha Parlamentar & Edição em Tempo Real:** Clique em qualquer assento no hemiciclo ou cartão na lista nominal para:
  - Ajustar diretamente o **controle deslizante (slider) de Ideologia Pessoal** (`-100` a `+100`) do parlamentar.
  - Realizar **Migração Partidária Instantânea**, transferindo o congressista para outra legenda com atualização imediata das bancadas.
  - Abrir o **Editor Completo de Ficha** para modificar nome, partido, UF, disciplina partidária, sensibilidade a emendas, relação com o Planalto ou **cassar/excluir o mandato**.
  - Conceder **Emendas Individuais (RP6)** ou articular apoio diretamente no gabinete.
- **Adição de Novos Parlamentares (Individual ou em Lote):** Adicione 1 ou dezenas de novos deputados e senadores a qualquer partido, escolhendo entre **criar cadeiras extras na Casa** (expandindo o Congresso e recalculando automaticamente os quóruns) ou **tomar assentos de outros partidos** (mantendo o total de cadeiras).

### 2. Comissões Permanentes & Filtro de Admissibilidade (CCJ, Finanças e Mérito)
- **Despacho e Pertinência Automática:** Antes de chegar ao Plenário, toda proposição (exceto MPVs, que possuem rito sumário) passa pelo crivo das comissões permanentes da Casa onde tramita:
  - **CCJC (Câmara) / CCJ (Senado):** Sempre pertinentes e de **caráter terminativo** (Art. 54, I RICD). Avaliam a constitucionalidade, juridicidade e técnica legislativa, penalizando severamente matérias com alto risco de ADI no STF.
  - **CFT (Câmara) / CAE (Senado):** Acionadas automaticamente quando a matéria possui impacto fiscal/orçamentário ou tema econômico, com **caráter terminativo** sobre adequação financeira (Lei de Responsabilidade Fiscal).
  - **Comissões de Mérito Temático:** Nome, sigla e escopo se adaptam dinamicamente ao tema da matéria (`CSPCCO`, `CDHMIR`, `CMADS`, `CDA`, `CDEC` na Câmara e suas equivalentes no Senado).
- **Plenário Interativo da Comissão:** Mapa de assentos exclusivo para cada colegiado, destacando visualmente o **Presidente da Comissão** e o **Relator Designado**, permitindo inspecionar cada titular e ajustar sua **ideologia individual** diretamente na comissão.
- **Relatoria e Manobras Regimentais:**
  - **Troca de Relator:** Articule com o Presidente da Comissão (o custo de Capital Político varia se o partido que preside o colegiado é da Base Aliada, Centrão ou Oposição) para designar um relator favorável ao governo.
  - **Substitutivo Saneador:** Caso o projeto tenha vícios constitucionais ou impacto fiscal sem fonte de custeio, negocie um Substitutivo que reduz em **-20% o risco de queda no STF** e corrige a inadequação orçamentária na CFT/CAE.
  - **Substituição de Titular por Suplente & Emendas de Comissão (RP8):** Troque titulares rebeldes por suplentes alinhados ou libere recursos de comissão para garantir votos estratégicos.
  - **Requerimento de Urgência (Art. 155 RICD):** Avoque a matéria diretamente ao Plenário pulando o filtro das comissões, assumindo o custo político e um acréscimo de **+12% no risco de inconstitucionalidade no STF** por ausência de saneamento prévio na CCJ.
  - **Recurso ao Plenário (Art. 58 §1º RICD):** Caso um projeto seja arquivado terminativamente na CCJ ou na CFT/CAE, recolha assinaturas para recorrer ao Plenário contra o parecer terminativo.

### 3. Ordem do Dia & Simulação Regimental (RICD / RISF)
- **Catálogo e Redação de Proposições:** Escolha projetos pré-configurados ou redija novas matérias legislativas definindo tipo normativo, tema, viés ideológico, impacto fiscal e risco de inconstitucionalidade.
- **Colégio de Líderes:** Configure a orientação de voto de cada bancada partidária (`SIM`, `NÃO`, `LIBERADO` ou `OBSTRUÇÃO`).
- **Mecânica de Obstrução:** Bancadas em obstrução retiram seus parlamentares do painel de presença para tentar impedir o **quórum de abertura da sessão** (maioria absoluta).
- **Painel Eletrônico Ao Vivo:** Simulação nominal voto a voto com iluminação progressiva dos assentos no hemiciclo e efeitos sonoros sintetizados via *Web Audio API* (inspirados nos bipes reais do painel do Congresso).
- **Esteira Bicameral em 6 Etapas:** Fluxo completo entre Comissões da Câmara $\rightarrow$ Plenário da Câmara $\rightarrow$ Comissões do Senado $\rightarrow$ Plenário do Senado $\rightarrow$ Sanção/Veto Presidencial $\rightarrow$ Controle de Constitucionalidade no STF.

### 4. Executivo & Presidencialismo de Coalizão
- **Esplanada dos Ministérios:** Distribua **12 pastas ministeriais** entre os partidos existentes ou recém-criados para construir base aliada na Câmara e no Senado.
- **Orçamento Impositivo e Barganha:** Libere **Emendas de Bancada (RP9)** para elevar a satisfação das legendas ou utilize capital político para destravar votações difíceis.
- **Sanção e Veto Presidencial:** Matérias aprovadas nas duas Casas chegam à mesa da Presidência da República para **Sanção** (conversão em Lei) ou **Veto Total**, podendo o Congresso se reunir para apreciar a manutenção ou derrubada do veto.

### 5. Supremo Tribunal & Controle de Constitucionalidade
- **Plenário de 11 Ministros:** Cada magistrado possui um perfil hermenêutico (Garantista, Progressista, Moderado/Institucionalista, Conservador, Originalista) e um ponto no espectro ideológico.
- **Julgamento de ADIs:** Leis sancionadas podem ser alvo de **Ação Direta de Inconstitucionalidade (ADI)**. Caso a maioria absoluta (6 de 11 votos) julgue a norma procedente, a lei é anulada, gerando impacto na estabilidade institucional.
- **Aposentadoria, Indicação e Sabatina:** Simule a vacância de uma cadeira na Corte, indique um novo jurista pelo Executivo e submeta seu nome à **Sabatina no Senado Federal** (exigindo aprovação por maioria absoluta dos senadores).

### 6. Gestão de Partidos, Ideologia & Editor de Cenário (Modo Sandbox)
- **Criador e Editor de Partidos Políticos:**
  - **Criar Novas Legendas:** Funde novos partidos definindo sigla, nome completo, cor no hemiciclo, bloco (`Governo`, `Centrão` ou `Oposição`), satisfação inicial, ideologia base (`-100` a `+100`) e número de cadeiras na Câmara e no Senado (normalizando o total ou adicionando cadeiras extras).
  - **Editar ou Extinguir/Fundir Partidos:** Modifique siglas, cores e blocos de qualquer partido existente, ou extinga uma legenda (migrando automaticamente seus parlamentares e ministérios para o partido ideologicamente mais próximo).
- **Controle de Ideologia Partidária & Sincronização de Bancada:**
  - Modifique a ideologia de qualquer partido (pelo modal de Gestão de Partidos ou ao vivo pelos sliders da Aba 6) escolhendo como a mudança afeta os membros daquela bancada:
    1. **Deslocamento Proporcional (*Shift*):** Desloca a ideologia individual de todos os membros do partido na mesma proporção.
    2. **Realinhamento com Variação Natural (*Align*):** Realinha toda a bancada em torno da nova ideologia do partido mantendo nuances individuais.
    3. **Fixação Exata (*Exact*):** Define exatamente a mesma ideologia para 100% dos membros da legenda.
    4. **Apenas Diretriz Partidária:** Altera o centro ideológico do partido mantendo intacta a ideologia pessoal atual de cada congressista.
  - **Ferramentas Globais de Ideologia:** Botões rápidos para deslocar simultaneamente todos os parlamentares do Congresso mais à Esquerda (`-15`), mais à Direita (`+15`) ou realinhá-los aos seus partidos.
- **Reconfiguração de Bancadas (Com ou Sem Normalização):** Ajuste as cadeiras de cada partido aplicando **valores exatos** (permitindo um Congresso de qualquer tamanho) ou **normalizando automaticamente** para **513 Deputados** e **81 Senadores**.
- **Editor de Comissões & Pertinência (Art. 58 CF):** Edite a distribuição partidária de assentos titulares, troque o partido que detém a **Presidência**, ajuste o **Rigor Técnico-Jurídico** (10% a 100%) e force ou dispense a **pertinência** de qualquer comissão.
- **Clima Ideológico da Sociedade & Presets:** Desloque o eixo ideológico da opinião pública ou carregue cenários prontos (*Polarizado*, *Super Centrão*, *Maioria Esquerda*, *Maioria Direita*).

---

## Regras Regimentais e Quóruns Implementados

### Quóruns de Plenário
O motor de votação calcula os quóruns dinamicamente a partir do total de assentos ativos em cada Casa (por padrão **513 na Câmara** e **81 no Senado**, recalculando automaticamente caso o jogador expanda ou reduza o número de cadeiras):

| Espécie Normativa | Sigla | Quórum de Abertura (Maioria Absoluta) | Quórum de Aprovação (Padrão Câmara - 513) | Quórum de Aprovação (Padrão Senado - 81) | Turnos por Casa |
| :--- | :---: | :---: | :--- | :--- | :---: |
| **Projeto de Lei Ordinária** | `PL` | $>50\%$ (257 Dep. / 41 Sen.) | Maioria Simples dos presentes | Maioria Simples dos presentes | 1 Turno |
| **Projeto de Lei Complementar** | `PLP` | $>50\%$ (257 Dep. / 41 Sen.) | **Maioria Absoluta (257 votos)** | **Maioria Absoluta (41 votos)** | 1 Turno |
| **Proposta de Emenda à Constituição** | `PEC` | $>50\%$ (257 Dep. / 41 Sen.) | **3/5 dos membros (308 votos)** | **3/5 dos membros (49 votos)** | **2 Turnos** |
| **Medida Provisória** | `MPV` | $>50\%$ (257 Dep. / 41 Sen.) | Maioria Simples (Pula Comissões) | Maioria Simples (Pula Comissões) | 1 Turno |

### Colegiados e Comissões Permanentes (Art. 58 CF)
A deliberação nas comissões exige quórum de abertura de maioria absoluta dos titulares e aprovação por maioria simples dos presentes:

| Casa | Comissão Permanente | Sigla | Titulares | Escopo e Natureza Regimental | Caráter do Parecer |
| :---: | :--- | :---: | :---: | :--- | :---: |
| **Câmara** | Constituição e Justiça e de Cidadania | `CCJC` | 66 Dep. | Admissibilidade constitucional, juridicidade e técnica legislativa | **Terminativo** (Art. 54, I RICD) |
| **Câmara** | Finanças e Tributação | `CFT` | 42 Dep. | Adequação financeira e orçamentária (LRF) e mérito tributário | **Terminativo** (Art. 54, II RICD) |
| **Câmara** | Comissão Temática de Mérito | Dinâmica | 36 Dep. | Análise do mérito específico conforme o tema da proposição | **Meritório** (Informa o Plenário) |
| **Senado** | Constituição, Justiça e Cidadania | `CCJ-SF` | 27 Sen. | Controle preventivo de constitucionalidade e regimentalidade | **Terminativo** (Art. 101 RISF) |
| **Senado** | Assuntos Econômicos | `CAE` | 27 Sen. | Compatibilidade fiscal, impacto econômico e dívida pública | **Terminativo** (Adequação Fiscal) |
| **Senado** | Comissão Temática do Senado | Dinâmica | 19 Sen. | Avaliação do mérito substantivo na Casa Revisora | **Meritório** (Informa o Plenário) |

---

## Algoritmo de Decisão Parlamentar

Durante uma votação nominal (nas Comissões ou no Plenário), a probabilidade $P(\text{Sim})$ de cada parlamentar é calculada dinamicamente com base em seis vetores:

1. **Alinhamento Ideológico:** Distância euclidiana entre a ideologia pessoal do parlamentar $(-100 \text{ a } +100)$ — editável individualmente ou via partido — e o viés da proposição.
2. **Orientação de Bancada (*Whip*) e Parecer do Relator:** No Plenário, o peso da orientação do líder é modulado pela **Disciplina Partidária** do congressista; nas Comissões, o **Parecer do Relator** e a posição do **Presidente do Colegiado** influenciam os titulares.
3. **Rigor Técnico-Jurídico e Fiscal (Exclusivo Comissões):** Na `CCJC`/`CCJ-SF`, projetos com alto risco de inconstitucionalidade sofrem penalidade proporcional ao rigor técnico do colegiado (salvo se houver **Substitutivo Saneador**); na `CFT`/`CAE`, projetos com impacto fiscal negativo sem compensação sofrem resistência técnica.
4. **Participação na Coalizão:** Peso do espaço ocupado pelo partido na Esplanada dos Ministérios em relação ao seu tamanho no Congresso.
5. **Execução Orçamentária:** Bônus direto concedido pela liberação de **Emendas Individuais (RP6)**, **Emendas de Comissão (RP8)** ou **Emendas de Bancada (RP9)**.
6. **Clima Social e Popularidade do Governo:** Pressão externa exercida pela opinião pública e pelo índice de aprovação presidencial.

---

## Partidos Políticos Fictícios (Configuração Inicial)

O simulador inicia com 6 partidos pré-configurados, mas o jogador pode **editar qualquer atributo**, **extinguir/fundir legendas** ou **criar novos partidos livremente** durante a partida:

| Sigla | Nome do Partido | Espectro Inicial | Perfil Predominante |
| :---: | :--- | :---: | :--- |
| **MTP** | Movimento Trabalhista Progressista | Esquerda (`-75`) | Trabalhismo, Estado de bem-estar social e expansão de direitos sociais |
| **BVS** | Bloco Verde e Sustentável | Centro-Esquerda (`-40`) | Sustentabilidade, transição energética, direitos civis e inovação |
| **UDN** | União Democrática Nacional | Centro / Centrão (`0`) | Fisiologismo pragmático, municipalismo, foco em emendas e governabilidade |
| **PSDC** | Partido Social-Democrata Cristão | Centro-Direita (`+30`) | Pragmatismo, equilíbrio institucional e políticas sociais moderadas |
| **FL** | Frente Liberal | Direita Liberal (`+65`) | Livre mercado, responsabilidade fiscal, privatizações e desburocratização |
| **RC** | Renovação Conservadora | Direita (`+85`) | Conservadorismo nos costumes, segurança pública rigorosa e punitivismo |

---

## Como Executar o Projeto

Por ter sido arquitetado como uma aplicação *Single-File* sem dependências de *build*, você não precisa instalar Node.js ou pacotes externos para rodá-lo:

1. Faça o download ou clone o arquivo `index.html`.
2. Abra o arquivo `index.html` diretamente em qualquer navegador moderno (Chrome, Edge, Firefox, Safari).

*(Opcional)* Se preferir servir via servidor HTTP local:
```bash
# Usando Python 3
python -m http.server 8080

# Ou usando Node.js (npx)
npx serve .
# Ou usando Node.js (npx)
npx serve .
