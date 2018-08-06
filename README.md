# get-zip-codes

#### This application has an:
 * input field;
 * button;
 * list of city, states.
 #### And has this functionality:
 * User enter a zipcode into the field and press the button to save the city and state to the list. 
 * Input cleared on submit.
 * Same zip code didn't store 2 or more times.
 * Selecting an item in the list fill the input with the zip code that was used to look up the city and state.
 * If the user enters a new zip code while an item is selected and hits the button, the record updated (if valid input).
 * User can to deselect selected item.

#### This project allows to enter zip code in input field and get city and state that corresponds to this input on click the button.
#### Project is written using pure JavaScript(ES6+). As assemble system webpack is used.

Project used [ZipCodeAPI](https://www.zipcodeapi.com/).
In the first step we must [Register](https://www.zipcodeapi.com/Register) application to get application key. 
Then we must set up javascript client key by using [Client Key Setup](https://www.zipcodeapi.com/ClientKeySetup). We must write domain name and this client key will only be accepted when used on this domain.
With using client key we can fetch information that provides this API.

The code is written with subsequent re-use of components and further support. Each file / module is responsible for its functionality. If there is a need to use another API, the changes will be minimal, mainly in zipController.js.
**We have components:**
**userInput.js** that validates entered value.
**zipCodeApi.js** that fetch information with entered zip code. In the response we received object (for example for zipCode=44444):
```
{
acceptable_city_names:[{…}],
city:"Newton Falls",
lat:0.718601,
lng:-1.41325,
state:"OH",
timezone:{timezone_identifier: "America/New_York", timezone_abbr: "EDT", utc_offset_sec: -14400, is_dst: "T"},
zip_code:"44444"
}
```
**zipController.js** - has methods to inite Store, render information and the click handler for the list item. 
**store.js** - the data is stored in the Store in the object with format:
```
{ 
zipCode1:{city:'city', 
          state:'state'}}, 
zipCode2:{city:'city',
          state:'state'}},
...
}
```
In this case, we can immediately get information, knowing the key.
