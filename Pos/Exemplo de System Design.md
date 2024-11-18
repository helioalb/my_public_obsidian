## Requisitos
### Requisitos funcionais
#### Funcionalidades core
- Compra de ingressos
- Apresentar ingresso na entrada do evento
- Gerenciamento da venda de ingressos por parceiros
#### Funcionalidades de suporte
- Pagamento
- Split de pagamento
- Busca de eventos
- Exibição gráfica dos lugares disponíveis
- Garantir que o mesmo ingresso não seja vendido para duas vezes
### Requisitos não funcionais
- Baixa latência
- Escalável
- Alta disponibilidade **
- Consistência de dados
** Talvez não seja possível ter alta disponibilidade e consistência de dados ao mesmo tempo (Ver teorema CAP)
### Plano de capacidade
Dados importantes:
- _DAU_ (Daily Active users): 1M
- Cada usuário faz 5 requests
- Cada request tem 50kb
- 5% dos usuários compram ingressos
- Reads vs Writes: 9:1
- Pode ter picos de acesso
- 