## Requisitos do sistema
### Requisitos funcionais
#### Funcionalidades Core
- Compra de ingressos
- Apresentar o ingresso comprado para entrar no evento
- Parceiros para gerenciar os eventos
#### Funcionalidades de suporte
- Pagamento e split do pagamento
- Busca dos eventos
- Exibição gráfica dos lugares disponíveis
- Garantia que em horários de pico, um ingresso não seja vendido para mais de uma pessoa.
### Requisitos não funcionais
- Baixa latência
- Escalável
- Alta disponibilidade
- Consistência dos dados
### Dados importantes
- **1M DAU** (*Daily Active Users*)
- Cada usuário faz **5 requests**
- Cada request resulta em **50kb**
- **5%** dos usuários compram 1 ingresso
- Reads vs Writes: **9:1**