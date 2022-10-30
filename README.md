
# Laravel Multi Sms Methods
Laravel Package For Sms Methods Multi Methods Usage.
## 🚀 About Me
I'm a Full-stack Developer with more than 6 years of a unique experience, I'm a self-learner and specialized in applying the best practices to design and implement scalable, concurrent, flexible, and robust software solutions, with a healthy focus on the expected business outcomes, Always I seek to gain new skills and grow up my knowledge.


## Supported Methods
- [x]  [SMS BOX](https://www.smsbox.com)
- [x]  [TWILIO](https://www.twilio.com)
- [ ]  Others On The Way...

## Features

- Send Single Sms
- Send Bulk Sms
- Check Sms Status
- Get Account Balance


## Installation

You Can Install Via Composer
```bash
composer require vectoor/laravel-multi-sms-methods
```


## Publish

You Should Publish Config File To Set Method Credentials
```bash
php artisan vendor:publish --provider="Vector\LaravelMultiSmsMethods\Providers\SmsServiceProvider"
```


## Config
Example Of Config File
```
<?php

return [
    /*
    |--------------------------------------------------------------------------
    | Sms Available Methods
    |--------------------------------------------------------------------------
    / @author Vector <mo.khaled.yousef@gmail.com>
    | Here are each of the Available sms Methods
    |
    */

    "enable_send_sms" => env('ENABLE_SEND_SMS', false), //Enable or Disable Sms
    'methods' => [
        /*
           |--------------------------------------------------------------------------
           | Sms Box Connection
           |--------------------------------------------------------------------------
           |
           | Here are credentials for sms Box gateway.
           |
           */
        'smsbox' => [
            'username' => env('SMSBOX_USERNAME'),
            'password' => env('SMSBOX_PASSWORD'),
            'gateway_id' => env('SMSBOX_GATWAY_ID'),
            'sender_id' => env('SMSBOX_SENDER_ID'),
        ],
          'twilio' => [
            'account_sid' => env('TWILIO_ACCOUNT_SID'),
            'auth_token' => env('TWILIO_AUTH_TOKEN'),
            'sms_phone_number' => env('TWILIO_SMS_PHONE_NUMBER'),
            'schedule_messaging_service_sid' => env('TWILIO_SCHEDULE_MESSAGING_SERVICE_SID'),
            'whatsapp_phone_number' => env('TWILIO_WHATSAPP_PHONE_NUMBER'),
        ],
    ]

];

```

## Facade Usage
Use Sms Facade

```bash
use Vector\LaravelMultiSmsMethods\Facade\Sms;
```
# Usage/Examples
## Request
### Sms Box
#### To Send Single Sms
```bash
  Sms::driver('smsbox')->sendSms($mobileNumber,$message);
```
| Variable        | Type     | Description                |
| :--------       | :------- | :------------------------- |
| `$mobileNumber` | `string` | **Required**. Is String Of Mobile Number With Country Code |
| `$message`      | `string` | **Required**. Is String Of Message Content |


#### To Send Schedule Sms
```bash
  Sms::driver('smsbox')->sendScheduleSms($mobileNumber,$message,$scheduleDate);
```
| Variable        | Type     | Description                |
| :--------       | :------- | :------------------------- |
| `$mobileNumber` | `string` | **Required**. Is String Of Mobile Number With Country Code |
| `$message`      | `string` | **Required**. Is String Of Message Content |
| `$scheduleDate`  | `date`   | **Required**. schedule Date If You Want To schedule Message |


#### To Send Multi Sms
```bash
  Sms::driver('smsbox')->sendMultiSms($mobileNumber,$message);
```

| Variable        | Type     | Description                |
| :--------       | :------- | :------------------------- |
| `$mobileNumbers` | `Array`  | **Required**. Is Array Of Mobile Numbers With Country Code |
| `$message`      | `string`  | **Required**. Is String Of Message Content |


### Twilio
#### To Send Single Sms
```bash
  Sms::driver('twilio')->sendSms($mobileNumber,$message);
```
| Variable        | Type     | Description                |
| :--------       | :------- | :------------------------- |
| `$mobileNumber` | `string` | **Required**. Is String Of Mobile Number With Country Code |
| `$message`      | `string` | **Required**. Is String Of Message Content |
#### To Send Multi Sms
```bash
  Sms::driver('twilio')->sendMultiSms($mobileNumber,$message);
```

| Variable        | Type     | Description                |
| :--------       | :------- | :------------------------- |
| `$mobileNumbers` | `Array`  | **Required**. Is Array Of Mobile Numbers With Country Code |
| `$message`      | `string`  | **Required**. Is String Of Message Content |

#### To Send Schedule Sms
```bash
  Sms::driver('twilio')->sendScheduleSms($mobileNumber,$message,$scheduleDate);
```
| Variable        | Type     | Description                                                     |
| :--------       | :------- |:----------------------------------------------------------------|
| `$mobileNumber` | `string` | **Required**. Is String Of Mobile Number With Country Code      |
| `$message`      | `string` | **Required**. Is String Of Message Content                      |
| `$scheduleDate`  | `date`   | **Required**. schedule Date If You Want To schedule Message ex  "2022-10-29T20:36:27Z" |

#### To Send Whatsapp Message
```bash
  Sms::driver('twilio')->sendWhatsappMessage($mobileNumber,$message);
```

| Variable        | Type     | Description                |
| :--------       | :------- | :------------------------- |
| `$mobileNumber` | `string` | **Required**. Is String Of Mobile Number With Country Code |
| `$message`      | `string` | **Required**. Is String Of Message Content |

#### To Get Sms Information
```bash
  Sms::driver('twilio')->getSmsDetails($messageID);
```

| Variable        | Type     | Description                     |
| :--------       | :------- |:--------------------------------|
| `$messageID` | `string` | **Required**. Id Of The Message |

## Response
### Example
```bash
  array:4 [
  "code" => 200
  "success" => true
  "message" => "Message Send Successfully"
  "data" => array:5 [
    "Message" => "Message Send Successfully"
    "Result" => "true"
    "NetPoints" => "4995.600"
    "messageId" => "79539c54-XXXX-XXXX-XXXX-2db9244b1969"
    "RejectedNumbers" => []
  ]
]
```
| Variable        | Type     | Description                |
| :--------       | :------- | :------------------------- |
| `code`          | `integer` | Response Code OF The Sent Api |
| `message`       | `string`  | The Response Message From Api |
| `success`       | `bool`    | The Response Status (If Success Or Not)  |
| `data`          | `array`   | The Full Response From Api   |


## Authors

- [@Vector](https://github.com/vect0o0r)


## 🔗 Links
[![portfolio](https://img.shields.io/badge/my_portfolio-000?style=for-the-badge&logo=ko-fi&logoColor=white)](https://dev-vector.com)
[![linkedin](https://img.shields.io/badge/linkedin-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/mohammed-khaled-yousef/)


## License

The Laravel SMS Gateway package is open-sourced software licensed under the [MIT license](https://github.com/vect0o0r/laravel-multi-sms-methods/blob/master/LICENSE).


## Support

For support, email mo.khaled.yousef@gmail.com .

