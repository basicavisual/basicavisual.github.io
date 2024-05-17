---
layout: post
title:  "Para publicar datos abiertos, deberíamos usar entidades, no palabras"
date:   2024-05-16 15:55:00 -0600
category: Datos Abiertos
image: assets/images/covers/pietro-jeng-n6B49lTx7NM-unsplash.jpg
image-alt: Photo by Pietro Jeng on Unsplash
tags: wikidata sparql
description: | 
  Pensando en tener datos abiertos sostenibles, me quedé con el concepto de Entidades. ¿Qué tal que siempre que habláramos de algo importante, lo representáramos no como texto, sino como un objeto con una URL?
---

<div class="alert">
  <p>
    Este es el primero de varios posts relativos al uso de Wikidata en una estrategia de datos abiertos y de gobernanza de datos.
  </p>
</div>

Pensando en tener datos abiertos sostenibles, me quedé con el concepto de **"Entidades"**. ¿Qué tal que siempre que habláramos de algo importante, lo representáramos no como texto, sino como un objeto con una URL? Así para la Ciudad de México no tendríamos una entrada de la base de datos llamada **"Ciudad de México"**, sino una URL que siempre referenciara dicha entidad: [https://www.wikidata.org/wiki/Q1489](https://www.wikidata.org/wiki/Q1489)

Para quien sea que haya trabajado con datos sabe que hacer análisis de datos cuando referenciamos las cosas por texto, requiere lidiar con las diferencias en cómo se crea la información. Así para crear un reporte a partir de una base, terminamos tratando de juntar las entradas para **"Ciudad de México"**,  **"CDMX"** o **"Cd. de México"**. Y cuando las cosas cambian de nombre, también tenemos que hacer arqueología de datos para entender que **"Ciudad de México"** también podía aparecer como **"México, D.F."**, **"México DF"**, **"DF"**, **"Distrito Federal"** y demás.

<figure>
  <img src="{{site.url}}/assets/images/posts/2024/2024-05-17-cdmx.png" alt="imagen que describe que la entidad de Wikidata para Ciudad de México representa sus diferentes nombres"/>
  <figcaption>La entidad de Wikidata para Ciudad de México es la misma aunque tenga diferentes nombres.</figcaption>
</figure>

Además de poder referenciar mediante un sólo URL diferentes cadenas de texto, wikidata nos da acceso a varios metadatos sobre la Ciudad de México que podemos usar tanto para limpiar como para enriquecer nuestra información. Por ejemplo, la tarjeta inicial de la entidad Ciudad de México contiene una lista de aliases que podemos usar para programáticamente limpiar bases de datos. 

<figure>
  <img src="{{site.url}}/assets/images/posts/2024/2024-05-17-aliases.png" alt="imagen que muestra la tarjeta inicial de wikidata para la Ciudad de México"/>
  <figcaption>La tarjeta inicial de wikidata para la Ciudad de México</figcaption>
</figure>

¿A qué me refiero con programáticamente? pues limpiar una sola ciudad no es muy difícil. Escribo una lista de nombres posibles de la CDMX y los uso en mi script de limpieza para identificar las diferentes formas de escribir Ciudad de México. Pero, si tuviera que hacer esto con los 2446 municipios en México ya no podría hacerlo fácilmente. Así que podría usar la base de conocimiento colectivo que es Wikidata para jalar con un sólo script todos los aliases documentados de los municipios mexicanos. Esto se hace con la siguiente consulta:

```sparql
SELECT ?alias
WHERE {
  wd:Q1489 skos:altLabel ?alias.
  filter(lang(?alias) = "es").
}
```
<iframe style="width: 100%; height: 50vh; border: none;" src="https://query.wikidata.org/embed.html#SELECT%20%3Falias%0AWHERE%20%7B%0A%20%20wd%3AQ1489%20skos%3AaltLabel%20%3Falias.%0A%20%20filter%28lang%28%3Falias%29%20%3D%20%22es%22%29.%0A%7D" referrerpolicy="origin" sandbox="allow-scripts allow-same-origin allow-popups" ></iframe>

Además de tener acceso a una lista de nombres conocidos para un objeto, Wikidata almacena metadatos y datos vinculados para cada entidad. Por ejemplo, ¿qué tal que quisiera no sólo tener los nombres de todas las entidades de la república, sino también saber quién los gobierna, su foto y a qué partido pertenecen? Se puede hacer con esta consulta:

```sparql
SELECT ?state ?stateLabel ?governor ?governorLabel ?party ?partyLabel ?photo
WHERE {
  ?state wdt:P31 wd:Q15149663.
  ?state wdt:P6 ?governor.
  ?governor wdt:P102 ?party.
  ?governor wdt:P18 ?photo.
  SERVICE wikibase:label { bd:serviceParam wikibase:language "es". }
}
```

Aquí el resultado:

<iframe style="width: 100%; height: 50vh; border: none;" src="https://query.wikidata.org/embed.html#SELECT%20%3Fstate%20%3FstateLabel%20%3Fgovernor%20%3FgovernorLabel%20%3Fparty%20%3FpartyLabel%20%3Fphoto%0AWHERE%20%7B%0A%20%20%3Fstate%20wdt%3AP31%20wd%3AQ15149663.%0A%20%20%3Fstate%20wdt%3AP6%20%3Fgovernor.%0A%20%20%3Fgovernor%20wdt%3AP102%20%3Fparty.%0A%20%20%3Fgovernor%20wdt%3AP18%20%3Fphoto.%0A%20%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22es%22.%20%7D%0A%7D" referrerpolicy="origin" sandbox="allow-scripts allow-same-origin allow-popups" ></iframe>

## ¿Qué pasa si hay algún error en los datos?

Wikidata es una base de datos estructurados mantenida colectivamente. Es un [bien público digital](https://digitalpublicgoods.net/). Así como Wikipedia se ha convertido en una fuente fidedigna de información gracias a sus muchos wikieditores, en Wikidata podemos formar una comunidad de Wikidateros que utilicen y actualicen los datos, que a través de utilizarlos para nuestros proyectos, aplicaciones, y demás, podamos custodiar que los datos de valor para la agenda de datos abiertos o para la gobernanza de datos en México, se encuentre limpia y actualizada en un repositorio que es de todos. 
