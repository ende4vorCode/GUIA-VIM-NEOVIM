# Guia de VIM o NeoVim

Quizas has escuchado sobre este editor de texto basado en terminal, si bien hoy en dia tenemos herramientas como Visual Studio Code, que nos permite navegar facilmente y con pocas o nula complicaion instalar plugins que nos ayudan a ser mas rapido con nuestro codigo, este se ve realmente lamentable en Linux. Por ello estoy decidido a aprender Neovim y este es mi camino para ello.
Nota: Los comandos utilizados son validos para VIM o Neovim

## Entrar a VIM

Todo esto es en la terminal. Por ello debes saber utilizarla.
`nvim programa.js` Abrimos con Neovim el archivo llamado "programa.js"
Para hacerlo con vim, reemplazamos `nvim` por `vim`

## Salir de VIM

A todos nos ha pasado que al entrar a VIM o Neovim, no sabemos que hacer y al presionar todas las teclas, nos deja salir misteriosamente. Pero bueno, la forma de salir realmente de VIM o Neovim es:
`esc + :q!` Para salir sin hacer cambios, en caso de que hayas hecho alguna modificacion por error.
`esc + :q` Para salir sin hacer cambios, en caso de que no hayas modificado nada.
`esc + :wq` Pasra guardar y salir.
Nota: Cuando utilizamos `!` significa "Forzar" ej: `:wq!` Forzamos el guardado y la salida.
`:w` Lo utilizamos para ir guardando lo que estemos escribiendo.

## Modos de VIM

Vim tiene dos modos principales el modo "Cursor" y el modo "Insertar"
- Modo normal: El modo normal nos permite movilidad, o sea desplazarnos por el codigo bastante rapido, sin utilizar el mouse, asi como seleccionar, borrar o copiar algun elemento.
	-	El modo normal es el modo por defecto, pero para entrar a el utilizamos `esc + esc` tambien podemos utilizar solamente `esc`, pero de esta forma puede tardar un poco mas.
-	Modo Insertar: Como dice su nombre, podemos insertar texto. Para entrar en este modo tenemos que estar en modo normal y louego utilizar la letra `a` donde queramos insertar texto, la `a` nos permite posicionar el normal en la zona posterior al caracter seleccionado. Otra forma de entrar al modo normal es con la `i` la cual nos llevaria hacia la parte anterior al caracter seleccionado.

## Mover el cursor

Para mover el cursor debemos estar estrictamente en el modo normal.

### Movimientos basicos

Los movimientos mas basicos que proporciona VIM, son las teclas `h-j-k-l`, cada una de estas teclas representa un movimiento.

`h` Mueve el cursor hacia la izquierda.
`j` Mueve el cursor hacia abajo.
`k` Mueve el cursor hacia arriba.
`l` Mueve el cursor hacia la derecha.

Obviamente si lo piensas, esta forma de moverse es bastante ineficiente al momento de saltar varias palabras, por ejemplo, si quisieras saltar 4 palabras de 10 letras, tendrias que hacerlo apretando `l` 43 veces, por ello utilizamos otras letras para hacer saltos de palabras. `w-e-b`

`w` Nos permite desplazamiento hacia el inicio del elemento siguiente.
`e` Nos permite desplazamiento hacia el final del elemento siguiente.
`b` Nos permite desplazamiento hacia el inicio del elemento anterior.

### Movimientos complejos

VIM tiene una funcionalidad muy interesante en cuanto a movimiento, y es que podemos hacer combinaciones de comandos, por ejemplo, si queremos movernos 10 lineas hacia arriba,en modo normal, podemos utilizar `10 + k` eso nos movera 10 linas hacia arriba. Este tipo de movimiento se puede combinar con todas las combinaciones de movimiento anteriormente mencionadas.

## Insertar texto

Para instertar texto debemos estar en el modo de insertar, por ello entramos con `a` o `i` como antes esta definido. Ahora puedes escribir, por ejemplo: "Soy un hacker, estoy utilizando VIM" y luego `esc + esc` y te puedes mover, o guardar `:w`.

A todos nos ha pasado que se nos olvida poner un ; por ello existe una forma de desplazarnos hacia el final de una linea rapidamente, por eso utilizariamos la siguiente combinacion. En modo normal `shift + a` Nos envia al final de la linea, ahora insertamos nuestro ';' y `esc + esc` y podemos seguir con lo que estabamos.

## Eliminar texto

Si nos posicionamos en modo normal y al inicio de la palabra o sobre la letra que queramos elimiar, utilizamos la `x` asi eliminamos caracter a caracter, tambien podemos mezclarlo con numeros.

## Buscar la deficion de una variable

Cuando tenemos mucho codigo, hay ocaciones en las cuales tenemos que buscar la deficion de una funcion o variable que estemos utilizando, y esto puede ser muy engorroso. Por ejemplo, imagina que tenemos el siguiente codigo:

```javascript
	
	let saluda = (nombre) => {
		console.log(`Hola ${nombre} como has estado?`)
	}

	saluda('Ende4vor')
	// salida "Hola Ende4vor como has estado?"
```
Esta es una funcion sencilla, la cual nos permite entregarle un nombre y la funcion saludara a ese nombre.

Entonces, como puedo ir a la definicion de dicha funcion? Nos tenemos que posicionar en la palabra que buscamos con modo normal y utilzamos la combinacion `gd` y nos lleva a la deficinion de la funcion.

## Movimiento entre archivos

VIM entrega una posibilidad muy interesante, la cual nos permite ir cambiando de archivos utilizando el mismo editor.

En caso de que estemos llamando a un archivo aparte en nuestro codigo, podemos hacer algo similar que en el caso anterior. Al posicionarnos en la funcion o variable que buscamos, utilizaremos  `gd` para ir a la definicion de la funcion y luego `gf` para ir al archivo. Para volver atras `ctrl + o`.

## Buffer

Vim trabaja con buffer, esto significa que guarda un historial de cambios, por ello es que funciona `ctrl + o` para regresar del archivo, pero para ir hacia adelante utilizamos `ctrl + i`.

## ELiminar, Undo, Redo

`dw` DELETE WORD - Elimina palabras una por una.
`u` UNDO - Deshacer.
`ctrl+r` REDO - Rehacer
`d+$` Elimina desde el cursor hasta el final de la linea.

## Combinar operadores y movimiento

VIM entrega una utilidad de mezclar operadores como numeros o movimientos a comandos, y asi hacer mezcla de estos, para hacer comandos mas complejos. Ej:

Si tengo 10 lineas que quiero borrar, puedo hacerlo de la siguiente forma.

Te posicionas al inicio de todas las lineas que quieras eliminar y haces la siguiente combinacion `10 + d + j` en palabras sencillas le dices "Quiero que repitas 10 veces eliminar una linea hacia abajo - 10 + delete + abajo"

Estas combinaciones se pueden hacer complejas de acuerdo a lo que necesites.

## Eliminar linea, pegar y reordenar

Siempre que eliminamos algo VIM recordara lo ultimo, en palabras secillas, eliminar no existe en VIM solo cortar.

`dd` Eliminamos la linea completamente.
`p` Pegamos el elemento que copiamos, justo abajo del cursor.
`shift + p` Pegamos el elemento que copiamos, justo arriba del cursor.

Si bien te mencione anteriormente una forma de eliminar muchas lineas, esa no era la forma mas eficiente, ahora puedes utilizar `10 + dd` O sea que repetimos 10 veces la elimnacion de lineas, esto se puede hacer con el numero de veces que necesites.

## Reemplazar

`r` Es un comando inutil xd, al posicionarse con el cursor en modo normal, sobre un caracter que queramos reemplazar.

## Operador de cambio

Me posiciono en el inicio de una palabra en modo normal
`c+w` Change word, con este cambiamos una palabra.
`c+i+w` Change inner word, eliminamos la palabra en cualquier posicion de la palabra.

## Salto de lineas

Saltar dentro del archivo.

`g+g` Nos lleva hasta el inicio del archivo.
`shift+g` Nos lleva al final del archivo.

## Busqueda
`/` Buscamos algo de adelante hacia atras.
`?` Buscamos algo de atras hacia adelante.
`n` Una vez seleccionamos algo, para ir saltando entre lineas.
`shift+n` Saltar hacia atras.

## Saltar al parentesis correspondiente

Nos posicionamos en el parentesis.
`%` Nos movemos al parentesis correspondiente.

## Saltar en la linea
`0` Nos lleva al inicio de la linea.
`$` Nos lleva al final de la linea.

## Reemplazando cadenas en la linea

`:s/palabra/palabron` Sustituir/cadena queremos reemplazar/nueva cadena.
`:s/palabra/palabron/g` Sustituye todas las ocurrencias de la linea.
`:%s/palabra/palabron/gc` Sustituye todas las ocurrencias dentro del archivo. El parametro % te pregunta si quieres reemplazar alguna de las que hara, si no lo pones, simplemente reemplazara todo.

## Nueva linea

`o` Crea una nueva lina por debajo.
`shift+o` Crea una nueva linea justo por arriba.

## Reemplazo de caracteres

`shift+r` Nos deja en modo reemplazar.

## Copiar y pegar

`v` Modo visual. Nos permite seleccionar donde nos estemos moviendo, podemos usar la `x` cortamos.
`v` Modo visiual, seleccionamos. Luego utilizamos `y` y luego `p` Copiamos y pegamos.

