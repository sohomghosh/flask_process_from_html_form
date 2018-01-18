# flask_process_from_html_form
#Taking data input from a html form using flask, doing calculations over this input, return a json stating location of generated file.
</br>
#How to run?</br>
#Create a folder /templates, keep html file here my-form.html inside /templates</br>
#Write the following code in this html form </br>

```
<form method="POST"> 
    <input name="text">
    <input type="submit">
</form>
```
 </br>-------------------------------------------- </br>
In the folder just outside templates </br>
vi flask_api_make.py </br>
 </br>
#Paste the following lines </br>
```
from pymongo import MongoClient
from flask import Flask, request, render_template, jsonify
from flask_cors import CORS, cross_origin
from datetime import datetime

app = Flask(__name__)
CORS(app, support_credentials=True)

@cross_origin(supports_credentials=True)
@app.route('/')
def my_form():
    return render_template('my-form.html')

@app.route('/', methods=['POST'])
def my_form_post():
    text = request.form['text']
    processed_text = text.upper()
    return processed_text
 

if __name__ == '__main__':
    app.debug = True
    app.run(host="172.189.189.190",debug=True)

``` 
 
//In the folder containing the flask code suppose flask_api_make.py change permission of the flask_api_make.py and keep running it in the background</br>
chmod +x flask_api_make.py </br>
nohup python3 flask_api_make.py &</br>
 </br>
#Source: https://stackoverflow.com/questions/12277933/send-data-from-a-textbox-into-flask  </br>
 </br>
