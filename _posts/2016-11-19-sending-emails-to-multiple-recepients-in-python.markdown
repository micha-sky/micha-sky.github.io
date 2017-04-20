---
layout: post
title:  "sending emails to multiple recepients in python"
date:   2016-11-19 10:04:58 +0200
categories: development
---

	

You need to understand the difference between the visible address of an email, and the delivery.

msg["To"] is essentially what is printed on the letter. It doesn't actually have any effect. Except that your email client, just like the regular post officer, will assume that this is who you want to send the email to.

The actual delivery however can work quite different. So you can drop the email (or a copy) into the post box of someone completely different.

There are various reasons for this. For example forwarding. The To: header field doesn't change on forwarding, however the email is dropped into a different mailbox.

The smtp.sendmail command now takes care of the actual delivery. email.Message is the contents of the letter only, not the delivery.

In low-level SMTP, you need to give the receipients one-by-one, which is why a list of adresses (not including names!) is the sensible API.

For the header, it can also contain for example the name, e.g. To: First Last <email@addr.tld>, Other User <other@mail.tld>. Your code example therefore is not recommended, as it will fail delivering this mail, since just by splitting it on , you still not not have the valid adresses!

following piece of code will allow you to send email with attachments to multiple recepients:

{% highlight python %}
def send_gmail(recipients_list, msg_text, fromaddr='from_email@gmail.com', subject="", attachment_path_list=None):

    s = smtplib.SMTP('smtp.gmail.com:587')
    s.starttls()
    s.login('gmail_login', 'gmail_password')
    s.set_debuglevel(1)
    msg = MIMEMultipart()
    sender = fromaddr

    msg['Subject'] = subject
    if fromaddr is not None:
        msg['From'] = sender
    msg['To'] = "recepient@mail.com"
    msg['Cc'] = ",".join(recipients_list)
    if attachment_path_list is not None:
        for each_file_path in attachment_path_list:
            try:
                file_name = each_file_path.split("/")[-1]
                part = MIMEBase('application', "octet-stream")
                part.set_payload(open(each_file_path, "rb").read())

                Encoders.encode_base64(part)
                part.add_header('Content-Disposition', 'attachment', filename=file_name)
                msg.attach(part)
            except:
                print "could not attach file"
    msg.attach(MIMEText(msg_text, 'html'))
    s.sendmail(sender, recipients_list, msg.as_string())
{% endhighlight %}
