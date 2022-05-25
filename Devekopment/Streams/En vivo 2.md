- Funciones
	- Como llamarlas
	- Orden en el codigo
	- Datos de entrada (parametros)
	- Datos de salida (retorno)
	- Sobreescritura.
	- Accesibilidad.

#### Uso
-Normalmente es para acomodar el codigo, en dadas ocasiones un conjunto de lineas se repite numerosas veces, y ahi es donde entra el uso de funciones.


``` java
	int a = 10;
	int b = 15;

	int c = a + b;

	int d = a + c;

	int e = a + d + c;
```

``` java
	private int sumar(valor1, valor2){
		return valor1+valor2;
	}

	private int sumar(valor1, valor2, valor3){
		return valor1+valor2+valor3;
	}
	int a = 10;
	int b = 15;

	int c = sumar(a, b);

	int d =sumar(a, c);

	int e = sumar(a, d, c);


````