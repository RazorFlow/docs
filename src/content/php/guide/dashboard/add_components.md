<meta>
{
    "title": "Add components to your dashboard",
    "subtitle": "",
    "id": "php_add_components",
    "index": 1
}
</meta>

{{ anchor("component_object", "What is a component object?") }}
### What is a component object?

A component object is an instance of a component class like {{ linkApi("php", "ChartComponent", "") }}, etc. For example, if you have the code:

~~~
$chart1 = new ChartComponent();
~~~

here, `$chart1` is the component object. Calling functions on this `$chart1` object like `$chart1->setCaption` will only affect this component and not any other function.

### Adding components the dashboard

Once you have created a dashboard, and configured the components, you can add components to the dashboard using `$this->addComponent`. So to summarize, the process is:

1. Create a class that extends from StandaloneDashboard
2. Implement the abastract function `buildDashboard`
3. Add a component object inside the `buildDashboard` function
4. Configure the component
5. Use `addComponent` to add the component to the dash board.
6. Create an object of the class that was defined
7. Render the dashboard

~~~
<?php

class SampleDasboard extends StandaloneDashboard{
  public function buildDashboard(){
    $chart = new ChartComponent("chart_1");
    $chart->setCaption ("Chart Caption goes Here");

    $this->addComponent($chart);
  }
}

$db = new SampleDasboard();
$db->renderStandalone();
~~~
