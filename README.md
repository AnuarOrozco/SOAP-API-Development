# Consumo de Servicios SOAP con Spring Boot y Maven

Este proyecto es una tarea práctica que consiste en consumir servicios web SOAP utilizando **Spring Boot** y **Maven**. El servicio consumido corresponde a una calculadora proporcionada en [http://www.dneonline.com/calculator.asmx](http://www.dneonline.com/calculator.asmx), cuya especificación WSDL se encuentra disponible en [http://www.dneonline.com/calculator.asmx?WSDL](http://www.dneonline.com/calculator.asmx?WSDL).

---

## Objetivos de la Tarea
1. Consumir un servicio web SOAP.
2. Configurar un cliente SOAP para realizar peticiones al servicio.
3. Configurar un BEAN para el cliente SOAP y un marshaller para gestionar la serialización/deserialización de mensajes SOAP.
4. Crear los **controladores** y **endpoints** para exponer las operaciones SOAP como servicios REST.
5. Comprender el proceso de **marshalling** y **unmarshalling** en SOAP, y su relación con la **serialización** y **deserialización** en REST.
6. Analizar las diferencias entre los servicios web SOAP y REST.

---

## Configuración del Proyecto

### Dependencias y Cliente SOAP
El proyecto utiliza dependencias específicas que permiten consumir servicios SOAP. Para generar las clases necesarias que representan los mensajes XML definidos en el WSDL, se utilizó un plugin de Maven que realiza la conversión de XML a clases Java. Estas clases facilitan la comunicación entre la aplicación y el servicio web.

### BEAN del Cliente y Configuración del Marshaller
En Spring Boot, un BEAN permite configurar un cliente SOAP para realizar peticiones y gestionar la comunicación con el servicio. El **marshaller** es una herramienta clave que:
- Convierte objetos Java en XML (marshalling) para que el servicio los entienda.
- Convierte las respuestas en XML del servicio a objetos Java (unmarshalling) para que la aplicación pueda utilizarlos.

---

## Creación de Controladores y Endpoints REST
Se desarrollaron controladores para exponer las operaciones del servicio SOAP mediante endpoints REST. Esto permite que otras aplicaciones o usuarios interactúen con el servicio utilizando métodos HTTP comunes como `GET` y `POST`. Cada operación, como sumar o restar, tiene un endpoint asociado que traduce las solicitudes REST en mensajes SOAP hacia el servicio y devuelve la respuesta correspondiente.

---

## Marshalling, Unmarshalling, Serialización y Deserialización

### SOAP
En SOAP, la comunicación entre la aplicación y el servicio ocurre en formato XML. Para que este XML sea comprensible para la aplicación Java:
- **Marshalling**: Convierte un objeto Java en XML.
- **Unmarshalling**: Convierte el XML recibido en un objeto Java.

Estas conversiones son necesarias porque SOAP utiliza un formato de datos más estructurado que necesita traducirse entre la representación de texto (XML) y los objetos de la aplicación.

### REST
En REST, los datos se envían y reciben en formatos ligeros como JSON o XML. Para trabajar con estos datos:
- **Serialización**: Convierte un objeto Java en JSON o XML.
- **Deserialización**: Convierte JSON o XML recibido en un objeto Java.

Aunque ambos procesos (marshalling/unmarshalling y serialización/deserialización) tienen propósitos similares, SOAP trabaja exclusivamente con XML, mientras que REST ofrece flexibilidad en los formatos utilizados.

---

## Diferencias entre SOAP y REST

### SOAP (Simple Object Access Protocol)
- Es un protocolo basado exclusivamente en XML.
- Requiere una descripción formal del servicio mediante WSDL.
- Soporta características avanzadas como transacciones y seguridad mediante WS-Security.
- Es más robusto y estructurado, pero también más complejo y pesado.

### REST (Representational State Transfer)
- Es un estilo arquitectónico que utiliza HTTP y formatos como JSON o XML.
- Es más sencillo, flexible y ligero, ideal para aplicaciones web modernas.
- No requiere un estándar estricto como WSDL, lo que facilita su implementación.
- Es más eficiente en términos de ancho de banda y procesamiento.

**Conclusión:** SOAP es adecuado para aplicaciones empresariales que requieren alta seguridad y transacciones complejas. REST es más adecuado para sistemas ligeros y rápidos como APIs públicas.

---

## Instrucciones para Ejecutar
1. Clona el repositorio del proyecto y asegúrate de tener configurado Maven.
2. Genera las clases necesarias a partir del archivo WSDL utilizando Maven.
3. Inicia la aplicación Spring Boot.
4. Accede a los endpoints REST configurados para realizar operaciones como suma, resta, multiplicación y división.

---

## Resultados
El proyecto permite consumir las operaciones expuestas por el servicio SOAP, transformando las respuestas en formatos comprensibles para la aplicación. Además, al exponer estas operaciones mediante endpoints REST, se facilita el acceso y la interacción desde aplicaciones externas o clientes REST.
