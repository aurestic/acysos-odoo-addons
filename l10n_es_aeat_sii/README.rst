.. image:: https://img.shields.io/badge/licence-AGPL--3-blue.svg
   :target: http://www.gnu.org/licenses/agpl-3.0-standalone.html
   :alt: License: AGPL-3

=============================================
Suministro Inmediato de Información en el IVA
=============================================

Módulo para la presentación inmediata del IVA
http://www.agenciatributaria.es/AEAT.internet/SII.html

Installation
============

Para instalar esté módulo necesita:

#. Libreria Python Zeep, se puede instalar con el comando 'pip install zeep'
#. Libreria Python Requests, se puede instalar con el comando 'pip install requests'
#. Libreria pyOpenSSL, versión 0.15 o posterior

Una vez instalado ejecute Account Chart Update para actualizar las claves
de las posiciones fiscales.

Configuration
=============

Para configurar este módulo necesitas:

#. En la compañia se almacenan las URLs del servicio SOAP de hacienda.
Estas URLs pueden cambiar según comunidades
#. Los certificados deben alojarse en una carpeta accesible por la instalación
de Odoo.
#. Preparar el certificado. El certificado enviado por la FMNT es en formato
p12, este certificado no se puede usar directamente con Zeep. Se tiene que
extraer la clave pública y la clave privada.
El linux se pueden usar los siguientes comandos:
- Clave pública: "openssl pkcs12 -in Certificado.p12 -nokeys -out publicCert.crt -nodes"
- Clave privada: "openssl pkcs12 -in Certifcado.p12 -nocerts -out privateKey.pem -nodes"
Connector:

#. Ajustar variables de configuración:

    ODOO_CONNECTOR_CHANNELS=root:4
 
  o otro canal de configuración. Por defecto es root:1

  Si xmlrpc_port no esta definido: ODOO_CONNECTOR_PORT=8069

       Arranca odoo con --load=web,web_kanban,connector y --workers más grande que 1.

Más información http://odoo-connector.com

Usuando fichero de configuración:

[options]
(...)
workers = 4
server_wide_modules = web,web_kanban,connector

(...)
[options-connector]
channels = root:4

Usage
=====

Cuando se valida una factura automáticamente envia la comunicación al servidor
de AEAT.


Known issues / Roadmap
======================

* Operación anual. Comunicación de cobros y pagos en métalico
* Determinadas facturas intracomunitarias (Articulo 66 RIVA)
* Operación anual. Libro de bienes de inversión (Libro anual se crea un módulo aparte)
* Regimenes especial de seguros y agencias de viaje

Credits
=======

Contributors
------------

* Ignacio Ibeas - Acysos S.L. <ignacio@acysos.com>
* Oihane Crucelaegui - Avanzosc S.L. <oihanecrucelaegi@avanzosc.es>
* Rubén Cerdà -Diagram Software S.L. <ruben.cerda.roig@diagram.es>
* Ramon Guiu - Minorisa S.L. <ramon.guiu@minorisa.net>
* Pablo Fuentes - Studio73 <pablo@studio73.es>
* Jordi Tolsà - Studio73 <jordi@studio73.es>
* Omar Castiñeira - Comunitea S.L. <omar@comunitea.com>
* Ismael Calvo - Factor Libre S.L.
* Alberto Martín Cortada - Guadaltehch


Maintainer
----------

.. image:: https://acysos.com/logo.png
   :alt: Acysos S.L.
   :target: https://www.acysos.com
