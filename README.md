Pipo Localization Package for Codeigniter
============

Simple package to ease internationalization on PHP projects especially when dealing with agglunative languages (such as Turkish).

Description
-------

In Turkish "Kubilay'a" and "Mehmet'e" means "to Kubilay" and "to Mehmet" respectively, but there's no way to choose affix (e or a) in language files.

Example:

    $lang['follow_started_to_follow'] = "%s takip etmeye başladınız.";
    sprintf(lang('follow_started_to_follow'), "Ahmet");
   
returns:
> Ahmet takip etmeye başladınız.

But in Turkish, actual response is **"Ahmet'i takip etmeye başladınız."**. 
To handle that, you can use localize function:

    $lang['follow_started_to_follow'] = "{turkish_i:%s} takip etmeye başladınız.";
    localize(sprintf(lang('follow_started_to_follow'), "Ahmet"));

returns:
> Ahmet'i takip etmeye başladınız.

Installation
------------

This is a third party package for CodeIgniter. 
Simply put folder content to `applications/third_party`, load `pipo-localization` package and `localization` helper.

Usage
-----

After loading localization helper, you'll be able to use localization tags in your language files.
Localization tags have following form:

    {function_name:String to localize}
    
You can replace `function_name` with any function that takes 1 string parameter. 

Localization helper autoloads a localization file, depending your current language configuration. 
For example if your current language is `turkish` this helper will look for `localizations/turkish_localization_helper.php` in your `helpers` folder.

In Turkish localization, there's a function named `turkish_e`, following is an example usage

    $lang['key'] = "{turkish_e:%s} gittim";
    <?= localize(sprintf(lang('key'), 'Ankara'); ?>
returns:
>Ankara'ya gittim

See [Turkish Localization Helper](/docs/turkish_localization.md) for learning about Turkish localization

Extending
--------

If you'd like to create a localization helper, simply create `localizations` folder in `application/helpers`. 
Then put your localization file in this folder.

Alternatively, you can load any helper manually and use it's functions that are taking 1 parameter as input.

Porting
-------

This package is for CodeIgniter only as it depends on configuration, but localization files are self contained and can be used for other frameworks, too.


