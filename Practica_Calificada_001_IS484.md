PRÁCTICA CALIFICADA 001

<!-- Start of picture text -->

ge<br>Jer Ng<br>foeSunless \ey<br>“a<br>UNIVERSIDAD<br>DE_HUAMANGA<br><!-- End of picture text -->

# Clasicación de Sistemas y Diseño de Agentes Inteligentes

INTELIGENCIA ARTIFICIAL I · IS-484 · 2026-II Escuela Profesional de Ingeniería de Sistemas Ing. Leidy Rosmery Maldonado Chauca

## 1. Parte 1: Informe de clasicación y cha PEAS

### 1.1. Clasicación de sistemas de IA

Elegir dos sistemas de la siguiente lista (o proponer uno propio):

-  Recomendador de Netix/Spotify, ltro anti-spam de Gmail, asistente de voz (Siri/Alexa)

-  Sistema de reconocimiento facial, chatbot de atención al cliente, predicción de tráco

-  Sistema anti-fraude bancario en tiempo real, balanceador de carga inteligente, sistema de autenticación biométrica

Completar, para cada sistema elegido: entrada, salida, tipo de problema (clasicación/regresión/clustering/generación) y área de IA, usando únicamente las siete categorías ociales vistas en clase (visión articial, NLP, sistemas de recomendación, robótica, sistemas expertos, reconocimiento de patrones, análisis predictivo).

### 1.2. Ficha PEAS de un sistema técnico

Elegir uno de los tres sistemas técnicos de la lista anterior (fraude, balanceo de carga o autenticación biométrica). Completar la cha PEAS del agente:

-  Percepción (S), Acciones (A), Entorno (E), Objetivo, Medida de desempeño (P)

-  Tipo de agente (reactivo, basado en modelos, en objetivos, en utilidad, de aprendizaje)

-  ¾Es racional? Además de justicar, describir una secuencia de percepciones especíca bajo la cual este agente dejaría de ser racional (ejemplo: si el sensor reporta un monto de transacción corrupto o negativo por un error de lectura)

-  ¾Corresponde a IA estrecha o IA General? Justicar

## 2. Parte 2: Diseño de tres agentes inteligentes

Diseñar y programar tres agentes distintos, siguiendo siempre el mismo proceso: cha PEAS _→_ reglas de decisión _→_ código _→_ simulación.

- 2.1. Ejercicio 1: Evaluación de solicitud de crédito bancario

Problema: un sistema evalúa automáticamente una solicitud de crédito, considerando:

-  ingreso_mensual: un número (en soles)

-  monto_solicitado: un número (en soles)

-  tiene_historial_moroso: True o False

El sistema debe calcular la relación entre el monto solicitado y el ingreso mensual (monto_solicitado / ingreso_mensual), y usar esa relación junto con el historial para decidir si aprueba, aprueba con condiciones, o rechaza la solicitud.

Percepción (S)

Acciones (A)

Entorno (E) Objetivo Medida de desempeño (P)

Proponer las reglas de decisión, considerando tanto la relación calculada como el historial. Justicar en 3 a 4 líneas por qué esas reglas son razonables desde la perspectiva del banco (no basta con que el código funcione). Escribir la función completa desde cero, retornando una tupla (accion, motivo), donde motivo explique en texto la razón de esa decisión:

<mark>def agente_credito(ingreso_mensual, monto_solicitado, tiene_historial_moroso): relacion = monto_solicitado / ingreso_mensual # Escribir aqui la logica completa, basada en las propias reglas</mark>

- <mark># Ejemplo de formato de salida esperado: # return "rechazar", "relacion monto/ingreso mayor a 0.5 con historial moroso" pass</mark>

Probar con al menos 6 combinaciones, incluyendo un caso donde la relación calculada quede justo en el borde entre dos decisiones.

Visualización (obligatoria): generar 200 solicitudes aleatorias (usando numpy.random, variando ingreso, monto e historial), calcular la decisión de cada una con el agente, y gracar con matplotlib un scatter de relacion vs. ingreso_mensual, coloreando cada punto según la acción que tomó el agente (por ejemplo, un color por cada una de las tres decisiones posibles).

2.2. Ejercicio 2: Escalamiento de tickets de soporte técnico

Problema: un sistema de mesa de ayuda decide a qué nivel de soporte enviar un ticket, considerando:

-  tiempo_espera_minutos: un número entero

-  nivel_urgencia: un texto, puede ser "baja", "media" o "alta"

-  cliente_premium: True o False

Percepción (S)

Acciones (A)

Entorno (E)

Objetivo

Medida de desempeño (P)

Proponer las reglas de decisión combinando las tres condiciones (por ejemplo, un ticket de urgencia alta se escala de inmediato, mientras que uno de urgencia media depende también del tiempo de espera). Justicar en 3 a 4 líneas por qué esas reglas son razonables desde la perspectiva del cliente y del equipo de soporte. Escribir la función completa, retornando una tupla (accion, motivo):

<mark>def agente_soporte(tiempo_espera_minutos, nivel_urgencia, cliente_premium): # Escribir aqui la logica completa, basada en las propias reglas # Ejemplo de formato de salida esperado: # return "escalar a nivel 3", "urgencia alta reportada por el cliente" pass</mark>

Probar con al menos 6 combinaciones distintas, incluyendo casos donde las tres condiciones no coincidan entre sí (por ejemplo, urgencia baja pero cliente premium con tiempo de espera alto).

### 2.3. Ejercicio 3: Inspección visual de un producto

Problema: en una línea de producción, una cámara captura una pequeña imagen de 5 _×_ 5 píxeles de cada producto, representada como una matriz de NumPy donde cada valor es 0 (píxel normal) o 1 (píxel defectuoso). El agente debe decidir qué hacer con el producto según cuántos píxeles defectuosos detecta.

Percepción (S)

Acciones (A) Entorno (E) Objetivo Medida de desempeño (P)

Proponer las reglas de decisión según el número de píxeles defectuosos (por ejemplo: 0 defectos _→_ aprobar; 1 a 3 _→_ revisión manual; más de 3 _→_ rechazar). Completar el esqueleto, retornando una tupla (accion, motivo):

<mark>import numpy as np</mark>

<mark>def agente_inspeccion(imagen): """ Percepcion (S): matriz 5x5 de NumPy (0 = normal, 1 = defectuoso) """</mark>

<mark>defectos = # COMPLETAR: contar cuantos valores de la matriz son 1 if defectos == 0: return # COMPLETAR: accion, motivo elif defectos <= 3: return # COMPLETAR: accion, motivo else: return # COMPLETAR: accion, motivo # Ejemplo de formato de salida esperado: # return "rechazar", "se detectaron 4 pixeles defectuosos" # Ejemplo de imagen para probar (0 = normal, 1 = defectuoso) imagen_prueba = np.array([ [0, 0, 0, 0, 0], [0, 1, 0, 0, 0], [0, 0, 0, 1, 0], [0, 0, 0, 0, 0], [0, 1, 0, 0, 0], ]) print(agente_inspeccion(imagen_prueba))</mark>

Probar con al menos 4 matrices propias, con distinta cantidad de píxeles defectuosos (incluir un caso con 0 defectos y un caso límite justo en el borde entre dos acciones). Opcional: visualizar cada imagen con plt.imshow(imagen, cmap="gray").
