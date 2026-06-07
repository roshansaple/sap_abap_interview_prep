In SAP ABAP, the concepts of "call by value" and "call by reference" are used to describe how data is passed to subroutines (FORM routines) and function modules. Understanding these concepts is crucial for effective ABAP programming.

### Call by Value

When parameters are passed by value, a copy of the actual parameter's value is passed to the subroutine or function module. Changes made to the parameter inside the subroutine or function module do not affect the original variable.

#### Example with FORM Routine

```ABAP
REPORT z_call_by_value.

DATA: lv_value TYPE i VALUE 10.

START-OF-SELECTION.
  WRITE: / 'Before calling subroutine, lv_value:', lv_value.
  PERFORM change_value USING lv_value.
  WRITE: / 'After calling subroutine, lv_value:', lv_value.

FORM change_value USING value TYPE i.
  value = 20.
  WRITE: / 'Inside subroutine, value:', value.
ENDFORM.
```

**Output:**
```
Before calling subroutine, lv_value: 10
Inside subroutine, value: 20
After calling subroutine, lv_value: 10
```

In this example, `lv_value` is passed to the subroutine `change_value` by value. Inside the subroutine, changing `value` does not affect `lv_value`.

### Call by Reference

When parameters are passed by reference, the subroutine or function module receives a reference to the actual parameter. Any changes made to the parameter inside the subroutine or function module affect the original variable.

#### Example with FORM Routine

```ABAP
REPORT z_call_by_reference.

DATA: lv_value TYPE i VALUE 10.

START-OF-SELECTION.
  WRITE: / 'Before calling subroutine, lv_value:', lv_value.
  PERFORM change_value USING REFERENCE(lv_value).
  WRITE: / 'After calling subroutine, lv_value:', lv_value.

FORM change_value USING value TYPE i.
  value = 20.
  WRITE: / 'Inside subroutine, value:', value.
ENDFORM.
```

**Output:**
```
Before calling subroutine, lv_value: 10
Inside subroutine, value: 20
After calling subroutine, lv_value: 20
```

In this example, `lv_value` is passed to the subroutine `change_value` by reference. Inside the subroutine, changing `value` affects `lv_value`.

### Call by Value and Call by Reference in Function Modules

Function modules in ABAP can also use both call by value and call by reference. This is controlled by the parameter types: `IMPORTING`, `EXPORTING`, `CHANGING`, and `TABLES`.

- **IMPORTING:** Call by value.
- **EXPORTING:** Call by value.
- **CHANGING:** Call by reference.
- **TABLES:** Call by reference.

#### Example with Function Module

1. **Create a function module (SE37):**
   - Name: `Z_CALL_BY_REF_FUNC`
   - Define parameters:
     - `IMPORTING` parameter: `IV_VALUE` TYPE `I`
     - `CHANGING` parameter: `CV_VALUE` TYPE `I`

2. **Function module code:**
   ```ABAP
   FUNCTION Z_CALL_BY_REF_FUNC.
   *"----------------------------------------------------------------------
   *"*"Local Interface:
   *"  IMPORTING
   *"     VALUE(IV_VALUE) TYPE  I
   *"  CHANGING
   *"     VALUE(CV_VALUE) TYPE  I
   *"----------------------------------------------------------------------
     CV_VALUE = IV_VALUE + 10.
   ENDFUNCTION.
   ```

3. **Call the function module in a report:**
   ```ABAP
   REPORT z_call_by_ref_func_example.

   DATA: lv_import_value TYPE i VALUE 10,
         lv_change_value TYPE i VALUE 20.

   START-OF-SELECTION.
     WRITE: / 'Before calling function module, lv_change_value:', lv_change_value.
     CALL FUNCTION 'Z_CALL_BY_REF_FUNC'
       IMPORTING
         iv_value = lv_import_value
       CHANGING
         cv_value = lv_change_value.
     WRITE: / 'After calling function module, lv_change_value:', lv_change_value.
   ```

**Output:**
```
Before calling function module, lv_change_value: 20
After calling function module, lv_change_value: 30
```

In this example, the `CHANGING` parameter `CV_VALUE` is passed by reference. The function module modifies `CV_VALUE`, and the change is reflected in the calling program.

### Summary

- **Call by Value:** A copy of the variable's value is passed to the subroutine or function module. Changes inside the subroutine or function module do not affect the original variable.
- **Call by Reference:** A reference to the variable is passed to the subroutine or function module. Changes inside the subroutine or function module affect the original variable.

Understanding these concepts helps ensure that your ABAP programs work correctly and efficiently, especially when dealing with large data structures or requiring precise control over variable modifications.