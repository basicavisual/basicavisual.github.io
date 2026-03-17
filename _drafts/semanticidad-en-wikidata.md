El concepto de referenciar entidades por URL no sólo resuelve este problema sino que además esas entidades están jerarquizadas. Por ejemplo, **"Ciudad de México"** es una instancia de una **"Entidad federativa de México"** que tiene su propia dirección en [https://www.wikidata.org/wiki/Q20528428](https://www.wikidata.org/wiki/Q20528428), y las **"Entidades federativas de México"** son un tipo de **"División administrativa de primer nivel"** [https://www.wikidata.org/wiki/Q10864048](https://www.wikidata.org/wiki/Q10864048) cuya descripción contiene **"división administrativa directamente subordinada o bajo administración de un gobierno nacional"**. En México a esto le llamamos "Estados" o "Entidades federativas" pero en otros países le llaman "Provincias", "Departamentos" o más. Nos vamos aproximando al nivel semántico. 

Si quisiera saber todos los nombres que tienen las divisiones administrativas de primer nivel (después de país) en todos los países ¿cómo lo haría? ¿buscaría en una enciclopedia política? ¿esperaría que alguien haya escrito de eso en internet? Pero ¿cómo me aseguraría de que la lista está actualizada? Este es el propósito de Wikidata: La base de datos estrucrturados mantenida por voluntarios más robusta del mundo. En Wikidata encontramos una gran cantidad de conceptos, lugares, personas, ideas, objetos, y más, documentados y actualizados diariamente por voluntarios. También se pueden hacer consultas como las que comenté arriba: "La lista de nombres de divisiones administrativas de primer nivel para todos los países del mundo". Esto se hace consultando Wikidata con un lenguaje llamado SPARQL. A continuación la consulta:

```sparql
SELECT ?item ?itemLabel ?country ?countryLabel
WHERE {
  ?item wdt:P279 wd:Q10864048.
  ?item wdt:P17 ?country.
 
  SERVICE wikibase:label { bd:serviceParam wikibase:language "[AUTO_LANGUAGE],en". }
}
```

Y aquí el resultado:
<iframe style="width: 100%; height: 50vh; border: none;" src="https://query.wikidata.org/embed.html#SELECT%20%3Fitem%20%3FitemLabel%20%3Fcountry%20%3FcountryLabel%0AWHERE%20%7B%0A%20%20%3Fitem%20wdt%3AP279%20wd%3AQ10864048.%0A%20%20%3Fitem%20wdt%3AP17%20%3Fcountry.%0A%20%0A%20%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22%5BAUTO_LANGUAGE%5D%2Cen%22.%20%7D%0A%7D%0A%0A" referrerpolicy="origin" sandbox="allow-scripts allow-same-origin allow-popups" ></iframe>

Continuaré escribiendo entradas sobre consultas interesantes de Wikidata para mi proyecto sobre la evolución de los datos abiertos. 