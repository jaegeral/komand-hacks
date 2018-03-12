# This is a script that can be used as a python3 module to parse CSV to json

It expects a CSV as base64 encoded string:

## Input

Sample csv
```
a,b,c,d
value1,value2,value3,value4
valueb1,valueb2,valueb3,valueb4
valuec1,valuec2,valuec3,valuec4
```

results in the base64 string

```json
{"converted" : "YSxiLGMsZAp2YWx1ZTEsdmFsdWUyLHZhbHVlMyx2YWx1ZTQKdmFsdWViMSx2YWx1ZWIyLHZhbHVlYjMsdmFsdWViNAp2YWx1ZWMxLHZhbHVlYzIsdmFsdWVjMyx2YWx1ZWM0Cg=="} 
```
## Output
```json
{
  "return_value": [
    {
      "a": "value1",
      "b": "value2",
      "c": "value3",
      "d": "value4"
    },
    {
      "a": "valueb1",
      "b": "valueb2",
      "c": "valueb3",
      "d": "valueb4"
    },
    {
      "a": "valuec1",
      "b": "valuec2",
      "c": "valuec3",
      "d": "valuec4"
    }
  ]
}
```
Is an array of strings

## Method

```python
def run(params={}):
    import base64
    import json
    import io
    import csv
    
    infile = params.get('converted')
    decoded = base64.b64decode(infile)
    decoded_string = decoded.decode("utf-8")
    reader2 = csv.DictReader(io.StringIO(decoded_string))
    fieldnames = reader2.fieldnames
    output = []
    for each in reader2:
        row = {}
        for field in fieldnames:
            row[field] = each[field]
        output.append(row)
    
    
    return {'return_value': output }
```
