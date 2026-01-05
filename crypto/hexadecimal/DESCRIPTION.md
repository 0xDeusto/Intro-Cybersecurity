# Criptografía Básica
## Hexadecimal

This challenge is named `hexadecimal`, and is located within module `crypto`.

## Hexadecimal

También conocido como base-16, es la representación más habitual de datos binarios en informática: tampoco por facilidad de visualización como por tamaño. Aunque internamente todo es binario, todo son unos y ceros, para nosotros ver todo como enormes cadenas de unos y ceros es inviable. Si cada cuatro dígitos binarios lo representamos con un valor [0-9A-F], se simplifica la representación.

**IMPORTANTE:** como ya sabemos, o deberíamos saber, en los sistemas modernos un byte son 8 bits, por tanto, un byte se representa fácilmente con dos dígitos hexadecimales. De esta manera, por ejemplo, 0xDEADBEEF son 8 caracteres hexadecimales representando dos bytes.

La representación hexadecimal es la más habitual para representar datos binarios (los ficheros binarios no se abren con editores de textos sino con editores binarios como pueden ser `hexer`, `hexedit`, `bless`, `okteta`, `ghex`, `wxHexEditor`, etc.) o para representar posiciones de memoria.

Es muy habitual poner el prefijo `0x` para indicar que algo está en hexadecimal, pero no es estrictamente necesario. Si el número es suficientemente grande, es fácil identificar si algo está en hexadecimal porque sólo contendrá números y las letras de A a la F.

### Utilidades interesantes

El comando `xxd` permite generar dumps en hexadecimal de un binario:

```bash
$ xxd imagen.png
00000000: 8950 4e47 0d0a 1a0a 0000 000d 4948 4452 .PNG........IHDR
00000010: 0000 0008 0000 0008 0806 0000 00c4 0fbe ................
00000020: 8b00 0000 d449 4441 5418 d32d 8d3f 4ac3 .....IDAT..-.?J.
00000030: 7000 46df 975f 6a06 2569 fc57 6807 dd5c p.F.._j.%i.Wh..\
00000040: 3a79 0807 17d1 c10b 28bd 8117 f00a 8283 :y......(.......
00000050: 1ea1 5341 c1c5 63d4 a583 752a 7633 940a ..SA..c...u*v3..
00000060: 6992 cfc1 bcf1 f1e0 89d1 38c6 2c7a 5b61 i.........8.,z[a
00000070: efe1 f204 03f7 2f33 a6eb 4d85 d98d 68c9 ....../3..M...h.
00000080: 92a0 fc20 5377 3fd3 e14e 47f8 dfc7 0067 ... Sw?..NG....g
00000090: fd6d 36c6 8faf 1f8a 43e4 b2b1 2e8e 5226 .m6.....C.....R&
000000a0: 5f3f 6d30 ec71 3a1c 2848 4420 0ba6 b36f _?m0.q:.(HD ...o
000000b0: 26f3 36f8 5c14 a449 f0a6 369d 20aa dacc &.6.\..I..6. ...
000000c0: 972b 50bb 1874 93f2 b89f c906 010d b0fe .+P..t..........
000000d0: 2d1b 4c2d 8074 347e ca3b d16d 2c54 1907 -.L-.t4~.;.m,T..
000000e0: a165 d9bc adcc 790c 50d8 7745 d9e4 c015 .e....y.P.wE....
000000f0: 42c0 3bf8 86e7 6bff 0120 a64e 39ea d965 B.;...k.. .N9..e
00000100: bb00 0000 0049 454e 44ae 4260 82 .....IEND.B`.
```

En la columna de la derecha se ve la línea en caracteres imprimibles. Si el carácter no es imprimible, aparece un punto. Es muy común usar los primeros bytes de un fichero para identificarlo (en este caso vemos que se trata de un PNG)

También se puede hacer lo contrario, dado un volcado hexadecimal de un fichero, convertirlo a un binario:

```bash
$ xxd imagen.png > volcado.hex # Hacemos un volcado a volcado.hex
$ file volcado.hex
volcado.hex: ASCII text
$ xxd -r volcado.hex > revertido # Revertimos el volcado en 'revertido'
$ file revertido
revertido: PNG image data, 8 x 8, 8-bit/color RGBA, non-interlaced
```

Se puede convertir un texto a hexadecimal, o viceversa, muy fácilmente con `xxd`:

```bash
$ echo "hola mundo" | xxd -p
686f6c61206d756e646f0a
$ echo "686f6c61206d756e646f0a" | xxd -r -p
hola mundo
```

Otro comando similar es `hexdump`

```bash
$ hexdump -C imagen.png | head -2
00000000 89 50 4e 47 0d 0a 1a 0a 00 00 00 0d 49 48 44 52 |.PNG........IHDR|
00000010 00 00 00 08 00 00 00 08 08 06 00 00 00 c4 0f be |................|
```

### Python

Obviamente, en Python también puedes trabajar con números hexadecimales. Para ello, pon como prefijo `0x`:

```python
>>> 0x41
65
>>> 0x41 + 0x01
66
>>> 0xDEC0DE
14598366
>>> 0xD3C0D3
13877459
```

Si necesitas ver la representación hexadecimal de un número, puedes usar la función `hex()` que te devuelve un string con la representación hexadecimal:

```python
>>> hex(15)
'0xf'
>>> hex(65)
'0x41'
>>> hex(13877459)
'0xd3c0d3'
```

Al igual que hemos visto con el código binario, podemos convertir un string con un texto que representa un número hexadecimal a un entero haciendo un casting con la función `int()`. Para ello, simplemente ponemos 16 (recuerda: hexadecimal es base-16) como segundo argumento de dicha función:

```python
>>> # Convertimos un string hexadecimal a entero
>>> int("0x41", 16)
65
>>> int("0xd3c0d3", 16)
13877459
>>> # Realmente, no hace falta que el string comience por 0x
>>> int("41", 16)
65
>>> int("d3c0d3", 16)
13877459
```
