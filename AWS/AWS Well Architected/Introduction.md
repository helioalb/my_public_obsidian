- **Component** = Um componente atende a um requisito de negócio. é composto de código + configuração + recurso da AWS. 
- **workload** = Conjunto de componentes que juntos entregam um valor de negócio.
- **architecture** = A maneira como os componentes interagem dentro de um workload.
- **milestone** = mudanças importantes na arquitetura conforme esta evolui.
- **technology portfolio** = coleção de workloads que são necessários para o negócio existir.
- **level of effort**
	- **High**: semanas a meses
	- **Medium**: dias a semanas
	- **Low**: horas a dias

## Princípios gerais de design

### Pare de adivinhar suas necessidades de capacidade
Avaliação mal feita (ou nem avaliar) pode fazer você gastar muito mais do que o necessário. Ou pior, seu sistema pode cair por falta de recursos.

### Test systems at production scale
Você pode criar um ambiente de teste que reflete exatamente o ambiente de produção. Você faz seus testes e depois descarta esse ambiente. Você só irá pagar por esse tempo de teste.

### Automate with architectural experimentation in mind
Automatize a construção de workloads de tal forma que precise pouco ou zero esforço manual. Isso economiza tempo. Exemplo: Quero reproduzir minha infraestrutura de produção completa para fazer testes de carga. Isso deveria ser feito com apenas um comando.

### Considere arquiteturas evolucionárias
Normalmente é escolhido um tipo de arquitetura como se esse fosse ser o modelo eterno. Qualquer mudança nessa arquitetura gera medo de as coisas darem errado. Isso é parecido com código sem testes. O ideal é deixar tudo automatizado para que a experimentação seja fácil e os impactos sejam mensuráveis.

### Conduza a evolução de sua arquitetura usando dados
Você deve coletar dados de seus workloads. Como sua infraestrutura está versionada em código você pode documentar as evoluções com as evidencias mostradas pelos dados.

### Improve through game days
Agende _game days_ para simular eventos em produção (simular black friday, por exemplo) (lembre-se do principio "TEST SYSTEMS AT PRODUCTION SCALE")

## Operational excellence
A idéia é dar suporte ao desenvolvimento e facilitar ao máximo a execução dos **workloads**.

Veja mais em [[Operational excellence]]
## Security
## Reliability
## Performance efficiency
## Cost optimization
## Sustainability
