MATCH (p:Persona)-[:TRABAJA_EN]->(e:Empresa)
RETURN p.nombre AS persona, e.nombre AS empresa
ORDER BY persona;