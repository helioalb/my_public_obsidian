---
tags:
  - aws
  - "#algorithms"
link: https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_evaluation-logic.html
---
## Tipos de avaliação

### Identity-based policies
Políticas que são anexadas a um IAM Identity (user, role, grupo de usuário).

### Resource-based policies
Dão permissão ao principla (user, account, role...)
Sempre que uma operação é realizada na AWS um request é enviado para o IAM  para que este avalie se deve permitir o acesso.

### IAM permission boundaries
Seta o máximo de permissão que um [Identity-based policies](#identity-based-policies) pode ter

### [[AWS Service Control Policies]] 

### Junção de tipos

#### [Identity-based policies](#identity-based-policies) + [Resource-based policies](#resource-based-policies)

é como se fosse o operador lógico **ou**(`||`). Vale tudo o que está em um ou outro (ou nos dois)

![[identity+resource.png]]

#### [Identity-based policies](#identity-based-policies) + [IAM permission boundaries](#iam-permission-boundaries)

é como se fosse o operador lógico **and** (`&&`) (ou simplismente uma interseção)

![[identity+scp.png]]
### Session policies
São políticas que são passadas por parametro em chamadas temporárias (via api, por exemplo)

## Passos para o evaluation

### Autenticação
O primeiro passo é autenticar o principal (principal == user, role, app...)

### Processamento do request
Aqui a aws extrai as seguintes informações:

- **Actions** - o que o principal está querendo fazer
- **Resources** - onde o principal está querendo fazer a action
- **Principal** - Informações de quem está querendo realizar a action no resource (aqui vem tudo do principal - policies, roles e tudo o que ele tem direto)
- **Environment data** - Informações de onde o principal está (ip, user, dia, mês) - Util para auditoria
- **Resource data** - Dados do recurso (tags, por exemplo)

### Avaliação

A avaliação acontece na seguinte ordem:

1. Explicity Deny
2. SCP
3. Resource-based policy
4. Identity-based policy
5. IAM Permissions Boundary
6. Session Policies

![[PolicyEvaluationHorizontal111621.png]]