# Project structure which we follow

we use package structure which is combination of package by layer, type and features.

“Splitting packages by layers alone is just like splitting co-workers by profession instead of splitting them into organization teams.”


## Package by type

We put all the classes of the same type in a folder named after the type. I’ve seen (and been involved with) projects where all the interfaces, because they are interfaces, are put together in an interfaces package. Then all the exceptions no matter where they are used, are in , you guessed it, exceptions package. The thinking goes, “I’m gonna have to work on an exception for this feature, let’s open the exceptions folder and find it there”.

## Package by layer

We have the UI layer, the Network layer, the Database layer and the dreaded Model layer. The class organization patterns, sometimes erroneously referred to as architectures, such as MVC, MVP and their siblings, often go this way.

## package by feature

It is an organizational style in which you group your code by functionalities rather than by layers. With package by feature, items that work closely together are placed next to one another, and that makes navigating through the code a lot easier.

Since all of these has there own advantages and pain points so using all of them combined would leverage us in the best package structure practise , as we get the edge of all the three types and reduce the cons of using any of the indivisual approch only .



```
├── App.kt
├── base
├── data
├── di
├── eventbus
├── everion
├── ihealth
├── interfaces
├── notification
├── ui
└── utils

```
## Base package 
```
├── base
│   ├── BaseActivity.kt
│   ├── BaseFragment.kt
│   └── BaseViewModel.kt
```
contains all the base classes of the project , which we use majorly for the Localisation support and all the common stuff which can be piled 

## Data package 
```
├── data
│   ├── local
│   │   ├── AppDB.kt
│   │   ├── dao
│   │   │   └──BioVotionDao.kt
│   │   └── entity
│   │       └──BioVotionVitalObject.kt
│   ├── model
│   │   ├── Menu.kt
│   │   ├── request
│   │   │   └── LogInRequestObj.kt
│   │   └── response
│   │       └── LogInResponseObj.kt
│   ├── remote
│   │   ├── BaseDataSource.kt
│   │   ├── auth
│   │       ├── AuthAPI.kt
│   │       └── AuthService.kt
│   └── repository
│       └── auth
│           └── AuthRepository.kt

```
this is the data layer , which interacts with the data from local and the remote data source , which is grouped as  Local ,Remote, Model, Repository 

usuall we have all the database related setup , DAO’s and data entities (usually Room is used as of now for DB) in the local package , 

then we have all the data model classes used for holding data and model classes which are used for makeing request objects and response objects for all the network operations throught the application in the model package ,

 and all the API calls and API services which interact with remote servers will be added in the remote package where each service is distributed in to a different package ,

 and finally we have the repository where the data is fetched from remote or local is decided and packeged depending on the service modules which it serves 



## DI package 
```
├── di
│   └── AppModule.kt

```
The di stands for Dependency Injection. It is a package that contains the AppComponent and general modules that do not relate to specific screens (for example, ApiModule, AppModule, AppContextModule, ExecutorsModule, etc.).Currently we are hilt for the DI in the projects 


## EventBus package 
```
├── eventbus
│   └── ForcedLogOutEvent.kt

```
this is package contains all the evernts we have created for the application , basically events are like callback interface without the boilerplate code , we use EventBuS for this 

## Everion package 
```
├── everion
│   ├── EverionManager.java
│   ├── EverionUtils.java
│   ├── listeners
│   │   └── EverionStatusListener.kt
│   ├── model
│   │   └── VitalRecordRequestObj.java
│   └── service
│       └── DeviceConnectionService.kt

```
## Ihealth package 
```
├── ihealth
│   ├── IHealthConnectionStatus.kt
│   ├── IHealthManager.kt
│   └── ihealthutils
│       ├── IHealthBPCallback.kt
│       └── IHealthWeightCallback.kt

```
IHEATH / Everion packages are to cater the devices which are used in the applications , any devices which will be integrated would be in there own seperate 

## Notification package 
```
├── notification
│   ├── NotificationChannelConstants.kt
│   └── NotificationServiceHelper.kt

```
As the name says contains all the things related to notifications , like services , builders and anything and everything related to notifications .

## UI package 
```
├── ui
│   ├── authentication
│   │   ├── AuthenticationActivity.kt
│   │   ├── AuthenticationViewModel.kt
│   │   ├── changepassword
│   │   │   ├── ChangePasswordFragment.kt
│   │   │   └── ChangePwdViewModel.kt
│   │   ├── forgotpassword
│   │   │   ├── ForgotPasswordDialogFragment.kt
│   │   │   └── ForgotPasswordViewModel.kt
│   │   └── login
│   │       ├── LoginFragment.kt
│   │       └── LoginViewModel.kt

```
This package basically uses package by feature internally , every sub package is usually a feature , and that sub package contains everything associated to that feature , many times these features package can contain many sub level features also , and this entire package contains anyting and everuthing related to user interface related to any perticuler feature .

## Utils package 
```
└── utils
    ├── AppConstants.kt
    ├── AppPreffs.kt
    ├── DateTimeUtil.kt
    ├── KeyboardUtils.kt
    ├── LocaleHelper.kt
    ├── RootUtil.java
    ├── customviews
    │   └── ObservableWebView.kt
    ├── extension
    │   └──  EditTextExtension.kt
    ├── networkutils
    │   ├── ApiErrorExchange.kt
    │   ├── CustomInterceptor.kt
    │   ├── DataAccessStrategy.kt
    │   ├── ErrorConstants.kt
    │   ├── Resource.kt
    │   └── TokenAuthenticator.kt
    └── validations
        ├── BloodPressureUtils.kt
        ├── ValidationUtils.kt
        └── WeightUtils.kt

```
This package contains all the common utility calsses and methods required by the entire application , usually like a toolbox for the whole project , can contain multiple utility packages which cater diffrent streams pr components like network utils, extention utils etc.

