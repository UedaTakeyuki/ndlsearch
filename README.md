# ndlsearch
Japan National Diet Library bibliographic search

# how to use
```php:
$isbn_str = '9784526077425'; # 10 or 13 column digit of ISBN code,
$ndl = new NDLsearch($isbn_str);
print "title: ".$ndl->title();
print "author: ".$ndl->creator();
print "subject: ".$ndl->subject();
print "description: ".$ndl->description();
print "language: ".$ndl->language();
```

# how to install
## use from Laravel 5
1. add ndlsearch to the "composer.json" on your laravel project as follows:
```
...
    "require": {
        ...
        "uedatakeyuki/ndlsearch": "dev-master"
    },
...
    "autoload": {
        "classmap": [
            ...
        ],
        "psr-4": {
            "App\\": "app/"
        },
	"files": [
		"vendor/uedatakeyuki/ndlsearch/ndlsearch.php"
	]
...
```

2. ```composer install```
3. ```composer dump-autoload```
4. add ``use App\Classes\NDLsearch;``` as follows:
```php: BibliographyController.php

<?php

namespace App\Http\Controllers;

use Illuminate\Http\Request;
use Illuminate\Support\Facades\Input;

use App\Classes\NDLsearch;

class BibliographyController extends Controller
{
...
    public function create()
    {
    ...
    $ndl = new NDLsearch($barcode);
    session(['title' => (string)$ndl->title()]);
    ...
    ```
