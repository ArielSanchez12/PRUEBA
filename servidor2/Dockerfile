# Usa una imagen base de Python
FROM python:3.12

# Copia los archivos de la aplicación al contenedor
COPY . .

# Instala las dependencias del sistema necesarias para mysqlclient
RUN apt-get update && apt-get install -y \
  gcc \
  default-libmysqlclient-dev \
  pkg-config \
  && rm -rf /var/lib/apt/lists/*

# Instala las dependencias de Python con timeout y reintentos
RUN pip install --timeout=120 --retries=5 Flask==2.3.2 Flask-MySQLdb==1.0.1

# Exponer el puerto
EXPOSE 5021

# Comando para iniciar la aplicación
CMD ["python", "app.py"]
