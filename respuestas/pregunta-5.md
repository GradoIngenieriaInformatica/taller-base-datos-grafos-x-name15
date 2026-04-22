MATCH path = (inicio:Persona)-[:AMIGO_DE*2..]->(fin:Persona)
WITH path, nodes(path)[1..-1] AS intermedios
WHERE size(intermedios) > 0
UNWIND intermedios AS p
MATCH (p)-[:VIVE_EN]->(c:Ciudad)
WITH path, collect(DISTINCT c.nombre) AS ciudades_intermedias
WHERE size(ciudades_intermedias) = 1
RETURN [n IN nodes(path) | n.nombre] AS camino, ciudades_intermedias[0] AS ciudad_intermedia
ORDER BY camino;