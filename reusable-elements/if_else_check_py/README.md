# Idea behind

Trying to add a decision block in a path that is already part of a join path element but want to check values and maybe act on, a good workaround is a python modele.

The function will take in that example two values subject and sender and will check if subject is empty it will return sender, else subject.

In the following steps you can then refer to the output of that python file

## Input

```json
{"subject":"{{[Parse EML File].[result].[subject]}}","sender":"{{[Parse EML File].[result].[from]}}"}
```

## Method
```python
def run(params={}):
    from datetime import datetime as dt
    subject = params.get('subject')
    sender = params.get('sender')
    if subject == "":
        return {'return_value':sender}
    else:
        return {'return_value' :subject}
```
