# Modelo Conceitual e Relacional – E-commerce

## Descrição do Projeto
Este projeto apresenta o **modelo conceitual e o modelo relacional** de um sistema de **e-commerce**, desenvolvido como parte de um desafio de banco de dados.  
O objetivo é modelar uma aplicação que permita o gerenciamento de **clientes (Pessoa Física e Jurídica)**, **produtos**, **pedidos**, **formas de pagamento** e **entregas**, aplicando boas práticas de modelagem e normalização.

O trabalho foi elaborado a partir de regras de negócio pré-definidas e refinadas para atender cenários reais de um comércio eletrônico, garantindo integridade, escalabilidade e clareza na estrutura dos dados.


---

## Regras de Negócio Implementadas
1. **Cliente PF/PJ exclusivo**  
   - Uma conta pode ser **Pessoa Física (PF)** ou **Pessoa Jurídica (PJ)**, mas nunca as duas ao mesmo tempo.
   - Regra implementada com atributo `tipo_cliente` e `CHECK` para validar CPF ou CNPJ.
   
2. **Pagamentos múltiplos**  
   - Cada cliente pode cadastrar **várias formas de pagamento** (cartões, Pix, boletos).
   - A tabela `metodo_pagamento` permite armazenar diferentes meios para uso em pedidos futuros.
   
3. **Entrega com rastreio**  
   - Cada pedido possui uma **entrega vinculada (1:1)**.
   - Campos obrigatórios: `status` (pendente, postado, em trânsito, entregue, devolvido) e `codigo_rastreio`.

---

## Estrutura do Banco de Dados

O modelo foi dividido em entidades principais:

- **cliente** – cadastro básico com dados pessoais/jurídicos e tipo (PF/PJ).
- **endereco** – endereços vinculados ao cliente.
- **produto** – informações sobre produtos disponíveis no e-commerce.
- **pedido** – registro da compra, vinculando cliente, endereço e status.
- **item_pedido** – itens e quantidades de cada pedido.
- **metodo_pagamento** – formas de pagamento cadastradas pelo cliente.
- **pagamento** – transações de pagamento para cada pedido.
- **entrega** – status e rastreamento de cada pedido.

---

## Modelo Conceitual (ERD)
O diagrama foi criado no [dbdiagram.io](https://dbdiagram.io) e exportado como imagem:

 *Arquivo*: `diagram.png`  
![Diagrama ERD](diagram.png)

---

## Modelo Relacional (MySQL)
O script SQL (`schema.sql`) contém:
- Criação de todas as tabelas.
- Definição de **chaves primárias** e **estrangeiras**.
- **Constraints** para validação de PF/PJ.
- Relacionamentos N:N e 1:N implementados corretamente.

---

## Decisões de Modelagem
- **PF/PJ exclusivo:** regra de negócio implementada com `CHECK` garantindo que apenas um dos campos `cpf` ou `cnpj` seja preenchido conforme o `tipo_cliente`.
- **Pagamentos múltiplos:** criada tabela separada (`metodo_pagamento`) para suportar diversas formas de pagamento por cliente.
- **Entrega 1:1:** definida tabela `entrega` com `pedido_id` único, garantindo que cada pedido tenha apenas uma entrega vinculada.

---

## Como Utilizar
1. Clone o repositório:
   ```bash
   git clone https://github.com/usuario/nome-repositorio.git
   
