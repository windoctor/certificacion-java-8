---
layout: post
title: Variables, Tipos primitivos y Objetos
date: 2015-11-29
tags: Java 8
category: certificacion
---

¿Qué son?
==============

<strong>Primitivos: </strong> Los tipos primitivos almacenan su valor directamente en la memoria y no tienen métodos. Para cuestiones del examen, no hay de otra mas que aprenderse de memoría los 8 tipos de datos primitivos en Java.

| Tipo     |      Tamaño            | Valor por default |
|----------|:-------------:         |:----------------------:|
| boolean |  true o false           | false    
| byte    |    8 bits               | 0
| short   | 16 bits                 | 0
| int     | 32 bits                 | 0
| long    | 64 bits                 | 0L   
| float   | 32 bits punto flotante  | 0.0f
| double  | 64 bits punto flotante  | 0.0d
| char    | 16 bit valor unicode    | '\u0000'

Los tipos primitivos <strong>no aceptan el valor null.</strong>

<strong>String</strong> no es un tipo primitivo, es un objeto.

<strong>Referencia de objetos:</strong> También llamados simplemente "referencias". Las referencias no almacenan el objeto en si, más bien apuntan a la dirección de memoria donde el objeto está almacenado.

** Por simplicidad, se suele decir "objeto" en lugar de "referencia de objeto". En términos estrictos, una referencia de objeto es un apuntador a donde se encuentra almacenado realmente el objeto.

Por default, las referencias de objetos se inicializan con null.

Declarando e inicializando
============================
Definimos "variable" como un espacio de memoria que almacena datos. Para declarar una variable se requiere de un tipo y de un nombre. El tipo puede ser cualquiera de los 8 tipos primitivos o un objeto.

Considere las siguientes reglas para declarar variables:

* Deben iniciar con una letra ó el simbolo $ ó el símbolo _
* Los caracteres subsecuentes a la primer letra si pueden ser números.
* No deben llamarse como alguna de las palabras reservadas de Java (y cabe recordar que Java es sensible a mayúsculas y minúsculas)

[Ver palabras reservadas](http://docs.oracle.com/javase/tutorial/java/nutsandbolts/_keywords.html) (no es necesario memorizar todas las palabras reservadas para el examen)

Algunas reglas adicionales que se explican con ejemplos, son las siguientes:

    // Compila OK
	private String nombre;
	private java.sql.Date fecha_nacimiento;
	
	// Compila OK
	// Declaración de variables múltiples en la misma linea
	// peso es declarada e inicializada
	// talla solamente es declarada
	private double $peso = 80.5, talla;
	
	// Error de compilacion
	// por default, los numeros son doubles
	// para indicar un float, se debe poner una f delante del numero
	// private float _estatura = 1.72f;
	private float _estatura = 1.72;
		
	// Error de compilacion
	// Solo es posible declarar en la misma linea variables del mismo tipo.
	private int edad, String apellidos;
	
	// Compila OK
	// Estan separados por un punto y coma (;) lo que indica una nueva linea.
	private String domicilio="Mexico, DF"; int numeroInterior = 1;


Ámbito de variables: locales, de instancia y de clase
=======================================

<strong>Locales:</strong> Aquellas definidas dentro de un método ó bloque de código. Un bloque de código es aquel que está definido entre llaves { }. Requieren ser inicializadas forsozamente para ser utilizadas.

<strong>De instancia:</strong> Son las que se declaran fuera de cualquier método y de cualquier bloque de código. Su alcance es a lo largo de toda la clase. No requieren ser inicializadas, el compilador las inicializa con su valor por default.

<strong>De clase:</strong> Son igual que las de instancia, pero tienen el modificador static.

	// Variable de clase
	private static String GENERO = "MASCULINO";
	
	// Variable de instancia
	private int edad;
	
	public void jugandoConVariables(int variable){
		int edad = 0; //variable local
		
		{
			int aux; //variable local en bloque de código
			System.out.println(aux); //error de compilacion, aux no ha sido inicializada.
		}
		
		// error de compilacion
		// aux no se conoce. Su alcance es solo en el bloque de arriba.
		System.out.println(aux);
		
		System.out.println(edad); // OK
		System.out.println(variable); // OK
	}
    
