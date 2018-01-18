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
from pymongo import MongoClient </br>
from flask import Flask, request, render_template, jsonify </br>
from flask_cors import CORS, cross_origin </br>
from datetime import datetime </br>
 </br>
app = Flask(__name__) </br>
CORS(app, support_credentials=True) </br>
 </br>
@cross_origin(supports_credentials=True) </br>
@app.route('/') </br>
def my_form(): </br>
    return render_template('my-form.html') </br>
 </br>
@app.route('/', methods=['POST']) </br>
def my_form_post(): </br>
    text = request.form['text'] </br>
    processed_text = text.upper() </br>
    return processed_text </br>
 </br>
//In the folder containing the flash code suppose flask_api_make.py </br>
chmod +x flask_api_make.py </br>
python3 flask_api_make.py </br>
 </br>
#Source: https://stackoverflow.com/questions/12277933/send-data-from-a-textbox-into-flask  </br>
 </br>
