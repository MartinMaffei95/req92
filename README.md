# Requisitos Chat92

## Login/Logout

### Facebook

La forma mas facil de logearnos con una cuenta de Facebook es utilizando el [SDK](https://developers.facebook.com/docs/javascript), nos retorna un token de acceso con permisos basicos previamente pedidos al usuario

Para crear este login en nuestro sitio necesitamos:

1. [Cuenta de desarrollador de Facebook](https://developers.facebook.com/docs/development/register)
2. [App registrada](https://developers.facebook.com/docs/development/create-an-app) y con la configuracion basica de [Login con Facebook](https://developers.facebook.com/docs/facebook-login/)
3. [SDK de Facebook](https://developers.facebook.com/docs/javascript)
4. Dominio con protocolo HTTPS p/obtener tokens _(En caso de no tenerlo Facebook rechazara la conexión)_

[REVISION DE APPS](https://developers.facebook.com/docs/app-review)

### Whatsapp

El [Registro insertado](https://developers.facebook.com/docs/whatsapp/embedded-signup) es una forma con la que cuentan los proveedores de soluciones comerciales (BSP) que permitir incorporar empresas a la Plataforma de WhatsApp Business directamente desde sus sitios web.

> Paso a paso del registro insertado en <a href="https://youtu.be/w0fyl-R5yCU">SleekFlow</a>

> Como ven los usuarios el <a href="https://www.youtube.com/watch?v=ebjs9xBp8kE&ab_channel=WhatsApp">Registro insertado</a>

Usando este modo de registro los negocios tienen sus propia WhatsApp Business Account (WABA) y comparten el acceso de estas directamente con nosotros permitiendo que los negocios administren su WABA y nos liberen de responsabilidad.

[Requisitos](https://developers.facebook.com/docs/whatsapp/embedded-signup/steps):

- **Administrador comercial**: Necesitamos una cuenta del administrador comercial para administrar la línea de crédito y las cuentas de WhatsApp Business (WABA) de los clientes.
- **App de Meta:** App creada de tipo comercial (_business_). Inicialmente cuentan con acceso estandar.Esto restringe el acceso de las apps de negocios solo a los datos de propiedad de los usuarios de la app que tienen un rol en la app o en la empresa. Para publicarla, es necesario someter a la app de Meta a la revisión de apps y solicitar acceso avanzado a los permisos:
  - `whatsapp_business_management`: **Debe someterse a la
    [REVISION DE APPS](https://developers.facebook.com/docs/app-review).** Se utiliza para administrar números de teléfono, plantillas de mensajes, el registro y el perfil de empresa en una cuenta de WhatsApp Business.
  - `business_management`: **Debe someterse a la
    [REVISION DE APPS](https://developers.facebook.com/docs/app-review).**. Se usa para administrar las cuentas comerciales de sus clientes y compartir sus líneas de crédito con los negocios de estos.

> Se recomienda realizar este proceso lo antes posible. No es necesario que esperes a que el registro insertado esté totalmente implementado para iniciar este proceso.

- **Usuario del sistema del administrador comercial**
- **Línea de crédito:** Es necesario que configures una línea de crédito para enviar mensajes con la API de la Plataforma de WhatsApp Business. Esta es la línea de crédito que compartirás con los negocios del cliente.  
  Consulta [Compartir acceso a la facturación mensual](https://www.facebook.com/business/help/236222650393613?id=2356205651275420) para obtener información sobre cómo compartir la línea de crédito a través del administrador comercial en vez de a través de la API.

#

## Chat

### Whatsapp

Accediendo a la app mediante el SDK de Facebook obtenemos un token extendido para la utilización de Whatsapp API
Para poder tener interacciones con numeros ajenos a los de la lista de desarrollo de la app necesitamos:

1. Token de acceso con los siguientes permisos:

- `whatsapp_business_management`: **Debe someterse a la
  [REVISION DE APPS](https://developers.facebook.com/docs/app-review).** Se utiliza para administrar números de teléfono, plantillas de mensajes, el registro y el perfil de empresa en una cuenta de WhatsApp Business.
- `whatsapp_business_messaging`: **Debe someterse a la
  [REVISION DE APPS](https://developers.facebook.com/docs/app-review).** Se utiliza para enviar y recibir mensajes de usuarios de WhatsApp y cargar y descargar archivos multimedia en una cuenta de WhatsApp Business.
- `business_management`: **Debe someterse a la
  [REVISION DE APPS](https://developers.facebook.com/docs/app-review).**

2. Webhooks configurados. Se utilizaran para poder recibir notificaciones HTTP en tiempo real desde la pltaforma de WAB. _Por ejemplo; se te envía un mensaje de un cliente o se realizan cambios en tu cuenta de WhatsApp Business (WABA)._

### Messenger

Mediante la **[API de conversaciones de la plataforma de Messenger](https://developers.facebook.com/docs/messenger-platform/conversations)** es posible obtener la siguiente información:

- Una lista de conversaciones de la página de Facebook o tu cuenta profesional de Instagram
- Una lista de mensajes dentro de cada conversación
- Información detallada acerca de cada mensaje, que incluye cuándo se envió el mensaje y quién lo envió

Necesitarás lo siguiente:

- El identificador de la página de Facebook de tu negocio o la página de Facebook vinculada a la cuenta profesional de Instagram
- Un token de acceso a la página solicitado a una persona que pueda realizar la tarea `MESSAGING` o `MODERATE` en la página
- Se requiere acceso avanzado para acceder a las conversaciones que se generan entre el negocio y las personas que no tienen un rol en tu app de mensajes, tu cuenta profesional de Instagram, tu página de Facebook o tu negocio

Para conversaciones de Messenger entre las personas y tu página

- Un token de acceso a la página solicitado por una persona que pueda realizar la tarea `MESSAGING` o `MODERATE` en la página
- Los permisos `pages_manage_metadata`, `pages_read_engagement` y `pages_messaging`

Para conversaciones de mensajes de Instagram entre las personas y la cuenta profesional de Instagram

- Un token de acceso a la página solicitado por una persona que pueda realizar la tarea `MESSAGING` en la página vinculada a tu cuenta comercial de Instagram
- Los permisos `instagram_basic`, `instagram_manage_messages` y `pages_manage_metadata`
- Tu app debe ser propiedad de un negocio verificado

Nuestro servicio necesitara tambien:

- **Acceso avanzado** para poder obtener informacion de paginas de personas que NO dispongan de un rol (desarrollo, testing o propiedad) en la app.
- **Business Verification**: Es requqerido para poder obtener el acceso avanzado.
- **APP revisada**: Probablemente debamos someter a revision nuestra app para poder acceder a los servicios de mensajeria en nombre de terceros

#
