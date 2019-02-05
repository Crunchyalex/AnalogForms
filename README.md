
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

The opening shift needs to report the temperature of the fridges. And if they report them outside the optimal range of 1-5C, we provide a field the baristas have to fill out, in case the milk has turned bad.

![BadMilk](https://raw.githubusercontent.com/Crunchyalex/AnalogForms/master/BadMilk.gif)

To create this effect, we created a permanently hidden text field with a default value set to a little piece of logic! 

```
isHidden = if LeftFridgeTemperature < 0 or RightFridgeTemperature < 0 then "Below 1C" else if 5 < LeftFridgeTemperature or 5 < RightFridgeTemperature then "Above 5C" else "Between 1-5C"
```

