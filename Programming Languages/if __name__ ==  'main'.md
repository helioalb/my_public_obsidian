Todo arquivo python é um modulo. E todo módulo tem um `__name__`.

Quando o módulo é chamado diretamente, o seu `__name__` é `'main'`.

Exemplo:

```python
# one.py

print(f"Module name of file one.py is: {__name__}")
```

```shell
python one.py
```

```shell
Module name of file one.py is: __main__
```

porém, esse mesmo módulo, quando importando em outro arquivo terá o `__name__` = `one`.

Exemplo:

```python
# two.py
import one

print(f"Module name of file two.py is: {__name__}")
```

```shell
python two.py
```

```shell
Module name of file one.py is: one
Module name of file two.py is: __main__
```

## Exemplo de uso

Imagine que queremos testar o módulo abaixo:

```python
# fire.py
def ready() -> str:
  return 'Preparar'

def aim() -> str:
  return 'Apontar'

def fire() -> str:
  return 'Fogo'

def main():
  print(ready())
  print(aim())
  print(fire())

if __name__ == '__main__':
  main()
```

```shell
python fire.py
```

```shell
Preparar
Apontar
Fogo
```

Não queremos que "disparar em um alvo" toda vez que testarmos. O que queremos é testar cada função. Lembre-se, o "Preparar, Apontar, Fogo" só executado aqui porque o nome do módulo é `__main__`. E se chamarmos esse módulo dentro de outro módulo? Aí o nome dele não será mais `__main__` (se chamará `fire`). Então, se o chamarmos em outro módulo, podemos testar cada função unitariamente, sem o "perigo" de disparar em um alvo :) .

Veja:

```python
# fire_test.py
import fire

def assert_equals(expected : str, current : str) -> str:
  if expected == current:
    print('Ok')
  else:
    print('Fail')

def main():
  assert_equals(fire.ready(), 'Preparar')
  assert_equals(fire.aim(), 'Apontar')
  assert_equals(fire.fire(), 'Fogo')

if __name__ == '__main__':
  main()
```

