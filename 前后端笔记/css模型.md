```
flex弹性盒子模型
```


```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <title>flex布局</title>
    <style type="text/css">
    .box {
        background: blue;
        display: flex;
    }

    .box div {
        width: 200px;
        height: 200px;
    }

    .box1 {
        background: red;
    }

    .box2 {
        background: orange;
    }

    .box3 {
        background: green;
    }
    </style>
</head>
<body>
    <div class="box">
        <div class="box1"></div>
        <div class="box2"></div>
        <div class="box3"></div>
    </div>
</body>
</html>
```
```
   .box {
        background: blue;
        display: flex;
         justify-content: flex-end;
    }
    justify-content: flex-start | flex-end | center | space-between | space-around;
```


