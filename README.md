<!--<p align="center">
    <img src="public/assets/img/logo.png" style="width : 18px;">
</p>-->


# Hyra Back-end PHP


## Index :

* [Introduction](#intro)
* [Installation](#install)
* [Configuration](#config)
* [Backoffice](#admin)
* [API](#api)
* [Licence](#licence)


## Introduction <a name="intro"></a>

### About Hyra

Hyra is a mobile application offering these users a platform to facilitate the relationship between owner and student looking for accommodation. The application needing to be administered it was necessary to develop a backoffice offering a strong management of the data (user, announcement of housing etc).

### Framework PHP :

<strong> Hyra's PHP Backoffice & API </strong>  is developed with Laravel 5.

> Current Version :
```Laravel 5.7```
>

If you are not familiar with it check the [Laravel documentation](https://laravel.com/docs) or read the "About Laravel" part below.

#### About Laravel

Laravel is a web application framework with expressive, elegant syntax. We believe development must be an enjoyable and creative experience to be truly fulfilling. Laravel attempts to take the pain out of development by easing common tasks used in the majority of web projects, such as:

- [Simple, fast routing engine](https://laravel.com/docs/routing).
- [Powerful dependency injection container](https://laravel.com/docs/container).
- Multiple back-ends for [session](https://laravel.com/docs/session) and [cache](https://laravel.com/docs/cache) storage.
- Expressive, intuitive [database ORM](https://laravel.com/docs/eloquent).
- Database agnostic [schema migrations](https://laravel.com/docs/migrations).
- [Robust background job processing](https://laravel.com/docs/queues).
- [Real-time event broadcasting](https://laravel.com/docs/broadcasting).

Laravel is accessible, yet powerful, providing tools needed for large, robust applications.

## Installation <a name="install"></a>

### Server requirements :

* PHP >= 7.1.3
* PDO PHP Extension
* JSON PHP Extension

### Installating Laravel :

Clone this repository or create a new Laravel Project and transfert the folders of this repository (exept vendor), for this, follow the [Laravel documentation](https://laravel.com/docs).

And use this command : 

```
composer update
```

## Configuration : <a name="config"></a>

### DotEnv :

Laravel utilizes the DotEnv PHP library by Vance Lucas. In a fresh Laravel installation, the root directory of your application will contain a .env.example file. If you clone this repository, this file will be named .env.production, you should rename the file manually to .env. To use Hyra's brackoffice you need to configure this file, to this, follow the  [documentation](https://laravel.com/docs/5.7/configuration#environment-configuration).

#### Exemple : 

```
APP_NAME=Hyra-Backoffice
APP_ENV=local
APP_KEY=
APP_DEBUG=true
APP_URL=http://localhost

DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=8889
DB_DATABASE=hyra
DB_USERNAME=user
DB_PASSWORD=pswd
```

### htaccess

Laravel includes a public/.htaccess file that is used to provide URLs without the index.php front controller in the path. Before serving Laravel with Apache, be sure to enable the mod_rewrite module so the .htaccess file will be honored by the server.
If the .htaccess file that ships with Laravel does not work with your Apache installation, try this alternative:

```
Options +FollowSymLinks -Indexes
RewriteEngine On

RewriteCond %{HTTP:Authorization} .
RewriteRule .* - [E=HTTP_AUTHORIZATION:%{HTTP:Authorization}]

RewriteCond %{REQUEST_FILENAME} !-d
RewriteCond %{REQUEST_FILENAME} !-f
RewriteRule ^ index.php [L]
```

If you are using Nginx, the following directive in your site configuration will direct all requests to the index.php front controller:

```php
location / {
    try_files $uri $uri/ /index.php?$query_string;
}
```

### Collective

To facilitate frontend development of the backoffice, Hyra use Laravel Collective 5.4.
If you have start with a fresh install of laravel follow the [Laravel Collective HTML](https://laravelcollective.com/docs/master/html) documentation to check your installation.


### Database <a name="db"></a> :

Laravel makes interacting with databases extremely simple across a variety of database backends using either raw SQL, the fluent query builder, and the Eloquent ORM. Currently, Laravel supports four databases:

* MySQL
* PostgreSQL
* SQLite
* SQL Server

Hyra's backoffice use the migration system of laravel, after created and connection your database in .env, you need to use this commande : 
```
php artisan migrate --seed
```

> (Don't forget to rename "database/seeds/DatabaseSeeder.php.exemple" without the ".example")

You can check : 
* [Laravel database documentation](https://laravel.com/docs/5.7/database)
* [Eloquent ORM documentation](https://laravel.com/docs/5.7/eloquent)

## Backoffice <a name="admin"></a>

### Authentification

Hyra uses Laravel's internal authentication system. Including Illuminate, the basic controllers concerning the authetification as well as the different views and routes, you can read the documentation of this system here : [Authentification](https://laravel.com/docs/5.7/authentication)

Default user :

> Login :
```admin@admin.com```
>
> Password :
```password```
>

#### Administration

//

## API <a name="api"></a>

Hyra uses an internal API to communicate with the mobile app. The API uses the laravel resource controllers system to define its endpoints through pre-defined routes, exemple:

| Verb | URI | Action |
| :--- | :--- | :--- |
| `GET` | `/photos' | index |
| `POST` | `/photos' | store |
| `GET` | `/photos/{photo}' | show |
| `PUT/PATCH` | `/photos/{photo}' | update |
| `DELETE` | `/photos/{photo}' | destroy |

For more information about this resource controller system, read the documentation of this system here : 
*[Resource Controllers](https://laravel.com/docs/5.7/controllers#resource-controllers)

The API files are stored in the "API" folder itself in the "Controllers" folder :

```

hyra-php-backoffice
│ 
├── app
│   ├── Console
│   └── Exeption
│   └── Http
│   │    └── Controllers
│   │    │    └── API
│   │    │    │   └── API FILE'S
│   │    │    └── ...
│   │    └── Middleware
│   │    └── Kernel.php
│   └── Provider
│   └── Repositories
│   └── ...
├── ...
└── README.md

```

### Authentification

The users of the application must be able to register or to connect in order to secure the data, for that we chose a Mobile Passwordless SMS Authentication to secure and promote the user experience.

```
    USER  <-------------------------------------> BACKEND
(Mobile App)                                   (API & Database)    

                            1
                ------------------------>
                    Send phone number
                    (+33 00 00 00 00)
                                        

                            2
                <------------------------
                    Send SMS with token
                        (012345)

                            3
                ------------------------>
                    Send the token
                        (012345)

                            4
                <------------------------
                        Validation 
                    & Authentification



```
        

#### Twilio

To send an SMS from the backend you have to use an external library. The one we chose is called Twilio. Twilio allows you to send / receive text messages and calls.

#### Configuration

//

### API Authentication

//

#### Passport

//

#### Security

//


## Licence <a name="licence"></a>

// LICENCE




