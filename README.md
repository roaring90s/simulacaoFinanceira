# Simulação de Investimento e Dashboard Financeiro

Este projeto é uma planilha Excel que simula o crescimento do patrimônio financeiro baseado em aportes mensais, perfil de investimento e taxas de rendimento. Além disso, possui um dashboard dinâmico para visualização clara dos resultados e alocações.

---

## Estrutura do Projeto

### 1. Aba **INPUTS**  
Armazena os parâmetros fixos e variáveis do usuário, como:  
- Salário  
- Sugestão de investimento (% do salário)  
- Horizonte de investimento (em meses)  
- Inflação anual (%)  
- Rendimentos estimados para renda fixa e variável (%)  
- Alocação percentual em renda fixa  
- Contribuição extra mensal  
- Alíquota de imposto de renda (%)  
- Meta final de patrimônio  

Esses dados alimentam os cálculos da simulação.

---

### 2. Aba **ATIVOS**  
Contém a base de dados dos tipos de fundos imobiliários (FIIs) com suas respectivas alocações percentuais por perfil (Conservador, Moderado, Agressivo).  

Exemplo de estrutura:  
| CHAVE             | PERFIL    | TIPO DE FII    | %   |  
|-------------------|-----------|----------------|-----|  
| Moderado-PAPEL    | Moderado  | PAPEL          | 32% |  
| Moderado-TIJOLO   | Moderado  | TIJOLO         | 35% |  
| ...               | ...       | ...            | ... |  

Esses dados são usados para cálculo de alocação no dashboard.

---

### 3. Aba **SIMULAÇÃO**  
Realiza os cálculos financeiros complexos com base nos inputs:  
- Converte o tempo de investimento em meses  
- Calcula o patrimônio acumulado usando fórmula de valor futuro (`VF`) considerando aporte mensal, taxa de rendimento e tempo  
- Calcula dividendos mensais estimados  
- Gera cenários de patrimônio e dividendos para diferentes horizontes (2, 5, 10, 20, 30 anos)  

Essa aba é a “fábrica” dos resultados financeiros.

---

### 4. Aba **DASHBOARD**  
Apresenta os dados prontos para o usuário, organizados para fácil visualização:  
- Seleção do perfil de investimento  
- Valor a ser investido por mês  
- Indicadores principais: patrimônio acumulado, dividendos mensais, taxa de rendimento média, progresso até a meta  
- Tabela de alocação detalhada por tipo de FII, puxando os percentuais da aba ATIVOS e multiplicando pelo valor investido  
- Gráficos dinâmicos:  
  - Gráfico de pizza mostrando a distribuição dos investimentos por tipo de FII  
  - Gráfico de linha mostrando a evolução do patrimônio ao longo dos anos, com base nos cenários da aba SIMULAÇÃO  

O dashboard não realiza cálculos, apenas puxa e organiza os dados de outras abas para facilitar a interpretação.

---

## Fluxo de Dados e Dependências

- O usuário configura parâmetros na aba **INPUTS**.  
- A aba **SIMULAÇÃO** usa esses parâmetros para calcular resultados financeiros e cenários.  
- A aba **ATIVOS** fornece a estrutura da carteira para diferentes perfis.  
- O **DASHBOARD** referencia as três abas anteriores para apresentar uma visão clara e visual dos dados, tornando o acompanhamento simples e intuitivo.

---

## Observações Técnicas

- Todas as fórmulas de cálculo consideram consistência nas unidades, especialmente taxas mensais versus anuais.  
- Os gráficos são inseridos no DASHBOARD, mas puxam os dados diretamente da aba SIMULAÇÃO para manter atualização automática.  
- As fórmulas de procura (`PROCV`) são usadas para relacionar perfil e alocação de ativos dinamicamente.  
- O eixo dos gráficos é configurado manualmente para melhor legibilidade, evitando marcações automáticas pouco intuitivas.  

---

Esse projeto é um ponto de partida funcional para simulações financeiras focadas em fundos imobiliários e pode ser facilmente adaptado para outras classes de ativos.

