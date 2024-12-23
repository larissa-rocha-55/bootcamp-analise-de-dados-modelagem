# bootcamp-analise-de-dados-modelagem

# OBJETIVO

Refinar um modelo de aplicação de e-commerce seguindo os seguintes itens:

- **Cliente PJ e PF**  
  Uma conta pode ser PJ ou PF, mas não pode ter as duas informações.
  
- **Pagamento**  
  Pode ter cadastrado mais de uma forma de pagamento (data de validade, informações, nome - coloca como atributo de cliente ou como entidade?).
  
- **Entrega**  
  Possui status e código de rastreio.

# RESULTADOS

## Cliente PJ e PF

- **Descrição**: Uma conta pode ser PJ ou PF, mas não pode ter as duas informações.
- **Decisão**: Foi optado por criar uma entidade para PF e outra para PJ, para garantir que não haja atributos conflitantes e realizar uma validação simplificada. Cada cliente será vinculado a uma tabela relacionada a PJ ou PF. O relacionamento será de **1:1**, onde cada cliente estará relacionado a um registro de PF ou PJ, mas nunca em ambos.

## Pagamento

- **Descrição**: Pode ter cadastrado mais de uma forma de pagamento.
- **Decisão**: Foi optado por criar uma entidade para **Pagamento**, com os seguintes atributos:
  - Tipo de Pagamento (Exemplo: "Cartão de Crédito", "Boleto", "Pix").
  - Informações (número do cartão, nome no cartão, chave Pix).
  - Preferencial (indicar se é a principal forma de pagamento ou não).
  
  O relacionamento será de **1:N** para **Cliente**, onde cada cliente pode ter várias formas de pagamento, e **1:1** para **Produto**, onde será um pagamento por pedido.

## Entrega

- **Descrição**: Possui status e código de rastreio.
- **Decisão**: Foi optado por criar uma entidade para **Entrega**, com os seguintes atributos:
  - **Código de Rastreio** (para rastrear a entrega).
  - **Status da Entrega** (status atual da entrega, como "Em Trânsito", "Entregue", "Cancelada", "Aguardando Retirada").
  - **Frete** (custo do frete associado à entrega, que pode variar dependendo do produto e fornecedor).
  
  O relacionamento será de **1:N**, permitindo várias entregas para um único pedido, caso os produtos sejam enviados por diferentes fornecedores.
