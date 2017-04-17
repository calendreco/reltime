# Reltime

Reltime is a simple regex-based library for tagging and grounding temporal expressions found in text. 

## Installation

Run `pip install reltime` to install the latest stable version from Pypi. 


## Usage

Reltime has two primary use cases: tagging date expressions, and grounding date expressions.

### tagging

Tagging is acomplished through `reltime.tag()`. It will tag all temporal expresions with `<TIME></TIME>`.

```
In [1]: import reltime

In [2]: reltime.tag("I'll see you next weekend")
Out[2]: "I'll see you <TIME>next week</TIME>end"
```

### grounding

Grounding is accomplished through `reltime.ground(), which operates on tagged text. It will return a list of datetimes representing the tagged temporal expressions and optionally the orignal text itself.

With replacement:
```
In [1]: import reltime

In [2]: from datetime import datetime

In [3]: base_date = datetime(2017,1,1,0,0,0)

In [4]: tagged = reltime.tag("I'll see you next weekend")

In [5]: reltime.ground(tagged, base_date, replace=True)
Out[5]:
("I'll see you <TIME>GroundedTime</TIME>end", [datetime.datetime(2017, 1, 8, 0, 0)])
```

Without replacement:
```
In [1]: import reltime

In [2]: from datetime import datetime

In [3]: base_date = datetime(2017,1,1,0,0,0)

In [4]: tagged = reltime.tag("I'll see you next weekend")

In [5]: reltime.ground(tagged, base_date, replace=False)
Out[5]: [datetime.datetime(2017, 1, 8, 0, 0)]
```


## Authors

Reltime was written at -Live- by [Mark Brenckle](https://github.com/brencklebox)
