**WebAPI**
0098sms.com Api Codes for devs

معرفی API و WebService سامانه پیامکی  [0098sms](https://0098sms.com)

سامانه 0098sms با بیش از 15 سال سابقه و 350 هزار کاربر یکی از جامع ترین سامانه های ارسال پیامک و مشتری مداری است.

[ثبت نام در سامانه 0098sms برای تست و ارسال](https://0098sms.com)

پس از ثبت نام، ارسال شما از طریق لینک و یا وب سرویس ممکن خواهد شد.

برای استفاده از لینک و یا وب سرویس نیازی به نصب ماژولی ندارید. در  [سامانه 0098sms](https://0098sms.com) ثبت نام کنید. سپس شماره احتصاصی خود را برای ارسال فعال نمایید.

**نحوه استفاده از لینک برای ارسال پیامک:**
~~~
username = "your username";
password = "your password";
to = "destination number";
from = "your panel number";
text = "text to send"; 
url = basic url + "username"=username&"password"=password&"from"=from&"to"=to&"text"=text;
WebRequest request = HttpWebRequest.Create(url);  
WebResponse response = request.GetResponse();  
StreamReader reader = new StreamReader(response.GetResponseStream());  
string urlResponse = reader.ReadToEnd(); // it takes the response from your url. now you can use as your need  

~~~
**نحوه استفاده از وب سرویس:**

برای استفاده از وب سرویس شما کافی است که پس از ثبت نام، از طریق آدرس موجود در پنل، وب سرویس ارسال را به پروژه خود اضافه کنید.


<hr/>

**اطلاعات بیشتر**

برای آشنایی بیشتر و دریافت راهنمای کامل وب سرویس و آشنایی با پارامتر های ورودی، خروجی و همچنین پاسخ ها به
سامانه 0098sms مراجعه و به صفحه api و وب سرویس وارد شوید.

<hr/>

**متدهای ارسال:**

**1- ارسال تکی:** برای ارسال تکی در زمان فراخوانی از متد SendSMS استفاده کنید.

**Asp.net Sample Code**
~~~
ServiceReference1.ServiceSoapClient ssc = new ServiceReference1.ServiceSoapClient(); 
string username = "username";
string password = "password";
string smstext = "smstext"; 
string mobileno = "091XXXXXXXX";
string panelno = "3000XXXX";
string responsecode = ssc.SendSMS(username, password, smstext, mobileno, panelno);
~~~
**Php Sample Code**
~~~
Enable extension=php_soap.dll

<?php
// turn off the WSDL cache
ini_set("soap.wsdl_cache_enabled", "0");
$sms_client = new SoapClient('basic WebService url', array('encoding'=>'UTF-8'));
$parameters['username'] = "username...";
$parameters['password'] = "password...";
$parameters['mobileno'] = "0912...";
$parameters['pnlno'] = "3000...";
$parameters['text'] = "test";
$parameters['isflash'] =false;

echo $sms_client->SendSMS($parameters)->SendSMSResult;
?>
~~~
**2- ارسال پیامک با قابلیت تنظیم تاریخ و زمان:** برای ارسال پیامک تکی با قابلیت تنظیم تاریخ و زمان از متد SendSMSWithTime استفاده کنید.

**Asp.net Sample Code**
~~~
ServiceReference1.ServiceSoapClient ssc = new ServiceReference1.ServiceSoapClient(); 
string username = "username";
string password = "password";
string smstext = "smstext"; 
string mobileno = "091XXXXXXXX";
string panelno = "3000XXXX";
string timestamp = " 1658939130";
string responsecode = ssc.SendSMSwithtime(username, password, smstext, mobileno, panelno , timestamp);
~~~
**Php Sample Code**
~~~
Enable extension=php_soap.dll
<?php
// turn off the WSDL cache
ini_set("soap.wsdl_cache_enabled", "0");
$sms_client = new SoapClient('basic WebService url', array('encoding'=>'UTF-8'));
$parameters['username'] = "username...";
$parameters['password'] = "password...";
$parameters['mobileno'] = "0912...";
$parameters['pnlno'] = "3000...";
$parameters['text'] = "test";
$parameters['timestamp'] = "1658939130";
$parameters['isflash'] =false;
echo $sms_client-> SendSMSwithtime($parameters)->SendSMSWithTimeResult;
?>
~~~
**3- ارسال پیامک تکی با قابلیت دریافت شناسه پیامک برای دریافت وضعیت:** برای ارسال پیامک تکی با قابلیت دریافت شناسه پیامک برای دریافت وضعیت از متد SendSMSWithID استفاده کنید. (خروجی این تابع در صورت موفقیت آمیز بودن، شناسه پیامک شماست)

**Asp.net Sample Code**
~~~
ServiceReference1.ServiceSoapClient ssc = new ServiceReference1.ServiceSoapClient(); 
string username = "username";
string password = "password";
string smstext = "smstext"; 
string mobileno = "091XXXXXXXX";
string panelno = "3000XXXX";
string responsecode = ssc.SendSMSWithID (username, password, smstext, mobileno, panelno);
~~~
**Php Sample Code**
~~~
Enable extension=php_soap.dll
<?php
// turn off the WSDL cache
ini_set("soap.wsdl_cache_enabled", "0");
$sms_client = new SoapClient('basic WebService url', array('encoding'=>'UTF-8'));
$parameters['username'] = "username...";
$parameters['password'] = "password...";
$parameters['mobileno'] = "0912...";
$parameters['pnlno'] = "3000...";
$parameters['text'] = "test";
$parameters['isflash'] =false;

echo $sms_client->SendSMSWithID($parameters)->SendSMSWithIDResult;
?>
~~~
**4- دریافت وضعیت پیامک (ارسال شده از طریق وب سرویس و دارا بودن شناسه پیامک):** برای دریافت وضعیت پیامک (ارسال شده از طریق وب سرویس و دارا بودن شناسه پیامک) از تابع smsdeliveryState استفاده نمایید.

**Asp.net Sample Code**
~~~
ServiceReference1.ServiceSoapClient ss = new ServiceReference1.ServiceSoapClient(); 
string username = "username";
string password = "password";
string smsid = "XXXXXXXXXX";
string deliverystate = ss.smsdeliveryState(username, password, smsid);
~~~
**Php Sample Code**
~~~
Enable extension=php_soap.dll
<?php
// turn off the WSDL cache
ini_set("soap.wsdl_cache_enabled", "0");
$sms_client = new SoapClient('basic WebService url', array('encoding'=>'UTF-8'));
$parameters['username'] = "username...";
$parameters['password'] = "password...";
$parameters['smsid'] = "xxxxxxxxxx";
$parameters['isflash'] =false;
echo $sms_client-> smsdeliveryState($parameters)-> smsdeliveryStateResult;
?>
~~~
**5- دریافت مانده موجودی پیامک:** برای دریافت مانده موجودی پیامک از تابع RemainSms استفاده نمایید.

**Asp.net Sample Code**
~~~
ServiceReference1.ServiceSoapClient ss = new ServiceReference1.ServiceSoapClient(); 
string username = "username";
string password = "password";
string remain = ss.RemainSms(username, password);
~~~
Php Sample Code
~~~
Enable extension=php_soap.dll
<?php
// turn off the WSDL cache
ini_set("soap.wsdl_cache_enabled", "0");
$sms_client = new SoapClient('basic WebService url', array('encoding'=>'UTF-8'));
$parameters['username'] = "username...";
$parameters['password'] = "password...";
$parameters['isflash'] =false;
echo $sms_client-> RemainSms($parameters)-> remainResult;
?>
~~~
