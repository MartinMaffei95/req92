# Requisitos Chat92

#

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

<p class="chip">Paso a paso del registro insertado en  <a href="https://www.youtube.com/watch?v=ebjs9xBp8kE&ab_channel=WhatsApp">SleekFlow</a></p>
<p class="chip">Como ven los usuarios el  <a href="https://youtu.be/w0fyl-R5yCU">Registro insertado</a></p>

Usando este modo de registro los engocios tienen sus propia WhatsApp Business Account (WABA) y comparten el acceso de estas directamente con nosotros permitiendo que los negocios administren su WABA y nos liberen de responsabilidad.

[Requisitos](https://developers.facebook.com/docs/whatsapp/embedded-signup/steps):

- <span class="req">Administrador comercial</span>: Necesitamos una cuenta del administrador comercial para administrar la línea de crédito y las cuentas de WhatsApp Business (WABA) de los clientes.
- <span class="req">App de Meta</span>:
  App creada de tipo comercial (_business_). Inicialmente cuentan con acceso estandar.Esto restringe el acceso de las apps de negocios solo a los datos de propiedad de los usuarios de la app que tienen un rol en la app o en la empresa. Para publicarla, es necesario someter a la app de Meta a la revisión de apps y solicitar acceso avanzado a los permisos:
  - <span class="req_permission">whatsapp_business_management</span>: **Debe someterse a la
    [REVISION DE APPS](https://developers.facebook.com/docs/app-review).** Se utiliza para administrar números de teléfono, plantillas de mensajes, el registro y el perfil de empresa en una cuenta de WhatsApp Business.
  - <span class="req_permission">business_management</span>: **Debe someterse a la
    [REVISION DE APPS](https://developers.facebook.com/docs/app-review).**. Se usa para administrar las cuentas comerciales de sus clientes y compartir sus líneas de crédito con los negocios de estos.

<p class="extra_info">Se recomienda realizar este proceso lo antes posible. No es necesario que esperes a que el registro insertado esté totalmente implementado para iniciar este proceso.  </p>

- <span class="req">Usuario del sistema del administrador comercial</span>:
- <span class="req">Línea de crédito</span>:Es necesario que configures una línea de crédito para enviar mensajes con la API de la Plataforma de WhatsApp Business. Esta es la línea de crédito que compartirás con los negocios del cliente.

#

## Chat

### Whatsapp

Accediendo a la app mediante el SDK de Facebook obtenemos un token extendido para la utilización de Whatsapp API
Para poder tener interacciones con numeros ajenos a los de la lista de desarrollo de la app necesitamos:

1. Token de acceso con los siguientes permisos:

- <span class="req_permission">whatsapp_business_management</span>: **Debe someterse a la
  [REVISION DE APPS](https://developers.facebook.com/docs/app-review).** Se utiliza para administrar números de teléfono, plantillas de mensajes, el registro y el perfil de empresa en una cuenta de WhatsApp Business.
- <span class="req_permission">whatsapp_business_messaging</span>: **Debe someterse a la
  [REVISION DE APPS](https://developers.facebook.com/docs/app-review).** Se utiliza para enviar y recibir mensajes de usuarios de WhatsApp y cargar y descargar archivos multimedia en una cuenta de WhatsApp Business.
- <span class="req_permission">business_management</span>: **Debe someterse a la
  [REVISION DE APPS](https://developers.facebook.com/docs/app-review).**

2. Webhooks configurados. Se utilizaran para poder recibir notificaciones HTTP en tiempo real desde la pltaforma de WAB. _Por ejemplo; se te envía un mensaje de un cliente o se realizan cambios en tu cuenta de WhatsApp Business (WABA)._

### Messenger

[Primeros pasos](https://developers.facebook.com/docs/messenger-platform/conversations)
Es posible obtener la siguiente información:

- Una lista de conversaciones de la página de Facebook o tu cuenta profesional de Instagram
- Una lista de mensajes dentro de cada conversación
- Información detallada acerca de cada mensaje, que incluye cuándo se envió el mensaje y quién lo envió

Necesitarás lo siguiente:

- El identificador de la página de Facebook de tu negocio o la página de Facebook vinculada a la cuenta profesional de Instagram
- Un token de acceso a la página solicitado a una persona que pueda realizar la tarea <span class="req_permission">MESSAGING</span> o <span class="req_permission">MODERATE</span> en la página
- Se requiere acceso avanzado para acceder a las conversaciones que se generan entre el negocio y las personas que no tienen un rol en tu app de mensajes, tu cuenta profesional de Instagram, tu página de Facebook o tu negocio

Para conversaciones de Messenger entre las personas y tu página

- Un token de acceso a la página solicitado por una persona que pueda realizar la tarea <span class="req_permission">MESSAGING</span> o <span class="req_permission">MODERATE</span> en la página
- Los permisos <span class="req_permission">pages_manage_metadata</span>, <span class="req_permission">pages_read_engagement</span> y <span class="req_permission">pages_messaging</span>

Para conversaciones de mensajes de Instagram entre las personas y la cuenta profesional de Instagram

- Un token de acceso a la página solicitado por una persona que pueda realizar la tarea MESSAGING en la página vinculada a tu cuenta comercial de Instagram
- Los permisos <span class="req_permission">instagram_basic</span>, <span class="req_permission">instagram_manage_messages</span> y <span class="req_permission">pages_manage_metadata</span>
- Tu app debe ser propiedad de un negocio verificado

#

- The <span class="req_permission">pages_show_list</span> permission and a User access token, requested by you. This allows your app, or the Graph API Explorer, to get your Page ID.
- The <span class="req_permission">pages_messaging</span> permission and a Page access token, requested by a person who can perform the MESSAGING task on your Page, allows your app to get the conversation ID and your Page-scoped ID (PSID)

<style>
    .req {
    font-weight:bold;
    letter-spacing:.02rem;
    background-color:#d46611;
    padding-inline:4px;
    border-radius:2px;
        color:#fff;
        }
.req_permission {
    font-family:consolas;
    letter-spacing:.02rem;
    background-color:#1d784a;
    padding-inline:4px;
    border-radius:2px;
    color:#fff;
        }

.chip{
    font-size:14px;
    font-style:italic;
    background-color:#d4d9d6;
    color:#232423;
    padding-inline:4px;
    border-radius:2px;
    position:relative;
    padding-left:1rem;
}
.chip::before{
    content:'';
    top:0;
    left:0;
    height:100%;
    width:.5rem;
    position:absolute;
    background-color:orange;
}

.extra_info{
    font-family:consolas;
    font-size:14px;
    font-style:italic;
    background-color:#d4d9d6;
    color:#232423;
    padding-inline:4px;
    border-radius:2px;
    position:relative;
    padding-left:1rem;
}
.extra_info::before{
    content:'';
    top:0;
    left:0;
    height:100%;
    width:.5rem;
    position:absolute;
    background-color:green;
}
</style>
