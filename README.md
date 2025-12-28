# Ex.05 Design a Website for Server Side Processing
## Date:

## AIM:
 To design a website to calculate the Body Mass Index(BMI) in the server side. 


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
~~~
server.html<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>BMI Calculator</title>
    <style>
        body {
            background-color: #1dadc1; 
        }
        .box {
            background-color: #e5e5e5; 
            width: 400px;
            margin-left: 100px;  
            margin-right: 50px;  
            border: 3px dotted #fca311; 
            padding: 20px;
            color: #14213d;
            border-radius: 12px;
        }

        .formelt {
            color: #14213d;
            text-align: center;
            margin-top: 7px;
            margin-bottom: 6px;
        }

        h1 {
            color: #fca311; 
            text-align: center;
            padding-top: 20px;
        }

        input[type="text"] {
            width: 120px;
            padding: 4px;
            text-align: center;
        }

        input[type="submit"] {
            background-color: #fca311;
            color: #14213d;
            border: none;
            padding: 6px 12px;
            cursor: pointer;
            border-radius: 5px;
            font-weight: bold;
        }

        input[type="submit"]:hover {
            background-color: #ffbe33;
        }
    </style>
</head>
<body>
    <br>
    <br>
    <br>
    <br>
    <br>
    <br>
    <div class="edge">
        <div class="box">
            <h1>Body Mass Index (BMI) Calculator</h1>
           <form method="POST">
  {% csrf_token %}
  <label>Height (cm):</label>
  <input type="text" name="height"><br>
  <label>Weight (kg):</label>

  <input type="text" name="weight"><br>

  <button type="submit">Calculate</button>
                <div class="formelt">
                    BMI : <input type="text" name="bmi" value="{{bmi}}"><br/>
                </div>
            </form>
        </div>
    </div>
</body>
</html>

views.py
from django.shortcuts import render

def calculate_bmi(request):
    bmi = None
    height_cm = None
    weight_kg = None

    if request.method == "POST":
        try:
            height_cm = float(request.POST.get("height"))
            weight_kg = float(request.POST.get("weight"))
            height_m = height_cm / 100  # convert cm to meters
            bmi = round(weight_kg / (height_m * height_m), 2)

            # Print all three values to the terminal
            print(f"Height (cm): {height_cm}")
            print(f"Weight (kg): {weight_kg}")
            print(f"Calculated BMI: {bmi}")

        except (TypeError, ValueError, ZeroDivisionError):
            bmi = None

    return render(request, "mathapp/math.html", {"bmi": bmi})

urls.py
from django.contrib import admin
from django.urls import path
from myapp import views

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', views.calculate_bmi, name='calculate_bmi'),
]
~~~



## SERVER SIDE PROCESSING:
<img width="1448" height="763" alt="image" src="https://github.com/user-attachments/assets/521db4b1-d7b5-4589-a7ee-28627a5580d4" />
<img width="1444" height="757" alt="image" src="https://github.com/user-attachments/assets/ae9d7695-737c-4c11-8d0d-2802f91982d2" />




## HOMEPAGE:
<img width="1443" height="725" alt="image" src="https://github.com/user-attachments/assets/9fd1e550-1541-49c8-88be-7f68af9b7f4e" />



## RESULT:
The program for performing server side processing is completed successfully.
