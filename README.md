# Modelo PLE Eliminatorias Conmebol

Modelo de programación lineal entera que chequea si Argentina está matemáticamente clasificado para la Copa Mundial 2026

# Preguntas interesantes (última fecha: 15/10/2024)

- ¿Argentina está clasificada?

No

- ¿Cuántos puntos tendría que haber tenido Argentina para clasificar?

32 puntos

- ¿A Argentina le alcanza con ganar en la próxima fecha para clasificar?

No

# Modelo

## Variables

$$
\delta_k = 1 \ \text{sii la k-esima combinacion se cumple}
$$

(Para que Argentina no tenga garantizada la clasificación, debe haber alguna forma para que alguna combinación de 6 países terminen por arriba de Argentina. 
En este caso, tenemos  $\binom{9}{6} = 84$ combinaciones).

$$
home_i = 1 \ \text{sii el equipo local del i-esimo partido gana}
$$

$$
away_i = 1 \ \text{sii el equipo visitante del i-esimo partido gana}
$$

$$
puntaje_c = \text{Puntaje final del país c}
$$

## Problema

$$
max \ \delta_1 + ... + \delta_{84} \\
$$

Sujeto a

$$
away_i = 1 \ \forall i \in locales(Argentina)
$$

$$
home_i = 1 \ \forall i \in visitantes(Argentina)
$$

"Argentina pierde de ahora en más"

$$
home_i + away_i + draw_i = 1 \ \forall i \in partidos
$$

"Consistencia de variables en cada partido"

$$
puntaje_c = 3 \sum_{i \in locales(c)} home_i + 3 \sum_{i \in visitantes(c)} away_i + \sum_{locales(c) \ \cup \ visitantes(c)} draw_i + PuntajeInicial(c)
$$

"Definición de la variable $puntaje_c$"

$$
puntaje_{argentina} < puntaje_c + M(1-\delta_k) \ \forall k \in Combinaciones, \ \forall c \in PaisesCombinacion(k)
$$

"Activación de la variable $\delta_k$ si la k-ésima combinación de países supera a Argentina al final"
