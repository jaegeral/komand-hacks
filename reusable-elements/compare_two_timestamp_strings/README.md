# Idea

The idea behind is to compare two Timestamp strings and alert if one is greater then the other.
As both values are strings, the Komand Built in compare mechanism will not work you only can compare for equal value

# input

Two string timestamps in format yyyy-mm-dd (can be adjusted, see code below)
```
{"date1":"{{[yourvalue].[timestamp]}}","date2":"{{[yourvalue2].[timestamp]}}"}
```
# python module

this can be used in a workflow

```python
def run(params={}):
    from datetime import datetime as dt
    hxdate = params.get('date1')
    addate = params.get('date2')
    date1_date = dt.strptime(date1, "%Y-%m-%d")
    date2_date = dt.strptime(date2, "%Y-%m-%d")
    if date1_date < date2_date:
        return {'issue_detected':'true'}
    else:
        return {'issue_detected' :'false'}
```
