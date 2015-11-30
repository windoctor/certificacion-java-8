---
layout: post
title: Bloques de inicialización de instancia
date: 2015-11-29
tags: Java 8
category: certificacion
---

¿Qué son?
===========
Aquellos fragmentos de código que se encuentran fuera de cualquier método y encerrados dentro de llaves.

``{ int variableEjemplo = 2; }``

Reglas básicas
============================

* Se ejecutan en el orden en el cual aparecen en el archivo.
* El constructor se ejecuta después de que los bloques de inicialización de instancia se han ejecutado.
* No pueden hacer referencia a variables que aún no hayan sido inicializadas.

### Cuál será el resultado de ejecutar este código?
    public class InicializadoresInstancia {
	
        public InicializadoresInstancia(){
            System.out.println("Constructor de la clase");
        }

        {
            System.out.println("Bloque de inicializacion de instancia");
        }

        public static void main(String[] args) {
            new InicializadoresInstancia();
            System.out.println("Metodo main");
        }
    }

Aunque una de las reglas mencionadas arriba es que se ejecutan en el órden en el que aparecen, lo cierto es que también se ejecutan antes del constructor, por lo tanto, la salida de ejecutar el código anterior es:


    Bloque de inicializacion de instancia
    Constructor de la clase
    Metodo main



Y ahora que ya somos expertos en inicializadores de instancia, cuál será la salida de este código?

        public class InicializadoresInstancia2 {

        public InicializadoresInstancia2(){
            numero = 5;
        }

        public static void main(String[] args) {
            InicializadoresInstancia2 obj = new InicializadoresInstancia2();
            System.out.println(obj.numero);
        }

        private int numero = 3;

        { numero = 4; }
    }

El primer valor que toma la variable "numero" es 3 para después tomar el valor de 4 en el bloque de inicialización de instancia puesto que ya dijimos que estos bloques se ejecutan antes que el constructor. Sin embargo, el último bloque de código que se ejecuta y modifica el valor de "numero" es el constructor a donde le asigna el valor de 5.

5 es la respuesta correcta.
--