---
title: "Python Libraries : JSON & YAML"
datePublished: Sat Jul 29 2023 15:39:51 GMT+0000 (Coordinated Universal Time)
cuid: clko6husy000409lc62gbeflq
slug: python-libraries-json-yaml
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1690637569308/ee0f33a3-3f85-47a1-8bae-9bb13aa30c91.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1690645159763/00d588e4-9658-4a6e-86a5-87b227794185.jpeg
tags: python, python3, devops, 90daysofdevops

---

## Introduction to JSON & YAML🐍

### JSON : JavaScript Object Notation

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690638601793/92e7cccd-40a7-427a-8dee-323c80e9b364.webp align="center")

* JSON is a data format used for structuring data in a readable and lightweight manner.
    
* Its primary purpose is to store and transfer data between web browsers and servers.
    
* Python also supports JSON through a built-in package called "JSON."
    
* The JSON package in Python offers various tools for working with JSON objects, such as parsing, serializing, deserializing, and more.
    
    ```bash
    # Example
    {
      "name": "John Doe",
      "age": 30,
      "is_student": false,
      "hobbies": ["reading", "painting", "gardening"]
    }
    ```
    
* Convert JSON to python object :
    
    * json.loads() method can be used to parse a valid JSON string and convert it into a Python Dictionary.
        
        ```bash
        import json
        # JSON string
        student = '{"id":"20", "name": "Shera", "department":"CS"}'
        print("This is JSON", type(student))
        
        print("\nNow convert from JSON to Python")
        
        # Convert string to Python dict
        student_dict = json.loads(student)
        print("Converted to Python", type(student_dict))
        print(student_dict)
        ```
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690639255455/d934a4ce-ee3d-4939-bf4c-2d401592d465.png align="center")
        
* Convert python object to JSON :
    
    * Here json.dumps() function will convert a subset of Python objects into a JSON string
        
        ```bash
        import json
        # JSON string
        student_dict = {'id': '20', 'name': 'Shera', 'department': 'CS'}
        print("This is Python", type(student_dict))
          
        print("\nNow Convert from Python to JSON")
          
        # Convert Python dict to JSON
        json_object = json.dumps(student_dict, indent=4)
        # indent parameter specifies the spaces that are 
        # used at the beginning of a line
        print("Converted to JSON", type(json_object))
        print(json_object)
        ```
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690639553503/931f2595-ad48-4560-89f2-c161679ef2e2.png align="center")
        

### YAML : YAML Ain't Markup Language

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690640837673/14013453-4abe-48e4-8efc-fe5691285b1e.png align="center")

* YAML is a data serialisation format that allows for script interaction. It is commonly used to create configuration files because it prioritises human readability over JSON.
    
* Can be installed using pip :
    
    ```bash
    pip install PyYAML
    # YAML example 
    name: John Doe
    age: 30
    is_student: false
    hobbies:
      - reading
      - painting
      - gardening
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690641461265/1bf63ea4-3f7c-4052-be01-5fcf849f0c7c.png align="center")
    

## Hands-On Practice⌨️

### Task1 :

Create a Dictionary in Python and write it to a json File .

```bash
import json
# Create the employee dictionary
employee = {
    "name": "Kumar Ankit",
    "age": 23,
    "job_title": "Software Engineer",
    "department": "Engineering"
}
# Printing dict data
print("This is Python Dictionary: \n",employee,type(employee))
print("\nNow Convert from Python to JSON")

# Convert Python dict to JSON , serializing json
json_object = json.dumps(employee, indent=4)
# indent parameter specifies the spaces that are
# used at the beginning of a line
print("Converted to JSON", type(json_object))
# Printing json object
print(json_object)
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690642757084/9fca941e-d364-425c-8886-c5fc7e86e543.png align="center")

### Task 2 :

Read a json file services.json kept in this folder and print the service names of every cloud service provider.

```bash
{
    "services": {
      "debug": "on",
      "aws": {
        "name": "EC2",
        "type": "pay per hour",
        "instances": 500,
        "count": 500
      },
      "azure": {
        "name": "VM",
        "type": "pay per hour",
        "instances": 500,
        "count": 500
      },
      "gcp": {
        "name": "Compute Engine",
        "type": "pay per hour",
        "instances": 500,
        "count": 500
      }
    }
  }
```

```bash
# solution 1
# creat a .py file in same directory where json file is stored
import json

with open("services.json","r") as file :
    data = json.loads(file.read())
data['services'].pop('debug')
for k,v in data['services'].items():
    print(k+ ":" +v['name'])
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690643858833/13e70166-a921-45da-be08-10770246d8c9.png align="center")

```bash
# solution 2
import json
with open("services.json") as s:
    # converting it to python dict
    data = json.load(s)
    print("type: ", type (data))
    print("aws:", data['services']['aws']['name'])
    print("azure:", data['services']['azure']['name'])
    print("gcp:", data['services']['gcp']['name'])
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690643890775/d97323ab-aef8-49b4-bfbd-338fd54e9668.png align="center")

### Task 3:

Read YAML file using python, file services.yaml and read the contents to convert yaml to json

```bash
---
services:
  debug: 'on'
  aws:
    name: EC2
    type: pay per hour
    instances: 500
    count: 500
  azure:
    name: VM
    type: pay per hour
    instances: 500
    count: 500
  gcp:
    name: Compute Engine
    type: pay per hour
    instances: 500
    count: 500
```

```bash
# yaml.load() function parses and converts a YAML object to a Python dictionary
import yaml
from yaml.loader import SafeLoader
import json

 # Open the YAML file and load its contents
 with open('services.yaml','r') as s:
     data = yaml.load(s , Loader=SafeLoader)
     print(data)
# now convert to dictionaryand then to a json string using json.dumps()
with open('new_json','w') as json_f:
    json.dump(data,json_f)
final_output = json.dumps(json.load(open('new_json')),indent=4)
print("json_file :\n",final_output)
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690645046896/75477f6b-08d0-4c50-851a-92333f97302f.png align="center")

> Stay tuned for more updates and more hands-on practice
> 
> HAppy Learning :D