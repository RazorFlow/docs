<meta>
{
	"title": "Filter submit events",
	"subtitle": "",
	"id": "php_filter_submit_event",
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
  // Find the locked component by Id.
  $table_obj = $this->getComponentByID("table_id");
  $table_obj->setCaption ("New Caption");
}
~~~

The `onApplyClicked` function takes the following parameters:
* Array of components to be locked.
* The function name that gets executed when the *Apply* button gets clicked.
