<meta>
{
	"title": "Getting Started with the filter component",
	"subtitle": "",
	"index": 1,
	"id": "php_filter_configure"
}
</meta>
### Add a filter component to the dashboard

You can add a filter component to the dashboard by creating an instance of the {{ linkApi("php", "FilterComponent", "") }} object in your code.

~~~
<?php

class SampleDasboard extends StandaloneDashboard{
  public function buildDashboard () {
    $filter = new FilterComponent("filter1");
    $filter->setDimensions (4, 4);

    $this->addComponent($filter);
  }
}

$db = new SampleDashboard();
$db->renderStandalone();
~~~

### Add form elements to filter component

A Filter Component is made up of one or more filters. Each filter is a form element to be displayed on the filter.

Each filter in the filter component will have a unique key. This key is used to retrieve the data from the filter.

#### Text Filter

A text filter allows the user to enter text. To add a text filter, use the {{ linkApi("php", "FilterComponent", "addTextFilter") }} function

~~~
$filter->addTextFilter ("product_name", "Product Name");
~~~

There are 2 parameters:

1. The key of the filter (`"product_name"`).
2. The label of the filter (`"Product Name"`)

You can specify a default value of the text to be filled in by passing a configuration object as an extra parameter

~~~
$filter->addTextFilter ("product_name", "Product Name", array(
	"defaultText" => "Potato Chips"
));
~~~

#### Drop-Down/Select Filter

You can add a Drop-Down select element to your filter using the {{ linkApi("php", "FilterComponent", "addSelectFilter") }}.

~~~
$filter->addSelectFilter ("delivery_status", "Delivery Status", array(
	"Delivered",
	"Refunded",
	"Cancelled"
));
~~~

There are 3 parameters:

1. The key of the filter (`"delivery_status"`).
2. The label of the filter (`"Delivery Status"`)
3. An array of options

By default, the first option is always selected. But you can set another option to be selected like this:

~~~
$filter->addSelectFilter ("delivery_status", "Delivery Status", array(
	"Delivered",
	"Refunded",
	"Cancelled"
), array(
	"defaultSelectedIndex" => 1
));
~~~

This selects index `1` in the array. Note that since the array starts from 0, "Refunded" is selected by default.

#### Multi Select filter

Multi select filters allow your users to select more than one option.

~~~
$filter->addMultiSelectFilter ("item_category", "Item Category", array(
	"Beverages",
	"Condiments",
	"Snacks",
	"Groceries"
));
~~~

There are 3 parameters:

1. The key of the filter (`"item_category"`).
2. The label of the filter (`"Item Category"`)
3. An array of options 

By default, no options are selected. You can specify the defaults:

~~~
$filter->addMultiSelectFilter ("item_category", "Item Category", array(
	"Beverages",
	"Condiments",
	"Snacks",
	"Groceries"
), array(
	"defaultSelectedOptions" => array(1, 2)
));
~~~

This selects indices `1` and `2` in the array. Note that since the array starts from 0, "Condiments" and "Snacks" are selected.

#### Date Filter

A date filter allows your users to pick a single date, use the {{ linkApi("php", "FilterComponent", "addDateFilter") }} function.

~~~
$filter->addDateFilter ("sale_date", "Sale Date");
~~~

There are 2 parameters:

1. The key of the filter (`"sale_date"`).
2. The label of the filter (`"Sale Date"`)

By default, the current date is displayed. You can specify another date to be shown as default by passing a configuration object as an extra parameter.

~~~
$filter->addDateFilter ("sale_date", "Sale Date", array(
	"defaultDate" => "03-12-2013"
));
~~~

#### Date Range Filter

A date range filter allows your users to select a range of dates by specifying a start and end date, use the {{ linkApi("php", "FilterComponent", "addDateRangeFilter") }} function.

~~~
$filter->addDateFilter ("sale_period", "Sale Period");
~~~

There are 2 parameters:

1. The key of the filter (`"sale_period"`).
2. The label of the filter (`"Sale Period"`)

By default, the end date is the current date, and the start date is 1 month behind the current date. For Example, if today is 8th August 2013:

* Start Date: 8th July 2013
* End Date: 8th August 2013

You can specify different defaults:

~~~
$filter->addDateFilter ("sale_date", "Sale Date", array(
	"defaultStartDate" => "03-12-2013",
	"defaultEndDate" => "06-12-2013"
));
~~~

If the default start date is not provided, the current date is used. If the default end date is not provided, the current date is used.


#### Numeric Range Filter

A numeric range filter allows your users to select a range of numbers by specifying a start and end values, use the {{ linkApi("js", "FilterComponent", "addNumericRangeFilter") }} function.

~~~
$filter->addDateFilter ("sale_amount", "Sale Amount", array(0, 100));
~~~

There are 3 parameters:

1. The key of the filter (`"sale_amount"`).
2. The label of the filter (`"Sale Amount"`)
3. An array with 2 elements containing start and end amounts

### What's next?

Learn to use the filter component to actually extract values.
