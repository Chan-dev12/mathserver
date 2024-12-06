# Ex.05 Design a Website for Server Side Processing
# Date:4\11\2024
# AIM:
To design a website to calculate the power of a lamp filament in an incandescent bulb in the server side.

# FORMULA:
P = I2R
P --> Power (in watts)
 I --> Intensity
 R --> Resistance

# DESIGN STEPS:
## Step 1:
Clone the repository from GitHub.

## Step 2:
Create Django Admin project.

## Step 3:
Create a New App under the Django Admin project.

## Step 4:
Create python programs for views and urls to perform server side processing.

## Step 5:
Create a HTML file to implement form based input and output.

## Step 6:
Publish the website in the given URL.

# PROGRAM :
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Lamp Power Calculator</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f9;
            color: #333;
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
        }
        .container {
            background: #fff;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
            width: 310px;
            text-align: center;
        }
        h1 {
            color: #4CAF50;
            margin-bottom: 20px;
        }
        input[type="number"] {
            width: 95%;
            padding: 10px;
            margin: 10px 0;
            border: 1px solid #ccc;
            border-radius: 5px;
        }
        input[type="text"] {
            width: 95%;
            padding: 10px;
            margin: 10px 0;
            border: 1px solid #ccc;
            border-radius: 5px;
        }
        button {
            background: #4CAF50;
            color: white;
            border: none;
            padding: 10px 15px;
            border-radius: 5px;
            cursor: pointer;
        }
        button:hover {
            background: #45a049;
        }
        .result {
            margin-top: 20px;
            font-size: 1.2em;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Lamp Power Calculator</h1>
        <form method="post">
            {% csrf_token %}
            <input type="number" name="intensity" step="any" placeholder="Intensity (I)" required>
            <input type="number" name="resistance" step="any" placeholder="Resistance (R)" required>
            <button type="submit">Calculate Power</button>
            <input type="text" id="ans" value="{{power}}" readonly>
        </form>
        {% if result is not None %}
            <div class="result">
                <strong>Power (P):</strong> {{ result }} Watts
            </div>
        {% endif %}
    </div>
</body>
</html>

# SERVER SIDE PROCESSING:
views.py
from django.shortcuts import render 
def lightpower(request): 
    context={} 
    context['power'] = "0" 
    context['i'] = "0" 
    context['r'] = "0" 
    if request.method == 'POST': 
        print("POST method is used")
        i = request.POST.get('intensity','0')
        r = request.POST.get('resistance','0')
        print('request=',request) 
        print('intensity=',i) 
        print('resistance=',r) 
        power = (int(i) * int(i)) * (int(r))
        context['power'] = power 
        context['i'] = i
        context['r'] = r 
        print('Power=',power) 
    return render(request,'index.html',context)
urls.py

from django.contrib import admin 
from django.urls import path 
from lampapp import views 
urlpatterns = [ 
    path('admin/', admin.site.urls), 
      path('area/',views.lightpower,name="areaofrectangleroot")
]
```

# HOMEPAGE:
![Screenshot 2024-12-06 234541](https://github.com/user-attachments/assets/7aa3c673-fffd-4e1e-8797-65ef90c9dce2)
![Screenshot 2024-12-06 234554](https://github.com/user-attachments/assets/3591abba-d1b7-4a76-9b9a-d301db372e11)


# RESULT:
The program for performing server side processing is completed successfully.
