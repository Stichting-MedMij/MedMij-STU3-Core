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
    id, join mapping.where(identity.startsWith('hcim-')) {name: defineVariable('elementIdentity', identity).select((%resource.mapping.where(identity = %elementIdentity).name | identity).first()), map, comment}
  order by name
  select
    'Mapping name': name,
    'Concept id': map,
    'FHIR element': id,
    Comments: comment
</fql>