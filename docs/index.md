---
layout: default
---

{{ title }}

### JavaScript Code

```js
// Javascript code with syntax highlighting.
var fun = function lang(l) {
  dateformat.i18n = require('./lang/' + l)
  return true;
}
```


### Java Code
```java
// Declaring constructors
public class Bunny {
    //public bunny(){} //Wrong: doesn't compile as java is case-sensitive
    public Bunny(){
        System.out.println("constructor");
    }

    //GOOD, WARNING: not a constructor, it's a method, but with similar name as
    public void Bunny(){

    };
    // constructor, it may be problematic
}
```