import smtplib
from email.mime.text import MIMEText
from email.mime.multipart import MIMEMultipart

# Email account credentials
smtp_server = 'smtp.gmail.com'
smtp_port = 587  # TLS
email_user = 'your-email@gmail.com'
email_password = 'your-app-password'  # Use an app password if 2FA is enabled

# Email content
body = 'This is a test email sent from Python!'

# Number of times to send the email
num_times = 5

# Connect and send email
for i in range(num_times):
    # Update the subject with the current iteration number
    subject = f'Test Email #{i + 1}'
    
    # Create MIME object
    message = MIMEMultipart()
    message['From'] = email_user
    message['To'] = 'recipient-email@example.com'
    message['Subject'] = subject
    
    # Attach the body with the message
    message.attach(MIMEText(body, 'plain'))
    
    try:
        with smtplib.SMTP(smtp_server, smtp_port) as server:
            server.starttls()  # Upgrade the connection to a secure encrypted SSL/TLS connection
            server.login(email_user, email_password)
            server.send_message(message)
        print(f'{i + 1} Email sent successfully with subject "{subject}"!')
    except smtplib.SMTPAuthenticationError:
        print('Authentication failed. Check your email and password.')
        break  # Exit loop if authentication fails
    except smtplib.SMTPException as e:
        print(f'Error sending email: {e}')
        break  # Exit loop if there's an error sending the email
