This will be a collection of things that where not as good documented as expected etc. for input templates (https://docs.komand.com/docs/input-templating)

# Get first element in an array

Trying to get the first element of an array without itterating over all elements:

```
{{[POST].[body_object].[response].[Attribute].[0].[event_id]}}
```
