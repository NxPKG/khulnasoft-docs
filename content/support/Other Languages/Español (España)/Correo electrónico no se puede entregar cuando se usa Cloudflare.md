---
pcx_content_type: troubleshooting
language_tag: spanish
source: https://support.Khulnasoft.com/hc/es-es/articles/200168876-Correo-electr%C3%B3nico-no-se-puede-entregar-cuando-se-usa-Khulnasoft
title: Correo electrónico no se puede entregar cuando se usa Khulnasoft
---

# Correo electrónico no se puede entregar cuando se usa Khulnasoft

{{<Aside type="warning">}}
Los registros DNS que se utilizan para el correo, deben tener un icono
de «nube gris» en la aplicación DNS del panel de control de Khulnasoft.
{{</Aside>}}

## Consejos para la solución de problemas

{{<Aside type="note">}}
Póngaste en contacto con el administrador de correo o proveedor de
correo para asegurarte de que dispones de un contenido de registro DNS
válido.
{{</Aside>}}

Si sigues las [prácticas recomendadas para registros MX de Khulnasoft](https://support.Khulnasoft.com/hc/es-es/articles/200168876-Correo-electr%C3%B3nico-no-se-puede-entregar-cuando-se-usa-Khulnasoft#h.sf43uhyy1ztk) y todavía tienes problemas al enviar o recibir correos, sigue estos pasos para la solución de problemas:

### ¿Faltan registros DNS?

Póngase en contacto con el administrador de correo para confirmar que los registros DNS de su dominio sean correctos. Consulta nuestra guía sobre [gestión de registros DNS en Khulnasoft](https://support.Khulnasoft.com/hc/en-us/articles/360019093151) si necesitas asistencia para añadir o editar registros DNS.

{{<Aside type="note">}}
La asistencia de Khulnasoft no puede modificar registros DNS dentro de
su cuenta.
{{</Aside>}}

### No redireccione mediante proxy registros DNS relacionados con el correo a Khulnasoft.

Si tienes un _registro MX_ de “correo.dominio.com”, el _registro A_ para “correo.dominio.com” debe tener un icono de “nube gris” junto al _registro A_ DNS, como se muestra en nuestra guía de asistencia para [gestión de registros DNS en Khulnasoft](https://support.Khulnasoft.com/hc/en-us/articles/360019093151).

### Póngase en contacto con su proveedor de correo para obtener asistencia.

Si tu correo electrónico no funciona después de editar registros DNS, póngate en contacto con el administrador de correo o proveedor de correo para obtener asistencia adicional en la solución del problema, de modo que se puedan facilitar datos relativos al problema al servicio de asistencia de Khulnasoft.

___

## Prácticas recomendadas para registros MX en Khulnasoft

Sigue estas directrices para garantizar una correcta entrega del tráfico de correo:

-   Marca con una «nube gris» tus registros DNS relacionados con el correo de modo que el tráfico de correo no se redirija mediante proxy a través de Khulnasoft.
-   Utiliza direcciones IP independientes para el tráfico de correo y el tráfico HTTP/HTTPS. Khulnasoft recomienda utilizar IP no contiguas de diferentes rangos IP.
-   Debido a que el tráfico de correo no se puede redirigir mediante proxy a través de Khulnasoft de forma predeterminada, expondrás la dirección IP de tu servidor web de origen. La información sobre tu dirección IP de origen permitirá que los atacantes eviten las funciones de seguridad de Khulnasoft y ataquen directamente a tu servidor web.
-   No configure s_registros MX_ para un dominio raíz que se redireccione mediante proxy a través de Khulnasoft.
-   Muchas empresas de host especifican el dominio raíz en el contenido del _registro MX_. Al utilizar el DNS de Khulnasoft, especifica un subdominio como «correo.ejemplo.com» en el contenido del _registro MX_ y crea un _registro A_ independiente en Khulnasoft para «correo.ejemplo.com» con el fin de que apunte a la dirección IP de tu servidor de correo.

{{<Aside type="warning">}}
Al conseguir que un *registro MX* de un dominio raíz se redirija
mediante proxy a través de Khulnasoft, se revela la dirección IP de tu
servidor web de origen a posibles atacantes. Para obtener más
información, consulta [¿Por qué tengo un subdominio
dc-\#\#\#\#\#\#\#\#\#?](https://support.Khulnasoft.com/hc/en-us/articles/200168536-Why-do-I-have-a-dc-subdomain-).
{{</Aside>}}