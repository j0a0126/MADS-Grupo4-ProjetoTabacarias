# MADS-Grupo4-ProjetoTabacarias

Biblioteca Python para gestão e análise de dados de tabacarias.

O módulo trabalha em memória e disponibiliza funções para:
- registo e listagem de tabacarias, produtos e utilizadores;
- registo e consulta de vendas;
- análise de desempenho (ranking);
- visualização em gráficos;
- visualização em mapa.

---

## Instalação

### A partir do PyPI

```bash
pip install mads-tabacarias
```

---

## Importação

```python
from mads_tabacarias import *
```


---

## Estrutura de dados (em memória)

O módulo mantém quatro estruturas globais:
- tabacarias (dict)
- produtos (dict)
- vendas (list)
- utilizadores (dict)

Isto significa que os dados existem apenas durante a execução do programa.

---

## Fluxo recomendado

1. Registar tabacarias com registar_tabacaria.
2. Registar produtos com registar_produto.
3. Registar utilizadores com registar_utilizador.
4. Registar vendas com registar_venda.
5. Consultar dados, ranking, gráficos e mapa.

---

## API Principal

### Registos

#### registar_tabacaria(nome, morada, horario, latitude, longitude)
Regista uma tabacaria.

Validações:
- todos os campos obrigatórios;
- latitude entre -90 e 90;
- longitude entre -180 e 180;
- nome único.

---

#### registar_produto(nome, tipo, preco)
Regista um produto.

Validações:
- nome e tipo obrigatórios;
- preço numérico e positivo;
- produto não pode existir previamente.

---

#### registar_utilizador(nome, nif)
Regista um utilizador.

Validações:
- NIF com 9 dígitos numéricos;
- utilizador único.

---

#### registar_venda(tabacaria, produto, quantidade)
Regista uma venda.

Regras:
- tabacaria e produto devem existir;
- quantidade inteira e positiva;
- cálculo automático do total.

---

### Listagens

- consultar_tabacarias()
- consultar_vendas()
- consultar_vendas_por_tabacaria(nome)

Estas funções apresentam informação diretamente no terminal.

---

### Ranking

#### ranking_tabacarias()
Apresenta ranking de tabacarias por volume de vendas.

---

### Gráficos

- grafico_vendas_tabacaria()
- grafico_produtos()

Permitem visualizar:
- total de vendas por tabacaria;
- produtos mais vendidos.

---

### Mapa

#### mapa()

Gera visualização de tabacarias num mapa com Folium.

Comportamento:
- utiliza coordenadas registadas;
- apresenta o mapa no ambiente interativo.

---

## Exemplo completo

```python
from mads_tabacarias import *

# Registos
registar_tabacaria("Loja Central", "Rua A, Porto", "08:00-20:00", 41.23, -8.62)
registar_produto("Jornal Público", "Jornal", 1.5)
registar_utilizador("Joao", "123456789")

# Venda
registar_venda("Loja Central", "Jornal Público", 10)

# Consultas
consultar_tabacarias()
consultar_vendas()

# Ranking
ranking_tabacarias()

# Gráficos
grafico_vendas_tabacaria()
grafico_produtos()

# Mapa
mapa()
```

---

## Notas importantes

- **Validação de coordenadas**:
  - Latitude entre -90 e 90
  - Longitude entre -180 e 180

- **Validação de NIF**:
  - Deve conter 9 dígitos

- **Validação de dados**:
  - Preços e quantidades devem ser positivos
  - Entidades devem existir antes de registar vendas

---


