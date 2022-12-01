
#Importamos el modulo FTP
from ftplib import FTP
#
#Estableciendo conexión al server
ftp = FTP('192.168.152.129')

#Logueamos el usuario establecido
ftp.login('johnny', '1727651')

#Ahora nos ubicamos en el directorio donde esta el archivo ADVERTENCIA.txt
ftp.cwd('upload')

#Ahora listamos los archivos del directorio
ftp.retrlines('LIST')

#Para finalizar, mandamos el archivo deseado
ftp.storlines('STOR ADVERTENCIA.txt', open('ADVERTENCIA.txt', 'rb'))

#Cerramos la conexion con el servidor
ftp.quit()

