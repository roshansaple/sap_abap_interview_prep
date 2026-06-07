Object-Oriented ABAP (OO ABAP) is an important concept in modern SAP development. When interviewing for a role that involves OO ABAP, you may be asked questions that test your understanding of object-oriented programming principles as they apply to ABAP, as well as your ability to implement these concepts in SAP systems. Below are common interview questions on OO ABAP:

### 1. **What is Object-Oriented Programming (OOP) in ABAP, and how is it different from procedural ABAP?**
- **Answer**: Object-Oriented Programming (OOP) in ABAP involves using classes and objects to structure the program in a more modular and reusable way. In contrast to procedural programming, which focuses on functions and procedures to handle data and processes, OOP emphasizes encapsulation, inheritance, polymorphism, and abstraction.

- **Differences from procedural ABAP**:
    - **Encapsulation**: Data and methods are bundled together inside classes, restricting direct access to data from outside.
    - **Inheritance**: Classes can inherit properties and methods from other classes.
    - **Polymorphism**: Methods can be redefined in subclasses.
    - **Abstraction**: Classes can define interfaces or abstract methods, which are implemented by subclasses.

### 2. **What are the main concepts of Object-Oriented Programming in ABAP?**
- **Answer**: The main concepts of OOP in ABAP include:
    - **Classes**: Define blueprints for objects; they contain attributes (data) and methods (functions).
    - **Objects**: Instances of classes created at runtime.
    - **Encapsulation**: Hiding the internal state and providing public methods to access or modify the data.
    - **Inheritance**: A class can inherit the properties and methods of another class.
    - **Polymorphism**: The ability to call different methods based on the object type, even though they share the same method signature.
    - **Abstraction**: Hiding the complex implementation details and showing only the essential features through abstract classes or interfaces.

### 3. **What is the difference between a class and an object in OO ABAP?**
- **Answer**:
    - **Class**: A class is a blueprint or template for creating objects. It defines attributes (variables) and methods (functions) that the objects of that class will have.
    - **Object**: An object is an instance of a class. It is created based on the class definition and holds specific data. Multiple objects can be created from the same class, each having its own set of data.

### 4. **What is the purpose of the `CONSTRUCTOR` method in a class?**
- **Answer**: The **`CONSTRUCTOR`** method is a special method in ABAP classes that is executed when an object is instantiated. It is used to initialize the object's attributes or perform any setup that is necessary when the object is created. The `CONSTRUCTOR` method does not return any value and is automatically called when an object is created using the `CREATE OBJECT` statement.

### 5. **Explain the difference between `PUBLIC`, `PROTECTED`, and `PRIVATE` visibility in ABAP classes.**
- **Answer**:
    - **`PUBLIC`**: Attributes and methods defined as public are accessible from anywhere in the program or from other classes.
    - **`PROTECTED`**: Protected attributes and methods can only be accessed by the class itself and its subclasses (derived classes).
    - **`PRIVATE`**: Private attributes and methods can only be accessed within the class in which they are defined. They are not visible to subclasses or external classes.

### 6. **What is inheritance in OO ABAP, and how do you implement it?**
- **Answer**: **Inheritance** allows a class (subclass) to inherit attributes and methods from another class (superclass). This enables code reuse and promotes a hierarchical relationship between classes.

To implement inheritance in ABAP, you define a subclass using the `INHERITING FROM` keyword. The subclass inherits the methods and attributes of the superclass.

Example:
   ```abap
   CLASS z_subclass DEFINITION INHERITING FROM z_superclass.
     PUBLIC SECTION.
       METHODS: new_method.
   ENDCLASS.
   ```

### 7. **What is polymorphism in OO ABAP? Can you provide an example?**
- **Answer**: **Polymorphism** in ABAP allows methods to behave differently depending on the object type, even if they have the same name. It enables dynamic method invocation at runtime. This is achieved through method overriding in subclasses.

Example:
   ```abap
   CLASS z_animal DEFINITION.
     PUBLIC SECTION.
       METHODS: make_sound.
   ENDCLASS.
   
   CLASS z_animal IMPLEMENTATION.
     METHOD make_sound.
       WRITE: 'Generic animal sound'.
     ENDMETHOD.
   ENDCLASS.
   
   CLASS z_dog DEFINITION INHERITING FROM z_animal.
     PUBLIC SECTION.
       METHODS: make_sound REDEFINITION.
   ENDCLASS.
   
   CLASS z_dog IMPLEMENTATION.
     METHOD make_sound.
       WRITE: 'Bark'.
     ENDMETHOD.
   ENDCLASS.
   
   DATA(obj) = NEW z_dog( ).
   obj->make_sound( ).  " Output: Bark
   ```

In the example, the `make_sound` method is overridden in the subclass `z_dog`, and when it is called from an instance of `z_dog`, it produces the dog-specific sound.

### 8. **What is the difference between `CREATE OBJECT` and `NEW` in OO ABAP?**
- **Answer**:
    - **`CREATE OBJECT`**: This is the traditional way to create an object in ABAP. It is used to instantiate objects of a class. Example:
      ```abap
      CREATE OBJECT obj TYPE class_name.
      ```
    - **`NEW`**: This is the modern, preferred way to create objects in ABAP, especially when using the object-oriented approach introduced in ABAP 7.40. It is simpler and allows the constructor to be called immediately. Example:
      ```abap
      DATA(obj) = NEW class_name( ).
      ```

### 9. **What is an abstract class in OO ABAP?**
- **Answer**: An **abstract class** is a class that cannot be instantiated directly. It is used as a blueprint for other classes. Abstract classes may contain abstract methods, which are methods that do not have a body and must be implemented by subclasses. Abstract classes are useful when you want to define a common interface or behavior that must be implemented by all subclasses.

Example:
   ```abap
   CLASS z_animal DEFINITION ABSTRACT.
     PUBLIC SECTION.
       METHODS: make_sound ABSTRACT.
   ENDCLASS.
   ```

### 10. **What are interfaces in OO ABAP, and how are they used?**
- **Answer**: An **interface** is a set of methods that a class must implement. Unlike abstract classes, interfaces cannot contain any implementation, only method definitions. Interfaces are used to define common functionality that multiple classes can implement.

Example:
   ```abap
   INTERFACE if_speaker.
     METHODS: speak.
   ENDINTERFACE.
   
   CLASS z_person DEFINITION.
     PUBLIC SECTION.
       INTERFACES: if_speaker.
       METHODS: speak REDEFINITION.
   ENDCLASS.
   
   CLASS z_person IMPLEMENTATION.
     METHOD speak.
       WRITE: 'Hello'.
     ENDMETHOD.
   ENDCLASS.
   ```

The class `z_person` implements the interface `if_speaker`, which forces it to define the `speak` method.

### 11. **How can you handle exceptions in OO ABAP?**
- **Answer**: In OO ABAP, exceptions are handled using **exception classes**. You can define exceptions in a class using the `RAISE` statement and handle them using the `TRY...ENDTRY` block. ABAP provides a built-in exception class `CX_SY_NO_HANDLER` for unhandled exceptions.

Example:
   ```abap
   CLASS z_my_class DEFINITION.
     PUBLIC SECTION.
       METHODS: divide IMPORTING num1 TYPE i num2 TYPE i.
     EXCEPTIONS: divide_by_zero.
   ENDCLASS.

   CLASS z_my_class IMPLEMENTATION.
     METHOD divide.
       IF num2 = 0.
         RAISE divide_by_zero.
       ELSE.
         WRITE: num1 / num2.
       ENDIF.
     ENDMETHOD.
   ENDCLASS.

   TRY.
       DATA obj TYPE REF TO z_my_class.
       CREATE OBJECT obj.
       obj->divide( 10 0 ).
     CATCH zcx_divide_by_zero.
       WRITE: 'Error: Division by zero'.
   ENDTRY.
   ```

### 12. **What is method overloading in OO ABAP?**
- **Answer**: **Method overloading** in OO ABAP allows you to define multiple methods with the same name but with different parameter types or numbers of parameters. However, ABAP does not support traditional method overloading as seen in other OOP languages like Java. You can achieve similar functionality by using optional parameters or default values.

Example:
   ```abap
   CLASS z_calculator DEFINITION.
     PUBLIC SECTION.
       METHODS: add IMPORTING value TYPE i,
                        add IMPORTING value1 TYPE i value2 TYPE i.
   ENDCLASS.
   ```

### 13. **What are static methods and attributes in OO ABAP?**
- **Answer**: **Static methods** and **static attributes** are associated with a class rather than an instance. Static methods and attributes are defined using the keyword `CLASS-DATA` (for static attributes) and `CLASS-METHODS` (for static methods). They can be accessed directly using the class name, without creating an object.

Example:
   ```abap
   CLASS z_calculator DEFINITION.
     PUBLIC SECTION.
       CLASS-METHODS: add IMPORTING value TYPE i.
       CLASS-DATA: result TYPE i.
   ENDCLASS.

   CLASS z_calculator IMPLEMENTATION.
     METHOD add.
       result = result + value.
     ENDMETHOD.
   ENDCLASS.
   ```

---

These questions help evaluate your understanding of object-oriented concepts, as well as your ability to apply them effectively within the ABAP environment. The key to answering these questions successfully is to demonstrate both theoretical knowledge and practical implementation skills.