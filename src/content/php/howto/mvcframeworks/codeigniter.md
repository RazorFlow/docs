<meta>
{
  "title": "CodeIgniter",
  "subtitle": "",
  "id": "php_mvc_frameworks_codeigniter",
  "index": 0
}
</meta>

## Integrating RazorFlow with CodeIgniter

* Copy the `razorflow_php` directory into `application/libraries`.
* Create a file called `Rf.php` in `application/libraries` with the following content:
  ~~~
  <?php

  if (!defined('BASEPATH')) {exit('No direct script access allowed');}

  require_once(APPPATH . 'libraries/razorflow_php/razorflow.php');

  class Rf {

    public function loadDashboard ($className) {
      $this->requireDashboardFile($className);
      $db = new $className();

      return $db;
    }

    private function requireDashboardFile ($file) {
      $filename = APPPATH . "rfDashboards/" . $file . ".php";
      require($filename);
    }

  }
  ~~~
* Create a directory called `rfDashboards` in the `application/` directory. This contains all your dashbboard files.
* Note that, the dashboard's classname and filename must match. i.e., If you would like to load a dashboard called `SampleDashboard`, then the filename must be called: `SampleDashboard.php`

You will have to load the RazorFlow wrapper for CodeIgniter.
To load the library use: `$this->load->library('rf')`

### Example Code to render Standalone Dashboard from your controller
In order to load a Standalone Dashboard do the following:

~~~
$this->load->library('rf');

$db = $this->rf->loadDashboard('<dashboardClassname>');
$db->renderStandalone();
~~~

### Example Code to render Embedded Dashboard
In order to load a Embedded Dashboard do the following:

~~~
$this->load->library('rf');

$db_embed = $this->rf->loadDashboard('<dashboardClassname>');
$data = array(
  "db" => $db_embed
);

$this->load->view('view_name', $data);

~~~

Inorder to render the Embedded Dashboard in your view file use:
~~~
<?php echo $db->renderEmbedded(); ?>
~~~