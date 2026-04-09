- Conjunto de módulos o funciones que se ocupan de controlar y administrar la ejecución de los programas sobre los recursos que brinda el equipo (hardware)
- Conjunto de programas/software/módulos relacionados entre sí que contribuyen a que la computadora lleve a cabo correctamente su trabajo

## Tipos de S.O. en la historia
### Programa por lotes
- Los sistemas operativos eran denominados sistemas de control y asistían a los operadores en la carga y monitoreo de tareas. También notificaban resultados.
- La evolución los tornó en spool (simultaneous peripheral operations on-line)

### Sistemas multiprogramados
- Maximiza el tiempo de uso del procesador, aprovechando los períodos de tiempo en que los procesos lo utilizan
- Se logra otorgando el uso del procesador a otros procesos (durante I/O), generando nuevas problemáticas de seguridad

### Sistemas de tiempo compartido
- Evolución del anterior. Se convierten en sistemas interactivos y de multiusuario
- Sirve para compilar y editar programas propios

## Funciones

### Inicialización

- Enciendo la computadora -> pasa electricidad a la BIOS -> se enciende -> corre sus rutinas (chequea memoria, procesador y demás, por último busca el loader del S.O.)
- El loader está grabado en MBR o registro 0. Deja la máquina en un estado tal que pueda ser utilizada (recuento de hardware, guarda información en tablas, lee el set-up, revisa disco, carga el kernel en memoria RAM).
- Cold-Load: arranque de cero
- Warm-Load: arranque de reset (máquinas virtuales)
### Máquina extendida

- Parte visible del S.O. (GUI, CLI, NUI o Natural User Interface)
- Es todo el código del S.O. encargado de ofrecer al usuario una interfaz para operar con la computadora (abstrae la complejidad del hardware, facilita la comunicación y acepta entradas de nuevos trabajos).
- Es la primer línea de seguridad (login)

### Administración de recursos

- Función principal del S.O.
- Gestiona políticas de asignación de recursos
- Optimiza la utilización de los recursos

### Aislamiento (seguridad)

- Garantiza la integridad de recursos y proceso (que un proceso no acceda al espacio de direccionamiento de otro proceso o del mismo sistema)
- Valida los usuarios del sistema
- Modo dual de ejecución del procesador:
	- Brinda un "modo protegido", que incluye una clasificación de las instrucciones del procesador y un bit para indicar el modo de operación
	- Set de instrucciones: operaciones que entiende el procesador (mov, add, sb, etc.) y están "guardados" en el mismo, ya que es dependiente de cada uno. Se guarda una copia en el kernel, la cual usa S.O.
	- Modo usuario: modo normal de operación. Si se intenta ejecutar una instrucción privilegiada, la CPU interrumpe la ejecución y genera una excepción o trap, pasándole el control al S.O.
	- Modo kernel o privilegiado: cuando se necesita utilizar alguna instrucción privilegiada, lo debe hacer el S.O., ya que se debe cambiar el modo de usuario (el cual vive en el mismo). La mayoría de las funciones realizadas por el S.O. requieren de este modo.

## Tipos de usuario

- Por usuario: se dividen en monousuario y multiusuario
- Por procesador: uniprocesador y multiprocesador
- Según concurrencia de procesos:
	- Monoprogramados
	- Multiprogramados: también llamados multitask, cuando un proceso se encuentra haciendo uso de algún dispositivo, se otorga el procesador a otro proceso
- Por propósito:
	- Propósito general: proporciona una amplia gama de servicios y se adapta a cualquier ambiente, tipo de aplicación, modo de operación, dispositivo, etc.
	- Propósito especial: construidos a medida debido a arquitecturas especiales o aplicaciones con requerimientos especiales. 
		- De tiempo real: garantiza respuestas a eventos externos dentro de límites de tiempo preestablecidos y en el que es crucial el tiempo de respuesta. 
		- Tolerantes a fallas: se utiliza cuando se debe proveer un servicio continuo. El S.O detecta y corrige errores. Se suele utilizar un conjunto de redundancias en recursos y chequeos internos.
		- Virtuales: generan máquinas virtuales que utilizan el mismo hardware que funciona por debajo.

## Arquitectura

- Sistemas monolíticos:
	- Se tiene un único proceso que opera en modo privilegiado. Dentro suyo, se encuentran las rutinas requeridas para las distintas tareas realizadas por el S.O.
	- Ofrece buena performance en la ejecución porque no requiere muchos mecanismos de comunicación
- Sistemas microkernel:
	- Mantiene el núcleo lo más reducido y simple posible. El resto de los procesos del sistema los saca a distintos módulos que se comunican con el S.O.
- Sistemas híbridos: