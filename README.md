# ISPFDEMO
## Create a demo of an ISPF dialog that looks and feels like the real thing.

    Syntax:    %ISPFDEMO demo-data-set
        or:    ISPFDEMO (as an edit macro)

    Usage Notes: The format of the demo-data-set is:

    All records prior to >START are ignored (comments)

    Attribute characters that may be used in the text are:
    + normal text
    % highlight text
    $ input variable
    @ output variable
    ~ reverse text
    [ yellow text
    ] red text
    ! blue text
    } may NOT be used as it is used for the scrollable panel
      area

    The 1st record to indicate all the following are key
    >START

    >PANEL table-name
     table-name is optional, indicating a table name and thus
                a table display (tbdispl) will be used
     Command ===>_zcmd is inserted automatically

    >PPANEL
     - a popup panel
     - Width and Depth are calculated
     - No Command ===> field
     - The Addpop Location (row/col) will be calculated)

    >SPANEL
     - a scrollable panel (non-table)
     - otherwise same as >PANEL
     Command ===>_zcmd is inserted automatically
     as is a Scroll field.

    >TPanel
     - a TSO panel with no meaningful attributes to show
       a pseudo TSO screen
     - Only data records allowed

    >T title-text
     a title text for the ISPF Panel
     - should come immediately after the panel record

    >V variable value
     - defines the variable in the )INIT section
     - may be placed anywhere

    >SF variable-name length
     Scrolling field
     - the scrolling indicator variable is SFT# (1 to n)
       with # incrementing for each field. Must be defined
       with the @ output attribute

    >C comment
     may be anywhere

    >M short / long-message
     may be anywhere but will be inserted into )PROC
     and invoked on 1st enter, then ignored.
     - use F1 to view the long message

    >TT table model header
     defines the header for a table display
     - may have multiple if each table row is multiple rows
    >TL
     defines the length of each table column
     - may have multiple if each table row is multiple rows
     - each >TL must match a >TT so they go in pairs for > 1
    >TR
     defines the variables and placement for the table
     - ALL variables are v for sel and v1 thru v9
     - on 1st use the )MODEL statement will be written

    For a table the $ is used for the 1st variable and @ for
    all others.

    >TABLE table-name
     defines a table and the name to call it
     below it are the table rows, separated by blanks

     if a variable value is . then it will be blank in the
     table

    >END
     defines the end of the control records

    Enter command B to back one panel (skipping Popups)
    Enter Enter to go forward
    Enter F3 to terminate immediately
