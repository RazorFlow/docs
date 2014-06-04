<meta>
{
	"title": "Get the values entered by users",
	"subtitle": "",
	"id": "php_filter_getvalues",
	"index": 3
}
</meta>

### Access the input values in a filter component

You can access the input values of a filter component 

You can access the input values that the user has input into the filter component at any time, by calling the {{ linkApi("php", "FilterComponent", "getInputValue") }} function on the FilterComponent object.

#### Get a single input value

You can get a single value that the user has currently entered into the form by using the {{ linkApi("php", "FilterComponent", "getInputValue") }} function. Note that {{ linkApi("php", "FilterComponent", "getInputValue") }} **only returns a value if the user input something**.

~~~
$selected_product = $filter->getInputValue ('product_name');
$selected_status = $filter->getInputValue ('delivery_date');
~~~

#### Text Filter

Calling {{ linkApi("php", "FilterComponent", "getInputValue") }} with a text filter returns a string which is the user's input.

~~~
$filter->getInputValue ("product_name");

// Returns:
// "Potato Chips"
~~~

#### Drop-Down/Select Filter

Calling {{ linkApi("php", "FilterComponent", "getInputValue") }} returns an object with 2 items:

* `text` - which is the text of the selected item
* `index` - which is the index of the seleted item (starting from 0)

~~~
$filter->getInputValue("delivery_status");

// Returns:
// array(
//   'text' => "Refunded",
//   'index' => 1
// )
~~~


#### Multi Select filter

Calling {{ linkApi("php", "FilterComponent", "getInputValue") }} returns an array with 2 items:

* `text` - which is an array containing texts of selected items
* `index` - which is the an array containing indices of the seleted items (starting from 0)

~~~
$filter->getInputValue("item_category");

// Returns:
// array(
//   'text' => ["Condiments", "Snacks"]
//   'index' => [1, 2]
// )
~~~

#### Date Filter

Calling {{ linkApi("php", "FilterComponent", "getInputValue") }} returns a string with date formatted in "YYYY-MM-DD" format.

~~~
$filter->getInputValue ("sale_date");

// Returns:
// "2013-08-18"
~~~

#### Date Range Filter

Calling {{ linkApi("php", "FilterComponent", "getInputValue") }} returns an array with two strings. The first string is starting date, and second string is the ending date.

~~~
$filter->getInputValue ("sale_period");

// Returns:
// ["2013-07-18", "2013-08-18"]
~~~

#### Numeric Range Filter

Calling {{ linkApi("php", "FilterComponent", "getInputValue") }} returns an array with two numbers. The first string is starting value, and second string is the ending value.

~~~
$filter->getInputValue ("sale_amount");

// Returns:
// [42, 55]
~~~

### Example for using this API

{{ embedExample("php", "filter") }}