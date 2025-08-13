# Challenge Telecom X (Parte 1)

## 📜 Sobre o Desafio
Este projeto foi desenvolvido como parte de um desafio de Análise de Evasão de Clientes (Churn) para a empresa fictícia Telecom X.
A companhia enfrenta um elevado índice de cancelamentos de serviços e busca compreender os fatores que levam os clientes a encerrar o contrato.

O papel designado foi atuar como assistente de análise de dados, sendo responsável por coletar, tratar e explorar o conjunto de dados, utilizando Python e suas principais bibliotecas para gerar insights estratégicos.
Essas análises servirão como base para que a equipe de Data Science avance no desenvolvimento de modelos preditivos e na criação de estratégias para reduzir a evasão.

## 🎯 Objetivos do Desafio
- Coletar e manipular dados a partir de uma API de forma eficiente.
- Aplicar conceitos de ETL (Extração, Transformação e Carga) para preparar os dados.
- Criar visualizações estratégicas para identificar padrões e tendências.
- Realizar Análise Exploratória de Dados (EDA) com foco em entender o comportamento de evasão.
- Gerar um relatório visual com insights relevantes para apoiar decisões.

## 🧽 Limpeza e Tratamento de Dados
| Etapa | Descrição                                                                                          | Código Utilizado                                                                                                                         |
| ----- | -------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------- |
| **1** | Remoção de duplicatas para evitar linhas repetidas.                                                | `df_Telecom = df_Telecom.drop_duplicates()`                                                                                              |
| **2** | Correção de valores textuais na coluna **account Contract** (substituição de hífen por espaço).    | `df_Telecom['account Contract'] = df_Telecom['account Contract'].str.replace('-', ' ', regex=True)`                                      |
| **3** | Remoção da string **"(automatic)"** da coluna **account PaymentMethod** para padronização.         | `df_Telecom['account PaymentMethod'] = df_Telecom['account PaymentMethod'].str.replace(' (automatic)', ' ')`                             |
| **4** | Substituição de valores em branco por `"0"` na coluna **account Charges Total** para tratar nulos. | `df_Telecom['account Charges Total'] = df_Telecom['account Charges Total'].replace(' ', '0')`                                            |
| **5** | Conversão da coluna **account Charges Total** para tipo `float64`.                                 | `df_Telecom['account Charges Total'] = df_Telecom['account Charges Total'].astype(np.float64)`                                           |
| **6** | Conversão das colunas **customer SeniorCitizen** e **customer tenure** para tipo `int64`.          | `df_Telecom[['customer SeniorCitizen', 'customer tenure']] = df_Telecom[['customer SeniorCitizen', 'customer tenure']].astype(np.int64)` |
| **7** | Criação da coluna derivada **Contas\_Diarias** (média diária das cobranças mensais).               | `df_Telecom['Contas_Diarias'] = df_Telecom['account Charges Monthly'] / 30`                                                              |

## 📊 Análise Exploratória de Dados
- Elaboração de 6 gráficos que representam de forma visual a relação e percentual de Churn em clientes de acordo com o histórico e perfil de cada cliente.
<img width="5970" height="2955" alt="resumo_evasao_clientes" src="https://github.com/user-attachments/assets/6dd6f724-02c7-4caa-bd38-884ed5fa4439" />

## 💡 Conclusões e Insights
- O gênero dos clientes não possuem relação com o percentual de churn.
- 41,9% dos clientes que contrataram o serviço de internet por fibra óptica optaram por cancelar o serviço.
- Clientes com menor tempo de contrato apresentam maior risco de evasão. Podemos observar que 42,7% dos clientes que optaram por contrato mensal, fizeram o cancelamento do serviço.
- Clientes idosos também possuem um percentual maior de cancelamento, representando 41,7% dos cancelamentos.
- Contratos recentes e consumo baixo podem indicar propensão a cancelar.
- Identificar grupos de clientes em risco permite ações proativas, as visualizações ajudam a segmentar clientes e priorizar campanhas de retenção.

## ✨ Recomendações
- Desenvolver programas de fidelização para clientes com menor tempo de contrato.
- Oferecer incentivos personalizados para planos e formas de pagamento com maior churn.
- Monitorar consumo e engajamento dos clientes para identificar risco de cancelamento antecipadamente.
- Criar dashboards internos com alertas de churn para equipe de atendimento.
- Oferecer um suporte mais atendo à clientes novos e/ou idosos.
- Analisar estrutura do serviço de internet por fibra óptica e verificar se há a possibilidade de melhorias.

