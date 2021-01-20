**MEAN Stack Deployment on Linux**


- Step1: Install NodeJs

``` sudo apt-get install -y nodejs```


- Step 2: Installation of MongoDB

Before installing MongoDB i added necessary keys

```sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 0C49F3730359A14518585931BC711F9BA15703C6```

```echo "deb [ arch=amd64 ] https://repo.mongodb.org/apt/ubuntu trusty/mongodb-org/3.4 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.4.list```


- I updated the package manager
```sudo apt-get update```


```sudo apt-get install -y mongodb```


```sudo service mongodb start```




 -I installed the body-parser package to help us process the JSON passed in requests to the server


 ```sudo npm install body-parser```


 - I created a folder named "Books"

 ```sudo mkdir Books```



- I moved in to the new folder created and added a file named server.js

```cd Books```

```sudo touch server.js```

![](https://github.com/drazen-dee28/MEAN-Stack-Deployment-on-Linux/blob/main/images/serverjs.jpg)


  **Install Express and set up routes to the server**

  Inside the "Books" folder ,i installed ```Express``` a minimal and flexible Node.js web application framework
  ```sudo npm install express mongoose```

- Inside the "Books" folder,i created another folder named "apps"
  
  ```sudo mkdir apps```

 -  I moved into "apps" folder


 ```cd apps```
-I added a file named routes.js
```sudo touch routes.js```

I edited ```routes.js```  pasted the code below into it as shown:

![](https://github.com/drazen-dee28/MEAN-Stack-Deployment-on-Linux/blob/main/images/app.jpg)


 - In the apps folder,i created a folder named "models" and added a file named "book.js"

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

```sudo mkdir public```


-I moved into the public folder and added a file named `script.js`


-I edited the script.js file by adding the following configuration:
```sudo nano script.js```

```
var app = angular.module('myApp', []);
app.controller('myCtrl', function($scope, $http) {
  $http( {
    method: 'GET',
    url: '/book'
  }).then(function successCallback(response) {
    $scope.books = response.data;
  }, function errorCallback(response) {
    console.log('Error: ' + response);
  });
  $scope.del_book = function(book) {
    $http( {
      method: 'DELETE',
      url: '/book/:isbn',
      params: {'isbn': book.isbn}
    }).then(function successCallback(response) {
      console.log(response);
    }, function errorCallback(response) {
      console.log('Error: ' + response);
    });
  };
  $scope.add_book = function() {
    var body = '{ "name": "' + $scope.Name + 
    '", "isbn": "' + $scope.Isbn +
    '", "author": "' + $scope.Author + 
    '", "pages": "' + $scope.Pages + '" }';
    $http({
      method: 'POST',
      url: '/book',
      data: body
    }).then(function successCallback(response) {
      console.log(response);
    }, function errorCallback(response) {
      console.log('Error: ' + response);
    });
  };
});
```



- In the public folder,i created a file named index.html

```sudo touch index.html```

- I added the following config to the `index.html` file

```sudo nano index.html```


```
<!doctype html>
<html ng-app="myApp" ng-controller="myCtrl">
  <head>
    <script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.6.4/angular.min.js"></script>
    <script src="script.js"></script>
  </head>
  <body>
    <div>
      <table>
        <tr>
          <td>Name:</td> 
          <td><input type="text" ng-model="Name"></td>
        </tr>
        <tr>
          <td>Isbn:</td>
          <td><input type="text" ng-model="Isbn"></td>
        </tr>
        <tr>
          <td>Author:</td> 
          <td><input type="text" ng-model="Author"></td>
        </tr>
        <tr>
          <td>Pages:</td>
          <td><input type="number" ng-model="Pages"></td>
        </tr>
      </table>
      <button ng-click="add_book()">Add</button>
    </div>
    <hr>
    <div>
      <table>
        <tr>
          <th>Name</th>
          <th>Isbn</th>
          <th>Author</th>
          <th>Pages</th>
 
        </tr>
        <tr ng-repeat="book in books">
          <td><input type="button" value="Delete" data-ng-click="del_book(book)"></td>
          <td>{{book.name}}</td>
          <td>{{book.isbn}}</td>
          <td>{{book.author}}</td>
          <td>{{book.pages}}</td>
        </tr>
      </table>
    </div>
  </body>
</html>
```

- I changed the directory back up to Books

`cd ..`



-I Started the server :

```sudo node server.js```

- I tested the server in a browser via address http://localhost:3300 

 ![](https://github.com/drazen-dee28/MEAN-Stack-Deployment-on-Linux/blob/main/images/testserver.jpg)