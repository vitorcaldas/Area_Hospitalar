# Área Hospitalar

# 🏥 Análise de Gestão de Leitos e Pacientes Hospitalares

Este projeto tem como objetivo resolver alguns gargalos no controle e acompanhamento de leitos, com a missão de propor, construir e apresentar uma solução digital simples para minimizar ações manuais e prover melhor assertividade nos controles.

---

## 🛠️ Tecnologias e Bibliotecas Utilizadas

O projeto foi desenvolvido em **Python 3.13+** utilizando os seguintes pacotes:
* **[Pandas](https://pandas.pydata.org/)**: Manipulação, limpeza e transformação de dados tabulares.
* **[Matplotlib](https://matplotlib.org/)**[cite: 2]: Criação de gráficos estáticos, personalizados e visualizações.
* **[Seaborn](https://seaborn.pydata.org/)**[cite: 2]: Interface de alto nível para gráficos estatísticos atraentes.
* **Openpyxl / Excel Engines**: Leitura e exportação de arquivos no formato `.xlsx`.
* **Power BI**: Criação de um dasboard interativo `.pbix`

---

## 📂 Estrutura do Conjunto de Dados

O projeto consome e processa três fontes principais de dados:
1. **`Dados_Tratados.xlsx` (Aba *Leitos*)**[cite: 2]: Contém informações cadastrais e operacionais dos leitos hospitalares (ID, Setor, Tipo, Status atual, paciente associado e datas de movimentação).
2. **`Dados_Tratados.xlsx` (Aba *Pacientes*)**[cite: 2]: Contém o perfil dos pacientes internados (ID, Idade, Sexo, Faixa Etária e Tipo de Internação).
3. **`eventos_movimentacao.csv`**[cite: 2]: Registro histórico de eventos de movimentação, admissões e altas.

---

## ⚙️ Etapas do Pipeline de Análise (Data Pipeline)

O script executa as seguintes etapas no tratamento e análise dos dados:

1. **Carregamento dos Dados:** Importação segura via `pandas` a partir de planilhas Excel e arquivos CSV delimitados por ponto e vírgula[cite: 2].
2. **Tratamento de Colunas e Tipos:** 
   * Padronização e renomeação de colunas para facilitar o acesso programático.
   * Conversão de colunas de texto para o formato `datetime` (datas de ocupação e liberação) com tratamento de erros (`errors='coerce'`).
   * Tratamento de valores nulos (ex: preenchimento de campos de pacientes ausentes com a tag `'sem paciente'`).
3. **Enriquecimento de Dados (Feature Engineering):**
   * Criação de uma coluna de **Classificação de Idade** baseada na faixa etária dos pacientes:
     * *Menor de idade* ($\le 17$ anos)
     * *Adulto* ($18$ a $60$ anos)
     * *Melhor idade* ($> 60$ anos)
4. **Agregações e Estatísticas Descritivas:**
   * Contagem de leitos por status (*Ocupado, Livre, Manutenção, Limpeza*).
   * Distribuição espacial por setor (*Enfermaria, UTI, Pediatria, Maternidade*).

---

## 📊 Principais Visualizações Geradas

O código gera automaticamente gráficos analíticos para apoiar a tomada de decisão médica e administrativa:
* **Distribuição de Leitos por Status Atual:** Gráfico de contagem evidenciando a proporção de leitos ocupados vs. disponíveis ou em manutenção.
* **Distribuição de Leitos por Setor:** Panorama quantitativo da infraestrutura por alas hospitalares.
* **Leitos Ocupados por Setor:** Visão específica da pressão de ocupação em cada departamento crítico.
* **Leitos em Manutenção / Limpeza por Setor:** Identificação de gargalos operacionais na liberação de infraestrutura.

---

## 🚀 Como Executar o Projeto

1. Certifique-se de ter o Python instalado em sua máquina.
2. Instale as dependências necessárias executando:
   ```bash
   pip install pandas matplotlib seaborn openpyxl
