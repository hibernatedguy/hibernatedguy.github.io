---
layout: post
title: Gmail SMTP with PHP using PHPMailer package
description: Gmail SMTP with PHP using PHPMailer package.
summary: Gmail SMTP with PHP using PHPMailer package.
tags: php
minute: 7
---

<p>
Yet another PHP problem to solve. <br />
One of my friend asked me to help him out with PHP contact form with Gmail SMTP configuration to send out the leads generated on the website.
</p>

<h4>1. Change settings in your Gmail to work with SMTP
</h4>

<ol>
<li>Login to your gmail account</li>
<li>Go to Manage your google account</li>
<li>Go to Security</li>
<li>Look for less secure app and Turn on the less secure app access</li>
</ol>

or&nbsp;Visit <a href="https://myaccount.google.com/lesssecureapps" rel="nofollow" target="_blank">Google Account Less Secure Apps</a>
<br /> 
<br /> 
<h4>2. Setting up PHPMailer</h4>

<p>
While I was looking for this solution, I came across PHPMailer ( The classic email sending library ).<br />
One of the most important and recommended way to install PHPMailer is composer.<br />
</p>

<p>
To setup composer, please follow the steps at <a href="https://getcomposer.org/download/" rel="nofollow" target="_blank">Download Composer</a>.<br />
To setup PHPMailer use the below command and detail documentation can be found at <a href="https://github.com/PHPMailer/PHPMailer" rel="nofollow" target="_blank">PHPMailer Github Link</a>.
</p>
<p>
Create a folder <i>smtp_php_test</i>.
</p>
<pre><code>mkdir smtp_php_test
cd smtp_php_test
</code></pre>

Run the below command on your terminal/command prompt. <br/>This command will create vendor folder in your smtp_php_test folder with phpmailer package.
<pre><code>composer require phpmailer/phpmailer</code></pre>

<p>After doing so many RnD I came to this final code snippet which works well.</p>
  Create a file smtp_test.php. You can use your favorite text editor to create this file.</p>
<pre><code>nano smtp_test.php</code></pre>
<p>
Add below snippet to <i>smtp_test.php</i> file.
</p>
<pre><code>&lt;?php session_start();
//Import PHPMailer classes into the global namespace
//These must be at the top of your script, not inside a function
use PHPMailer\PHPMailer\PHPMailer;
use PHPMailer\PHPMailer\SMTP;
use PHPMailer\PHPMailer\Exception;

//Generated by composer
//Load Composer's autoloader
require 'vendor/autoload.php';

try{	
<span>&nbsp;&nbsp; &nbsp;</span>//change with your emailID [ FROM ] and name
<span>&nbsp;&nbsp; &nbsp;</span>$mail_to = '[your-sender-email-address]';
<span>&nbsp;&nbsp; &nbsp;</span>$mail_to_name = '[your-sender-username]';

<span>&nbsp;&nbsp; &nbsp;</span>//php mailer
<span>&nbsp;&nbsp; &nbsp;</span>$mail = new PHPMailer(true);

<span>&nbsp;&nbsp; &nbsp;</span>//smtp settings and credentials
<span>&nbsp;&nbsp; &nbsp;</span>$mail-&gt;SMTPDebug = 2;

<span>&nbsp;&nbsp; &nbsp;</span>$mail-&gt;isSMTP();
<span>&nbsp;&nbsp; &nbsp;</span>$mail-&gt;Host = 'smtp.gmail.com';
<span>&nbsp;&nbsp; &nbsp;</span>$mail-&gt;SMTPAuth = true;
<span>&nbsp;&nbsp; &nbsp;</span>$mail-&gt;Username = $mail_to;
<span>&nbsp;&nbsp; &nbsp;</span>$mail-&gt;Password = '[replace-with-your-superduper-password]';
<span>&nbsp;&nbsp; &nbsp;</span>$mail-&gt;SMTPSecure = 'tls';
<span>&nbsp;&nbsp; &nbsp;</span>$mail-&gt;Port = 587;
	
<span>&nbsp;&nbsp; &nbsp;</span>//recipients - from
<span>&nbsp;&nbsp; &nbsp;</span>$mail-&gt;setFrom($mail_to, $mail_to_name);

<span>&nbsp;&nbsp; &nbsp;</span>//recipients - to - send self email.
<span>&nbsp;&nbsp; &nbsp;</span>$mail-&gt;addAddress($mail_to);
<span>&nbsp;&nbsp; &nbsp;</span>$mail-&gt;addReplyTo($mail_to);
					
<span>&nbsp;&nbsp; &nbsp;</span>//content
<span>&nbsp;&nbsp; &nbsp;</span>$mail-&gt;isHTML(true);
<span>&nbsp;&nbsp; &nbsp;</span>$mail-&gt;Subject = $subject;
<span>&nbsp;&nbsp; &nbsp;</span>$mail-&gt;Body=$body_message;

<span>&nbsp;&nbsp; &nbsp;</span>//send email
<span>&nbsp;&nbsp; &nbsp;</span>$mail-&gt;send();
<span>&nbsp;&nbsp; &nbsp;</span>echo 'Message has been sent';
} catch (Exception $e){
<span>&nbsp;&nbsp; &nbsp;</span>echo 'Message could not be sent. Error: ', $mail-&gt;ErrorInfo;
}
?&gt;
</code></pre>
<p>
Run and test your PHP code.
</p>