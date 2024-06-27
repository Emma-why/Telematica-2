# guia

aqui voy a subir to y como sea voy a quemar igualito

# Indices

1. [Conceptos OSPFv2](#MODULO-1)
2. [Configuración de OSPFv2](#MODULO-2)
3. [Conceptos de Seguridad en Redes](#MODULO-3)
4. [Conceptos de ACL](#MODULO-4)
5. [Configuración de ACL para IPv4](#MODULO-5)
6. [NAT en IPv4](#MODULO-6)
7. [VPN](#MODULO-8)


---
## https://ccnadesdecero.es/ccna-3/#Modulo_1_Conceptos_OSPFv2_de_Area_Unica_CCNA_3_v7
---
+
show ip ospf neighbor
show ip protocols
show ip ospf
show ip ospf interface

## MODULO-1
Conceptos OSPFv2

el protocolo de ospf es un protocolo de enrutamiento de estaos de enlace desarollado como alternativa de l protocolo de routing por vector de distancas, rip es ospf entajas , significa sobre el rip en el sentido que ofrece una convergencias mas rapida y escala a implementaciones de redes muchos mas mediante grafos y redes grandes ya que cuenta con uan base de datos

un es un protocolo sin clase que utiliza conceptos de areas para realizar escabilidad un administracion de red puede dividir el dominio de enrutamiento en areas distintas que ayudan a controlar el trafico en la actualidad de la red en su enrutamiento

la informacion acerca del estado dicho se conoce ya de antes mano con los tipos de paquetes

* paquetes de saludo
* paquetes de descripcion de la base de datos
* paquete de solicitud de estado de enalce
* paquete de actualizacion de base de datos 
* paquete de recibo de estado de enlace

se actualiza contastenmente con capa cambio

* corre el algortimo de ospf base de datos de reenvio
* base de datos de estado de enlaces
* abyacentes de vecino

el router de topologia para ellos los resultados de calculso realizados a partie del algortimo son las mas eficentes

operaciones de etado de enlace

* establecer de abyacecias de vecinos
* intercambio de anuncios de estado de enlace
* crear ala base de datos de estado de enlace
* ejecuta sft
* se elige la mejor ruta

Las opciones de diseño de topología jerárquica con OSPF multiárea pueden ofrecer estas ventajas:

* más pequeñas :Tablas de enrutamiento las tablas son más pequeñas porque hay menos entradas de tabla de enrutamiento. Esto se debe a que las direcciones de red se pueden resumir entre áreas. La sumarización de ruta no está habilitada de manera predeterminada.
  
* Sobrecarga de actualizaciones de estado de enlace reducida - el diseño de OSPF multiárea con áreas más pequeñas minimiza los requisitos de procesamiento y memoria.

* Menor frecuencia de cálculos de SPF - Multiárea OSPF localiza el impacto de un cambio de topología dentro de un área. Por ejemplo, minimiza el impacto de las actualizaciones de enrutamiento, debido a que la saturación con LSA se detiene en el límite del área.

### se usan los siguientes paquetes

* hello
  Descubre los vecinos y construye adyacencias entre ellos
* dbd / Descriptores de bases de datos 
Controla la sincronización de bases de datos entre routers.
* lsr / Solicitud de estado de enlace
Solicita registros específicos de estado de enlace de router a router
* lsu / Actualización de estado de enlace
Envía los registros de estado de enlace específicamente solicitados
* lasck / Acuse de recibo de estado de enlace

* Estado inactivo	
Ningún paquete de hello recibido = Down.
El router envía paquetes de hello.
Transición al estado Init.


* Estado Init	
Se reciben los paquetes de hello del vecino.
Estos contienen el router ID del router emisor.
Transición al estado Two-Way.

* Estado Two-Way	
En este estado, la comunicación entre los dos routers es bidireccional.
En los enlaces de acceso múltiple, los routers eligen una DR y una BDR.
Transición al estado ExStart.

* Estado ExStart	En redes punto a punto, los dos routers deciden qué router iniciará el intercambio de paquetes DBD y deciden sobre el número de secuencia de paquetes DBD inicial.

* Estado de intercambio	
Los routers intercambian paquetes DBD.
Si se requiere información adicional del router, entonces haga la transición a Cargando; de lo contrario, la transición al estado Completo.

* Estado Loading	
Las LSR y las LSU se usan para obtener información adicional de la ruta.
Las rutas se procesan mediante el algoritmo SPF.
Transición al estado Full.

* Estado Full
La base de datos de estado de vínculo del router está completamente sincronizada.

¿Por qué se necesita elegir un DR y un BDR?

Las redes multiacceso pueden crear dos retos para OSPF en relación con la saturación de las LSA:

Creación de varias adyacencias:las redes Ethernet podrían interconectar muchos routers OSPF con un enlace común. La creación de adyacencias con cada router es innecesaria y no se recomienda Conduciría al intercambio de una cantidad excesiva de LSA entre routers en la misma red.
Saturación intensa con LSA:los routers de estado de enlace saturan con sus LSA cada vez que se inicializa OSPF o cuando se produce un cambio en la topología. Esta saturación puede llegar a ser excesiva.

R1(config)# router ospf 10
R1(config-router)# ?
  area                   OSPF area parameters
  auto-cost              Calculate OSPF interface cost according to bandwidth
  default-information    Control distribution of default information
  distance               Define an administrative distance
  exit                   Exit from routing protocol configuration mode
  log-adjacency-changes  Log changes in adjacency state
  neighbor               Specify a neighbor router
  network                Enable routing on an IP network
  no                     Negate a command or set its defaults
  passive-interface      Suppress routing updates on an interface
  redistribute           Redistribute information from another routing protocol
  router-id              router-id for this OSPF process

  El router ID de OSPF es un valor de 32 bits, representado como una dirección IPv4. EL router ID se utilizan para identificar un router OSPF. Todos los paquetes OSPF incluyen el router ID del router de origen. Para participar en un dominio OSPF, cada router requiere un router ID. El router ID puede estar definido por un administrador o puede ser asignado en forma automática por el router. El router ID es utilizada por un router habilitado por OSPF para hacer lo siguiente:

Participar en la sincronización de bases de datos OSPF : durante el estado de Exchange, el router con el ID más alto enviará primero sus paquetes de descriptor de base de datos (DBD).
Participar en la elección del router designado (DR) - En un entorno LAN multiacceso, el router con el ID más alto se elige el DR. El dispositivo de enrutamiento con el segundo router ID más alto, se elige como el router designado de respaldo (BDR).
Nota: El proceso electoral de DR y BDR se discute con más detalle más adelante en este módulo.

---

## MODULO-2
Configuración de OSPFv2

---
## MODULO-3
Conceptos de Seguridad en Redes


---
## MODULO-4
Conceptos de ACL

---
## MODULO-5
Configuración de ACL para IPv4



---
## MODULO-6
NAT en IPv4

---

## MODULO-8

3DES es un cifrado de cifrado derivado del Estándar de cifrado de datos (DES) original. Se hizo prominente a finales de los noventa, pero desde entonces ha caído en desgracia debido al surgimiento de algoritmos más seguros, como AES-256 y XChaCha20.

Aunque quedará obsoleto en 2023, aún se implementa en algunas situaciones. Dado que se basa en uno de los primeros algoritmos ampliamente publicados y estudiados, DES, sigue siendo importante aprender qué es 3DES y cómo funciona.

En esta guía te explicaremos cada paso del proceso DES en detalle, cómo se modifica DES en 3DES para hacerlo más seguro y los diversos problemas de seguridad y si debes o no usar el algoritmo.

