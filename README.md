# flask_process_from_html_form
#Taking data input from a html form using flask, doing calculations over this input, return a json stating location of generated file.

from pymongo import MongoClient
from flask import Flask, request, render_template
from flask import jsonify
from flask_cors import CORS, cross_origin
from datetime import datetime


#How to run?
#Create a folder /templates, keep html file here my-form.html inside /templates
#Write the following code in this html form
<form method="POST">
    <input name="text">
    <input type="submit">
</form>
--------------------------------------------
In the folder just outside templates,
vi flask_api_make.py

#Paste the following lines
from flask import Flask, request, render_template

app = Flask(__name__)
CORS(app, support_credentials=True)

@app.route('/')
def my_form():
    return render_template('my-form.html')

@app.route('/', methods=['POST'])
def my_form_post():
    text = request.form['text']
    processed_text = text.upper()
    return processed_text

//In the folder containing the flash code suppose flask_api_make.py
chmod +x flask_api_make.py
python3 flask_api_make.py

#Source: https://stackoverflow.com/questions/12277933/send-data-from-a-textbox-into-flask
