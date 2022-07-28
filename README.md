# Práctica 7 - Conexión de VM a través de redes virtuales

## Innovaccion Virtual (VII Edición) #IAWizards

### Semana 2 - Sesión 5

En esta práctica se realizó una intercomunicación entre dos máquinas virtuales a través de redes virtuales en la nube de Azure.

--------------------------------------------------------------

#### Requerimientos

- Cuenta de Azure con suscripción.

--------------------------------------------------------------

#### Pasos a seguir

1. Ingresar a portal.azure.com y creamos un grupo de recursos. Posteriormente, creamos una red virtual el cual estará alojada en el grupo de recursos previamente creado. En el apartado de ‘Direcciones IP’ del editor de la red virtual, nos aseguramos de que en el ‘Espacio de direcciones IPv4’ se encuentre la dirección 10.0.0.0/16. Aquí mismo, le damos en ‘Agregar subred’ y le damos un nombre a la nueva subred a crear, así como también le damos un intervalo de red (10.0.0.0/24) y le damos en ‘agregar’, ‘revisar y crear’ y ‘crear’ (hay que asegurarse de que no hay otra subred por default creada).

![P7I1](Images\Sesión 5 - P7 01.PNG)

![P7I2](Images\Sesión 5 - P7 02.PNG)

![P7I3](Images\Sesión 5 - P7 03.PNG)

2. Seguidamente, creamos otra red virtual en el mismo grupo de recursos. En el apartado de ‘Direcciones IP’ creamos otra subred la cual estará en la dirección 10.1.0.0/24.

![P7I4](Images\Sesión 5 - P7 04.PNG)

3. Una vez tengamos creado el grupo de recursos con las redes virtuales, creamos una máquina virtual, eligiendo como grupo de recursos la que habíamos creado en un principio. En tipo de autenticación le ponemos ‘Contraseña’ y en imagen escogemos Windows 10 Pro (O cualquier otro SO). En el apartado de ‘Cuenta de administrador’ colocamos una cuenta de usuario y contraseña. En el apartado de ‘Redes’ seleccionamos en ‘Red virtual’ la primera red virtual que creamos.

![P7I5](Images\Sesión 5 - P7 05.PNG)

![P7I6](Images\Sesión 5 - P7 06.PNG)

4. Creamos una máquina virtual más con imagen de Linux (o cualquier otro SO) con cuenta y contraseña, y en el apartado de ‘Redes’ seleccionamos en ‘Red virtual’ la segunda red virtual creada. Al finalizar la creación para ambas VM pedirá descargar un archivo de acceso, los cuales debemos guardar para poder ingresar a las VM.

![P7I7](Images\Sesión 5 - P7 07.PNG)

![P7I8](Images\Sesión 5 - P7 08.PNG)

5. Para conectar las VM entre sí, se puede usar Azure Cloud Shell (se encuentra ubicada en la pestaña superior, al lado de la barra de búsqueda del apartado ‘Conectar’ de la VM). Para esto, primero le damos en ‘Conectar’ (estando en una VM) y en ‘SSH’, y en el apartado 4 copiamos el texto que está después de “<>”.

![P7I9](Images\Sesión 5 - P7 09.PNG)

![P7I10](Images\Sesión 5 - P7 10.PNG)

6. Abrimos el Cloud Shell y si pide crear una cuenta de almacenamiento, la creamos ahí mismo. Una vez habiendo hecho esto, aparecerá la consola de comandos. Aquí escribimos “ssh” y pegamos el texto copiado en el paso 5 y después de unos segundos escribimos “yes”, para luego pedir la contraseña de la cuenta creada.

![P7I11](Images\Sesión 5 - P7 11.PNG)

7. Vamos al apartado de redes virtuales, y buscamos la primer red virtual creada. Aquí, buscamos el apartado de emparejamiento y le damos en ‘Agregar’ para crear un emparejamiento. Le ponemos un nombre al emparejamiento en ‘Nombre del vínculo de emparejamiento’ y en ‘Nombre del vínculo de emparejamiento’ también agregamos un nombre y como red virtual de destino elegimos la segunda red virtual creada. Le damos en ‘Agregar’ y esperamos a que en ‘Peering Status’ aparezca como ‘Connected’.

![P7I12](Images\Sesión 5 - P7 12.PNG)

![P7I13](Images\Sesión 5 - P7 13.PNG)

8. Una vez habiendo hecho la conexión de las redes virtuales, vamos a la segunda red virtual, y en el apartado de ‘Dispositivos conectados’ copiamos la dirección IP de la segunda VM y en la consola de comandos escribimos “ping” y pegamos la dirección IP copiada. Mostrará en pantalla los paquetes enviados a la segunda VM.

![P7I14](Images\Sesión 5 - P7 14.PNG)

![P7I15](Images\Sesión 5 - P7 15.PNG)

![P7I16](Images\Sesión 5 - P7 16.PNG)

***Información Adicional:*** Las subredes creadas en el paso 1 en realidad se realiza para cambiar el nombre de “default” a uno que queramos. Los recursos y el grupo de recursos deben ser creados en la misma región para evitar errores.