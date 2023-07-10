# Linux Ubuntu Python Flask
![Linux-Ubuntu-Python-Flask](https://github.com/danielurra/linux-ubuntu-python-flask/assets/51704179/46106143-fe2b-40b0-b281-95c582303e64)


## Basic Web App - Animation
Basic web App, has no database yet, just hardcoded items.
![ubu-py-flask](https://github.com/danielurra/linux-ubuntu-python-flask/assets/51704179/79b9db9a-d654-448b-819e-5672e2b9e1fc)

## Grab the Python code
```python
from flask import Flask, render_template, request, redirect, url_for, jsonify
app = Flask(__name__)

shopping_list = ['Milk', 'Eggs', 'Potatoes', 'Oranges', 'Bananas']

@app.route('/', methods=['GET', 'POST'])
def index():
    global shopping_list
    if request.method == 'POST':
        shopping_list.append(request.form['item'])
    return render_template('index.html', items=shopping_list)

@app.route('/remove/<name>')
def remove_item(name):
    global shopping_list
    if name in shopping_list:
     shopping_list.remove(name)
    return redirect(url_for('index'))

@app.route('/api/items')
def get_items():
   global shopping_list
   return jsonify({'items': shopping_list})

if __name__ == '__main__':
    app.run(debug=True)
```
