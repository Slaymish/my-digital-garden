
REMEMBER to give CONSTRUCTIVE feedback. 

You can use this spreadsheet to total marks up as you mark assignments
[https://docs.google.com/spreadsheets/d/1DjZO48IuRHWLQQWto6MktMd8f7orOjpTfxkwTueo-lY/edit?usp=sharing](https://docs.google.com/spreadsheets/d/1DjZO48IuRHWLQQWto6MktMd8f7orOjpTfxkwTueo-lY/edit?usp=sharing) 
Note that your own copy of the spreadsheet should ONLY be used to calculate the mark of a student and
SHOULD NOT link it in any way to a student as it is against university rules. 
Do clear up the content of column D as you go along.

# DeShredder

***
**Core**
    `[40]`: Load the list of all Shreds in a directory - load(...) works
    `[20]`: doMouse(...) fully works
              `[10]` move Shreds from the list of all Shreds into the working strip
              `[5]` move Shreds around in the working strip
              `[5]` move Shreds back to the list of all Shreds
      `[5]`: allow the user to see all the Shreds in the list - rotateList() works
  
**Completion:**
      `[2]`: allow the user to shuffle the Shreds in the list - ShuffleList() works
      `[3]`: move the working strip to the end of the list of completed strips and initialise a new working strip - completeStrip() works
      `[3]`: enable the user to change the order of the completed strips, and to move a completed strip back to the working strip
      `[7]`: core works with no exceptions,  roughly 2 marks off per error case below:
    
Test that the app does not cause exceptions or loss of data when:
      - there are no Shreds in a list and user presses it
      - the user tries to select (or move) a shred from beyond the ends of the list
      - the user tries to move a non-existent completed strip
      - the user tries to move a completed strip on top of a non-empty working strip.

**Challenge:**
      `[up to 10]`: Extend the program to allow the user to save the completed strips as reconstructed document in a single image file
      `[up to 10]`: Make the program help the user by highlighting Shreds that might be neighbours of the last Shred in the working strip.

## Style Adherence:

***
`[-2]` lack of relatively strategic/informative method doc or inline comments
`[-2]` Genuinely confusing or bad naming conventions (for variables, methods or classes)
`[-1]` Bad indentation
`[-1]` Inconsistent brackets
`[-5]` Unprofessional eg swears or offensive language, immediate 5 marks and flag the student