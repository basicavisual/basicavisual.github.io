---
layout: post
title:  "Consulta de sparql para gobernadores de México"
date:   2024-05-14 15:55:00 -0600
category: wikidata
image: assets/images/covers/wikidata-cover.png
image-alt: Portada con logo de wikidata
  
---

```sparql
SELECT ?item ?itemLabel ?state ?stateLabel
WHERE {
  # from all items that are subclass of state governor of mexico retrieve all items that have property p:P1308 and all items that have property p:1001
  ?wiki_items p:P1308 ?statement. 
  ?wiki_items wdt:P279 wd:Q17810142.
  ?statement ps:P1308 ?item.
  ?wiki_items p:P1001 ?other_statement.
  ?other_statement ps:P1001 ?state.
  SERVICE wikibase:label { bd:serviceParam wikibase:language "[AUTO_LANGUAGE],en". }
}
```

<iframe style="width: 100%; height: 50vh; border: none;" src="https://query.wikidata.org/embed.html#SELECT%20%3Fitem%20%3FitemLabel%20%3Fstate%20%3FstateLabel%0AWHERE%20%7B%0A%20%20%23%20from%20all%20items%20that%20are%20subclass%20of%20state%20governor%20of%20mexico%20retrieve%20all%20items%20that%20have%20property%20p%3AP1308%20and%20all%20items%20that%20have%20property%20p%3A1001%0A%20%20%3Fwiki_items%20p%3AP1308%20%3Fstatement.%20%0A%20%20%3Fwiki_items%20wdt%3AP279%20wd%3AQ17810142.%0A%20%20%3Fstatement%20ps%3AP1308%20%3Fitem.%0A%20%20%3Fwiki_items%20p%3AP1001%20%3Fother_statement.%0A%20%20%3Fother_statement%20ps%3AP1001%20%3Fstate.%0A%20%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22%5BAUTO_LANGUAGE%5D%2Cen%22.%20%7D%0A%7D" referrerpolicy="origin" sandbox="allow-scripts allow-same-origin allow-popups" ></iframe>

Lista de gacetas oficiales en México

```sparql
SELECT ?diarios ?diariosLabel ?estados ?estadosLabel
WHERE {
  ?diarios wdt:P31 wd:Q2065227;
           wdt:P17 wd:Q96.
  ?diarios wdt:P17 ?estados.
  SERVICE wikibase:label { bd:serviceParam wikibase:language "[AUTO_LANGUAGE],en". }
}
```