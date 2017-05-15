# Reltime

Reltime is a simple regex-based library for tagging and grounding temporal expressions found in text, including _most_ natural language references to dates, times, and time ranges. 

## Installation

Run `pip install reltime` to install the latest stable version from Pypi. 


## Usage

Reltime has two primary use cases: tagging date/time expressions, and grounding/time date expressions.

### tagging

Tagging is acomplished through `reltime.tag()`. It will tag all temporal expresions with `<DATE></DATE>`, `<TIME></TIME>`, `<TIME_RANGE></TIME_RANGE>`.

```
In [1]: import reltime

In [2]: reltime.tag("I'll see you next week")
Out[2]: "I'll see you <DATE>next week</DATE>"
```

### grounding

Grounding is accomplished through `reltime.ground()`. It will return a list of datetimes representing the tagged temporal expressions and optionally the text with the grounded sections removed. When grouding, the replaced text will be `<GroundedTime>`, `<GroundedDate>`, `<GroundedRange>`  

With replacement:
```
In [1]: import reltime

In [2]: from datetime import datetime

In [3]: base_date = datetime(2017,1,1,0,0,0)

In [4]: reltime.ground("I'll see you next weekend", base_date, replace=True)
Out[4]: ("I'll see you <GroundedDate> ", [datetime.datetime(2017, 1, 8, 0, 0)])
```

Without replacement:
```
In [1]: import reltime

In [2]: from datetime import datetime

In [3]: base_date = datetime(2017,1,1,0,0,0)

In [4]: reltime.ground("I'll see you next week", base_date, replace=False)
Out[4]: [datetime.datetime(2017, 1, 8, 0, 0)]
```


## Authors

Reltime was written at -Live- by [Mark Brenckle](https://github.com/brencklebox)
