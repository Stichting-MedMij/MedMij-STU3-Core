---
topic: fql-get-mappings-zib
---

<fql>
  using scope
  
  from
    StructureDefinition
  where
    url = %canonical
  for
    snapshot.element
  select
    id, join mapping.where(identity.startsWith('zib-')) {identity, map, comment}
  order by identity
  select
    'Mapping name': identity,
    'Concept id': map,
    'FHIR element': id,
    Comments: comment
</fql>