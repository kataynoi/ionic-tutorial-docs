# SQLite plugin

รายละเอียดเพิ่่มเติม [https://github.com/litehelpers/Cordova-sqlite-storage](https://github.com/litehelpers/Cordova-sqlite-storage)

### ติดตั้ง ngCordova (http://ngcordova.com/docs/plugins/sqlite/)

ดาวน์โหลด ngCordova จากเว็บไซต์ [https://github.com/driftyco/ng-cordova/archive/master.zip](https://github.com/driftyco/ng-cordova/archive/master.zip)
ทำการแตก zip ไฟล์ แล้ว copy ไฟล์ `ng-cordova.min.js` ในโฟลเดอร์ `dist` ไปไว้ใน โฟลเดอร์ `www/lib` ดังรูป

![](./images/04/img01.png)

จากนั้นทำการแก้ไขไฟล์ `www/js/app.js` โดยทำการ Inject module ชื่อ `ngCordova` ดังนี้

```
angular.module('starter', ['ionic', 'ngCordova'])
```

## ติดตั้ง plugin

```
ionic plugin add https://github.com/litehelpers/Cordova-sqlite-storage.git
```

## ตัวอย่างการใช้งาน

```
module.controller('MyCtrl', function($scope, $cordovaSQLite) {

  var db = $cordovaSQLite.openDB({
    name: "my.db",
    location: 'default',
    iosDatabaseLocation: 'Library'
    });

  $scope.execute = function() {
    var query = "INSERT INTO test_table (data, data_num) VALUES (?,?)";
    $cordovaSQLite.execute(db, query, ["test", 100]).then(function(res) {
      console.log("insertId: " + res.insertId);
    }, function (err) {
      console.error(err);
    });
  };

});
```

## สร้าง database

```
var db = $cordovaSQLite.openDB({
  name: "my.db",
  location: 'default',
  iosDatabaseLocation: 'Library'
  });
```

## Initial Data

```
angular.module('app', [])
.run(function ($ionicPlatform, $cordovaSQLite) {
  $ionicPlatform.ready(function () {
    var sql = 'CREATE TABLE IF NOT EXISTS users(id number primary key, name text)';

    $cordovaSQLite.execute(db, sql, []).then(function(res) {
      console.log("Success");
    }, function (err) {
      console.error(JSON.stringify(err));
    });

  });
})
```

## Save data

```
var sql = 'INSERT INTO users(name) VALUES(?)';

$cordovaSQLite.execute(db, sql, ["AngularJS"]).then(function(res) {
  console.log("Success");
  console.log('resultSet.insertId: ' + res.insertId);
  console.log('resultSet.rowsAffected: ' + res.rowsAffected);
}, function (err) {
  console.error(JSON.stringify(err));
});
```

## Update data

```
var sql = 'UPDATE users SET name=? WHERE id=?';

$cordovaSQLite.execute(db, sql, ["Ionic Framework", 1]).then(function(res) {
  console.log("Success");
}, function (err) {
  console.error(JSON.stringify(err));
});
```

## Remove data

```
var sql = 'DELETE FROM users WHERE id=?';

$cordovaSQLite.execute(db, sql, [1]).then(function(res) {
  console.log("Success");
  console.log('resultSet.rowsAffected: ' + res.rowsAffected);
}, function (err) {
  console.error(JSON.stringify(err));
});
```

## Search data

```
var sql = 'SELECT * FROM users';

$cordovaSQLite.execute(db, sql, ["Ionic Framework", 1]).then(function(res) {
  for (var i = 0; i <= res.rows.length - 1; i++) {
      $log.info(res.rows.item(i));
      var obj = {};
      obj.name = res.rows.item(i).name;
      $scope.users.push(obj);
    }
}, function (err) {
  console.error(JSON.stringify(err));
});
```

