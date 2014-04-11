<meta>
{
  "title": "CakePHP",
  "subtitle": "",
  "id": "php_mvc_frameworks_cakephp",
  "index": 1
}
</meta>

## Integrating RazorFlow with CakePHP

* Copy the `razorflow_php` directory into `vendors/`.
* Copy the `Rf.php` into `App/Lib/`.
* Create a directory called `RfDashboards` in the `App/` directory. This contains all your dashbboard files.
* Note that, the dashboard's classname and filename must match.

You will have to load the RazorFlow wrapper for CakePHP.
To load the library use: `App::uses('Rf', 'Lib')`

### Example Code to render Standalone Dashboard from your controller
In order to load a Standalone Dashboard do the following:

~~~
$rf = new Rf();

$db = $rf->loadDashboard('<dashboardClassname>');
$db->renderStandalone();
~~~

### Example Code to render Tabbed Dashboard from your controller
In order to load a Tabbed Dashboard do the following:

~~~
$rf = new Rf();

$db1 = $rf->loadDashboard('<dashboardClassname>');
$db2 = $rf->loadDashboard('<dashboardClassname>');

$tabbed = $rf->loadTabbedDashboard (array($db1, $db2));
$tabbed->setTabbedDashboardTitle ('My Tabbed Dashboard');
$tabbed->setActive ($db2);

$tabbed->renderTabbed ();
~~~
