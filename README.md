# richtextpy

An [operational transformation](https://en.wikipedia.org/wiki/Operational_transformation) library for rich text documents. Enables collaborative editing scenarios by providing a rich text document format as well as **compose** and **transform** methods for managing changes.

This is a Python version of the [Javascript Rich Text](https://github.com/ottypes/rich-text) library.

## Example

```python
from richtextpy import Delta

delta = Delta([
  {'insert': 'Gandalf', 'attributes': {'bold': True}},
  {'insert': ' the '},
  {'insert': 'Grey', 'attributes': {'color': '#ccc'}}
])

# keep the first 12 characters, delete the next 4, and insert a white 'White'
death = Delta().retain(12).insert('White', {'color': '#fff'}).delete(4)

"""
this produces:

[
	{'retain': 12 },
	{'insert': 'White', 'attributes': {'color': '#fff'}},
	{'delete': 4 }
]
"""

delta.compose(death)

"""
delta is now:

[
	{'insert': 'Gandalf ', 'attributes': {'bold': True}},
	{'insert': ' the '},
	{'insert': 'White', 'attributes': {'color': '#fff'}}
]
"""
```

## Installation
```python
python setup.py install
```

## Running the tests
```python
python setup.py test
```

## License

The MIT License (MIT)

Copyright (c) 2016 Sachin Rekhi

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.
