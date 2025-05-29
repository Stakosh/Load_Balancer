# Cómo ejecutar `main.py` y probar el Load Balancer

Estos pasos asumen que tienes dos scripts en la raíz de tu repositorio (por ejemplo `~/tics317/balanceador`):

- `app.py` – la aplicación de tareas (servidor web).  
- `main.py` – el balanceador de carga que reparte las solicitudes.  

---

## 1. Instalar dependencias

Abre tu terminal en la carpeta del proyecto y ejecuta:

```bash
pip install flask requests
```

---

## 2. Abrir tres terminales

Prepara tres instancias de terminal (o PowerShell):

- **Terminal A** – Primer servidor  
- **Terminal B** – Segundo servidor  
- **Terminal C** – Balanceador de carga  

---

## 3. Iniciar el primer servidor (Puerto 5001)

En **Terminal A**, sitúate en la carpeta del proyecto y arranca la app:

```bash
cd C:/Users/JaviS/Documents/tics317/balanceador
python app.py 5001
```

Deberías ver algo así:

```
 * Running on http://127.0.0.1:5001/ (Press CTRL+C to quit)
```

---

## 4. Iniciar el segundo servidor (Puerto 5002)

En **Terminal B**, repite el mismo proceso cambiando el puerto:

```bash
cd C:/Users/JaviS/Documents/tics317/balanceador
python app.py 5002
```

Verás:

```
 * Running on http://127.0.0.1:5002/ (Press CTRL+C to quit)
```

---

## 5. Iniciar el balanceador de carga

En **Terminal C**, lanza el load balancer:

```bash
cd C:/Users/JaviS/Documents/tics317/balanceador
python main.py
```

Por defecto escucha en el puerto **8080** y mostrará:

```
 * Load Balancer running on http://127.0.0.1:8080/
```

---

## 6. Probar la aplicación

Abre tu navegador y visita:

- **http://localhost:8080** → a través del balanceador.  
- **http://localhost:5001** → directo al servidor 1.  
- **http://localhost:5002** → directo al servidor 2.  

Agrega o elimina tareas vía el balanceador y observa:

- El color de fondo cambia según el servidor que atiende.  
- La carga se reparte entre los puertos 5001 y 5002.  

> **Tip:** Si `main.py` tiene opciones de línea de comandos (por ejemplo, cambiar puertos), ejecuta:
> ```bash
> python main.py --help
> ```
> para ver las opciones disponibles.
