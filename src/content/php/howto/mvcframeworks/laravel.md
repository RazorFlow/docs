<meta>
{
  "title": "Laravel",
  "subtitle": "",
  "id": "php_mvc_frameworks_laravel",
  "index": 3
}
</meta>

## Integrating RazorFlow with Laravel

* Copy the `razorflow_php` directory into `vendor/`.
* Copy the `Rf.php` into your custom `libraries/` if you have one and include the same in the `composer.json`.
* For Eg., if you keep all your library files in `app/lib/`, then include `app/lib` in the `classmap` of the `autoload` section of `composer.json`.
* Run `composer dump-autoload`
* Create a directory called `rfDashboards` in the `app/` directory. This contains all your dashbboard files.
* Note that, the dashboard's classname and filename must match.

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
