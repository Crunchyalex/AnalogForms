
# Starting out
Before starting my fourth semester at ITU, Jonas and I set ourselves to create the new shift forms for Analog.
These forms being both the shift report for opening, middle and closing shifts, but also the "receiving of goods" forms (milk being the main one).

The forms are created on [CognitoForms](https://www.cognitoforms.com/), where we gather data filled in on every submission. This data is then sent to [Podio](http://Podio.com) through [Zapier](https://zapier.com/). Zapier and Podio are super helpful tools, but we'll focus mainly on what we've done in Cognito forms.

Surprisingly, creating these forms proved a fun challenge, and some of those challenges perhaps were self-inflicted on the "swu-ish" ideas Jonas and I got along the way. 

## Shift Report

On every shift, our baristas need to fill in a report. The
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
