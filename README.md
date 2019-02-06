
# Starting out
Before starting my fourth semester at ITU, Jonas and I set ourselves to create the new shift forms for Analog.
We needed the shift report for opening, middle and closing shifts, but also the "receiving of goods" forms.

The forms are created on [CognitoForms](https://www.cognitoforms.com/). The submitted form data is then sent to [Podio](http://Podio.com) through [Zapier](https://zapier.com/). Zapier and Podio are super helpful tools, but here I'll focus mainly on what we've done in Cognito forms.

Surprisingly, creating these forms proved a fun challenge, and while some of those challenges perhaps were self-inflicted on the "swu-ish" ideas Jonas and I got along the way, they were overcome with ferocious stubborness.

## Shift Report
On every shift, our baristas need to fill in a report.
They need to type their own initials, and a date needs to go alongside that.
Besides this, they need to select which shift they are on, either opening, middle or closing.


![TheBasics](https://raw.githubusercontent.com/Crunchyalex/AnalogForms/master/TheBasics.png)


Because each type of shift require their own fields, we only want display the those relevant and have the rest hidden.
This is easy to implement with the inbuilt click-logic of CognitoForms.


![ShowMiddle](https://raw.githubusercontent.com/Crunchyalex/AnalogForms/master/ShowMiddle.png)


Showing a section then, is super simple. But what do we include in the sections?

### Opening
The first thing we do on opening (besides checking in!) is checking the temperature of our fridges!
If our barista reports anything outside the range of 1-5C, the barista has to fill out a required field.


![BadMilk](https://raw.githubusercontent.com/Crunchyalex/AnalogForms/master/BadMilk.gif)


As we saw with hidding / showing a section, Cognito Forms provides a basic interface for applying logic.
But you can also create custom conditional logic written with code! 
[CognitoForms documentation](https://www.cognitoforms.com/support/)
Jonas and I investigated a bit and found the code to be something Microsoft related. 
_Which later turned out to be Visual Basic._
Knowing this, we coded this!

```vb
fridgeTemp = if LeftFridgeTemperature < 1 or RightFridgeTemperature < 1 
             then "Below 1C"
             else if 5 < LeftFridgeTemperature or 5 < RightFridgeTemperature
             then "Above 5C"
             else "Between 1-5C"
```

But as you might be able to tell, this doesn't really tell a field whether or not it needs to be hidden! 

Hold on to your butts, because this is when things get _Wild._

We made use of _Hidden Fields_ acting as variables..! 

Any text field can have a default value, set by a function. That's right. We made the default value of a hidden field be 
equal to the above logic. 
Then, our required field looks at the hidden field value and if it's equal to "Between 1-5C", the required field stays hidden.





