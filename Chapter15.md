 # Mail
* If you’re using Mailgun, you’ll want to bring in Symfony’s Mailgun Mailer
and its HTTP client

```
composer require symfony/mailgun-mailer \
 symfony/http-client

```


* If you’re using Postmark, you’ll pull in Symfony’s Postmark Mailer and its
HTTP client
* https://postmarkapp.com/developer
```
composer require symfony/postmark-mailer \
 symfony/http-client
```

* if you use the SES driver, you’ll want to pull in the AWS SDK:

```
composer require aws/aws-sdk-php

```
* make a mailable

```
php artisan make:mail Name
```

```
class AssignmentCreated extends Mailable
{
 use Queueable, SerializesModels;
 public function __construct()
 {

 }

 public function envelope(): Envelope

 {

 return new Envelope(
 subject: 'Assignment Created',

 );

 }


 public function content(): Content
 {

 return new Content(
 view: 'view.name',

 );

 }

 public function attachments(): array

 {

 return [];  //if want to attach any files to the mail

 }
}

```

*  You can also customize some other details of your mail, like the CC
and BCC, as part of the inline call chain.

```
// With CC/BCC/etc.
Mail::to($user1))
 ->cc($user2)
 ->bcc($user3)
 ->send($mail);

```


* Attaching Files and Inlining Images

```
public function attachments(): array
{
 return [
 Attachment::fromPath('/absolute/path/to/file'),
 ];
}
 
public function attachments(): array
{
 return [
 
 Attachment::fromStorage('/path/to/file'),
 
 Attachment::fromStorageDisk('s3', '/path/to/file'),
 ];
}


public function attachments(): array
{
 return [
 Attachment::fromData(fn () => file_get_contents($this->pdf), 'whitepaper.pdf'
 ->withMime('application/pdf'),
];
}
```
* Create Markdown 

```
php artisan make:mail Markdown

```

Ex :-

```
 

class MarkdownMail extends Mailable
{
    use Queueable, SerializesModels;

    public function build()
    {
        return $this->markdown('emails.markdown.mail')
                    ->subject('Your Subject Here')
                    ->with([
                        'data' => 'Some additional data',
                    ]);
    }
}

```
* Create a Resource Markdown 
```
@component('mail::message')
# Introduction

The body of your message.

@component('mail::button', ['url' => ''])
Button Text
@endcomponent

Thanks,<br>
{{ config('app.name') }}
@endcomponent


```



* Queues in Laravel provide a way to defer the processing of a time-consuming task, such as sending emails or processing uploaded files, to improve application performance and responsiveness. By using queues


* Mailtrap is a service for capturing and inspecting emails in development
environments. You send your mail to the Mailtrap servers via SMTP, but
instead of sending those emails off to the intended recipients, Mailtrap
captures them all and provides you with a web-based email client for inspecting them, regardless of which email address is in the to field

```

```
 








