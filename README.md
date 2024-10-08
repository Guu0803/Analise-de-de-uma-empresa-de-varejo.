# PROCEDIMENTO/ATIVIDADE  

## ATIVIDADE PROPOSTA:  
Você trabalha em uma empresa de varejo e precisa analisar os dados de vendas do último ano para identificar padrões e insights para melhorar o desempenho. Os dados estão armazenados em um banco de dados SQLite, e você utilizará a biblioteca Pandas para manipular e analisar esses dados, além de gerar visualizações utilizando Matplotlib e Seaborn.

---

### Passo 1: Conectar ao banco de dados SQLite e criar uma tabela  
- Primeiro, você precisa estabelecer uma conexão com o banco de dados SQLite e carregar os dados relevantes para análise.

```python
import sqlite3

# Passo 1.1: Conectar ao banco de dados (ou criar, se não existir)
conexao = sqlite3.connect('dados_vendas.db')

# Passo 1.2: Criar um cursor
cursor = conexao.cursor()

# Passo 1.3: Criar uma tabela (se não existir)
cursor.execute('''
CREATE TABLE vendas1 (
    id_venda INTEGER PRIMARY KEY AUTOINCREMENT,
    data_venda DATE,
    produto TEXT,
    categoria TEXT,
    valor_venda REAL
)
''')

# Passo 1.4: Inserir alguns dados
cursor.execute('''
INSERT INTO vendas1 (data_venda, produto, categoria, valor_venda) VALUES
    ('2023-01-01', 'Produto A', 'Eletrônicos', 1500.00),
    ('2023-01-05', 'Produto B', 'Roupas', 350.00),
    ('2023-02-10', 'Produto C', 'Eletrônicos', 1200.00),
    ('2023-03-15', 'Produto D', 'Livros', 200.00),
    ('2023-03-20', 'Produto E', 'Eletrônicos', 800.00),
    ('2023-04-02', 'Produto F', 'Roupas', 400.00),
    ('2023-05-05', 'Produto G', 'Livros', 150.00),
    ('2023-06-10', 'Produto H', 'Eletrônicos', 1000.00),
    ('2023-07-20', 'Produto I', 'Roupas', 600.00),
    ('2023-08-25', 'Produto J', 'Eletrônicos', 700.00),
    ('2023-09-30', 'Produto K', 'Livros', 300.00),
    ('2023-10-05', 'Produto L', 'Roupas', 450.00),
    ('2023-11-15', 'Produto M', 'Eletrônicos', 900.00),
    ('2023-12-20', 'Produto N', 'Livros', 250.00);
''')

# Passo 1.5: Confirmar as mudanças
conexao.commit()