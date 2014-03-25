<meta>
{
    "title": "Installing For PHP",
    "id": "php_installation",
    "index": 1
}
</meta>

Under most circumstances, installing RazorFlow is simple and will take under five minutes to complete.

### Things you need before installing Dashboards for PHP

1. A web server running on Windows, or Linux, or OSX.

  If you don’t have a web server installed, RazorFlow highly recommends XAMPP which is available for Windows, Linux and OSX.

  RazorFlow officially supports Apache 2 at this time of writing. Instructions for other web servers including IIS, nginx, lighttpd, Cherokee will be added soon.
2. PHP 5.4 (or above) installed and configured on your web server. 
3. Databases and database drivers for PHP. Please see database_setup for more details.

### Installing on a local computer for development

1. [Download](https://razorflow.com/download) as a zip file.
2. Determine the Document Root. The Document Root is the folder on your computer, where all your web pages are located.
3. Unzip the contents of the downloaded ZIP File somewhere inside your document root. A Single directory rf is created.
4. If you extracted the rf folder in http://localhost/rf/, then run the installer at http://localhost/rf/src/install.php.
5. Follow the instructions on the installation screen.

### Connecting to a Database

You can connect to Databases using RazorFlow. To access these databases from PHP, you need to install the PDO PHP Driver. On most PHP installations, the driver will be automatically installed. Otherwise, you can find instructions to install these drivers your the vendor’s website.

### Verifying Install is Successful
You can verify that the installation is successful by opening the sample dashboards bundled with RazorFlow. Open http://localhost/rf/demos/index.php in your browser, and click on any one of the demos.

*Important*: You need to install a SQLite driver to view the demo dashboards. This is because the data is in a SQLite database.

The type of the dashboard you are creating is called a "Standalone Dashboard". We will cover the different types of dashboards in a later article.
