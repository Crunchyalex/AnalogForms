
Starting my fourth semester at ITU

Analog has gotten itself new and shinny forms to fill out during the shift! 

Jonas anker

### isEvenWeek
```=!(Math.Round(((Form.TheBasics.Date.DayOfYear + 6)/7)%2)==1)```

shiftDay
'''= if (Form.TheBasics.Date.DayOfWeek = "Monday")
  then if (IsEvenWeek.Equals("true"))
  then "MondayEven"
  else "MondayUneven"
else if (Form.TheBasics.Date.DayOfWeek = "Tuesday")
  then if (IsEvenWeek.Equals("true"))
  then "TuesdayEven"
  else "TuesdayUneven"
else if (Form.TheBasics.Date.DayOfWeek = "Wednesday")
  then if (IsEvenWeek.Equals("true"))
  then "WednesdayEven"
  else "WednesdayUneven"
else if (Form.TheBasics.Date.DayOfWeek = "Thursday")
  then if (IsEvenWeek.Equals("true"))
  then "ThursdayEven"
  else "ThursdayEven"
else if (Form.TheBasics.Date.DayOfWeek = "Friday")
  then if (IsEvenWeek.Equals("true"))
  then "FridayEven"
  else "FridayUneven"
else "Weekend"
'''
hiddenCleanState
=
if ShiftDay.Equals("MondayEven")
    then "Fridges"
else if ShiftDay.Equals("FridayUneven")
    then "Ice Machine"
else if ShiftDay.Equals("TuesdayEven")
    then "Filter Coffee"
else if ShiftDay.Equals("ThursdayUneven")
    then "Espresso and Filter Grinder"
else "General

showWhyNot
=(!DidYouCleanBothFridges and
  !DidYouCleanBothGrinders and !DidYouCleanTheDrawerCoversInTheKitchenAndBar and !DidYouCleanTheFilterCoffeeMachines and
  !DidYouCleanTheIceMachine and
  !DidYouCleanTheShelves and !DidYouCleanTheThermosAndDifferentContainers and
  !DidYouCleanTheTrashCansAndBins and
  !DidYouCleanTheWallsAndSinks and !DidYouEmptyAndCleanAllTheDrawers)

hiddenStatusState
  = if (WhyNot.length > 0 and ShowWhyNot.Equals("true"))
   then "Error"
  else "Completed"
