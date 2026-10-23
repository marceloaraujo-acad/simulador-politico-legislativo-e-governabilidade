# Simulador de um Congresso: Legislativo & Poderes (inspirado em Lawgivers II)

![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)
![TailwindCSS](https://img.shields.io/badge/Tailwind_CSS-38B2AC?style=for-the-badge&logo=tailwind-css&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)
![Status](https://img.shields.io/badge/Status-Funcional-success?style=for-the-badge)
![License](https://img.shields.io/badge/Licença-MIT-blue?style=for-the-badge)

Um simulador e jogo de estratégia política de página única (*Single-File Web Application*), fortemente inspirado na franquia **Lawgivers** e adaptado para a engenharia institucional do **Presidencialismo de Coalizão brasileiro**. 

O projeto permite visualizar, inspecionar e manipular membro a membro a **Câmara dos Deputados (513 cadeiras)** e o **Senado Federal (81 cadeiras)**, gerenciar a governabilidade do **Poder Executivo**, simular o controle de constitucionalidade no **Supremo Tribunal (STF)** e conduzir votações nominais em tempo real respeitando os quóruns e ritos regimentais.

---

## Visão Geral

Em **Congresso Sim**, o jogador assume o controle da articulação política e do desenho institucional do país. Cada um dos **594 parlamentares** possui atributos próprios de **espectro ideológico**, **disciplina partidária**, **satisfação governamental** e **histórico de emendas**, reagindo dinamicamente às orientações de bancada, à pressão popular e às negociações com o Palácio do Planalto.

---

## Funcionalidades Principais

### 1. Plenário em Hemiciclo & Inspeção Individual
* **Renderização Interativa:** Visualização completa dos **513 Deputados Federais** e **81 Senadores** dispostos em hemiciclo.
* **Camadas de Visualização (*Layers*):** Alterne a coloração do plenário entre **Partidos Políticos**, **Bloco de Coalizão** (Governo, Centrão/Independentes, Oposição), **Espectro Ideológico** (Esquerda $\leftrightarrow$ Direita) e **Mapa do Último Voto** (`SIM`, `NÃO`, `ABSTENÇÃO`, `OBSTRUÇÃO`).
* **Ficha Parlamentar Individual:** Clique em qualquer assento ou cartão na lista filtrável para inspecionar o congressista, verificar sua lealdade partidária e realizar articulação individual (concessão de **Emendas Individuais RP6** ou persuasão direta no gabinete).

### 2. Ordem do Dia & Simulação Regimental (RICD / RISF)
* **Catálogo e Redação de Proposições:** Escolha projetos pré-configurados ou redija novas matérias legislativas definindo tipo normativo, tema, viés ideológico e risco de inconstitucionalidade.
* **Colégio de Líderes:** Configure a orientação de voto de cada bancada partidária (`SIM`, `NÃO`, `LIBERADO` ou `OBSTRUÇÃO`).
* **Mecânica de Obstrução:** Bancadas em obstrução retiram seus parlamentares do painel de presença para tentar impedir o **quórum de abertura da sessão** (maioria absoluta).
* **Painel Eletrônico Ao Vivo:** Simulação nominal voto a voto com iluminação progressiva dos assentos no hemiciclo e efeitos sonoros sintetizados via *Web Audio API* (inspirados nos bipes reais do painel do Congresso).
* **Rito Bicameral Completo:** Fluxo automático entre Casa Iniciadora (Câmara) $\rightarrow$ Casa Revisora (Senado) $\rightarrow$ Sanção/Veto Presidencial $\rightarrow$ Controle de Constitucionalidade no STF.

### 3. Executivo & Presidencialismo de Coalizão
* **Esplanada dos Ministérios:** Distribua **12 pastas ministeriais** entre os partidos para construir base aliada na Câmara e no Senado.
* **Orçamento Impositivo e Barganha:** Libere **Emendas de Bancada (RP9)** para elevar a satisfação das legendas ou utilize capital político para destravar votações difíceis.
* **Sanção e Veto Presidencial:** Matérias aprovadas nas duas Casas chegam à mesa da Presidência da República para **Sanção** (conversão em Lei) ou **Veto Total**, podendo o Congresso se reunir para apreciar a manutenção ou derrubada do veto.

### 4. Supremo Tribunal & Controle de Constitucionalidade
* **Plenário de 11 Ministros:** Cada magistrado possui um perfil hermenêutico (Garantista, Progressista, Moderado/Institucionalista, Conservador, Originalista) e um ponto no espectro ideológico.
* **Julgamento de ADIs:** Leis sancionadas podem ser alvo de **Ação Direta de Inconstitucionalidade (ADI)**. Caso a maioria absoluta (6 de 11 votos) julgue a norma procedente, a lei é anulada, gerando impacto na estabilidade institucional.
* **Aposentadoria, Indicação e Sabatina:** Simule a vacância de uma cadeira na Corte, indique um novo jurista pelo Executivo e submeta seu nome à **Sabatina no Senado Federal** (exigindo aprovação por maioria absoluta de **41 votos**).

### 5. Editor de Cenário (Modo Sandbox)
* **Reconfiguração de Bancadas:** Altere livremente a quantidade de cadeiras de cada partido na Câmara e no Senado com normalização automática para **513** e **81** assentos.
* **Clima Ideológico da Sociedade:** Desloque o eixo ideológico predominante na opinião pública, influenciando o comportamento dos parlamentares indecisos e a popularidade presidencial.
* **Presets Rápidos:** Carregue cenários prontos como *Fragmentação Extrema (Centrão Forte)*, *Polarização Ideológica*, *Supermaioria Governista* ou *Congresso Hostil*.

---

## Regras Regimentais e Quóruns Implementados

O motor de votação respeita as regras constitucionais e regimentais simplificadas para aprovação de cada espécie normativa:

| Espécie Normativa | Sigla | Quórum de Abertura | Quórum de Aprovação (Câmara - 513) | Quórum de Aprovação (Senado - 81) | Turnos por Casa |
| :--- | :---: | :---: | :--- | :--- | :---: |
| **Projeto de Lei Ordinária** | `PL` | 257 Dep. / 41 Sen. | Maioria Simples dos presentes | Maioria Simples dos presentes | 1 Turno |
| **Projeto de Lei Complementar** | `PLP` | 257 Dep. / 41 Sen. | **Maioria Absoluta (257 votos)** | **Maioria Absoluta (41 votos)** | 1 Turno |
| **Proposta de Emenda à Constituição** | `PEC` | 257 Dep. / 41 Sen. | **3/5 dos membros (308 votos)** | **3/5 dos membros (49 votos)** | **2 Turnos** |
| **Medida Provisória** | `MPV` | 257 Dep. / 41 Sen. | Maioria Simples dos presentes | Maioria Simples dos presentes | 1 Turno |

---

## Algoritmo de Decisão Parlamentar

Durante uma votação nominal, a probabilidade $P(\text{Sim})$ de cada parlamentar é calculada dinamicamente com base em cinco vetores:

1. **Alinhamento Ideológico:** Distância euclidiana entre a ideologia pessoal do parlamentar $(-100 \text{ a } +100)$ e o viés da proposição.
2. **Orientação de Bancada (*Whip*):** Se o líder partidário orientou `SIM` ou `NÃO`, o peso da decisão é modulado pelo atributo de **Disciplina Partidária** do congressista.
3. **Participação na Coalizão:** Peso do espaço ocupado pelo partido na Esplanada dos Ministérios em relação ao seu tamanho no Congresso.
4. **Execução Orçamentária:** Bônus direto concedido pela liberação de **Emendas Individuais (RP6)** ao parlamentar ou **Emendas de Bancada (RP9)** ao seu partido.
5. **Clima Social e Popularidade do Governo:** Pressão externa exercida pela opinião pública e pelo índice de aprovação presidencial.

---

## Partidos Políticos Fictícios

| Sigla | Nome do Partido | Espectro | Perfil Predominante |
| :---: | :--- | :---: | :--- |
| **MTP** | Movimento Trabalhista Progressista | Esquerda | Trabalhismo, Estado de bem-estar social e expansão de direitos sociais |
| **BVS** | Bloco Verde e Sustentável | Centro-Esquerda | Sustentabilidade, transição energética, direitos civis e inovação |
| **PSD-C** | Partido Social-Democrata Cristão | Centro | Pragmatismo, equilíbrio institucional e políticas sociais moderadas |
| **UDN** | União Democrática Nacional | Centro / Centrão | Fisiologismo pragmático, municipalismo, foco em emendas e governabilidade |
| **FL** | Frente Liberal | Centro-Direita | Livre mercado, responsabilidade fiscal, privatizações e desburocratização |
| **RC** | Renovação Conservadora | Direita | Conservadorismo nos costumes, segurança pública rigorosa e punitivismo |

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
