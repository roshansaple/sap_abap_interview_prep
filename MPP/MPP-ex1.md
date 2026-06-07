Sure, let's rewrite your module pool program code using best practices and the latest syntax features of ABAP. We'll also add exception handling where appropriate.

### Best Practices and Latest Syntax Features
1. **Use of `DATA` within `FORM` and `MODULE`:** Declare data locally within the scope where they are used.
2. **Inline Declarations:** Use `DATA` inline declarations for variables where possible.
3. **Field Symbols and Data References:** Use field symbols for improved performance.
4. **Modern LOOP and SELECT Statements:** Use the latest syntax for looping and selecting data.
5. **Exception Handling:** Use `TRY...CATCH` blocks for exception handling.

### Updated Code

Here's the updated code:

```abap
*&---------------------------------------------------------------------*
*& Modulpool  ZNS90R_MPP_DIS_COM_PUR_DETAILS
*&---------------------------------------------------------------------*
PROGRAM zns90r_mpp_dis_com_pur_details.

DATA gv_bukrs TYPE knb1-bukrs.

TYPES: 
  BEGIN OF ty_knb1,
    bukrs TYPE knb1-bukrs,
    kunnr TYPE knb1-kunnr,
    akont TYPE knb1-akont,
  END OF ty_knb1.

TYPES: 
  BEGIN OF ty_t001,
    bukrs TYPE t001-bukrs,
    butxt TYPE t001-butxt,
  END OF ty_t001.

*&---------------------------------------------------------------------*
*&      Module  USER_COMMAND_1000_DIS_BACK  INPUT
*&---------------------------------------------------------------------*
*       Handles the user commands for displaying data or going back.
*----------------------------------------------------------------------*
MODULE user_command_1000_dis_back INPUT.

  CASE sy-ucomm.
    WHEN 'DIS'.
      PERFORM fetch_knb1_data.
    WHEN 'BACK'.
      LEAVE TO SCREEN 0.
    WHEN OTHERS.
      MESSAGE 'Unknown command' TYPE 'E'.
  ENDCASE.

ENDMODULE.

*&---------------------------------------------------------------------*
*&      Module  F4_HELP_ON_COM_CD  INPUT
*&---------------------------------------------------------------------*
*       Handles the F4 help for company codes.
*----------------------------------------------------------------------*
MODULE f4_help_on_com_cd INPUT.

  DATA lt_t001 TYPE TABLE OF ty_t001.

  TRY.
      SELECT bukrs, butxt 
        FROM t001 
        INTO TABLE @lt_t001.

      CALL FUNCTION 'F4IF_INT_TABLE_VALUE_REQUEST'
        EXPORTING
          retfield    = 'BUKRS'
          dynpprog    = 'ZNS90R_MPP_DIS_COM_PUR_DETAILS'
          dynpnr      = '1000'
          dynprofield = 'GV_BUKRS'
          value_org   = 'S'
        TABLES
          value_tab   = lt_t001
        EXCEPTIONS
          OTHERS      = 1.

      IF sy-subrc <> 0.
        MESSAGE 'F4 help failed' TYPE 'E'.
      ENDIF.

    CATCH cx_sy_open_sql_db.
      MESSAGE 'Database error occurred while fetching company codes' TYPE 'E'.
  ENDTRY.

ENDMODULE.

*&---------------------------------------------------------------------*
*&      Form  FETCH_KNB1_DATA
*&---------------------------------------------------------------------*
*       Fetches and displays data from KNB1 table.
*----------------------------------------------------------------------*
FORM fetch_knb1_data.

  DATA: lt_knb1 TYPE TABLE OF ty_knb1.

  TRY.
      SELECT bukrs, kunnr, akont 
        FROM knb1 
        INTO TABLE @lt_knb1
        WHERE bukrs = @gv_bukrs.

      IF sy-subrc <> 0.
        MESSAGE 'No data found for the given company code' TYPE 'I'.
        RETURN.
      ENDIF.

      LEAVE TO LIST-PROCESSING.

      LOOP AT lt_knb1 ASSIGNING FIELD-SYMBOL(<ls_knb1>).
        WRITE: / <ls_knb1>-bukrs, <ls_knb1>-kunnr, <ls_knb1>-akont.
      ENDLOOP.

    CATCH cx_sy_open_sql_db.
      MESSAGE 'Database error occurred while fetching KNB1 data' TYPE 'E'.
  ENDTRY.

ENDFORM.
```

### Explanation of Changes

1. **Local Variable Declarations:**
    - Declared `lt_t001` and `lt_knb1` locally within the modules and forms where they are used.
    - This keeps the scope of the variables limited, improving readability and maintainability.

2. **Inline Declarations:**
    - Used the `@` symbol for inline variable declarations in `SELECT` statements.

3. **Field Symbols:**
    - Used `FIELD-SYMBOL` for looping through internal tables to improve performance.

4. **TRY...CATCH Blocks:**
    - Added `TRY...CATCH` blocks to handle potential database errors during `SELECT` operations.
    - Included specific exception classes like `cx_sy_open_sql_db` for more precise error handling.

5. **Consistent Naming Conventions:**
    - Used meaningful names for all the variables and modules.

6. **Modern Syntax:**
    - Used the latest ABAP syntax for `SELECT` and `LOOP` statements, which are more efficient and concise.

By following these best practices and using the latest syntax features, the code becomes more robust, readable, and maintainable. If you have any more questions or need further assistance, feel free to ask!