---
topic: fql-get-lm-mappings
---

<fql>
  from
    StructureDefinition
  where
    url = %canonical
  for
    differential.element
  select
    id, join mapping {name: defineVariable('elementIdentity', identity).select((%resource.mapping.where(identity = %elementIdentity).name | identity).first()), map, comment}
  order by name
  select
    'Mapping name': name,
    'Concept id': map,
    'Logical element': id.replace('medmij-core-lm-', ''),
    Comments: comment
</fql>