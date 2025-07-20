# Requerimientos mínimos del proyecto final

Cada equipo deberá diseñar un sistema distribuido funcional basado en ESP32, cumpliendo con los siguientes requisitos técnicos mínimos.  Se recomienda usar esta lista la como checklist de validación por equipo y agregar los temas que consideren pertinentes.

---

## 1. Estructura y programación general

* [ ] El código debe evitar el uso de `delay()` para temporización. Se debe utilizar `millis()` u otras técnicas no bloqueantes.
* [ ] Uso de tipos de datos fijos del encabezado `<stdint.h>`: `uint8_t`, `int16_t`, `float`, etc.
* [ ] Implementación de EEPROM (Arduino) o `Preferences` (ESP32) para almacenar datos persistentes.
* [ ] El código debe estar organizado en múltiples archivos `.cpp` y `.h`, de forma modular.
* [ ] Uso de directivas del preprocesador: `#define`, `#ifdef`, `#pragma once`, etc.
* [ ] Uso de al menos una estructura (`struct`) para encapsular múltiples variables relacionadas.
* [ ] Uso de apuntadores y referencias en funciones o estructuras, para acceder a datos dinámicos.
* [ ] Implementación de una máquina de estados finita utilizando estructura `switch-case`.
* [ ] Uso de `enum` para definir estados, comandos o identificadores legibles por nombre.
* [ ] Uso del operador módulo `%` para control de tiempo no bloqueante (temporización periódica).
* [ ] El sistema debe manejar correctamente el desbordamiento de `millis()` (cada \~49 días).
* [ ] Uso de al menos una librería personalizada creada por el equipo, con cabecera propia (`.h`) y archivo fuente (`.cpp`).
* [ ] El sistema debe estar diseñado para funcionar de forma completamente autónoma, alimentado por batería o pila USB, sin conexión al IDE ni a una PC durante la operación.

---

## 2. Interfaz y periféricos

* [ ] Inclusión de al menos un teclado matricial 4x4, utilizado para ingresar comandos, datos o IDs.
* [ ] Inclusión de al menos una pantalla: OLED (128x32 o 128x64), o LCD 16x2 con módulo I2C.
* [ ] Navegación básica por menú o visualización de múltiples mensajes.
* [ ] Visualización en pantalla de al menos 3 tipos de datos o estados diferentes.

---

## 3. Sensores y adquisición de datos

* [ ] Integración de dos sensores diferentes: uno analógico (ej. LM35, TMP36, potenciómetro) y uno digital (ej. MAX30102, DHT11, pulsador digital).
* [ ] Los sensores deben ser muestreados periódicamente.
* [ ] Las lecturas deben mostrarse en pantalla local y transmitirse por red.

---

## 4. Comunicación inalámbrica

* [ ] Implementación de Bluetooth clásico (SPP) en al menos un nodo.
* [ ] Implementación de WiFi (modo cliente / STA) para comunicación con el servidor.
* [ ] Uso de HTTP (GET y POST) o WebSocket para transmisión de datos entre nodos y servidor.
* [ ] Al menos un ejemplo de comunicación bidireccional, en donde un cliente envíe comandos al nodo sensor y reciba respuesta.
* [ ] Reenvío coordinado Bluetooth ↔ WiFi desde un nodo puente (bridge).

---

## 5. Sistema distribuido y colaboración entre nodos

* [ ] Al menos un nodo sensor autónomo que mida y transmita señales.
* [ ] Al menos un nodo puente que reciba datos por Bluetooth y los reenvíe por WiFi.
* [ ] Un servidor en PC, implementado en Python con Flask o Node.js con Express.
* [ ] Al menos un cliente remoto (ESP32) que consulte y muestre datos desde el servidor.
* [ ] Visualización adicional en navegador (celular o PC cliente).

---

## 6. Control remoto y comandos

* [ ] El servidor web deberá incluir un formulario para enviar comandos a los nodos sensores.
* [ ] El sistema debe interpretar:

  * Comandos fijos, como `NUEVA`, `REINICIAR`, `FRECUENCIA:5`.
  * Comandos libres en texto (ej. mostrar mensajes personalizados).
* [ ] Los comandos deben propagarse por la red hasta llegar al nodo sensor (incluso vía Bluetooth).

---

## 7. Almacenamiento y consulta de historial

* [ ] El servidor debe almacenar cada lectura en una base de datos local, preferentemente SQLite (mínimo requerido) o MySQL (opcional).
* [ ] Cada dato almacenado debe incluir: fecha y hora, ID de paciente, y valores medidos.
* [ ] La página web del servidor debe permitir consultar el historial por paciente, mostrando todos los registros recibidos.
* [ ] Opcional: los clientes ESP32 pueden también consultar el historial y visualizarlo en su pantalla.

---

## 8. Extras opcionales para puntos adicionales

* [ ] Uso de animaciones o efectos visuales (barras de progreso, transiciones, íconos personalizados).
* [ ] Visualización gráfica en tiempo real (HTML5, Chart.js o similar).
* [ ] Servidor ESP32 como Access Point.
* [ ] Nodo que actúe como router o intermediario para múltiples sensores.
* [ ] Interfaz remota desde el navegador para cambiar configuración (sin teclado físico).
* [ ] Soporte para múltiples idiomas o modos de visualización en pantalla.
