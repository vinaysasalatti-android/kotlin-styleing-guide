# Project structure

we use package structure which is combination of package by layer, type and features.

“Splitting packages by layers alone is just like splitting co-workers by profession instead of splitting them into organization teams.”


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

## DI package 
```
├── di
│   └── AppModule.kt

```

## EventBus package 
```
├── eventbus
│   └── ForcedLogOutEvent.kt

```
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
## Notification package 
```
├── notification
│   ├── NotificationChannelConstants.kt
│   └── NotificationServiceHelper.kt

```

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

