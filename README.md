# 🏭 Dashboard de Acompanhamento de Produção vs. Metas (Power BI)

![Visão Anual](assets/visao_anual.png)

## 📌 Visão Geral do Projeto
Painel executivo e operacional desenvolvido no **Microsoft Power BI** para monitorar o desempenho de uma linha de produção frente às metas estabelecidas (mensais e anuais)[cite: 16]. A solução permite à gestão de operações identificar rapidamente desvios de performance por período, produto, maquinário e turno de trabalho.

---

## 🎯 Problema de Negócio
A área de Operações precisava consolidar os apontamentos diários de produção e cruzá-los com o planejamento de metas para responder a perguntas estratégicas:
- Qual o percentual atual de atingimento da meta (mensal e acumulado no ano).
- Em quais meses ou dias específicos ocorreram quedas de rendimento em relação ao planejado.
- Quais produtos, máquinas ou turnos estão impactando negativamente o resultado.

---

## 🏗️ Arquitetura e Modelagem de Dados
O modelo foi estruturado no formato **Constelação de Fatos (Galaxy Schema)**, garantindo integridade referencial e evitando ambiguidades entre diferentes granularidades de dados:

![Modelo de Dados](assets/modelo_dados.png)

- **Tabelas Fato:**
  - `f_Producao`: Registros de volume produzido por data, máquina, produto e turno.
  - `f_Meta`: Planejamento de metas estabelecidas por data, máquina, produto e turno.
- **Tabelas Dimensão:**
  - `d_Calendario`, `d_Maquina`, `d_Produto` e `d_Turno` (filtrando ambas as tabelas fato em relacionamento `1:*`).
- **Tabela de Métricas:**
  - `#Medidas`: Repositório centralizado de cálculos DAX (`% Produção vs Meta`, indicadores acumulados e regras de formatação condicional).

---

## 📊 Estrutura do Painel e Insights Obtidos

### 1. Visão Anual de Metas
- **Recorte Temporal:** Os registros de apontamento produtivo compreendem o período de **01/01 a 05/10**, enquanto o planejamento de metas contempla todo o exercício anual (Jan a Dez).
- **KPI Principal:** Medidor de atingimento global (**72,19%**, representando **8 Mi** produzidos frente à meta anual total de **11 Mi**).
- **Evolução Acumulada:** Comparativo progressivo mostrando que a produção acompanhou o ritmo da meta nos primeiros meses, apresentando leve descolamento a partir de agosto e encerrando a janela de dados em 05/10 com **7,9 Mi** acumulados (considerando que outubro possui apenas 5 dias apurados).
- **Performance Mensal:** Gráfico de colunas com **formatação condicional dinâmica**, destacando em vermelho os meses que ficaram abaixo da meta mensal (como Janeiro, Abril, Julho, Agosto e o parcial de Outubro) e em verde/azul os meses que superaram o planejado (Fevereiro e Março).

### 2. Visão Mensal de Metas
![Visão Mensal](assets/visao_mensal.png)
- **Detalhamento Diário:** Ao selecionar um mês específico (ex.: Julho, com **73,34%** de atingimento e **879 Mil** unidades produzidas), o painel exibe a curva acumulada diária (desvio de **-27%**, com `0,88 Mi` realizados frente a `1,20 Mi` previstos) e o comportamento dia a dia da operação frente à meta[cite: 18].
- **Navegação & UX:** Botões interativos no cabeçalho permitem alternar fluidamente entre as visões Anual e Mensal, acompanhados de segmentadores dinâmicos por **Máquina**, **Produto** e **Turno**.

---

## 🛠️ Tecnologias e Técnicas Utilizadas
- **Power BI Desktop** (Modelagem dimensional, DAX avançado e formatação condicional)
- **UI/UX Design:** Layouts escuros customizados em SVG (`Visão Anual` e `Visão Mensal`) para reduzir a fadiga visual e destacar os indicadores críticos.

---

## 📁 Estrutura do Repositório
- `Projeto 2 - Acompanhamento de Produção vs Metas.pbix`: Arquivo principal do Power BI.
- `/assets`: Capturas de tela das páginas do dashboard e do modelo de dados.
<img width="1554" height="742" alt="image" src="https://github.com/user-attachments/assets/ed35d2b9-a575-40e9-93a8-de2900ff2639" />
<img width="1418" height="796" alt="image" src="https://github.com/user-attachments/assets/6565cd9e-ba9d-494d-b909-f49713bd2ba1" />
<img width="1421" height="798" alt="image" src="https://github.com/user-attachments/assets/b2fa8b95-78ec-45df-8d97-bb384212478d" />
