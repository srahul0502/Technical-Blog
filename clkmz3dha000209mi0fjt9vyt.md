---
title: "Python Data Types and Data Structures"
datePublished: Fri Jul 28 2023 19:24:52 GMT+0000 (Coordinated Universal Time)
cuid: clkmz3dha000209mi0fjt9vyt
slug: python-data-types-and-data-structures
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1690560280702/bdee6318-2985-4703-9e61-bbc12fba1302.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1690572060340/8fcfdf7a-62ab-41ae-a220-905963901136.png
tags: python, devops, datatypes, 90daysofdevops

---

## Python Data Types ⌨️

* Data types are the classification or categorization of data items. It represents the kind of value that tells what operations can be performed on a particular data.
    
* Since everything is an object in Python programming, data types are actually classes and variables are instance (object) of these classes.
    
* Python has the following data types built-in by default: Numeric(Integer, complex, float), Sequential(string,lists, tuples), Boolean, Set, Dictionaries, etc
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690560340832/195eb147-3c55-4f60-901d-19b6f5ad7929.png align="center")
    
* To check what is the data type of the variable you used , wrtie : type(variable)
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690560924344/7b76b219-fa1b-4714-8f22-22237a7690dc.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690560934716/b8624cc1-495e-4a1f-ada9-fae210d0829f.png align="center")
    

## Data Structures 🏗️

* Data Structures are a way of organizing data so that it can be accessed more efficiently depending upon the situation. Data Structures are fundamentals of any programming language around which a program is built. Python helps to learn the fundamental of these data structures in a simpler way as compared to other programming languages.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690571889797/75aac55e-9885-4719-a955-098d7feff1e2.jpeg align="center")
    
* **Lists :** Python Lists are just like the arrays, declared in other languages which is an ordered collection of data. It is very flexible as the items in a list do not need to be of the same type.
    
    ```bash
    # we use [] to write list
    List = [1, 2, 3, 4]
    # to access list using index
    print(List[0]) # index starts from 0 [0 1 2 3 4 5 6]
    # to sort the list 
    List.sort() #sorts them in alphabetic / numeric format
    ```
    
    * Accessing elements is done through zero-based indexing, allowing for easy retrieval of specific elements.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690566582546/cbf6014f-3225-43af-ac89-021d8742c2dd.png align="center")
        
    * Python provides a wide range of built-in methods for list manipulation, including append(), pop(), extend(), and more
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690566556154/e30f7798-45ef-4198-aa1d-d45425189734.png align="center")
        
    * You can learn more about lists [here](https://www.geeksforgeeks.org/python-lists/?ref=lbp) .
        
* **Tuple:** Python Tuple is a collection of Python objects much like a list but Tuples are immutable in nature i.e. the elements in the tuple cannot be added or removed once created. Just like a List, a Tuple can also contain elements of various types.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690568718112/e73b3faa-0d21-4b1d-859c-c40be4921844.png align="center")
    
    * Unlike lists, they are immutable, Once created, tuples cannot be changed. Elements cannot be added, removed, or modified
        
        ```bash
        tuple1 = (0, 1, 2, 3)
        tuple2 = ('python', 'tuple')
         
        # Concatenating above two
        print(tuple1 + tuple2)
        ```
        
    * You can learn more about tuple [here](https://www.geeksforgeeks.org/python-tuples/?ref=lbp) .
        
* **Dictionary:** Python dictionary is like hash tables in any other language with the time complexity of O(1). It is an unordered collection of data values, used to store data values like a map, which, unlike other Data Types that hold only a single value as an element, Dictionary holds the key:value pair. Key-value is provided in the dictionary to make it more optimized .
    
    * Dictionaries are not ordered collections, meaning elements are not indexed or sorted.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690571121045/cea1af8a-5288-499d-8f31-9d37783934f7.png align="center")
        
    * Access element using key :
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690571341879/4e915ed7-bf5d-4f00-b3bc-1547c3984e40.png align="center")
        
        ```bash
        # to access element using key
        print(dict['key'])
        ```
        
    * You Can learn more about dictionary [here](https://www.geeksforgeeks.org/python-dictionary/) .
        
* **Set:** Sets are unordered collections of unique elements. They are useful when dealing with data that requires distinct values and set operations .
    
    * Like dictionaries, sets are unordered collections and do not support indexing.
        
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690571701527/61d452ec-ce99-4e7f-8427-d40ad94a0b2d.png align="center")
    
    * You can learn more about set [here](https://www.geeksforgeeks.org/sets-in-python/?ref=lbp) .
        

## Difference between List , tuple , Dictionary and set❗

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690571982810/b88c99ff-280c-4bc7-a36b-5a9e11fd96ea.jpeg align="center")