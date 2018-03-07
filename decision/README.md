# Overview

This is to give some things that where found to be useful when creating decisions

# Error evaluating rule for path "XYZ": The variable xyz wasn't defined

That can be solved modifying the rule to:

```
is_defined({{[Parse EML File].[result].[subject]}} ) AND ({{[Parse EML File].[result].[subject]}} contains "XYZ")
```

Then it will not fail
