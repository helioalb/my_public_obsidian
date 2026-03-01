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
#### Dados importantes:
- _DAU_ (Daily Active users): 1M
- Cada usuário faz 5 requests
- Cada request tem 50kb
- 5% dos usuários compram ingressos
- Reads vs Writes: 9:1
- Pode ter picos de acesso
#### Notação científica
- 1.000 = 10³
- 10.000 = 10⁴
- 100.000 = 10⁵
- 1.000.000 = 10⁶

Exemplos:
- 7000 = 7 * 10³
- 95.000 = 95 * 10³ ou 9.5 * 10⁴

##### Conversão
- MB para GB: 10³
- GB para TB: 10³
- MB para TB: 10⁶
##### Arredondamentos
- Segundos por dia = 86400 =~ 100.000 = 10⁵
- Minutos por dia = 1440 =~ 2000 = 2 * 10³
##### Requests
RPS = Requests por dia / segundos por dia
RPS = 5 * 10⁶ / 10⁵ = 5 * 10 = 50 requests por segundo

45 rps de read
5 rps de write
##### Compras
5% de 10⁶ = 5 * 10⁴
###### Compras por segundo
5 * 10⁴ / 10⁵ = 5 * 0.1 = 0.5 compras por segundo.
##### Bandwidth
50 rps * 50kb = 2500 kb/s / 10³ = 2.5MB/s
##### Storage
- writes per sec * request size * replication factor
- 5 rps * 50kb * 3 = 250kb/s * 3* = 750kb/s = 0.75MB/s
###### Storage por dia
- storage por segundo * 10⁵
- 0.75MB/s * 10⁵ => para GB (divide por 10³) => 0.75 * 10⁵ / 10³ = 0.75 * 10² = 75GB
###### Storage por ano
- storage por segundo * 3.65 * 10² * 10⁵ = storage por segundo * 3.65 * 10⁷
- 0.75MB/s * 3.65 * 10⁷ = 2.7MB/s * 10⁷ / 10⁶ => 2.7 * 10 = 27TB por ano
###### Storage por 5 anos
- storage por segundo * 3.65 * 10⁷ * 5 = 18.25 * 10⁷ = 1.8 * 10⁸ => 2 * 10⁸
- 0.75MB/s * 2 * 10⁸ / 10⁶ = 1.50MB/s * 10² => 150TB por 5 anos





