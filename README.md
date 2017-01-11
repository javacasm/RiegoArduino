<h1>Comunicaciones Radio</h1>
<p>Algo que cada vez se requiere en más proyectos es la comunicación inalámbrica entre diferentes componentes del mismo. El realizar proyectos distribuidos y el añadir capacidad de procesamiento lleva a utilizar cada vez más sistemas semiíntenligentes</p>
<p>Existen diferentes tecnologías para conseguir esta comunicación por radio. Unas usan tecnología digital, otras analógica, los primeros consiguen mayor calidad, frente al menor precio de los segundos. Algunos dispositivos digitales son capaces de garantizar la entrega de los paquetes y permiten que el microcontrolador no tenga que realizar tareas de este tipo.</p>
<p>Cuando vayamos a utilizarlos en algún proyecto debemos estudiar la capacidad de comunicación que necesita nuestro proyecto, tanto en ancho de banda como la calidad del mismo.</p>
<p>Normalmente tendremos que desarrollar un protocolo propio para enviar nuestra información, protocolo que se basará en el propio protocolo de transporte del dispositivo usado.</p>
<p>En este vídeo vamos a ver algunas de las distinas formas de utilizar comunicaciones radio con Arduino</p>
<p><br> <iframe width="960" height="720" src="http://www.youtube.com/embed/_uRbiYx_nPQ" frameborder="0" allowfullscreen=""></iframe></p>
<p>Veamos ahora cómo usarlos, con librerías y conexiones</p>
<p><iframe width="960" height="720" src="http://www.youtube.com/embed/QKExgg_kUtM" frameborder="0" allowfullscreen=""></iframe></p>
<p>Existen otras librerias con mayor funcionalidad, capaces de controlar los dispositivos Nordic</p>
<p><br> <iframe width="960" height="720" src="http://www.youtube.com/embed/3lMUoepgeQg" frameborder="0" allowfullscreen=""></iframe></p>
<p>Si tuvieramos que elegir un sistema de comunicaciones inalámbrica sería sin duda el NRF: es un todo-terreno que podría sustituir a cualquier 485. Además nos evita el cableado que es un infierno en obra ya terminada. Me imagino que has visto que se usa en proyecto de Riego de esta Unidad y se habla en el 3 en la parte de comunicaciones.</p>
<p>Efectivamente existen 2 librerías muy usadas Mirf y la RF24. La primera creo que es más usada por motivos históricos, pero la RF24 es más avanzada y ademas se puede usar en la serie ATTiny lo que te permite montar un nodo de la red en un espacio completamente enano.</p>
<p>Sobre el tema de la interferencias, cobertura, &nbsp;y alcance no hay que preocuparse, porque si bien los modelos más baratos tienen un alcance algo limitado en interiores existen otros equipos con conector SMA a los que les puedes poner antenas de alta ganancia alcanzando hasta Km sin problema. Otro ventaja en este tema es que puedes regular la potencia de transmisión con lo que puedes ahorrar energía.</p>
<p>Sobre las interferencias es algo que te evitas al usar un protocolo con ACK &nbsp;(confirmación de llegada) y reintento automático. Si no necesitas enviar muchos datos por segundo sólo tendrías que ampliar el timeout para garantizar que siempre se entrega. Un sencillo contador de paquetes perdidos puede permitirte llevar una estadísticas y en caso de detectar pérdidas, ampliar la potencia de envío.</p>
<p>En uno de los proyectos del módulo 6, el riego, &nbsp;se explican los pasos para completar un proyecto que usa radio.</p>

## Proyecto de Riego con Arduino via Nordic

<h1>Riego usando comunicaciones RF</h1>
<p>En el siguiente proyecto propio vamos a poner en funcionamiento un sistema de riego completo comunicado por radiofrecuencia.</p>
<p>La idea es hacer un sistema modular, con sensores de humedad, lluvia y meteorológicos y con actuadores que en principio serán ventiladores y bombas de agua. Incluiremos una centralita accesible por el usuario donde pueda visualizar los datos.&nbsp;</p>
<p>Al tratarse de equipos en distintas ubicaciones intentaremos usar siempre que sea posible alimentaciones propias de sistemas aislados, como energía solar o baterías.</p>
<p>Vamos a comenzar con los sensores a utilizar.</p>
<p><br> <iframe width="640" height="480" src="http://www.youtube.com/embed/u-RYOKm2BOQ" frameborder="0" allowfullscreen=""></iframe></p>
<p></p>
<p>Veremos ahora las comunicaciones entre los sensores de riego y la centralita, a la que dotaremos de una pantalla LCD.</p>
<p><br> </p>
<p>Vamos a comenzar con la descripción del hardware que usaremos</p>
<p><iframe width="640" height="480" src="http://www.youtube.com/embed/O1iA9qXBZMQ" frameborder="0" allowfullscreen=""></iframe> </p>
<p>Vamos a ver ahora el software que usaremos para controlar el sistema</p>
<p><br> <iframe width="640" height="480" src="http://www.youtube.com/embed/3YhfpnyclbM" frameborder="0" allowfullscreen=""></iframe> </p>
<p>Veremos ahora ya las comunicaciones funcionando</p>
<p><br> <iframe width="640" height="480" src="http://www.youtube.com/embed/nE8y3oKWcFg" frameborder="0" allowfullscreen=""></iframe> </p>
<p>Algo a tener en cuenta con este sistema de comunicaciones es que cualquier integrante del sistema puede saturar el canal dando lugar a que el resto no pueda comunicarse. Vamos a verlo en unos vídeos</p>
<p></p>
<p>Envío masivo de B saturando el canal</p>
<p><br> <iframe width="640" height="480" src="http://www.youtube.com/embed/Wn2IJO-4T4U" frameborder="0" allowfullscreen=""></iframe> </p>
<p>Ahora es A el que satura el canal con sus envíos</p>
<p><br> <iframe width="640" height="480" src="http://www.youtube.com/embed/fta5koiCVdQ" frameborder="0" allowfullscreen=""></iframe> </p>
<p>Envío equilibrado, ambas participantes envían datos sin problema</p>
<p><br> <iframe width="640" height="480" src="http://www.youtube.com/embed/iAIGMFyru80" frameborder="0" allowfullscreen=""></iframe> </p>
<p>CONTINUARÁ....</p>
<p><span style="font-size: 1.5em; font-weight: bold; line-height: 1.4;">Apéndice: Usando SPI</span></p>
<p>Para ampliar los conocimientos de Nordic vamos a ver algunos datos Veamos ahora algunos detalles</p>
<p>Formato paquetes:</p>
<p>1 octets PREAMBLE<br>4 octets ADDRESS<br>9 bits packet control field<br>0 to 32 octets PAYLOAD<br>2 octets CRC</p>
<p></p>
<p></p>
<p>Más sobre Nordic</p>
<p>http://www.insidegadgets.com/2012/08/22/using-the-nrf24l01-wireless-module/<br>http://www.diyembedded.com/tutorials/nrf24l01_0/nrf24l01_tutorial_0.pdf</p>
