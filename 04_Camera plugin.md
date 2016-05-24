# Camera plugin
## Install plugin

### ติดตั้ง ngCordova (http://ngcordova.com/docs/plugins/camera/)

ดาวน์โหลด ngCordova จากเว็บไซต์ [https://github.com/driftyco/ng-cordova/archive/master.zip](https://github.com/driftyco/ng-cordova/archive/master.zip)
ทำการแตก zip ไฟล์ แล้ว copy ไฟล์ `ng-cordova.min.js` ในโฟลเดอร์ `dist` ไปไว้ใน โฟลเดอร์ `www/lib` ดังรูป

![](./images/04/img01.png)

จากนั้นทำการแก้ไขไฟล์ `www/js/app.js` โดยทำการ Inject module ชื่อ `ngCordova` ดังนี้

```
angular.module('starter', ['ionic', 'ngCordova'])
```

### ติดตั้ง camera plugin

รายละเอียดเพิ่มเติม [http://ngcordova.com/docs/plugins/camera/](http://ngcordova.com/docs/plugins/camera/)

ทำการติดตั้ง plugin โดยใช้คำสั่ง ดังนี้ (ในโฟล์เดอร์ project)

```
$ ionic plugin add cordova-plugin-camera
```

### Options

```
var options = {
  quality: 50,
  destinationType: Camera.DestinationType.FILE_URI,
  sourceType: Camera.PictureSourceType.CAMERA,
  allowEdit: true,
  encodingType: Camera.EncodingType.PNG,
  targetWidth: 200,
  targetHeight: 200,
  popoverOptions: CameraPopoverOptions,
  saveToPhotoAlbum: true,
  correctOrientation: true
};
```

### Get Image from Camera

```

# option

destinationType: Camera.DestinationType.DATA_URL

###################################################################

.controller(function ($ionicPlatform, $cordovaCamera) {

  $scope.image = {};

  $ionicPlatform.ready(function () {
    $cordovaCamera.getPicture(options).then(function(imageData) {
        $scope.image.src = "data:image/jpeg;base64," + imageData;
      }, function(err) {
        // error
      });
  });

});

# HTML

<img ng-src="{{image.src}}">

```

### Get Image from Photo library


```

# option

destinationType: Camera.DestinationType.FILE_URI

###################################################################

$scope.image = {};

$ionicPlatform.ready(function () {
  $cordovaCamera.getPicture(options).then(function(imageUri) {
      $scope.image.src = imageUri;
    }, function(err) {
      // error
    });
});

# HTML

<img ng-src="{{image.src}}">
```

## Upload image to server

```
    $scope.uploadImage = function () {

      $ionicPlatform.ready(function () {

        let serverUrl = 'http://192.168.43.76:3000/uploads/image';
        $cordovaFileTransfer.upload(serverUrl, $scope.image.src, { params: {hospcode: '11053'}})
          .then(function (result) {
            // Success!
            $log.info(result);
          }, function (err) {
            // Error
            $log.error(err);
          }, function (progress) {
            // constant progress updates
            $log.info(progress);
          });

      });

    };
```