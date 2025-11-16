# D-licias_Fast_Food
# Desplegar Proyecto Web D'Licias Fast Food Localmente con Windows

Pasos a Seguir:

📋 Qué Necesitas

- XAMPP instalado

- El proyecto descomprimido

1. Preparar XAMPP
Abrir XAMPP Control Panel
Iniciar Apache y MySQL
![local-xampp-start](imagenes/local-xampp-start.png)

2. Colocar tu Proyecto
Copiar tu carpeta del proyecto a: C:\xampp\htdocs\

![local-colocar-proyecto](imagenes/local-colocar-proyecto.png)

4. Configurar Base de Datos en phpMyAdmin
Abrir navegador
Ir a: http://localhost/phpmyadmin

Crear nueva base de datos:
Click en "Nueva"
Nombre: db_broasteria
Click "Crear"
![local-phpmyadmin1](imagenes/local-phpmyadmin1.png)
![local-phpmyadmin2](imagenes/local-phpmyadmin2.png)

Pantalla principal
Crear base de datos

4. Importar o Crear Tablas
Seleccionar tu base de datos
Click en "Importar" para subir archivo .sql
O crear tablas manualmente con "SQL"

En este Caso Crearemos las tablas con algunos datos.
![local-bd](imagenes/local-bd.png)
![local-bd2](imagenes/local-bd2.png)

5. Configurar Conexión a BD en tu Proyecto
Asegurate que tu archivo archivo PHP de conexión este de la siguiente forma:

![local-configuracion](imagenes/local-configuracion.png)

6. Verificamos la pagina en red local todo deberia funcionar con normalidad

![local-pagina-funciona](imagenes/local-pagina-funciona.png)



# Desplegar Proyecto Web D'Licias Fast Food en la nube AWS EC2 con Windows Server 2019
🚀 Guía: Desplegar Proyecto Web D'Licias Fast Food en la nube AWS EC2 con Windows Server 2019

📋 Prerrequisitos

    Cuenta de AWS

    Proyecto web listo para desplegar

    Conocimientos básicos de AWS EC2

1. Crear Instancia EC2 con Windows Server 2019
Configuración en la consola de AWS:

    Servicio: EC2

    Imagen de máquina de Amazon: "Windows Server 2019 Base"

    Tipo de instancia: t3.small

    Par de claves: connect (.pem)

Configuración de red:

    Ir a Configuraciones de red → Firewall (Grupos de seguridad)

    Seleccionar Crear grupo de seguridad

    Marcar las casillas:

        ✅ Permitir el tráfico de RDP desde 0.0.0.0/0

        ✅ Permitir el tráfico de HTTPS desde Internet

        ✅ Permitir el tráfico de HTTP desde Internet

![seleccion-ami](imagenes/paso1-seleccion-ami.png)
![tipo-instancia](imagenes/paso1-tipo-instancia.png)
![configuracion-red](imagenes/paso1-configuracion-red.png)
![configuracion-almacenamiento](imagenes/paso1-configuracion-almacenamiento.png)

Vista de instancias creadas:

![instancia-creada](imagenes/paso1-instancia-creada.png)

2. Configurar Reglas de Seguridad (Grupo de Seguridad)
En la consola de AWS:

    Ir a "Grupos de Seguridad"

    Crear nuevo grupo o editar el existente

    Agregar reglas:

Tipo	Protocolo	Puerto	Origen	Descripción
HTTP	TCP	80	0.0.0.0/0	Acceso web
HTTPS	TCP	443	0.0.0.0/0	SSL
RDP	TCP	3389	0.0.0.0/0	Administración

![reglas-seguridad](imagenes/paso2-reglas-seguridad.png)

3. Conectar a la Instancia Windows

![conexion-instancia](imagenes/paso3-conexion-instancia.png)

Procedimiento:

    Presionar Conectar → Cliente de RDP

    En la sección contraseña hacer clic en Obtener contraseña

    Subir el archivo .pem generado previamente

    Copiar la contraseña generada

Conexión RDP:

    Usar Conexión Escritorio Remoto

    IP pública: 34.201.62.196 (usar tu IP específica)

    Usuario: Administrator

    Contraseña: La generada en el paso anterior

![conexion-rdp](imagenes/paso3-conexion-rdp.png)

4. Configurar Xampp en Windows Server 2019

En la instancia Windows, instalar y configurar Xampp:

![xampp-1](imagenes/paso4-xampp-1.png)
![xampp-2](imagenes/paso4-xampp-2.png)

5. Configurar Sitio Web

Desplegar el proyecto web en la carpeta htdocs de Xampp:

![sitio-1](imagenes/paso5-sitio-1.png)
![sitio-2](imagenes/paso5-sitio-2.png)

Configurar regla en el firewall de Windows:

![firewall-1](imagenes/paso5-firewall-1.png)
![firewall-2](imagenes/paso5-firewall-2.png)
![firewall-3](imagenes/paso5-firewall-3.png)
![firewall-4](imagenes/paso5-firewall-4.png)
![firewall-5](imagenes/paso5-firewall-5.png)
![firewall-6](imagenes/paso5-firewall-6.png)

6. Probar el Sitio Web
Obtener IP pública de tu instancia EC2:

![ip-publica](imagenes/paso6-ip-publica.png)

Acceso al sitio web:

Abrir navegador y acceder mediante:

    IP pública: http://34.201.62.196/

    DNS público: http://ec2-34-201-62-196.compute-1.amazonaws.com/

![sitio-funcionando](imagenes/paso6-sitio-funcionando.png)
