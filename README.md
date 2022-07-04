# RL-Pytorch-LunarLander
Practica de Reinforcement Learning with Pytorch

![Lunar Lander](img/lunarlander.jpeg)

## Descripción
Este entorno es un problema clásico de optimización de la trayectoria de un cohete. De acuerdo con el principio máximo de Pontryagin, lo óptimo es encender el motor a toda velocidad o apagarlo. Esta es la razón por la que este entorno tiene acciones discretas: encendido o apagado del motor.

Hay dos versiones de entorno: discreto o continuo. La plataforma de aterrizaje siempre está en las coordenadas (0,0). Las coordenadas son los dos primeros números en el vector de estado. Es posible aterrizar fuera de la plataforma de aterrizaje. El combustible es infinito, por lo que un agente puede aprender a volar y luego aterrizar en su primer intento.

## Espacio de acción

Hay cuatro acciones discretas disponibles: no hacer nada, disparar el motor de orientación izquierda, disparar el motor principal, disparar el motor de orientación derecha.

## Espacio de observación

Hay 8 estados: las coordenadas del módulo de aterrizaje en x e y, sus velocidades lineales en x e y, su ángulo, su velocidad angular y dos valores booleanos que representan si cada pierna está en contacto con el suelo o no.

## Recompensas

La recompensa por moverse desde la parte superior de la pantalla hasta la plataforma de aterrizaje y detenerse es de aproximadamente 100-140 puntos. Si el módulo de aterrizaje se aleja de la plataforma de aterrizaje, pierde la recompensa. Si el módulo de aterrizaje se estrella, recibe -100 puntos adicionales. Si llega a descansar, recibe +100 puntos adicionales. Cada pierna con contacto con el suelo es +10 puntos. Disparar el motor principal es -0.3 puntos cada cuadro. Disparar el motor lateral es -0.03 puntos cada fotograma. El problema se resuelve al alcanzar los 200 puntos.

## Estado inicial

El módulo de aterrizaje comienza en el centro superior de la ventana gráfica con una fuerza inicial aleatoria aplicada a su centro de masa.

## Terminación del episodio

El episodio termina si:

- el módulo de aterrizaje se estrella (el cuerpo del módulo de aterrizaje entra en contacto con la luna);

- el módulo de aterrizaje sale de la ventana gráfica (la coordenada x es mayor que 1);

- el módulo de aterrizaje no está despierto. De los documentos de Box2D, un cuerpo que no está despierto es un cuerpo que no se mueve y no choca con ningún otro cuerpo:
