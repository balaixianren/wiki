# Aspect 使用文档
提供切面功能函数before/after，该类不能单独使用，基于events类，需通过base进行调用。

标签： aralejs

---

## 使用说明
`before` 和 `after` 函数是按注册的先后顺序执行的，先注册先执行。

```javascript
    var Dialog = Base.extend({
    
        show: function() {
            //...
        }
        
    });

    var dialog = new Dialog();
    
    dialog.before('show', function() {
        console.log(2);
    });

    dialog.before('show', function() {
        console.log(1);
    });

    dialog.show(); // ==> 2, 1
```

---

### **before** `object.before(methodName, callback, [context])`
在 `object[methodName]` 方法执行前，先执行 `callback` 函数。可以在`callback`函数通过 **return fasle** 来阻止原函数执行。

```javascript
    var Dialog = Base.extend({
    
        show: function() {
            console.log(2);
        }
        
    });

    var dialog = new Dialog();
    
    dialog.before('show', function() {
        console.log(1);
    });

    dialog.show(); // ==> 1, 2
```

### **after** `object.after(methodName, callback, [context])`
在 `object[methodName]` 方法执行后，再执行 `callback` 函数。

```javascript
    var Dialog = Base.extend({
    
        show: function() {
            console.log(2);
        }
        
    });

    var dialog = new Dialog();
    
    dialog.before('show', function() {
        console.log(1);
    });
    
    dialog.after('show', function() {
        console.log(3);
    });

    dialog.show(); // ==> 1, 2, 3
```





