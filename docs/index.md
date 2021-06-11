---
layout: default
---

{{ title }}

## Open JDK: Java Mission Control/Java Flight Recorder
[How to build easily JMC/JFR](./blog/2021/how-to-build-easily-jmc-jfr)



### How to create a class and it's instance
```java
// Declaring constructors
public class Blog {

    //public blog(){} //ALERT: doesn't compile as java is case-sensitive
    
    public Blog(){
        System.out.println("default constructor");
    }

    //WARNING: Compiles but it's not a constructor, it's a method
    public void Blog(){};
    /**
     * Constructor can be already a big fun, but 
     * Java offers much more challenges
     * Keep Reading
    */
}
```