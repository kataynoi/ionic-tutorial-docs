# Basic Angular

## Installation
```
$ mkdir helloWorld
$ cd helloWorld
$ npm init -y
$ npm install angular bootstrap angular-ui-router --save
```

## Controller

### Create controller

```
angular.module('app', [])
    .controller('MainCtrl', function ($scope) {
       $scope.name = 'Satit Rianpit';
       $scope.showName = function () { alert($scope.name); };
    });
```

### Controller directive

```
<div ng-controller="MainCtrl">
    Welcome, {{ name }}
</div>
```

### Data binding

```
# JavaScript
$scope.name = 'Satit Rianpit';

# HTML
Welcome, <strong>{{ name }}</strong> <!-- one way -->
<input type="text" ng-model="name" /> <-- two way -->
```

### Event

```
# JavaScript
$scope.showName = function () { alert($scope.name); };
$scope.setName = function (name) { $scope.name = name; };
$scope.setMe = function (event) {
  console.log(event.keyCode);
  if (event.keyCode == 13) {
    alert('Hi, ' + $scope.name);
  }
};
# HTML
<button type="button" ng-click="showName">Show name</button>
<button type="button" ng-click="setName('John Doe')">Set name</button>
<input type="text" ng-model="name" ng-keypress="setMe($event)" />
```

## Directives

### `ng-repeat`

```
# app.js
$scope.languages = ["TH", "EN", "FR", "DE"];
$scope.postcodes = [
    {code: '50', name: 'Chaing Mai'},
    {code: '44', name: 'Maha Sarakham'},
    {code: '43', name: 'Nong Khai'},
    {code: '21', name: 'Rayong'}
];

# index.html
<h1>Languages</h1>
<ul>
    <li ng-repeat="t in items">{{ t }}</li>
</ul>
<h1>Post Codes</h1>
<input type="text" ng-model="query" />
<ul>
    <li ng-repeat="c in postcodes | filter: query">
        {{ c.code }} - {{ c.name }}
    </li>
</ul>
```

### `ng-if/ng-hide/ng-show`

```
# JavaScript
$scope.success = true;
$scope.show = function () { $scope.success = true; };
$scope.hide = function () { $scope.success = false; };
$scope.toggle = function () { $scope.success = !$scope.success };

# HTML
<div class="alert alert-success" ng-if="success">Show/Hide me please</div>
<button type="button" class="btn btn-success" ng-click="show()">Show</button>
<button type="button" class="btn btn-danger" ng-click="hide()">Hide</button>
<button type="button" class="btn btn-primary" ng-click="toggle()">Toggle</button>
```

## Service

### Create service

```
angular.module('app', [])
.controller('MyCtrl', function (MyService) {
    $scope.name = MyService.name; // Satit Rianpit
    MyService.setName('John Doe');
    $scope.name = MyService.getName(); // John Doe
})
.factory('MyService', function () {
    return {
        name: 'Satit Rianpit',
        getName: function () {
            return this.name;
        },
        setName: function (_name) {
            this.name = _name;
        }
    }
});
```

### Ajax with `$http`

```
.factory('MyService', function ($http) {
    return {
        getUsers: function () {
            return $http.get('/api/users/list')
            .then(function (res) {
                return res.data;
            })
        }
    }
});
```

## Module and Dependencies Injection

### App structure

--app

----controllers

----services

----filters

--templates

--index.html

### Create module

```
# controller

angular.module('app.controllers.Main', [])
    .controller('MainCtrl', function () { });

# service

angular.module('app.services.Main', [])
    .factory('MainService', function () {
        return {
            all: function () {},
            update: function (id, name) {}
        };
    });

# filter

angular.module('app.filters.Convertor', [])
    .filter('Convertor', function () {
        return function (number) {
            return number.fixed(2);
        };
    });

```

### Injection

file: `app.js`

```
angular.module.('app', [
    'app.controllers.Main',
    'app.filters.Convertor',
    'app.controllers.Users'
    ])
    .controller('ListCtrl', function ($scope, MainService) {
        $scope.all = function () {
            $scope.users = MainService.all();
        };

        $scope.update = function (id, name) {
            MainService.update(id, name);
        }
    };
```

file: `users.js`

```
angular.module('app.controllers.Users', ['app.services.Main', 'app.filters.Convertor'])
    .controller('UserCtrl', function ($scope) {

    });
```


## Routing
### Install ui-router

```
$ npm install angular-ui-router --save
```

### Configure routing

file: `app.js`

```
angular.module('app', ['ui-router'])
    .config(function($stateProvider, $urlRouterProvider) {
        $urlRouterProvider.otherwise('/');

        $stateProvider
        .state('main', {
            url: '/',
            template: 'Welcome to my app'
        })

    })
```

### Create template

file: `index.html`

```
<body>
    <div class="container">
        <ui-view></ui-view>
    </div>
</body>
```

### Controller and Template

```
angular.module('app', ['ui-router'])
    .config(function($stateProvider, $urlRouterProvider) {

        $stateProvider
        .state('main', {
            url: '/',
            template: 'Welcome to my app',
            controller: function ($scope) {
                $scope.name = 'Satit Rianpit';
            }
        })
        .state('about', {
            url: '/about',
            template: './templates/about.html',
            controller: 'AboutCtrl'
        })

    });
```

### `$stateParams`

```
.state('detail', {
    url: '/detail/:id',
    templateUrl: './templates/detail',
    controller: function ($scope, $stateParams, UserService) {
        var userId = $stateParams.id;
        UserService.detail(userId)
            .then(function (detail) {
                $scope.detail = detail;
            });
    }
});

# Html
<a href="#/detail/20">User detail</a>

```

### `$state`

```
angular.module('app.controllers.Detail', [])
.controller('MainCtrl', function ($scope, $state) {
    $scope.redirect = function (state) {
        $state.go(state);
    };

    $scope.redirectParameter = function (id) {
        $state.go('detail', {id: 20});
    };
});

```