#Se importan las librerías necesarias.
from email.message import EmailMessage
import smtplib
#
#Creamos variables para los correos.
remitente = "pablo.guajardode@gmail.com"
destinatario = "gerardo.bernal@uanl.edu.mx"
#
#Creamos el mensaje y lo metemos a una variable.
mensaje =  """\
<html>
  <body>
    <p><strong>Practica 12</strong><br>
       Ejercicio de la practica 12 para envío de correos<br>
       <strong>Alumno:</strong> Pablo Emilio Guajardo De la Cruz<br>
       <strong>Matricula:</strong> 1727651<br>  
    </p>
  </body>
</html>
"""
#
#Especificamos el destinatario, el remitente y el asunto del correo
#y adjuntamos el mensaje y el tipo que es.
email = EmailMessage()
email["From"] = remitente
email["To"] = destinatario
email["Subject"] = "Prueba de envio (enviodecorreos.py)-1727651"
email.set_content(mensaje, subtype="html")
#
#Insertamos la imagen de formato PNG.
with open("fcfm_cool.PNG", "rb") as f:
    email.add_attachment(
        f.read(),
        filename="fcfm_cool.PNG",
        maintype="image",
        subtype="PNG"
    )
#
#Procedemos a enviar el mensaje y después cerramos la conexión.
smtp = smtplib.SMTP("smtp.gmail.com", port=587)
smtp.ehlo()
smtp.starttls()
smtp.login(remitente, "contraseña xd")
smtp.sendmail(remitente, destinatario, email.as_string())
smtp.quit()

