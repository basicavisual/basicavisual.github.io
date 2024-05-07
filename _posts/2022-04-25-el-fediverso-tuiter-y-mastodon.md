---
layout: post
title:  "El fediverso y cómo escapar de facebook, tuíter y las redes centralizadas"
date:   2022-04-24 14:54:12 -0500
category: web semantica
image: assets/images/covers/shubham-dhage-gC_aoAjQl2Q-unsplash.jpg
image-alt: Photo by Shubham Dhage on Unsplash 
  
---

Con las noticias de que twitter.com aceptó ser comprado por [Elon Musk](https://en.wikipedia.org/wiki/Elon_Musk) ha surgido un nuevo interés por las redes sociales descentralizadas. Y no es casualidad. Elon [ha sido criticado](https://en.wikipedia.org/wiki/The_Boring_Company#Criticism) por optar por soluciones privativas a problemas sociales, tal es el caso de su [Boring Company](https://en.wikipedia.org/wiki/The_Boring_Company) que propone la construcción de "túneles para evitar el tráfico" de un sólo carril que sólo pueden ser transitados por vehículos privados eléctricos.

Por el contrario, el creador de tuíter, [Jack Dorsey](https://en.wikipedia.org/wiki/Jack_Dorsey), quien recientemente [abandonó la presidencia de la compañía](https://twitter.com/jack/status/1465347002426867720?ref_src=twsrc%5Etfw),  ha mostrado interés por la descentralización, a pesar de haber fundado una red social centralizada. Incluso fundío dentro de tuíter un equipo para la investigación y el desarrollo de un protocolo de redes sociales descentralizadas llamado [Blue Sky](https://twitter.com/bluesky/status/1518707597532024832) que a la fecha continúa por fuera sus labores de investigación para mantener la imparcialidad del proyecto

### ¿Qué es una red social descentralizada?

Es una red social que trata el contenido de otras redes sociales del mismo modo que el contenido propio. Hace esto utilizando protocolos de compartición de  contenidos que le permite transmitir todo su contenido a otras redes, y consume contenido de otras redes también. A este proceso de transmisión y recepción de contenido se le llama [*federación*](https://en.wikipedia.org/wiki/Federated_database_system) y es todo lo opuesto al internet 2.0 que conocemos hoy.


### ¿y qué es la web 2.0?

La web 2.0 se trató de habilitar a cualquier persona, independientemente de su conocimiento de internet, a crear contenido. Durante esta época vimos el advenimiento de las primeras redes sociales, que permitían a los usuarios crear su propio sitio web, como Geocities, o tener una página personal como Fotolog. La segunda etapa de esta web se vio marcada por redes sociales como Facebook, Twitter, Tumblr, y otras, que desarrollaron tecnologías que quitaron la necesidad de refrescar la página, permitiendo que sin necesidad de navegar entre sitios, automáticamente recibiéramos actualizaciones de contenido en el mismo portal. A este paradigma se le llama "Single Page Application" o aplicación de una sola, porque sin navegar directorios era posible hacer un rango de actividades.

El advenimiento de la web sin embargo creó gigantes de contenido, que gracias a su tecnología podían capturar la atención de sus usuarios por más tiempo y producir un público cautivo. Según Statista, al 2021 el 70% de los usuarios de internet en el mundo tienen una cuenta de facebook.

<a href="https://www.statista.com/statistics/183460/share-of-the-us-population-using-facebook/" rel="nofollow"><img src="https://www.statista.com/graphic/1/183460/share-of-the-us-population-using-facebook.jpg" alt="Statistic: Facebook usage penetration in the United States from 2017 to 2026 | Statista" style="width: 100%; height: auto !important; max-width:1000px;-ms-interpolation-mode: bicubic;"/></a><br />Find more statistics at  <a href="https://www.statista.com" rel="nofollow">Statista</a>

La lógica de empresas como esta es mantener una base de usuarios constante de la que puedan minar datos para vender o exponer a anuncios, por lo que invierten en funcionalidades que hagan al usuario gastar más tiempo en el sitio. Desde juegos, hasta el marketplace, en el caso de facebook, la verificación de cuentas en twitter que le permite servir de canal oficial a gobiernos, empresas y figuras públicas, o el desarrollo de algoritmos de descubrimniento que facilita la viralización o monetización del contenido que publican los usuarios. Por ende, a pesar de que las personas son autoras del contenido, el mismoes controlado y monetizado por tuíter, y a pesar de que puede ser compartido en otra plataforma, no existe una portabilidad del mismo, donde puedas trasladar tu contenido a otra o múltiples plataformas.

Este tuit describe mejor las implicaciones de esto.

<blockquote class="twitter-tweet"><p lang="en" dir="ltr">Do you own your own tweets? 🧵</p>&mdash; Kelsey Hightower (@kelseyhightower) <a href="https://twitter.com/kelseyhightower/status/1473745249113620489?ref_src=twsrc%5Etfw">December 22, 2021</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

### ¿Por qué querríamos una red social descentralizada?

¿Cuántas cuentas de redes sociales tienes? Probablemente tienes Instagram, Facebook, Twitter, TikTok, Tumblr, Pinterest, Youtube. En cada una de ellas tienes a tu familia, amigos, colegas, o personas con intereses parecidos. Además quizá debas mantenerte al día en varios servicios de mensajería: Facebook Messenger, Whatsapp, Telegram, Signal. En cierto punto se ha convertido en demasiado trabajo "socializar". Gastamos muchísimas horas en cada una de estas aplicaciones y a veces, por nuestro trabajo o porque tenemos relaciones importantes, entrar a estas aplicaciones es la única forma de mantenernos al día con nuestros familiares, colegas o amigos.

Una red social descentralizada o federada resuelve este problema. Al utilizar un protocolo para compartir tus posts de redes, likes o mensajes directos, es posible comunicarte entre "instancias" (sitios distintos de redes sociales). Imagina que al postear tu contenido en twitter, tus amigos que tienen TikTok pero no tienen twitter pudieran seguirte y ver tus posts. La brecha entre centennials y millenials se acortaría. Desafortunadamente, puedes pensar, también significa que no podríamos escapar a TikTok para huir de nuestros padres, pero no es así. El protocolo incluye las funcionalidades de privacidad que conocemos y al final, siempre puedes tener una cuenta federada para tus colegas y otra para tus familiares

### ¿Cómo funciona una red social descentralizada?

Funciona utilizando algún protocolo que permita que tus posts, likes y mensajes directos se puedan publicar entre diferentes sitios web. El protocolo abierto más importante para esto es [ActivityPub](https://www.w3.org/TR/activitypub/), impulsado por la W3C, el organismo que rige las tecnologías sobre las que funciona el internet.

El protocolo sólo es "el lenguaje" de intercambio de información, pero además de ello debe existir una aplicación que hable el lenguaje y se comunique con otra aplicación. Afortunadamente existen aplicativos de código abierto que son relativamente fáciles de implementar. Un aplicativo de este tipo se instala en un servidor, y las personas que usan la aplicación, o sea, nosotros, únicamente nos preocupamos por entrar al sitio web, poner nuestro usuario y contraseña y comenzar a publicar.

El hecho de que cualquier persona u organización pueda instalar un aplicativo que hable este protocolo implica que si se quisieran construir redes sociales cerradas pero que se hablen entre sí, por ejemplo, entre activistas de varios países que requieren seguridad en sus comunicaciones, es posible hacerlo. Pero también existen instancias abiertas a las que nos podemos conectar. La ventaja de estas instancias es que, a diferencia de los aplicativos de la web 2.0 como facebook y tuíter, no importa mucho que hagamos la cuenta en una de estas instancias ya existentes o en otra, ya que podremos seguir a nuestros amigos que hayan hecho sus cuentas en cualquier instancia pública.

### ¿Cómo puedo entrar a una red descentralizada?

Bueno, ya alguien escribió un mejor artículo que este al respecto sobre crear tu cuenta en Mastodon. Mastodon es uno de esos softwares de código abierto que varias personas u organizaciones han instalado en servidores. Puedes elegir uno de los servidores que más te interese o en el que más confíes y crear tu cuenta ahí. Incluso si llegaras a no querer crear tu cuenta en el servidor de alguien más podrías instalarte un servidor propio e igual podrías comunicarte con tus amigos.

Puedes encontrar el artículo en esta liga: [Mastodon: Mejor tootear que tuitear, por RadiosLibres.net](https://radioslibres.net/mastodon-mejor-tootear-que-tuitear/)
