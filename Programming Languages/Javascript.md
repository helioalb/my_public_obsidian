- [[Javascript - Binary Search Tree - Post order example]]
## async vs def

- HHHH = HTML parse
- ______ _ _ _ _= HTML parse paused
- DDDD= Script download
- eee= Script execution

```html
<html>
<body>
  <div></div>
  <script></script>
  <div></div>
</html>
```
### `<script>`

PPPPPPPPPPPPPP----------------------PPPPPPPPPPPPPPPPP
				DDDDDDeeeeeeeeee

### `<script async>`

PPPPPPPPPPPPPPPPPPPPP------------PPPPPPPPPPPPPPPPP
				DDDDDDeeeeeeeeee

### `<script defer>`

PPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPP
				DDDDDD                                      eeeeeeeeee