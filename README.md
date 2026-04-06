# MonopolyETSE (POO)
César Poza González, Jaime Romero Martínez, David Sánchez Míguez. 

Proyecto de Monopoly por consola desarrollado en Java para la asignatura de Programacion Orientada a Objetos.

## Que se ha hecho

Se ha implementado una version jugable por terminal con:

- Gestion de partida, turnos, jugadores y avatares.
- Tablero con casillas de distintos tipos (solares, transportes, servicios, especiales, impuestos, etc.).
- Compra de propiedades, edificacion, hipoteca/deshipoteca y bancarrota.
- Sistema de tratos entre jugadores.
- Cartas de Suerte y Caja de Comunidad.
- Parseo de comandos de texto y gestion de errores mediante excepciones personalizadas.

## Estructura del proyecto

- `monopoly/`: logica principal del juego, menu, tablero, casillas, tratos y punto de entrada.
- `partida/`: entidades de partida (jugador, avatar, dado y tipos de avatar).
- `excepciones/`: jerarquia de excepciones para errores de formato, uso y ejecucion.

Punto de entrada:

- Clase principal: `monopoly.MonopolyETSE`

## Requisitos

- Sistema: Linux (probado en Ubuntu).
- JDK: Java 17 o superior (recomendado Java 21).
- Herramientas: `javac` y `java` disponibles en PATH.

Comprobar instalacion:

```bash
javac -version
java -version
```

## Compilacion

Desde la raiz del repositorio:

```bash
rm -rf out
mkdir -p out
javac -d out $(find . -name "*.java")
```

Esto genera todos los `.class` en el directorio `out/` respetando los paquetes.

## Ejecucion

Una vez compilado:

```bash
java -cp out monopoly.MonopolyETSE
```

Al arrancar, el juego solicita crear al menos 2 jugadores (nombre y tipo de avatar).

Comandos utiles dentro del juego:

- `help`
- `lanzar dados`
- `acabar turno`
- `comprar <propiedad>`
- `ver tablero`
- `end`

## Limpieza

Para limpiar compilados:

```bash
rm -rf out
find . -name "*.class" -delete
```

Nota: si siempre compilas con `-d out`, normalmente con borrar `out/` es suficiente.

## Como se ha hecho

El desarrollo sigue un enfoque orientado a objetos y modular:

1. Modelo del dominio del Monopoly con clases separadas por responsabilidad (casillas, propiedades, jugadores, avatares, cartas, etc.).
2. Orquestacion central en `Juego`, que controla turnos, reglas y acciones.
3. Interaccion por consola en `Menu`, con un parser de comandos de texto.
4. Validacion de errores y casos no validos mediante excepciones personalizadas agrupadas por categoria.
5. Encapsulacion de comportamiento especifico (p. ej., tipos de avatar y modos de movimiento) en clases concretas.

Este diseno facilita ampliar reglas/comandos y mantener el codigo de forma organizada.