# Ferds Validator

## Features

Now, let’s describe the ideal features:

- Check for required data.
- Simple basic validation rules
- Verify that the data is of the correct type, and meets the correct criteria. For example, if a username is submitted it must be validated to contain only permitted characters. It must be of a minimum length, and not exceed a maximum length. Etc.

## Installation

$ npm install ferds-validator

## Usages

### Simple validation usage

Examples of simple use :

```javascript
var validator = require( 'ferds-validator' );
var setup = [
	{
		"name": "Alpha Only", // field description
		"value": "ABC", // value that will be validated
		"rules": "alpha" // validate alphabet characters only
	},
	{
		"name": "Required Alpha Only",
		"value": "",
		"rules": "required|alpha"
	},
	{
		"name": "Age",
		"value": 25,
		"rules": "required|numeric|greater_than_equal_to(30)" // Return false, because the value must be greater or equal to 30
	}
}
var run_validator = validator.run( setup ); // Set to variable
console.log( run_validator ); // Raw output

if ( run_validator.status == false ) {
	// your code...
}
else {
	// your code...
}
```

Raw output :

```json
{
	"status": false,
	"message": "Unfortunately, some error has occured.",
	"error_lists": [
		"The Required Alpha Only field is required. ",
		"The Age field must contain a number greater than or equal to 30. "
	]
}
```

## Rule Reference

The following is a list of all the native rules that are available to use:

| Rule | Parameter | Description |
| ------------- |:-------------:|:-------------:|
| alpha | NO | Returns FALSE if the form element contains anything other than alphabetical characters.	 |