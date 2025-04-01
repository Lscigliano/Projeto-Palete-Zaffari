# 💼 Projeto de Cobrança de Paletes

## 🚀 Tecnologias Utilizadas

- **PL/SQL - Oracle**
- **API REST**
- **ERP Consinco**
  **Foi utilizado API, pois para criar automaticamente um pedido via insert no banco diretamente, era mais complexo, visto que as tabelas necessárias eram mais de 6, com a API, era mais simples apenas fazendo uma requisição POST.
---

## 🎯 Objetivo do Projeto

Automatizar o processo de **cobrança de paletes**, onde o usuário informa a **nota fiscal de entrada de terceiros** e o sistema realiza o **cálculo automático** do valor a ser cobrado do fornecedor.

Esse valor pode ser:

- Baseado em um **padrão previamente estabelecido**, ou  
- Calculado por **média de quantidade**, caso o padrão não exista.

Com o cálculo automático:

- Será gerada uma **pré-venda** com o produto chamado, por exemplo, **"Serviço Palete"**.
- O valor da cobrança será inserido automaticamente.
- Evita **fraudes e alterações manuais indevidas**, protegendo a tesouraria.

---

## 🚚 Fluxo do Processo

### 1. Chegada do Caminhão

Se o fornecedor precisar de **serviço de descarga**, a solicitação é feita para a **equipe de logística**.

---

### 2. Consulta e Cálculo da Cobrança

O cálculo do valor é feito via sistema:


---

### 3. Criação do Pedido de Venda

Caso o motorista esteja com o valor da cobrança:


O operador deve preencher:

- Número da loja  
- Nota fiscal a ser cobrada  
- CNPJ (se necessário faturar em nome de terceiro)  
  - Se for o mesmo CNPJ do fornecedor, informar **valor "0"**

Após a confirmação:

- Um **pedido de venda** é gerado automaticamente.
- Se já existir pedido anterior para a mesma nota:
  - O **pedido anterior é cancelado**.
  - A **sequência do novo pedido é mantida**.
- Se o valor da cobrança for **isento**, o pedido é **cancelado automaticamente**.

---

### 4. Execução do Serviço de Descarga

O serviço é realizado **após o pagamento** do pedido de venda.

---

### 5. Conferência e Entrada da Carga

- Realizar a **conferência** da carga.  
- Dar **entrada nas notas fiscais** vinculadas.

---

### 6. Controle Financeiro

Após a entrada da nota fiscal:

> A nota será exibida no relatório:  
> **Palete > Cobrança de Descarga > Financeiro - Paletes**
