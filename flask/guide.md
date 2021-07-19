```python
from flask import Flask

app = Flask(__name__)

@app.route("/")
def hello_world():
    return "<p>Hello, World!</p>"
```

- `@app.route()`는 조건
  - route('/') 는 최상위 경로

- `import Flask, request`
  - `requests`가 아닌 Flask 내부의  `request`임
