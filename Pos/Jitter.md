---
link: https://www.youtube.com/watch?v=rHiqD9VnVH8
---

Exemplo:

No jitter:
<=><=><=><=><=><=><=><=><=><=><=><=>

Com jitter:
<=>     <=><=>           <=><=><=>  <=> <=> 

Analogia:

Carros passando por um pedágio: Aos invés de ficarem todos a uma mesma distancia, acontece que um saí e anda, aí fica um espaço para o próximo carro. E assim por diante. Esse espaço varia entre os carros. No final das contas o pedágio causou um atraso. O jitter é a medida da variação entre essas distancias entre um carro e outro.

No voip isso causa pausas.
Imagine alguém falando a frase no whatsapp: mil centro e quarenta e sete. 

Imagine também que a pessoa do outro lado está anotando.

Se não há jitter, a anotação vai ser 1147

Se há jitter.
mil                                   centro e quarenta              e                        sete

a pessoa do outro lado vai anotar ~~1000~~ ~~1140~~ 1147


Site legal para ver o jitter: https://speed.cloudflare.com/

manualmente dá para ver com o comando ping também.

Exemplo:

```shell
ping www.google.com 
PING www.google.com(2800:3f0:4001:831::2004 (2800:3f0:4001:831::2004)) 56 data bytes
64 bytes from 2800:3f0:4001:831::2004 (2800:3f0:4001:831::2004): icmp_seq=1 ttl=57 time=14.1 ms
64 bytes from 2800:3f0:4001:831::2004 (2800:3f0:4001:831::2004): icmp_seq=2 ttl=57 time=16.3 ms
64 bytes from 2800:3f0:4001:831::2004 (2800:3f0:4001:831::2004): icmp_seq=3 ttl=57 time=232 ms
64 bytes from 2800:3f0:4001:831::2004 (2800:3f0:4001:831::2004): icmp_seq=4 ttl=57 time=153 ms
64 bytes from 2800:3f0:4001:831::2004 (2800:3f0:4001:831::2004): icmp_seq=5 ttl=57 time=87.3 ms
64 bytes from 2800:3f0:4001:831::2004 (2800:3f0:4001:831::2004): icmp_seq=6 ttl=57 time=110 ms
64 bytes from 2800:3f0:4001:831::2004 (2800:3f0:4001:831::2004): icmp_seq=7 ttl=57 time=134 ms
```
O jitter é a diferença entre os `time`.
