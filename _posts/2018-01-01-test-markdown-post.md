---
toc: true
layout: post
description: Running Python app with Docker
categories: [markdown]
title: Deploying a Python app with Docker (Part 1)
---
# Deploying a Python app with Docker (Part 1)

In this tutorial, we show how you can build and deploy a really simple Python app using Docker. To demonstrate, we'll create an API to return details of the TFL train lines in London. We'll use [Flask](https://flask.palletsprojects.com/en/2.2.x/) to build the application.

## Create a Flask app

First, create a python flask app which returns details about the TFL trains. This application serves a very basic API with details on London's TFL trains.

```python
from flask import Flask, jsonify, request
import sys
import logging

logging.basicConfig(level=logging.INFO)

app = Flask(__name__)

tasks = [
    {
        'id': 1,
        'service': 'tube',
        'line': 'northern',
        'colour': 'black'
    },
    {
        'id': 2,
        'service': 'tube',
        'line': 'circle',
        'colour': 'red'
    }
]

def shutdown_server():
    func = request.environ.get('werkzeug.server.shutdown')
    if func is None:
        raise RuntimeError('Not running with the Werkzeug Server')
    func()

@app.route('/trains', methods=['GET'])
def get_tasks():
    return jsonify({'tasks': tasks})

@app.route('/')
def hello_world():
    return 'Welcome to trains API'

@app.route('/exit')
def exit():
    message = logging.info("Stopping application")
    shutdown_server()
    print("The Flask server has been shutdown.")

if __name__ == '__main__':
    app.run(debug=True, host='0.0.0.0')
```

