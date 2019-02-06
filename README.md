
# Starting out

Before the 2019 spring semester began, Jonas and I had to create new shift forms for Analog.
These were the shift report for opening, middle and closing shifts, but also the "receiving of goods" forms.

The forms were to be created on [CognitoForms](https://www.cognitoforms.com/). Where the submitted form data is sent to [Podio](http://Podio.com) through [Zapier](https://zapier.com/). Zapier and Podio are both super exciting, and helpful tools, but for this post, we'll focus on Cognito Forms.

Surprisingly, creating these forms proved a bit of a challenge, and while some of those challenges perhaps were self-inflicted on the "swu-ish" ideas Jonas and I got along the way, they were very fun to overcome! 

## Shift Report
On every shift, our baristas need to fill in a report.
They need to type their own initials, and a date needs to go alongside that.
Besides this, they need to select which shift they are on, either opening, middle or closing.


![TheBasics](https://raw.githubusercontent.com/Crunchyalex/AnalogForms/master/TheBasics.gif)


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

Jonas and I investigated a bit, and found the code to be Visual Basic! 
Knowing this, we started coding our first function.

```vb
fridgeTemp = if LeftFridgeTemperature < 1 or RightFridgeTemperature < 1 
             then "Below 1C"
             else if 5 < LeftFridgeTemperature or 5 < RightFridgeTemperature
             then "Above 5C"
             else "Between 1-5C"
```
And Voila! 

As you might be able to tell, this doesn't really tell a field whether or not it needs to be hidden. So how do we achieve this? 

Well, I hope you're prepared, because this is when things get _Wild._

We made use of _Hidden Fields_ acting as variables..! 

Okay, okay. Maybe not _that_ wild. But still!

Any text field can have a default value, set by a function. That's right. We made the default value of a hidden field be 
equal to the above logic. 
Then, our required field looks at this hidden field value and if it is equal to "Between 1-5C", the required field stays hidden!







