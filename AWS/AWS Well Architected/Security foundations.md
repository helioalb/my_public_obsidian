---
link: https://docs.aws.amazon.com/wellarchitected/latest/security-pillar/security.html
---
## Design principles
### Implement a strong identity foundation
Sempre busque a regra de menor privilégio. Tenha privilégios distintos para cada tipo de tarefa. Evite credenciais estáticas de longo prazo.
### Maintain traceability
Monitore ações em seu ambiente em tempo real. Qualquer coisa suspeita dever alertada o quanto antes.
### Apply security at all layers
Rede, VPC, Security Groups, Aplicação, load balancer, sistema operacional, código...
### Automate security best practices
Crie mecanismos de segurança via código (terraform)
### Protect data in transit and at rest.
Classifique o nível de confidencialidade dos dados. Quando necessário use mecanismos como criptografia, acesso restrito e o que mais for necessário.
### Keep people away from data
Crie mecanismo e procedimentos para evitar que dados sejam manipulados manualmente. Isso evita erros que podem causar perda de dados. Exemplo "Delete sem where"
### Prepare for security events
Tenha um plano definido do que fazer. Treine esse plano. Use ferramentas que agilizam a detecção e correção.