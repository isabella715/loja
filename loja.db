import sqlite3

# Conecta (ou cria) o banco de dados
conn = sqlite3.connect("loja.db")
cursor = conn.cursor()

# Criar tabela Cliente
cursor.execute("""
CREATE TABLE IF NOT EXISTS Cliente (
    id_cliente INTEGER PRIMARY KEY AUTOINCREMENT,
    nome TEXT,
    email TEXT,
    telefone TEXT,
    endereco TEXT
);
""")

# Criar tabela Produto
cursor.execute("""
CREATE TABLE IF NOT EXISTS Produto (
    id_produto INTEGER PRIMARY KEY AUTOINCREMENT,
    nome TEXT,
    preco REAL,
    estoque INTEGER,
    categoria TEXT
);
""")

# Criar tabela Pedido
cursor.execute("""
CREATE TABLE IF NOT EXISTS Pedido (
    id_pedido INTEGER PRIMARY KEY AUTOINCREMENT,
    data TEXT,
    status TEXT,
    id_cliente INTEGER,
    FOREIGN KEY (id_cliente) REFERENCES Cliente(id_cliente)
);
""")

# Criar tabela Pagamento
cursor.execute("""
CREATE TABLE IF NOT EXISTS Pagamento (
    id_pagamento INTEGER PRIMARY KEY AUTOINCREMENT,
    tipo_pagamento TEXT,
    valor REAL,
    id_pedido INTEGER,
    FOREIGN KEY (id_pedido) REFERENCES Pedido(id_pedido)
);
""")

# Criar tabela Fornecedor
cursor.execute("""
CREATE TABLE IF NOT EXISTS Fornecedor (
    id_fornecedor INTEGER PRIMARY KEY AUTOINCREMENT,
    nome TEXT,
    telefone TEXT
);
""")

# Criar tabela ItemPedido (ligação entre Pedido e Produto)
cursor.execute("""
CREATE TABLE IF NOT EXISTS ItemPedido (
    id_item INTEGER PRIMARY KEY AUTOINCREMENT,
    id_pedido INTEGER,
    id_produto INTEGER,
    quantidade INTEGER,
    preco_unitario REAL,
    FOREIGN KEY (id_pedido) REFERENCES Pedido(id_pedido),
    FOREIGN KEY (id_produto) REFERENCES Produto(id_produto)
);
""")

print("Tabelas criadas com sucesso!")
conn.commit()
conn.close()
