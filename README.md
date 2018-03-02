# LL-1-Parsing-Table
The following repo contains a C code which takes the number of productions and a regular grammar as input and generates the FirstPos , and FollowPos of the non - Terminals and displays its corresponding LL(1) Parsing Table. Then it will ask the user for a sample string to demonstrate its LL(1) parsing action. Each step of the LL(1) parsing is then shown with the final result at the end :- Either the string gets accepted or rejected by our LL(1) parser !!
The test cases have been provided above for the user's reference(make sure you follow the format as shown in the sample test cases).

Following are some of the assumptions I have made :-

1) Epsilon is represented by '#'.
2) Productions are of the form A=B , where 'A' is a single Non-Terminal and 'B' can be any combination of Terminals and Non- Terminals.
3) The L.H.S. of the first production rule is the start symbol.
4) Grammer is not left recursive.
5) Each production of a non terminal is entered on a different line.
6) Only Upper Case letters are Non-Terminals and everything else is a terminal.
7) Do not use '!' or '$' as they are reserved for special purposes.
8) All input Strings have to end with a '$'.
                      
                      A PREVIEW OF ONE OF THE SAMPLE TEST CASES CAN BE SEEN BELOW :-


How many productions ? :8

Enter 8 productions in form A=B where A and B are grammar symbols :

E=TR

R=+TR

R=#

T=FY

Y=*FY

Y=#

F=(E)

F=i

----------------------------------------------
 First(E)= { (, i, }

 First(R)= { +, #, }

 First(T)= { (, i, }

 First(Y)= { *, #, }

 First(F)= { (, i, }

-----------------------------------------------

 Follow(E) = { $, ),  }

 Follow(R) = { $, ),  }

 Follow(T) = { +, $, ),  }

 Follow(Y) = { +, $, ),  }

 Follow(F) = { *, +, $, ),  }


                              The LL(1) Parsing Table for the above grammer :-
                             ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

      ======================================================================================================
              |       +               *               (               )               i               $
      ======================================================================================================
         E    |                                       E=TR                            E=TR
      ------------------------------------------------------------------------------------------------------
         R    |       R=+TR                                           R=#                             R=#
      ------------------------------------------------------------------------------------------------------
         T    |                                       T=FY                            T=FY
      ------------------------------------------------------------------------------------------------------
         Y    |       Y=#             Y=*FY                           Y=#                             Y=#
      ------------------------------------------------------------------------------------------------------
         F    |                                       F=(E)                           F=i
      ------------------------------------------------------------------------------------------------------


Please enter the desired INPUT STRING = i+i*i$

                    ===========================================================================
                            Stack                   Input                   Action
                    ===========================================================================
                            $E                      i+i*i$                  E=TR
                            $RT                     i+i*i$                  T=FY
                            $RYF                    i+i*i$                  F=i
                            $RYi                    i+i*i$                  POP ACTION
                            $RY                     +i*i$                   Y=#
                            $R                      +i*i$                   R=+TR
                            $RT+                    +i*i$                   POP ACTION
                            $RT                     i*i$                    T=FY
                            $RYF                    i*i$                    F=i
                            $RYi                    i*i$                    POP ACTION
                            $RY                     *i$                     Y=*FY
                            $RYF*                   *i$                     POP ACTION
                            $RYF                    i$                      F=i
                            $RYi                    i$                      POP ACTION
                            $RY                     $                       Y=#
                            $R                      $                       R=#
                            $                       $                       POP ACTION

            =======================================================================================
                                            YOUR STRING HAS BEEN ACCEPTED !!
            =======================================================================================
