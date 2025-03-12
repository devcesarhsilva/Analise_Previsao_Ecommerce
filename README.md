📊 Análise de Vendas e Previsão de Receita em E-commerce 🚀
🔍 Visão Geral
Este projeto realiza a análise de vendas de um e-commerce fictício, utilizando Python, SQLite e Power BI. Além da exploração dos dados, também implementamos um modelo de previsão de receita baseado em regressão linear.

📁 Estrutura do Projeto
📂 analise-vendas-ecommerce
├── 📜 ecommerce.db (Banco de dados SQLite com as vendas)
├── 📜 analise_vendas.ipynb (Notebook com a análise em Python)
├── 📜 dados_vendas.csv (Arquivo exportado para o Power BI)
├── 📜 dashboard.pbix (Dashboard criado no Power BI)
├── 📜 README.md (Este arquivo explicativo)

🚀 Tecnologias Utilizadas
🐍 Python (Pandas, SQLite, Matplotlib, Seaborn, Scikit-Learn)
🗃️ SQLite (Banco de Dados)
📊 Power BI (Dashboard interativo)
📂 Git & GitHub (Versionamento de código)
📌 Passo a Passo do Projeto
🔹 1️⃣ Coletando os Dados
Criamos um banco de dados SQLite com informações de vendas, como data, categoria, produto, quantidade e receita.

python
Copiar
Editar
import sqlite3
import pandas as pd

# Conectar ao banco de dados
conn = sqlite3.connect("ecommerce.db")

# Carregar os dados
df = pd.read_sql_query("SELECT * FROM vendas", conn)
conn.close()

# Exibir as primeiras linhas
print(df.head())
🔹 2️⃣ Análise Exploratória de Dados (EDA)
Utilizamos Pandas e Seaborn para entender os padrões das vendas, como receita por categoria e evolução ao longo do tempo.

python
Copiar
Editar
import seaborn as sns
import matplotlib.pyplot as plt

sns.barplot(x=df["categoria"], y=df["receita"], estimator=sum, ci=None, palette="viridis")
plt.title("Receita Total por Categoria")
plt.xlabel("Categoria")
plt.ylabel("Receita (R$)")
plt.show()
🔹 3️⃣ Criando um Modelo de Previsão
Implementamos uma regressão linear para prever a receita com base nos dados históricos.

python
Copiar
Editar
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LinearRegression
from sklearn.metrics import mean_absolute_error

X = df[["quantidade", "preco_unitario"]]
y = df["receita"]

X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

modelo = LinearRegression()
modelo.fit(X_train, y_train)

y_pred = modelo.predict(X_test)
erro = mean_absolute_error(y_test, y_pred)
print(f"Erro médio absoluto: R$ {erro:.2f}")
🔹 4️⃣ Criando um Dashboard no Power BI
Os dados foram exportados para CSV e carregados no Power BI para criar um dashboard interativo.

python
Copiar
Editar
df.to_csv("dados_vendas.csv", index=False)
📊 Dashboard Power BI
<img src="dashboard.png" width="600">
⚡ Inclui:

Receita total por categoria
Evolução da receita ao longo do tempo
Produtos mais vendidos
🛠️ Como Executar o Projeto
1️⃣ Clone o repositório:

bash
Copiar
Editar
git clone https://github.com/seu-usuario/analise-vendas-ecommerce.git
2️⃣ Instale as dependências:

bash
Copiar
Editar
pip install pandas numpy matplotlib seaborn scikit-learn
3️⃣ Rode o código no Jupyter Notebook ou VS Code.
4️⃣ Abra dashboard.pbix no Power BI para visualizar os gráficos.

📌 Conclusão
✅ Exploramos dados de vendas para extrair insights importantes
✅ Criamos um modelo simples para prever faturamento
✅ Desenvolvemos um dashboard interativo no Power BI
✅ Publicamos nosso projeto no GitHub para fortalecer nosso portfólio