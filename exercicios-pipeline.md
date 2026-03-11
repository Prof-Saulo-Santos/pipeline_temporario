# Exercícios Práticos: Pipeline de Pré-processamento (Estilo Titanic)

Para consolidar as técnicas aprendidas nesta aula (Análise Exploratória [EDA], imputação de nulos, tratamento de outliers, encoding de variáveis categóricas e balanceamento de classes como o SMOTE), o ideal é praticar em bases de **Classificação Binária** que possuam características reais (ou seja, dados "sujos" na medida certa e mistura de formatos categóricos e numéricos).

Abaixo estão três dos melhores datasets do Kaggle para você treinar e aprimorar suas habilidades de Engenharia de Dados e Machine Learning:

---

### 1. Spaceship Titanic (O Sucessor Espiritual)
**Link:** [Kaggle - Spaceship Titanic](https://www.kaggle.com/competitions/spaceship-titanic)

*   **A História:** É literalmente a versão sci-fi e atualizada do desafio original, mantida pela própria equipe do Kaggle! O ano é 2912, e a espaçonave *Titanic* se chocou com uma anomalia espacial. Metade dos passageiros foi transportada para uma dimensão alternativa. A missão é prever quem foi transportado (Target = `Transported`).
*   **Por que praticar neste dataset?**
    *   Possui a mesma estrutura do desafio clássico do Titanic, porém com mais variáveis (14 *features*).
    *   Contém colunas categóricas excelentes para treinar Encoding (como Planeta de Origem, Destino e o status de "CryoSleep" - sono criogênico).
    *   Possui dados numéricos com distorções financeiras (Right-skewed) que exigem Transformação Logarítmica e uso de scalers (como os gastos com "RoomService", "FoodCourt" e "Spa").
    *   A coluna de cabines (`Cabin`) vem num formato composto (`deck/num/side`, ex: `A/0/S`), permitindo o treino de Engenharia de Features (Feature Engineering) com manipulação de strings em Python para extrair novas colunas.
    *   Apresenta dados nulos espalhados por todo o dataset, forçando a aplicação e a escolha entre Média, Mediana ou Moda durante a etapa de limpeza.

---

### 2. Churn Modelling (Previsão de Evasão Bancária)
**Link:** [Kaggle - Bank Customer Churn Prediction](https://www.kaggle.com/datasets/barelydedicated/bank-customer-churn-modeling)

*   **A História:** Um banco europeu com operações em 3 países quer descobrir o perfil de clientes que fecham a conta e abandonam a instituição (Target = `Exited`). É um dos problemas clássicos e mais procurados pelo mercado de trabalho contemporâneo.
*   **Por que praticar neste dataset?**
    *   **Desbalanceamento Severo:** Essa base é incrível para treinar a técnica **SMOTE**. A esmagadora maioria das pessoas (cerca de 80%) NÃO sai do banco. Se você rodar um modelo preditivo sem balancear, ele "mentirá" informando uma acurácia de 80% apenas prevendo que ninguém nunca sai.
    *   Requer a aplicação de *One-Hot Encoding* (*pd.get_dummies*) em features categóricas cruciais como Geografia (País) e Gênero.
    *   Possui features colossais (como `Balance` - Saldo em Conta, e `EstimatedSalary` - Salário Estimado) que precisam obrigatoriamente do `StandardScaler`.
    *   Contém colunas que não agregam valor analítico e devem ser dropadas, como `RowNumber`, `CustomerId` e `Surname` (Sobrenome), provando a regra de ouro: "IDs não preveem comportamento".

---

### 3. IBM Telco Customer Churn
**Link:** [Kaggle - Telco Customer Churn](https://www.kaggle.com/datasets/blastchar/telco-customer-churn)

*   **A História:** Um banco de dados real disponibilizado pela gigantesca IBM. Mostra clientes de uma empresa de Telecomunicações que assinam serviços de Internet e Telefone, focando em descobrir quem cancelou a assinatura (Target = `Churn`).
*   **Por que praticar neste dataset?**
    *   **O Rei do Encoding:** Essa base transborda variáveis categóricas dicotômicas ("Sim", "Não", "Sem Serviço"). Você precisará aplicar técnicas de Label Encoding ou One-Hot Encoding consistentemente em colunas como `InternetService`, `OnlineSecurity`, `TechSupport` e `Contract`.
    *   **Problemas reais do cotidiano de um Cientista de Dados:** A coluna numérica `TotalCharges` (Total Cobrado) frequentemente é carregada pelo Pandas como uma `string` (texto). Isso ocorre porque clientes recém-cadastrados, que ainda não geraram fatura, têm o campo preenchido incorretamente pela IBM com um **espaço em branco** (`" "`). Isso quebra os códigos! Você terá que forçar a coerção numérica usando `pd.to_numeric(errors='coerce')` e lidar com os Nulos inesperados que surgem dessa conversão.
    *   Trata-se de uma base levemente desbalanceada, ótima ferramenta para compor seu arsenal de portfólio.
