# LL-1-Parsing-Table
The following repo contains a C code which takes the number of productions and a regular grammar as input and generates the FirstPos , and FollowPos of the non - Terminals and displays its corresponding LL(1) Parsing Table. Then it will ask the user for a sample string to demonstrate its LL(1) parsing action. Each step of the LL(1) parsing is then shown with the final result at the end :- Either the string gets accepted or rejected by our LL(1) parser !!
The test cases have been provided above for the user's reference(make sure you follow the format as shown in the sample test cases).
                      
                      A PREVIEW OF ONE OF THE SAMPLE TEST CASE CAN BE SEEN BELOW :-


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

                        =====================================================================================================================
                                |       +               *               (               )               i               $
                        =====================================================================================================================
                           E    |                                       E=TR                            E=TR
                        ---------------------------------------------------------------------------------------------------------------------
                           R    |       R=+TR                                           R=#                             R=#
                        ---------------------------------------------------------------------------------------------------------------------
                           T    |                                       T=FY                            T=FY
                        ---------------------------------------------------------------------------------------------------------------------
                           Y    |       Y=#             Y=*FY                           Y=#                             Y=#
                        ---------------------------------------------------------------------------------------------------------------------
                           F    |                                       F=(E)                           F=i
                        ---------------------------------------------------------------------------------------------------------------------


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

                        =======================================================================================================================
                                                                YOUR STRING HAS BEEN ACCEPTED !!
                        =======================================================================================================================
