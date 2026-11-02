# Sistema Móvil IoT de Preservación de Archivos Históricos 

**Estudiante:** Yoshua Alberto Castillo Martínez  

## 1. Definición del Proyecto (Paso 1)
* **Problemática OT:** Conservación preventiva del microclima en bóvedas de manuscritos y obras patrimoniales (control estricto entre 18 °C y 21 °C y humedad de 45% a 55%).
* **Herramientas:** Android Studio, Kotlin, Material Design Components, SQLite (`SQLiteOpenHelper`) y Sockets inalámbricos TCP/IP.

## 2. Diseño de la Solución y Seguridad ISO/IEC 27400 (Paso 2 y 3)
* **Comunicación Inalámbrica:** Enlace Wi-Fi TCP/IP en el puerto `8888` entre Dispositivo Emisor (Sensor Bóveda) y Dispositivo Receptor (Consola del Curador).
* **Seguridad ISO 27400:**
  1. Cifrado de credenciales en base de datos mediante algoritmo **SHA-256**.
  2. Verificación de integridad de paquetes inalámbricos mediante firma **Checksum SHA-256** por trama.
  3. Principio de privilegios mínimos en `AndroidManifest.xml`.

## 3. Matriz de Pruebas de Funcionamiento (Paso 3)
| ID | Prueba | Resultado Esperado | Estado |
| :--- | :--- | :--- | :--- |
| **P01** | Autenticación SQLite + SHA-256 | Valida credenciales correctas (`admin`/`1234`) y rechaza contraseñas adulteradas. | APROBADO |
| **P02** | Enlace Inalámbrico entre Dispositivos | Transmite y recibe tramas de temperatura, humedad y estado HVAC sin pérdida de paquetes. | APROBADO |
| **P03** | Persistencia y Consulta en Tiempo Real | Inserta lecturas en tabla `telemetry` y actualiza el historial cronológico en UI. | APROBADO |
| **P04** | Cumplimiento Seguridad ISO 27400 | Verifica hash de usuario y descarta tramas con checksum inválido. | APROBADO |
