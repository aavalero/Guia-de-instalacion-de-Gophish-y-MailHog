
## PASOS PREVIOS

### ACTUALIZAR LOS REPOSITORIOS

sudo su
apt update && apt upgrade -y
![Pasted image 20251029203057.png](Pasted image 20251029203057.png)

apt install -y wget curl git sudo
![Pasted image 20251029203145.png](Pasted image 20251029203145.png)
### INSTALACION DE GOPHISH

sudo apt install -y gophish
![Pasted image 20251029203249.png](Pasted image 20251029203249.png)

Para iniciar gopohish
![Pasted image 20251029203541.png](Pasted image 20251029203541.png)
![Pasted image 20251029203554.png](Pasted image 20251029203554.png)
### INSTALACIÓN DE MAILHOG

Utilizamos Go para instalarlo

sudo apt-get -y install golang-go
![Pasted image 20251029204003.png](Pasted image 20251029204003.png)

go install github.com/mailhog/MailHog@latest
![Pasted image 20251029204238.png](Pasted image 20251029204238.png)

Para iniciar MailHog
![Pasted image 20251029204933.png](Pasted image 20251029204933.png)
![Pasted image 20251029204948.png](Pasted image 20251029204948.png)

CONFIGURACIÓN DE GOPHISH
 1. SENDING PROFILES
		En este apartado configuramos la dirección del servidor SMTP, el correo desde el que se manada el phising y el usuario y contraseña (al hacerlo en local no aplica).
		![Pasted image 20251030203146.png](Pasted image 20251030203146.png)
		Si lo hiciéramos fuera del entorno local habría que poner un usuario y contraseña, además de incluir las cabeceras de correo correspondientes (Google) para que el correo no sea desviado a la carpeta de spam.
		![Pasted image 20251030203442.png](Pasted image 20251030203442.png)
		
 2. USERS & GROUPS
		En este apartado irían las direcciones de correo a las que queremos enviar nuestro phishing, pero al estar usando mailHog, cada vez que se envíe un correo será interceptado por este (En la captura se ve la dirección a la que se debería enviar el correo).
		![Pasted image 20251030202349.png](Pasted image 20251030202349.png)
		![Pasted image 20251030202428.png](Pasted image 20251030202428.png)
3. EMAIL TEMPLATES
		En este apartado configuramos la plantilla del correo que vamos a mandar:
		El Envelope Sender es el correo desde el que se envía el correo, siendo la parte visible que va a ver el usuario destinatario (Para pruebas reales se recomienda que coincida con el SMTP From de la sección Sending Profile)
		![Pasted image 20251030204302.png](Pasted image 20251030204302.png)
4. LANDING PAGES
		En este apartado tenemos que indicar a que página va a redirigir el correo que enviamos.
		Una vez el usuario haga click en el correo, será redigido a nuestro login, y cuando introduzca los datos, será redirigido nuevamente a otro sitio (opcional)
		![Pasted image 20251030205200.png](Pasted image 20251030205200.png)
		![Pasted image 20251030205212.png](Pasted image 20251030205212.png)
5. CAMPAINGS
	1. Una vez tenemos el entorno configurado, procedemos a lanzar la camapaña:
		Rellenamos los campos según las plantillas que hemos creado previamente y lanzamos la campaña (Al ser local la URL puede ser localhost)
		![Pasted image 20251030205348.png](Pasted image 20251030205348.png)
	2. Lanzamos la campaña y observamos que se ha recibido en mailHog
		![Pasted image 20251030205611.png](Pasted image 20251030205611.png)
	3. Revisamos el correo recibido
		![Pasted image 20251030205639.png](Pasted image 20251030205639.png)
	4. Nos redirige a nuestra landing page
		![Pasted image 20251030205721.png](Pasted image 20251030205721.png)
	5. Al enviar los datos se redirige a otra web que hemos indicado
		![Pasted image 20251030210035.png](Pasted image 20251030210035.png)
	6. Si revisamos las estadísticas de la campaña podemos observar los datos recabados
		![Pasted image 20251030210214.png](Pasted image 20251030210214.png)
		![Pasted image 20251030210230.png](Pasted image 20251030210230.png)


