<meta>
{
	"title": "Filter submit events",
	"subtitle": "",
	"id": "filter_submit_event",
	"index": 2
}
</meta>

You can execute a PHP function when the "Apply" button on the filter has been clicked, by using the `onApplyClicked` function. This callback gives you all the data in an easy to use form.

~~~
<?php

public function buildDashboard(){
  $filter_obj->onApplyClicked (array($table_obj, "function_name"));
}

public function function_name($source, $target, $params){

}
~~~

The `onApplyClicked` function takes the following parameters:
* Array of components to be locked.
* The function name that gets executed when the *Apply* button gets clicked.
