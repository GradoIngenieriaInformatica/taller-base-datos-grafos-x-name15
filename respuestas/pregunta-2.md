MATCH (p:Persona)-[:VIVE_EN]->(c:Ciudad {nombre: "Madrid"})
RETURN p.nombre AS persona
ORDER BY persona;