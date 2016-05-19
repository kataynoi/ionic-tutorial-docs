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

*** `align-title` *** สามารถกำหนดได้เป็น `left`, `right`, หรือ `center` ค่าปกติ คือ `center`

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

## Page navigation

## List and Form
## Modal and Action Sheet
## Tabs
## Emulate and Debugging

