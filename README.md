# Ex.05 Design a Website for Server Side Processing
## Date:5/12/24

## AIM:
 To design a website to calculate the power of a lamp filament in an incandescent bulb in the server side. 


## FORMULA:
P = I<sup>2</sup>R
<br> P --> Power (in watts)
<br> I --> Intensity
<br> R --> Resistance

## DESIGN STEPS:

### Step 1:
Clone the repository from GitHub.

### Step 2:
Create Django Admin project.

### Step 3:
Create a New App under the Django Admin project.

### Step 4:
Create python programs for views and urls to perform server side processing.

### Step 5:
Create a HTML file to implement form based input and output.

### Step 6:
Publish the website in the given URL.

## PROGRAM :
```
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Power Calculator</title>
    <style>
        body {
            background-color: #e0f7fa;
            font-family: Arial, sans-serif;
            color: #333;
            margin: 0;
            padding: 0;
        }
        .container {
            width: 400px;
            margin: 50px auto;
            text-align: center;
            background-color: #ffffff;
            padding: 30px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
            border-radius: 10px;
        }
        h1 {
            font-size: 24px;
            color: #00796b;
            margin-bottom: 20px;
        }
        label {
            display: block;
            text-align: left;
            margin-bottom: 5px;
            font-weight: bold;
        }
        input[type="text"] {
            width: calc(100% - 20px);
            padding: 10px;
            margin-bottom: 20px;
            border: 1px solid #ccc;
            border-radius: 5px;
        }
        button {
            padding: 10px 20px;
            background-color: #00796b;
            color: #ffffff;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            font-size: 16px;
        }
        button:hover {
            background-color: #004d40;
        }
        h2 {
            margin-top: 20px;
            color: #d32f2f;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Power Calculator</h1>
        <form method="POST">
            {% csrf_token %}
            <label for="intensity">Intensity (I in Amps):</label>
            <input type="text" name="intensity" id="intensity" required>

            <label for="resistance">Resistance (R in Ohms):</label>
            <input type="text" name="resistance" id="resistance" required>

            <button type="submit">Calculate</button>
        </form>
        {% if power is not None %}
            <h2>Calculated Power: {{ power }} Watts</h2>
        {% endif %}
    </div>
</body>
</html>

views.py

from Django.shortcuts import render

def power_calculator(request):
    power = None  

    if request.method == 'POST':
        
        intensity = request.POST.get('intensity')
        resistance = request.POST.get('resistance')

        
        if intensity and resistance:
            try:
            
                I = float(intensity)
                R = float(resistance)
                power = I**2 * R
                print('intensity=',I)
                print('resistance=',R)
                print('power=',power)  

            except ValueError:
                power = "Invalid input. Please enter numerical values."

    
    return render(request, 'mathapp/math.html', {'power': power})

urls.py

from Django.contrib import admin
from Django.urls import path
from mathapp import views

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', views.power_calculator, name='power_calculator'), 
]


```


## SERVER SIDE PROCESSING:
![Screenshot (27)](https://github.com/user-attachments/assets/3057eb95-1d66-48b9-ab60-13e9b2ba7ac5)


## HOMEPAGE:
![Screenshot (28)](https://github.com/user-attachments/assets/12b5f2ee-b2fd-41ad-9fab-036ec0671589)

## RESULT:
The program for performing server side processing is completed successfully.
