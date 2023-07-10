# Linux Ubuntu Python Flask
![Linux-Ubuntu-Python-Flask](https://github.com/danielurra/linux-ubuntu-python-flask/assets/51704179/46106143-fe2b-40b0-b281-95c582303e64)


## Flask first Web App
`Flask` is a **small framework**, available with a good number of auxiliary functions, suitable for developing
**small and medium applications** such as:
* Blog
* Forum
* Personal website
* etc.
  
Our example is a basic web App that has no database yet, just hardcoded items.
![ubu-py-flask](https://github.com/danielurra/linux-ubuntu-python-flask/assets/51704179/79b9db9a-d654-448b-819e-5672e2b9e1fc)

## Saving modules to a .txt file
```bash
pip freeze > requirements.txt
```
## requirements.txt
```bash
blinker==1.6.2
certifi==2023.5.7
charset-normalizer==3.2.0
click==8.1.4
defusedxml==0.7.1
Flask==2.3.2
httpie==3.2.2
idna==3.4
itsdangerous==2.1.2
Jinja2==3.1.2
markdown-it-py==3.0.0
MarkupSafe==2.1.3
mdurl==0.1.2
multidict==6.0.4
Pygments==2.15.1
PySocks==1.7.1
requests==2.31.0
requests-toolbelt==1.0.0
rich==13.4.2
urllib3==2.0.3
Werkzeug==2.3.6
```
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
## Jsonify in action
If you want to return something else like JSON, then you have to use the jsonify function.<br>
The **Flask** `jsonify()` **function** converts its argument to a JSON string and returns it, along with the HTTP response header indicating that it’s JSON, tha's **application/json** as the content type in the HTTP header.<br>
Recent versions of Flask will automatically convert it to JSON and return it.<br>
![jsonify-02](https://github.com/danielurra/linux-ubuntu-python-flask/assets/51704179/f1adb672-5271-4e1f-8f31-e4c5f88ee881)


