# Criptografía Básica
## Binario

This challenge is named `binario`, and is located within module `crypto`.

## Binario

Ya deberíamos saber que los ordenadores trabajan con código binario (1s y 0s).

### Python

En Python también puedes trabajar con números binarios. Un número binario va precedido de '0b':

```python
>>> 0b101
5
>>> 0b101 + 0b001
6
>>> 0b1000001 + 0b11
68
```

Si necesitas ver la representación de un número en binario, puedes usar la función `bin()`. Esta función te convierte el número a un string en binario:

```python
>>> bin(5)
'0b101'
>>> bin(65)
'0b1000001'
```

Puedes convertir cadenas de texto (strings) que representan números binarios a enteros haciendo casting con la función `int()`. Si a la función `int()` le pasamos un segundo argumento (la base), entonces procesará la cadena entiendo que el string representa un número escrito en dicha base. Cuando no pasamos nada entiende que el string está en decimal (es decir, en base 10). Recuerda que el código binario es base 2.

```python
>>> # Puedes convertir un string de binario con int
>>> int("0b101", 2)
5
>>> # No hace falta que el string comience por 0b
>>> int("101", 2)
5
>>> int("1000001", 2)
65
```

Obviamente, puedes trabajar con operadores lógicos a nivel de bit si necesitas (Python te sirve como calculadora):

```python
>>> # OR es '|'
>>> bin(0b101 | 0b010)
'0b111'
>>> # AND es '&'
>>> bin(0b101 & 0b010)
'0b0'
>>> # XOR es '^' (números diferentes: 1, números iguales 0)
>>> bin(0b101 ^ 0b010)
'0b111'
>>> bin(0b101 ^ 0b011)
'0b110'
>>> # NOT es '~'
>>> bin(~0b011)
'-0b100'
>>> # Desplazamiento hacia la derecha '>>'
>>> bin(0b101 >> 1)
'0b10'
>>> # Desplazamiento hacia la izquierda '<<'
>>> bin(0b101 << 1)
'0b1010'
```
