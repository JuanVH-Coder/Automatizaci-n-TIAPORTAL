Control PID de Temperatura con PLC S7-1500 y HMI
Este proyecto implementa un sistema de control PID para regular la temperatura mediante un servomotor y un variador de frecuencia, usando un PLC Siemens S7-1500. Además, se incluye la integración con un HMI desarrollado en WinCC y el manejo de datos en una nube para monitoreo remoto.

Índice
Objetivos
Tecnologías Usadas
Arquitectura del Sistema
Configuración del Entorno
Funcionamiento
Instrucciones de Instalación
Conclusiones

Objetivo General
Diseñar e implementar un sistema automatizado de control de temperatura para un horno de dos cámaras utilizando
PLC S7-1500, integrando técnicas y equipos de control industrial para desarrollar una plataforma de aprendizaje
práctica que simule procesos térmicos industriales reales.
Objetivos Específicos
• Desarrollar y construir un prototipo de planta térmica con componentes electrónicos integrados,
incorporando etapas de potencia adecuadas, sistemas de sensores y actuadores para un control preciso de
temperatura.
• Implementar y analizar diferentes estrategias de control PID utilizando el PLC S7-1500, comparando
métodos de sintonización manual y automática para lograr una regulación óptima de temperatura con error en
estado estacionario inferior al 2%.
• Diseñar e implementar una interfaz HMI intuitiva que permita el monitoreo en tiempo real, la
configuración de puntos de referencia de temperatura y la gestión de alarmas de seguridad para el sistema
térmico.
• Validar el desempeño del sistema mediante pruebas experimentales y análisis de datos, documentando
el comportamiento de las diferentes estrategias de control y su eficacia en el mantenimiento de las condiciones
deseadas de temperatura.


Tecnologías Usadas
Hardware:
PLC Siemens S7-1500
Servomotor
Variador de frecuencia
Software:
TIA Portal v16
WinCC Advanced
Plataforma de almacenamiento en la nube (FIREBASE-NODERED)

ARQUITECTURA:
![image](https://github.com/user-attachments/assets/6361349e-77c6-42cb-8c64-1ce92cff5832)

MODELADO MATEMATICO
Para modelar matemáticamente una planta térmica de dos recámaras, se emplean las ecuaciones de balance de energía
y las leyes de transferencia de calor.
![image](https://github.com/user-attachments/assets/399b40e9-c06c-41c2-82db-1c3704fc635d)
Notación de las variables:
• C1: Capacidad calorífica de la recámara 1.
• C2: Capacidad calorífica de la recámara 2.
• R12: Resistencia térmica entre las recámaras 1 y 2.
• R2a: Resistencia térmica entre la recámara 2 y el ambiente (asumiendo que el ambiente está a una temperatura
constante Ta).
• T1: Temperatura en la recámara 1.
• T2: Temperatura en la recámara 2.
• q1: Flujo de calor de la recámara 1 a la recámara 2.
• q2: Flujo de calor de la recámara 2 al ambiente.
![image](https://github.com/user-attachments/assets/5823ebd0-6a28-4955-b8b9-e19c20353d56)

![image](https://github.com/user-attachments/assets/9ab78a9f-0ea1-46c6-b539-46a4749d2ac4)


PID COMPACT
Se crea un bloque de organización cíclico (OB30) para el control de temperatura, donde se implementa el bloque
tecnológico PID_COMPACT, en el que automáticamente genera sus propias ganancias del PID. Este procedimiento se
realiza a través de la ventana de propiedades , donde se selecciona la temperatura como el tipo de regulación , se
configuran los parámetros de entrada/Salida: La entrada es una analógica para realizar la lectura del sensor, y la salida
para el control de la planta térmica, para lo anterior es crucial realizar un correcto escalamiento de señales, convirtiendo
las señales eléctricas entre 0-5V a unidades de (°C) para la temperatura, y definiendo apropiadamente los rangos de
control para el actuador. En los ajustes avanzados, se define el tiempo de muestreo para el proceso de la planta térmica,
fue un tiempo de muestreo entre 100-500ms, y se selecciona el modo de operación que es para el calentamiento de la
cámara en donde va el sensor. La sintonización del controlador PID se puede realizar mediante dos métodos principales:
la sintonización automática, utilizando las funciones integradas de "Optimización inicial" y "Optimización final" del
PID_Compact, que calculan automáticamente los parámetros óptimos del controlador; o la sintonización manual, donde
se ajustan los parámetros Kp (ganancia proporcional), Ti (tiempo integral) y Td (tiempo derivativo) basándose en la
respuesta observada del sistema. Cada paso se puede observar en los anexos.
Sintonización Manual:
En el proceso de sintonización manual utilizando el método gráfico de Ziegler-Nichols, Se realiza el respectivo análisis
de la respuesta térmica ante una entrada escalón. A partir de los datos que se obtuvieron de la curva característica en la
siguiente figura

![image](https://github.com/user-attachments/assets/1bd20848-1e27-48ce-9a9b-1cd25e8ca191)

anexos: 
![image](https://github.com/user-attachments/assets/f9bcfea7-da2c-46ad-856e-0327b5d6368d)

![image](https://github.com/user-attachments/assets/7245f0c8-0983-4f0c-aa88-3ea7d17db71b)

![image](https://github.com/user-attachments/assets/cb288592-7a5b-4220-b0b8-6703770feb1e)

![image](https://github.com/user-attachments/assets/7b3012cc-c6e3-42d0-8d56-eec82bf962c0)








