# Strings
Laravel5 offers a great way to manipulate strings through the Illuminate\Support\Str class and its useful methods. We can manipulate strings with very little code which is awesome. Let's see a fast example for our blog posts:

	use Illuminate\Support\Str;

	$article = 'Lorem ipsum dolor sit amet, consectetur adipiscing elit.';
	
	{{Str::words($article, 5)}}
	
	'Lorem ipsum dolor sit amet...'
	
Great! We tackled the length of the post with ease so we provided a nice introductory text for our post. Let's create a slug from our article's title to provide later a SEF url:

	use Illuminate\Support\Str;
	
	$title = 'Laravel is great';
	
	$slug = Str::slug($title);
	
	$slug = 'laravel-is-great';

This was so fast and useful! So Laravel5 has prepared quite a few tools to help us manipulate long or ugly strings in so many ways.

Below every method of Str class is explained with some brief and declarative examples per method so you can grasp their functionality with ease.

## ascii()

Transliterate a UTF-8 value to ASCII.

**Method:**
	
	public static function ascii($value);
	
**Example:**

	use Illuminate\Support\Str;
	
	{{Str::ascii('Με λένε Μάριο!')}}
	
**Result:**
	
	'Me lene Mario!'
	
**Notes:**

We use a simple phrase in greek and the `ascii()` method transforms every char in ascii.

## camel()

Convert a value to camel case.

**Method:**
	
	public static function camel($value);
	
**Example:**

	use Illuminate\Support\Str;
	
	{{Str::camel('Laravel is really awesome')}}
	
**Result:**
	
	'laravelIsReallyAwesome'
	
**Equivalent Helper Function:**

	camel_case($value);
	
**Notes:**

We use a simple string and the `camel()` method creates the camel case version of it.

## contains()

Determine if a given string contains a given substring.

**Method:**
	
	public static function contains($haystack, $needles);
	
**Parameters:**

The second parameter named $needles can be a string or an array of strings.  
	
**Example 1:**

	use Illuminate\Support\Str;
	
	{{Str::contains('Laravel is really awesome', 'Laravel')}}
	
**Result:**
	
	true
	
**Example 2:**

	use Illuminate\Support\Str;
	
	{{Str::contains('Laravel is really awesome', ['Laravel', 'is'])}}
	
**Result:**
	
	true
	
**Example 3:**

	use Illuminate\Support\Str;
	
	{{Str::contains('Laravel is really awesome', ['laravel', 'is'])}}
	
**Result:**
	
	true
	
**Example 4:**

	use Illuminate\Support\Str;
	
	{{Str::contains('Laravel is really awesome', ['laravel', 'his'])}}
	
**Result:**
	
	false
	
**Equivalent Helper Function:**

	str_contains($haystack, $needles);
	
**Notes:**

As i mentioned before the second parameter can be a string or an array of strings. In case it is a string the method returns true or false accordingly by searching in a case-sensitive manner. In case we pass an array of strings then the method returns true as long as it has at least one match no matter how many strings the `$needles` array contains. So in our third example the method returned true because there was 1 match while for in fourth example returned false because of 0 matches.

## endsWith()

Determine if a given string ends with a given substring.

**Method:**
	
	public static function endsWith($haystack, $needles);
	
**Parameters:**

The second parameter named $needles can be a string or an array of strings.  
	
**Example 1:**

	use Illuminate\Support\Str;
	
	{{Str::endsWith('Laravel is really awesome', 'awesome')}}
	
**Result:**
	
	true
	
**Example 2:**

	use Illuminate\Support\Str;
	
	{{Str::endsWith('Laravel is really awesome', 'Awesome')}}
	
**Result:**
	
	false
	
**Example 3:**

	use Illuminate\Support\Str;
	
	{{Str::endsWith('Laravel is really awesome', ['Awesome', 'awesome'])}}
	
**Result:**
	
	true
	
**Equivalent Helper Function:**

	ends_with($haystack, $needles);
	
**Notes:**

As i mentioned before the second parameter can be a string or an array of strings. In case it is a string the method returns true or false accordingly by checking in a case-sensitive manner. In case we pass an array of strings then the method returns true as long as one of the strings is the correct one.

## finish()

Cap a string with a single instance of a given value.

**Method:**
	
	public static function finish($value, $cap);
	
**Example 1:**

	use Illuminate\Support\Str;
	
	{{Str::finish('Laravel is really awesome', ' and superb')}}
	
**Result:**
	
	'Laravel is really awesome and superb'
	
**Example 2:**

	use Illuminate\Support\Str;
	
	{{Str::finish('http://home/', '/')}}
	
**Result:**
	
	'http://home/'
	
**Equivalent Helper Function:**

	str_finish($value, $cap);
	
**Notes:**

If the cap already exists then nothing happens and the initial string is returned.
	
## is()

Determine if a given string matches a given pattern.

**Method:**
	
	public static function is($pattern, $value);
	
**Example 1:**

	use Illuminate\Support\Str;
	
	{{Str::is('Laravel', 'Laravel is really awesome')}}
	
**Result:**
	
	false
	
**Example 2:**

	use Illuminate\Support\Str;
	
	{{Str::is('Laravel*', 'Laravel is really awesome')}}
	
**Result:**
	
	true
	
**Example 3:**

	use Illuminate\Support\Str;
	
	{{Str::is('*is*', 'Laravel is really awesome')}}
	
**Result:**
	
	true

**Equivalent Helper Function:**

	str_is($pattern, $value);
	
**Notes:**

Use the asterisk to indicate that more chars are before or after the `$pattern` we are searching for so you can have a match.

## length()

Return the length of the given string.

**Method:**
	
	public static function length($value);
	
**Example:**

	use Illuminate\Support\Str;
	
	{{Str::length('Laravel is really awesome')}}
	
**Result:**
	
	25
	
## limit()

Limit the number of characters in a string.

**Method:**
	
	public static function limit($value, $limit = 100, $end = '...');
	
**Example 1:**

	use Illuminate\Support\Str;
	
	{{Str::limit('Laravel is really awesome')}}
	
**Result:**
	
	'Laravel is really awesome'
	
**Example 2:**

	use Illuminate\Support\Str;
	
	{{Str::limit('Laravel is really awesome', 7)}}
	
**Result:**
	
	'Laravel...'
	
**Example 3:**

	use Illuminate\Support\Str;
	
	{{Str::limit('Laravel is really awesome', 7, '!!!')}}
	
**Result:**
	
	'Laravel!!!'
	
**Equivalent Helper Function:**

	str_limit($value, $limit = 100, $end = '...');
	
## lower()

Convert the given string to lower-case.

**Method:**
	
	public static function lower($value);	
**Example:**

	use Illuminate\Support\Str;
	
	{{Str::lower('Laravel is really awesome')}}
	
**Result:**
	
	'laravel is really awesome'
	
## words()

Limit the number of words in a string.

**Method:**
	
	public static function words($value, $words = 100, $end = '...');	
**Example 1:**

	use Illuminate\Support\Str;
	
	{{Str::words('Laravel is really awesome')}}
	
**Result:**
	
	'Laravel is really awesome'
	
**Example 2:**

	use Illuminate\Support\Str;
	
	{{Str::words('Laravel is really awesome', 3)}}
	
**Result:**
	
	'Laravel is really...'
	
**Example 3:**

	use Illuminate\Support\Str;
	
	{{Str::words('Laravel is really awesome', 2, '###')}}
	
**Result:**
	
	'Laravel is###'
	
**Notes:**

Very useful to provide an introductory part of your content.
	
## parseCallback()

Parse a Class@method style callback into class and method.

**Method:**

	public static function parseCallback($callback, $default);
	
**Example 1:**
	
	use Illuminate\Support\Str;
	
	{{Str::parseCallback('Test@tester', 1)}}
	
**Result:**

	['Test', 'tester']
	
**Example 2:**
	
	use Illuminate\Support\Str;
	
	{{Str::parseCallback('Test', 1)}}
	
**Result:**

	['Test', 1]
	
**Notes:**

In case you refer to a class and its method like `Class@method` then with this method you can fast distinguish the class from its method and have an array with their names. If there is no `@` then the value of the callback is used as the name of the method in the array.

## plural()

Get the plural form of an English word.

**Method:**

	public static function plural($value, $count = 2);
	
**Example 1:**
	
	use Illuminate\Support\Str;
	
	{{Str::plural('test')}}
	
**Result:**

	'tests'
	
**Example 2:**
	
	use Illuminate\Support\Str;
	
	{{Str::plural('category')}}
	
**Result:**

	'categories'
	
**Example 3:**
	
	use Illuminate\Support\Str;
	
	{{Str::plural('money')}}
	
**Result:**

	'money'
	
**Equivalent Helper Function:**

	str_plural($value, $count = 2);
	
## random()

Generate a more truly "random" alpha-numeric string.

**Method:**

	public static function random($length = 16);
	
**Example 1:**
	
	use Illuminate\Support\Str;
	
	{{Str::random()}}
	
**Result:**

	'Q7EPToH8la5M0SDh' // 16 chars long random alphanumeric string
	
**Example 2:**
	
	use Illuminate\Support\Str;
	
	{{Str::random(3)}}
	
**Result:**

	'w4G' // 3 chars long random alphanumeric string
	
**Equivalent Helper Function:**

	str_random($length = 16);
	
**Notes:**

Uses php 5.3.0 `openssl_random_pseudo_bytes ( int $length [, bool &$crypto_strong ] );` function to produce random strings. If we want a string strong and sufficient for cryptography this is the method we need.
	
## quickRandom()

Generate a "random" alpha-numeric string.

**Method:**

	public static function quickRandom($length = 16);
	
**Example 1:**
	
	use Illuminate\Support\Str;
	
	{{Str::quickRandom()}}
	
**Result:**

	'Q7EPToH8la5M0SDh' // 16 chars long random alphanumeric string
	
**Example 2:**
	
	use Illuminate\Support\Str;
	
	{{Str::quickRandom(3)}}
	
**Result:**

	'w4G' // 3 chars long random alphanumeric string
	
**Notes:**

Uses a pool which contains all alpha-numeric chars and picks some of them in random position to provide fast a random string. If we want a string sufficient for cryptography then we should use method `random()`.

## upper()

Convert the given string to upper-case.

**Method:**

	public static function upper($value);
	
**Example:**

	use Illuminate\Support\Str;
	
	{{Str::upper('Laravel is really awesome')}}
	
**Result:**
	
	'LARAVEL IS REALLY AWESOME'
	
## title()

Convert the given string to title case.

**Method:**

	public static function title($value);
	
**Example:**

	use Illuminate\Support\Str;
	
	{{Str::title('Laravel is really awesome')}}
	
**Result:**
	
	'Laravel Is Really Awesome'
	
## singular()

Get the singular form of an English word.

**Method:**

	public static function singular($value);
	
**Example 1:**
	
	use Illuminate\Support\Str;
	
	{{Str::singular('tests')}}
	
**Result:**

	'test'
	
**Example 2:**
	
	use Illuminate\Support\Str;
	
	{{Str::singular('categories')}}
	
**Result:**

	'category'
	
**Example 3:**
	
	use Illuminate\Support\Str;
	
	{{Str::singular('money')}}
	
**Result:**

	'money'
	
**Equivalent Helper Function:**

	str_singular($value);
	
## slug()

Get the singular form of an English word.

**Method:**

	public static function slug($title, $separator = '-');
	
**Example 1:**
	
	use Illuminate\Support\Str;
	
	{{Str::slug('Laravel is really awesome')}}
	
**Result:**

	'laravel-is-really-awesome'
	
**Example 2:**
	
	use Illuminate\Support\Str;
	
	{{Str::slug('Laravel is really awesome', '_')}}
	
**Result:**

	'laravel_is_really_awesome'
	
**Equivalent Helper Function:**

	str_slug($title, $separator = '-');
	
**Note:**

A fast way to create SEF urls for your application.
	
## snake()

Convert a string to snake case.

**Method:**

	public static function snake($value, $delimiter = '_');
	
**Example 1:**
	
	use Illuminate\Support\Str;
	
	{{Str::snake('Laravel is really awesome')}}
	
**Result:**

	'laravel_is_really_awesome'
	
**Example 2:**
	
	use Illuminate\Support\Str;
	
	{{Str::slug('Laravel is really awesome', '-')}}
	
**Result:**

	'laravel-is-really-awesome'
	
**Equivalent Helper Function:**

	snake_case($value, $delimiter = '_');
	
## startsWith()

Determine if a given string starts with a given substring.

**Method:**
	
	public static function startsWith($haystack, $needles);
	
**Parameters:**

The second parameter named $needles can be a string or an array of strings.  	
**Example 1:**

	use Illuminate\Support\Str;
	
	{{Str::startsWith('Laravel is really awesome', 'laravel')}}
	
**Result:**
	
	false
	
**Example 2:**

	use Illuminate\Support\Str;
	
	{{Str::startsWith('Laravel is really awesome', 'Laravel')}}
	
**Result:**
	
	false
	
**Example 3:**

	use Illuminate\Support\Str;
	
	{{Str::startsWith('Laravel is really awesome', ['Laravel', 'laravel'])}}
	
**Result:**
	
	true
	
**Equivalent Helper Function:**

	starts_with($haystack, $needles);
	
**Notes:**

The second parameter can be a string or an array of strings. If it is a string the method returns true or false accordingly by checking in a case-sensitive manner. In case we pass an array of strings then the method returns true as long as one of the strings is the correct one.

## studly()

Convert a value to studly caps case.

**Method:**
	
	public static function studly($value);
	
**Example:**

	use Illuminate\Support\Str;
	
	{{Str::studly('Laravel is really awesome')}}
	
**Equivalent Helper Function:**
	
	function studly_case($value);
	
**Result:**
	
	'LaravelIsReallyAwesome'
