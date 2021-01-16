


- Step1: Install NodeJs

``` sudo apt-get install -y nodejs```


- Step 2: Install MongoDB

Before installing MongoDB add necessary keys

```sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 0C49F3730359A14518585931BC711F9BA15703C6```

```echo "deb [ arch=amd64 ] https://repo.mongodb.org/apt/ubuntu trusty/mongodb-org/3.4 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.4.list```


-  Update the package manager
```sudo apt-get update```


```sudo apt-get install -y mongodb```


```sudo service mongodb start```




 - Install the body-parser package to help us process the JSON passed in requests to the server


 ```sudo npm install body-parser```


 - Create a folder named "Books"

 ```sudo mkdir Books```



- Move in to the new folder created and Add a file named server.js

```cd Books```

```sudo touch server.js```

![](https://github.com/drazen-dee28/MEAN-Stack-Deployment-on-Linux/blob/main/images/serverjs.jpg)


  **Install Express and set up routes to the server**

  ```sudo mkdir apps```

 -  Move into apps folder


 ```cd apps```
- Add a file named routes.js
```sudo touch routes.js```

Edit ```routes.js```  paste the code below into it as shown:

![](https://github.com/drazen-dee28/MEAN-Stack-Deployment-on-Linux/blob/main/images/app.jpg)


 - In the apps folder, create a folder named "models" and add a file named "book.js"

```sudo mkdir models```
 ```cd models```
 ```sudo touch book.js```
 
 - Edit book.js as shown below
 ```sudo nano book.js```

 ![](https://github.com/drazen-dee28/MEAN-Stack-Deployment-on-Linux/blob/main/images/bookjs.jpg)





 **Access the routes with AngularJS**

 - Move to the Books directory


```cd Books```

- Create a folder named public

'''sudo mkdir public```