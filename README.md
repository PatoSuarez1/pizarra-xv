# Pizarra XV

Pizarra tactica de rugby. Una cancha a escala real, 15 fichas por equipo y jugadas
que se guardan por pasos y se reproducen con la pelota moviendose sola.

**Abrila acá: https://patosuarez1.github.io/pizarra-xv/**

## Que hace

- **Cancha a escala**: 100 x 70 m mas los dos in-goal, con las 22, los 10 punteados,
  las de 5 y los corredores de 5 y 15 desde cada touch.
- **Formaciones armadas**: scrum, line, ruck, fase abierta y salida. Se eligen la
  altura de la cancha y el lado, y arman a los DOS equipos: ocho contra ocho, y del
  otro lado la linea defensiva enfrente. En el line se elige de cuantos es (7 a 2)
  y los que no entran esperan 10 m atras.
- **Jugadas por pasos**: se acomodan las fichas, se agrega un paso, se vuelven a
  mover. Al reproducir, la animacion interpola entre pasos y dibuja las flechas.
- **Flechas de corrida, pase y patada, que son ORDENES**: al abrir el paso
  siguiente se ejecutan todas. Cada corrida corre a su jugador —o a todo el grupo
  que estaba marcado cuando se dibujo— y la pelota va de pase en pase mientras
  encuentre una flecha que salga de quien la lleva, asi una cadena 9 -> 10 -> 5 se
  resuelve en un solo paso. El que la tiene la arrastra consigo cuando se lo mueve.
- **Seleccion multiple**: se encierran varias fichas y se mueven, giran o espejan
  como un bloque, sin deformar la formacion.

## Jugadas incluidas

Vienen dos armadas, siempre disponibles en la biblioteca:

- **Line en la mitad, 2 contra 1 por afuera** (7 pasos). Nadie se corre de su
  canal: cada uno arranca enfrentado a su par —el 10 al 10, el 12 al 12, el 13 al
  13— y la jugada sucede sobre eso. El 9 la saltea por encima del 10 y va al 12,
  que avanza con el 13; el 10 aparece por detras, recibe el pase atras, endereza
  la carrera y la abre al 15. Todos los pases pasan antes de la linea defensiva:
  el 15 es el unico que llega a la defensa y ahi juega el dos contra uno con el
  wing.
- **Salida de scrum por afuera** (4 pasos).

## Como se usa

| | Escritorio | Celular |
|---|---|---|
| Mover una ficha | arrastrar | arrastrar |
| Seleccionar varias | arrastrar sobre pasto vacio | mantener apretado y arrastrar |
| Acercar | boton + | dos dedos |
| Bajar a los controles | — | deslizar sobre el pasto, o "Controles" |

## Como esta hecho

Un solo archivo HTML, sin dependencias, sin build y sin backend. La cancha es un
SVG en metros: todo el dominio (formaciones, ruteo de la pelota, interpolacion)
trabaja en metros de cancha y solo el dibujo sabe de pixeles.

Las jugadas se guardan en el navegador de cada uno (localStorage).

## Publicacion

El sitio sale de `index.html` en la raiz de `main`, servido por GitHub Pages con
la opcion *Deploy from a branch*. No hay build ni workflow: cada push a `main`
actualiza la pagina publicada.
