# Basic Ionic core components
## Create/Run/Debug project
### Create project
```
$ ionic start myApp blank|tabs|sidemenu
```
### Run project
```
$ ionic serve
```

### Emulate
```
$ ionic emulate android | ios
```

### Run on device

```
$ ionic run android | ios
```

## Colors

![](./images/img09.png)

## Header and Footer

![](./images/img14.png)

### Header

สามารถใช้ได้ทั้ง css (class) และ directive

#### CSS class

โดยใช้ class `.bar .bar-header`

```
<div class="bar bar-header bar-positive">

</div>
```

#### Directive

โดยใช้ directive `ion-header-bar`

```
<ion-header-bar align-title="left" class="bar-positive">

</ion-header-bar>
```

`align-title` สามารถกำหนดได้เป็น `left`, `right`, หรือ `center` ค่าปกติ คือ `center`

#### Header with button

```
<div class="bar bar-header bar-positive">
  <button class="button button-clear">Left</button>
  <div class="title">Welcome to My App</div>
  <button class="button button-clear">Right</button>
</div>
```

### Sub Header

```
<div class="bar bar-header">
  <h1 class="title">Header</h1>
</div>
<div class="bar bar-subheader">
  <h2 class="title">Sub Header</h2>
</div>
```

### Footer

สามารถใช้ได้ทั้ง css (class) และ directive

#### CSS class

```
<div class="bar bar-footer bar-balanced">
  <div class="title">Footer</div>
</div>
```

#### Directive

```
<ion-content class="has-footer">
  Some content!
</ion-content>

<ion-footer-bar align-title="left" class="bar-assertive">

</ion-footer-bar>
```

`align-title` สามารถกำหนดได้เป็น `left`, `right`, หรือ `center` ค่าปกติ คือ `center`

#### Footer with button

```
<div class="bar bar-footer">
  <button class="button button-clear">Left</button>
  <div class="title">Title</div>
  <button class="button button-clear">Right</button>
</div>
```

## Button

### Default button

ตัวอย่าง

![](./images/img10.png)

```
<button class="button">
  Default
</button>

<button class="button button-stable">
  button-stable
</button>
```

### Block button

ตัวอย่าง

![](./images/img11.png)

```
<button class="button button-block button-positive">
  Block Button
</button>
```

### Button Size

ตัวอย่าง

![](./images/img12.png)

```
<button class="button button-small button-assertive">
  Small Button
</button>
<button class="button button-large button-positive">
  Large Button
</button>
```

### Outlined button

ตัวอย่าง

![](./images/img13.png)

```
<button class="button button-outline button-positive">
  Outlined Button
</button>
```

## List

![](./images/img15.png)

list เราสามารถใช้ได้ทั้ง css และ directive

### ใช้ CSS

```
<ul class="list">
    <li class="item">
      ...
    </li>
</ul>
```

### ใช้ Directive

```
<ion-list>
  <ion-item>
    ...
  </ion-item>
</ion-list>
```

### List with icon

![](./images/img16.png)

```
<div class="list">

  <a class="item item-icon-left" href="#">
    <i class="icon ion-email"></i>
    Check mail
  </a>


  <a class="item item-icon-left" href="#">
    <i class="icon ion-mic-a"></i>
    Record album
    <span class="item-note">
      Grammy
    </span>
  </a>

  <a class="item item-icon-left" href="#">
    <i class="icon ion-person-stalker"></i>
    Friends
    <span class="badge badge-assertive">0</span>
  </a>

</div>
```

## Card

![](./images/img17.png)

```
<div class="card">
  <div class="item item-text-wrap">
    This is a basic Card which contains an item that has wrapping text.
  </div>
</div>
```

### Card with Header and Footer

![](./images/img18.png)

```
<div class="card">
  <div class="item item-divider">
    I'm a Header in a Card!
  </div>
  <div class="item item-text-wrap">
    This is a basic Card with some text.
  </div>
  <div class="item item-divider">
    I'm a Footer in a Card!
  </div>
</div>
```

## Form

![](./images/img19.png)

```
<div class="list">
  <label class="item item-input">
    <input type="text" placeholder="First Name">
  </label>
  <label class="item item-input">
    <input type="text" placeholder="Last Name">
  </label>
  <label class="item item-input">
    <textarea placeholder="Comments"></textarea>
  </label>

  <button class="button button-block button-positive activated">Submit</button>
</div>
```
## Toggle

![](./images/img20.png)

### Baisc Toggle

```
<label class="toggle">
   <input type="checkbox">
   <div class="track">
     <div class="handle"></div>
   </div>
</label>
```

### Toggle with list

```
<ul class="list">

  <li class="item item-toggle">
     HTML5
     <label class="toggle toggle-assertive">
       <input type="checkbox">
       <div class="track">
         <div class="handle"></div>
       </div>
     </label>
  </li>

  ...

</ul>
```

## Range

![](./images/img21.png)

```
<div class="item range">
  <i class="icon ion-volume-low"></i>
  <input type="range" name="volume">
  <i class="icon ion-volume-high"></i>
</div>

<div class="list">
  <div class="item range range-positive">
    <i class="icon ion-ios-sunny-outline"></i>
    <input type="range" name="volume" min="0" max="100" value="33">
    <i class="icon ion-ios-sunny"></i>
  </div>
</div>
```

## Page navigation

## List and Form
## Modal and Action Sheet
## Tabs
## Emulate and Debugging

