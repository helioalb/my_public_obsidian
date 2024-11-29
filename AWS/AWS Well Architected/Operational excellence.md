---
link: https://docs.aws.amazon.com/wellarchitected/latest/operational-excellence-pillar/welcome.html
---
## Design principles
### Organize teams around business outcomes

Para alcançar os resultados desejados o time tem que que ter visão de liderança. Tendo excelentes resultados como meta, os processos serão automaticamente melhorados a cada dia.

### Implement observability for actionable insights

Metrifique. Saiba tudo sobre o comportamento do **workload**, sua performance, sua confiabilidade, custo e saúde. Seja proativo em cada um desses aspectos.

### Automatize com segurança onde possível.

Faça infraestrutura através de código (*terraform*). Todo processo manual deve ser automatizado. Você pode empregar segurança através de guardrails, rate control, error limits e aprovações. Isso vai diminuir erros e vai reduzir trabalho.

### Faça mudanças frequentes, pequenas e reversíveis

Projete **workloads** que sejam escaláveis e fracamente acoplados. Isso permite que sejam realizadas mudanças frequentes (sem impactar quase nada). Como é fácil fazer mudanças, faça mudanças pequenas (e que possam ser revertias)

### Refine operations procedures frequently

Revise os procedimentos com frequência. Certifique-se que ainda são efetivos e que a equipe sabe lidar com eles. Se estão obsoletos, remova-os, se podem ser melhorados, melhore-os. Garanta que toda mudança seja comunicada eficientemente à equipe.

### Antecipe falhas

Conduza as soluções para lidar com cenários de falhas. Simule esses cenários e veja como seu time reage a essas situações. Entenda bem o tamanho do impacto dessas falhas nos resultados da empresa.

### Learn from all operational events and metrics

Aprenda com todos os eventos operacionais e principalmente com as falhas. Compartilhe os aprendizados com a empresa toda.

### Use managed services

Sempre que possível, use serviços gerenciados. Existem pessoas especializadas cuidando deles. É mais caro, mas os riscos são muito menores.

## Best practices

### Organization
- Todo mundo deve conhecer o workload, o seu papel nesse workload e os objetivos de negócio desse workload.
- Prioridades bem definidas maximizam o eficiência do time. Converse com stackholders (internos e externos), veja necessidades de desenvolvimento e de operação para determinar onde se deve focar.
- Esteja atento a regulamentações da empresa, governamentais e compliance.
- Valide se você tem mecanismos para saber quando há updates nas regulamentações (Exemplo - Software contábil: Como saber que houve mudança na legislação?)
- Avalie os riscos (exemplo: risco de vazamento de informações). Mantenha esses riscos anotados num registro de riscos.
- Avalie impactos dos riscos. Exemplo: Para fazer o projeto andar rápido abrimos mão do controle de custos.
- Certifique-se de que tudo tem um "dono". Quem é o responsável pela app? Quem é o responsável pelo workload?
- Dê suporte aos membros do time. 
- Incentive experimentações para acelerar o aprendizado e manter seu time engajado.

#### Perguntas
##### 1 - Como determinar quais são suas prioridades?
Todas as pessoas da equipe devem saber qual é o seu papel para atingir os objetivos da empresa. Mantenha todas as metas compartilhadas entre todos.

##### 2 - Como você estrutura sua organização para dar suporte aos resultados de negócio esperados?

Seus times precisam saber qual é o seu papel no resultados do negócio. Seus times devem entender qual é o seu papel no sucesso de outros times. Devem entender que é o papel de outros times no seu resultado. E também devem entender quais são metas compartilhadas. Entendendo suas responsabilidades, responsabilidade de outros times e quem tem autoridade para tomadas de decisão vai ajudar no foco de esforços e irá maximizar o valor dos times.

##### 3 - Como sua cultura organizacional pode dar suporte aos resultados de negócio desejados?

Dando suporte às equipes para que essas sejam mais efetivas em suas ações.

### Prepare

1) Entenda bem seus **workloads**. Saiba o que você espera deles. Assim você vai conseguir projetá-los para fornecer os dados que dizem se você está no caminho certo.
2) Identifique os KPI's do negócio.
3) Revise sempre as estratégias de observabilidade.
4) Adote estratégias que facilitem a subida de mudanças em produção. (Exemplo: deploy automatizado)
5) Adote estratégias que facilitem a reversão de mudanças (Exemplo: Rollback facilitado)
6) Sempre faça mudanças que sejam pequenas e facilmente reversíveis.
7) Tenha sempre playbooks (o que fazer) e runbooks (como fazer)
8) Infraestrutura deve estar em código.
9) Faça "pré-mortens" para prever falhas e assim confeccionar playbooks e runbooks.

#### Perguntas

##### 4 - Como implementar observabilidade no seu workload?

Implemente a observabilidade de tal maneira que você possa saber o seu estado atual e possa fazer modificações guiadas pelos requisitos de negócio.

##### 5 - Como você reduz defeitos, facilita "remediações" e melhora o fluxo em produção?

Adote abordagens que facilitem o deploy em produção (e também facilitem rollbacks). Também é importante adotar estratégias que permitam mensurar mudanças realizadas.

##### 6 - Como você mitiga riscos de deploy?

Adote abordagens que forneçam um feedback rápido sobre a qualidade de deploys recém lançados. Além disso tenha um mecanismo que permita um rápido rollback.

##### 7 - Como você sabe que está pronto para suportar um workload?

Avalie a prontidão operacional do seu workload, processos e procedimentos. Além disso, garanta que o time entenda quais são os riscos operacionais do seu workload.

## Operate

1) Tenha observabilidade
2) Configure alertas
3) O sucesso de um workload é medido pelos seus resultados comerciais. Defina os resultados esperados.
4) Determine as métricas de satisfação do cliente e as monitore ativamente.
5) Mapeie todos os eventos operacionais. Para os bem definidos, use _runbooks_. Use playbooks para auxiliar na resolução de problemas.
6) Priorize respostas a eventos que impactam diretamente o cliente.
7) Cada alerta deve ter um proprietário e uma ação pré-estabelecida para que possa ser executada no momento do disparo do alerta.
8) Comunique o status operacional através de _dashboards_ (customizados para cada publico alvo: Exemplo: Gerentes, vendedores, operação, clientes, desenvolvedores...)
9) Toda métrica coletada deve estar relacionada a um objetivo de negócio.

#### Perguntas

##### 8 - Como você utiliza a observabilidade do workload na sua organização?

Garanta a saúde ideal do _workload_ usando observabilidade. Utilize logs, métricas e _tracings_ relevantes para obter uma visão abrangente do workload e facilitar a resolução de problemas.

##### 9 - Como você entende a saúde de suas operações?

Defina, capture e analise métricas dos eventos operacionais. Assim você terá boa visibilidade e pode tomar medidas adequadas.