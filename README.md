# Android Developer Guide

This guide is different from others you may see, here we will be focousing for a smooth onboarding process for development to follow some guidlines which we follow accross every project we build, We created this guide to keep the code in our projects consistent so every developer can unite anytime without any hustle 

Our overarching goals are __conciseness__, __readability__ and __simplicity__.



## Inspiration

This style-guide is somewhat of a mash-up between the existing Kotlin language style guides, and a tutorial-readability focused Swift style-guide. The language guidance is drawn from: 

- The [Android Kotlin style guide](https://android.github.io/kotlin-guides/style.html)
- The [Kotlin Coding Conventions](https://kotlinlang.org/docs/reference/coding-conventions.html) 
- The [Android contributors style guide](https://source.android.com/source/code-style.html)
- The [Google Java Style Guide](https://google-styleguide.googlecode.com/svn/trunk/javaguide.html).
- The [Raywenderlich Guide](https://github.com/raywenderlich/kotlin-style-guide/blob/master/README.md).

## Android Studio Coding Style

It is possible to get Android Studio to adhere to these style guidelines, via a rather complex sequence of menus. To make it easier, we've provided a coding style that can be imported into Android Studio.

The file can be found [here](https://github.com/vinaysasalatti-android/kotlin-styleing-guide/blob/master/ktstyle.xml.zip).

To install the file, open Android Studio Settings and go to **Editor > Code Style > Kotlin**, then click the gear menu and choose **Import Scheme...**.

From now on, projects you create _should_ follow the correct style guidelines and similer package structurs .

## Project structure which we follow

we use package structure which is combination of package by layer, type and features
- [Package by type](https://github.com/vinaysasalatti-android/kotlin-styleing-guide/blob/master/Project%20structure.md#package-by-type)
- [Package by layer](https://github.com/vinaysasalatti-android/kotlin-styleing-guide/blob/master/Project%20structure.md#package-by-layer)
- [Package by feature](https://github.com/vinaysasalatti-android/kotlin-styleing-guide/blob/master/Project%20structure.md#package-by-feature)

The whole Project structure guidlines can he found here [Project structure which we follow](https://github.com/vinaysasalatti-android/kotlin-styleing-guide/blob/master/Project%20structure.md#project-structure-which-we-follow)

## Git Guidelines 
we would like to commit code more often so the big tasks can be broken in to pieces and committed stage wise, so we can drilldown development bugs easily on grass root levels, task based push will avoid mixup of more features in single commit which would keep commits history cleaner, following this give us advantages of reverting entire commit when unstable code surfaces, frequent commit eases development with less conflicts :]

### Git commit messages
Good commit messages have 3 critical benefits:

1. Help speed up the code review process
2. Help in writing good release notes 
3. Help future maintainers \(and your future self\) understand why a change was made, or what exactly a particular bug was

### Sample commit message

```text 
(syntax would be as below)
 main line (70 chars or less)
  - sub lines / related small bullets points if nessary(50 chars or less)
  - related collateral changes bullets points if nessary(50 chars or less)
  
(example would be as below)
-single line-
fix: Fixed issue with headerText going under status text (internal fixes which wont have tikets :])
fix: IN-753 - Changed date to UTC value

-multi line- 
Add: IN-749 - Create API to fetch Prom Details
     - Create Prom Response data class
     - Define API to fetch Prom details
```

* Main line start with words like “Add:”, “Update:”, and “Fix:”
* Main line should have a Jira ticket numbers associated with the task / subtask / story / bug - _eg_ - IN-674
* Main lines should be followed by a short note, never end with a period
* Sub lines can be some short details in bullet form (not mandatory to have one)
* The explanatory text isn’t required but encouraged, especially when a commit fixes a bug. It’s good practice to explain clearly why a certain issue was occurring and how the commit fixes it. 


## Table of Contents for our "Style Guide"

- [Nomenclature](#nomenclature)
  + [Packages](#packages)
  + [Classes & Interfaces](#classes--interfaces)
  + [Methods](#methods)
  + [Fields](#fields)
  + [Variables & Parameters](#variables--parameters)
  + [Misc](#misc)
- [Declarations](#declarations)
  + [Visibility Modifiers](#visibility-modifiers)
  + [Fields & Variables](#fields--variables)
  + [Classes](#classes)
  + [Data Type Objects](#data-type-objects)
  + [Enum Classes](#enum-classes)
- [Spacing](#spacing)
  + [Indentation](#indentation)
  + [Line Length](#line-length)
  + [Vertical Spacing](#vertical-spacing)
- [Brace Style](#brace-style)
- [When Statements](#when-statements)
- [Types](#types)
  + [Type Inference](#type-inference)
  + [Constants vs. Variables](#constants-vs-variables)
  + [Companion Objects](#companion-objects)
  + [Optionals](#optionals)
- [String constants, naming, and values](#String-constants-naming-and-values)
- [Arguments in Fragments and Activities](#Arguments-in-Fragments-and-Activities)
- [XML Guidance](#xml-guidance)



## Nomenclature

On the whole, naming should follow Java standards, as Kotlin is a JVM-compatible language.

### Packages

Package names are similar to Java: all __lower-case__, multiple words concatenated together, without hypens or underscores:

__BAD__:

```kotlin
com.orgnization.some_widget
```

__GOOD__:

```kotlin
com.orgnization.somewidget
```

### Classes & Interfaces

Written in __UpperCamelCase__. For example `ArcSlider`. 

### Methods

Written in __lowerCamelCase__. For example `setValue`.

### Fields

Generally, written in __lowerCamelCase__. 

Example field names:

```kotlin
class MyClass {
  var publicField: Int = 0
  val person = Person()
  private var privateField: Int?
}
```

Constant values in the companion object should be written in __uppercase__, with an underscore separating words:

```kotlin
companion object {
  const val THE_CONSTENT = 46
}
```

### Variables & Parameters

Written in __lowerCamelCase__.

Single character values must be avoided, except for temporary looping variables.

### Misc

In code, acronyms should be treated as words. For example:

__BAD:__

```kotlin
XMLHTTPRequest
URL: String? 
findPostByID
```
__GOOD:__

```kotlin
XmlHttpRequest
url: String
findPostById
```

## Declarations

### Visibility Modifiers

Only include visibility modifiers if you need something other than the default of public.

**BAD:**

```kotlin
public val wideOpenProperty = 1
private val myOwnPrivateProperty = "private"
```

**GOOD:**

```kotlin
val wideOpenProperty = 1
private val myOwnPrivateProperty = "private"
```

### Access Level Modifiers

Access level modifiers should be explicitly defined for classes, methods and member variables.

### Fields & Variables

Prefer single declaration per line.

__GOOD:__

```kotlin
username: String
twitterHandle: String
```

### Classes

Exactly one class per source file, although inner classes are encouraged where scoping appropriate.

### Data Type Objects

Prefer data classes for simple data holding objects.

__BAD:__

```kotlin
class Person(val name: String) {
  override fun toString() : String {
    return "Person(name=$name)"
  }
}
```

__GOOD:__

```kotlin
data class Person(val name: String)
```

### Enum Classes

Enum classes without methods may be formatted without line-breaks, as follows:

```kotlin
private enum CompassDirection { EAST, NORTH, WEST, SOUTH }
```

## Spacing

Spacing is especially important in raywenderlich.com code, as code needs to be easily readable as part of the tutorial. 

### Indentation

Indentation is using spaces - never tabs.

#### Blocks

Indentation for blocks uses 2 spaces (not the default 4):

__BAD:__

```kotlin
for (i in 0..9) {
    Log.i(TAG, "index=" + i)
}
```

__GOOD:__

```kotlin
for (i in 0..9) {
  Log.i(TAG, "index=" + i)
}
```

#### Line Wraps

Indentation for line wraps should use 4 spaces (not the default 8):

__BAD:__

```kotlin
val widget: CoolUiWidget =
        someIncrediblyLongExpression(that, reallyWouldNotFit, on, aSingle, line)
```

__GOOD:__

```kotlin
val widget: CoolUiWidget =
    someIncrediblyLongExpression(that, reallyWouldNotFit, on, aSingle, line)
```

### Line Length

Lines should be no longer than 100 characters long.


### Vertical Spacing

There should be exactly one blank line between methods to aid in visual clarity and organization. Whitespace within methods should separate functionality, but having too many sections in a method often means you should refactor into several methods.

## Comments

When they are needed, use comments to explain **why** a particular piece of code does something. Comments must be kept up-to-date or deleted.

Avoid block comments inline with code, as the code should be as self-documenting as possible. *Exception: This does not apply to those comments used to generate documentation.*

## Brace Style

Only trailing closing-braces are awarded their own line. All others appear the same line as preceding code:

__BAD:__

```kotlin
class MyClass
{
  fun doSomething()
  {
    if (someTest)
    {
      // ...
    }
    else
    {
      // ...
    }
  }
}
```

__GOOD:__

```kotlin
class MyClass {
  fun doSomething() {
    if (someTest) {
      // ...
    } else {
      // ...
    }
  }
}
```

Conditional statements are always required to be enclosed with braces, irrespective of the number of lines required.

__BAD:__

```kotlin
if (someTest)
  doSomething()
if (someTest) doSomethingElse()
```

__GOOD:__

```kotlin
if (someTest) {
  doSomething()
}
if (someTest) { doSomethingElse() }
```

## When Statements

Unlike `switch` statements in Java, `when` statements do not fall through. Separate cases using commas if they should be handled the same way. Always include the else case.

__BAD:__

```kotlin
when (anInput) {
  1 -> doSomethingForCaseOneOrTwo()
  2 -> doSomethingForCaseOneOrTwo()
  3 -> doSomethingForCaseThree()
}
```

__GOOD:__

```kotlin
when (anInput) {
  1, 2 -> doSomethingForCaseOneOrTwo()
  3 -> doSomethingForCaseThree()
  else -> println("No case satisfied")
}
```


## Types 

Always use Kotlin's native types when available. Kotlin is JVM-compatible so **[TODO: more info]**

### Type Inference

Type inference should be preferred where possible to explicitly declared types. 

__BAD:__

```kotlin
val something: MyType = MyType()
val meaningOfLife: Int = 46
```

__GOOD:__

```kotlin
val something = MyType()
val meaningOfLife = 42
```

### Constants vs. Variables 

Constants are defined using the `val` keyword, and variables with the `var` keyword. Always use `val` instead of `var` if the value of the variable will not change.

*Tip*: A good technique is to define everything using `val` and only change it to `var` if the compiler complains!

### Companion Objects

** TODO: A bunch of stuff about companion objects **

### Nullable Types

Declare variables and function return types as nullable with `?` where a `null` value is acceptable.

Use implicitly unwrapped types declared with `!!` only for instance variables that you know will be initialized before use, such as subviews that will be set up in `onCreate` for an Activity or `onCreateView` for a Fragment.

When naming nullable variables and parameters, avoid naming them like `nullableString` or `maybeView` since their nullability is already in the type declaration.

When accessing a nullable value, use the safe call operator if the value is only accessed once or if there are many nullables in the chain:

```kotlin
editText?.setText("foo")
```

## String constants, naming, and values

Many elements of the Android SDK such as `SharedPreferences`, `Bundle`, or `Intent` use a key-value pair approach so it's very likely that even for a small app you end up having to write a lot of String constants.

When using one of these components, you __must__ define the keys as a `static final` fields and they should be prefixed as indicated below.

| Element            | Field Name Prefix |
| -----------------  | ----------------- |
| SharedPreferences  | `PREF_`             |
| Bundle             | `BUNDLE_`           |
| Fragment Arguments | `ARGUMENT_`         |
| Intent Extra       | `EXTRA_`            |
| Intent Action      | `ACTION_`           |

Note that the arguments of a Fragment - `Fragment.getArguments()` - are also a Bundle. However, because this is a quite common use of Bundles, we define a different prefix for them.

Example:

```java
// Note the value of the field is the same as the name to avoid duplication issues
static final String PREF_EMAIL = "PREF_EMAIL";
static final String BUNDLE_AGE = "BUNDLE_AGE";
static final String ARGUMENT_USER_ID = "ARGUMENT_USER_ID";

// Intent-related items use full package name as value
static final String EXTRA_SURNAME = "com.myapp.extras.EXTRA_SURNAME";
static final String ACTION_OPEN_USER = "com.myapp.action.ACTION_OPEN_USER";
```
## Arguments in Fragments and Activities

When data is passed into an `Activity` or `Fragment` via an `Intent` or a `Bundle`, the keys for the different values __must__ follow the rules described in the section above.

When an `Activity` or `Fragment` expects arguments, it should provide a `public static` method that facilitates the creation of the relevant `Intent` or `Fragment`.

In the case of Activities the method is usually called `getStartIntent()`:

```java
public static Intent getStartIntent(Context context, User user) {
	Intent intent = new Intent(context, ThisActivity.class);
	intent.putParcelableExtra(EXTRA_USER, user);
	return intent;
}
```

For Fragments it is named `newInstance()` and handles the creation of the Fragment with the right arguments:

```java
public static UserFragment newInstance(User user) {
	UserFragment fragment = new UserFragment();
	Bundle args = new Bundle();
	args.putParcelable(ARGUMENT_USER, user);
	fragment.setArguments(args)
	return fragment;
}
```

__Note 1__: These methods should go at the top of the class before `onCreate()`.

__Note 2__: If we provide the methods described above, the keys for extras and arguments should be `private` because there is not need for them to be exposed outside the class.

## XML Guidance

Because the lack of XML namespaces, makes managing Android resources tedious. And causes things to grow out of control easily, especially in large projects.
So let’s introduce a simple scheme that will solve your pains.
 
  + easy lookup of any resource (autocomplete)
  + logical, predictable names
  + clean ordering of resources
  + strongly typed resources

### Basic principle

All resource names follow a simple convention.

![whatwheredescriptionsize](/assets/whatwheredescriptionsize.jpg)

Let’s first describe every element briefly. After the advantages, we’ll see how this applies to each resource type.

` <WHAT>`
- Indicate what the resource actually represents, often a standard Android view class. Limited options per resource type.(e.g. MainActivity -> activity)

` <WHERE>`
- Describe where it logically belongs in the app. Resources used in multiple screens use all, all others use the custom part of the Android view subclass they are in. (e.g. MainActivity -> main, ArticleDetailFragment -> articledetail)

`<DESCRIPTION>`
- Differentiate multiple elements in one screen.(e.g. title)

`<SIZE> (optional)`
- Either a precise size or size bucket. Optionally used for drawables and dimensions.(e.g. 24dp, small))

![resourcenaming_cheatsheet](/assets/resourcenaming_cheatsheet.png)

### Advantages

#### 1. Ordering of resources by screen
The WHERE part describes what screen a resource belongs to. Hence it is easy to get all IDs, drawables, dimensions,… for a particular screen.

#### 2. Strongly typed resource IDs
For resource IDs, the WHAT describes the class name of the xml element it belongs to. This makes is easy to what to cast your findViewById() calls to.

#### 3. Better resource organizing
File browsers/project navigator usually sort files alphabetically. This means layouts and drawables are grouped by their WHAT (activity, fragment,..) and WHERE prefix respectively. A simple Android Studio plugin/feature can now display these resources as if they were in their own folder.

#### 4. More efficient autocomplete
Because resource names are far more predictable, using the IDE’s autocomplete becomes even easier. Usually entering the WHAT or WHERE is sufficient to narrow autocomplete down to a limited set of options.

#### 5. No more name conflicts
Similar resources in different screens are either all or have a different WHERE. A fixed naming scheme avoids all naming collisions.

#### 6. Cleaner resource names
Overall all resources will be named more logical, causing a cleaner Android project.

#### 7. Tools support
This naming scheme could be easily supported by the Android Studio offering features such as: lint rules to enforce these names, refactoring support when you change a WHAT or WHERE, better resource visualisation in project view,…


### Layouts
Layouts are relatively simple, as there usually are only a few layouts per screen. Therefore the rule can be simplified to:

![layouts](/assets/layouts.png)

Where` <WHAT> `is one of the following:

| Prefix   | Usage   |
| ------------ | ------------ |
| activity   |  contentview for activity |
|  fragment  | view for a fragment  |
|  view  | inflated by a custom view  |
|  item  | layout used in list/recycler/gridview  |
|  layout  | layout reused using the include tag  |

##### Examples:

- **activity_main:** content view of the MainActivity
- **fragment_articledetail:** view for the ArticleDetailFragment
- **view_menu:** layout inflated by custom view class MenuView
- **item_article:** list item in ArticleRecyclerView
- **layout_actionbar_backbutton:** layout for an actionbar with a backbutton (too simple to be a customview)


### Strings

The `<WHAT>` part for Strings is irrelevant. So either we use `<WHERE>` to indicate where the string will be used:

![strings](/assets/strings.png)

or all if the string is reused throughout the app:

![strings](/assets/strings2.png)

##### Examples:

- **articledetail_title:** title of ArticleDetailFragment
- **feedback_explanation:** feedback explanation in FeedbackFragment
- **feedback_namehint:** hint of name field in FeedbackFragment
- **all_done:** generic “done” string

`<WHERE>` obviously is the same for all resources in the same view.


### Drawables

The `<WHAT>` part for Drawables is irrelevant. So either we use `<WHERE>` to indicate where the drawable will be used:

![drawables  ](/assets/drawables.png)

or all if the drawable is reused throughout the app:

![drawables  ](/assets/drawables2.png)

Optionally you can add a `<SIZE>` argument, which can be an actual size “24dp” or a size qualifier “small”.

##### Examples:

- **articledetail_placeholder:** placeholder in ArticleDetailFragment
- **all_infoicon:** generic info icon
- **all_infoicon_large:** large version of generic info icon
- **all_infoicon_24dp:** 24dp version of generic info icon


### IDs

For IDs, `<WHAT>` is the class name of the xml element it belongs to. Next is the screen the ID is in, followed by an optional description to distinguish similar elements in one screen.

![ids](/assets/ids.png)

##### Examples:

- **tablayout_main ->** TabLayout in MainActivity
- **imageview_menu_profile ->** profile image in custom MenuView
- **textview_articledetail_title ->** title TextView in ArticleDetailFragment


### Dimensions

Apps should only define a limited set of dimensions, which are constantly reused. This makes most dimensions all by default.

Therefore you should mostly use:

![dimensions](/assets/dimensions.png)

and optionally use the screen specific variant:

![dimensions](/assets/dimensions2.png)

Where `<WHAT>` is one of the following:

| Prefix   |  Usage  |
| ------------ | ------------ |
| width   |  width in dp |
|  height  |  height in dp |
| size   | if width == height  |
| margin   |  margin in dp |
| padding   | padding in dp  |
|elevation    | elevation in dp  |
|  keyline  | absolute keyline measured from view edge in dp  |
| textsize   | size of text in sp  |

Note that this list only contains the most used `<WHAT>`s. Other dimensions qualifiers like: rotation, scale,… are usually only used in drawables and as such less reused.

##### Examples:

- **height_toolbar:** height of all toolbars
- **keyline_listtext:** listitem text is aligned at this keyline
- **textsize_medium:** medium size of all text
- **size_menu_icon:** size of icons in menu
- **height_menu_profileimage:** height of profile image in menu

# License

```
Copyright 2020.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
```


