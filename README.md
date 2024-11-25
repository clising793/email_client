# AWS Lambda Function Node Project

This AWS Lambda function project efficiently manages email operations, enabling users to send, retrieve, delete, and save emails using SMTP and IMAP protocols.

## Sending Email API:

- Endpoint: https://d6aljed0n5.execute-api.eu-west-1.amazonaws.com/v1/send-email

- Payload:

    ```json
    {
      "smtpCredentials": {
        "host": "*",
        "port": 587,
        "secure": false,
        "auth": {
          "user": "source_email",
          "pass": "*"
        }
      },
      "mailOptions": {
        "from": "source_email",
        "to": [
          "des_email_1",
          "des_email_2"
        ],
        "cc": [
          "cc_email_1",
          "cc_email_2"
        ],
        "subject": "Hello from SendGrid!",
        "text": "This is a test email using SendGrid API in Node.js.",
        "html": "<strong>This is a test email using SendGrid API in Node.js.</strong>",
        "attachments": [
          {
            "filename": "test.txt",
            "content": "VGhpcyBpcyBhdHRhY2htZW50IHRlc3Qu",
            "encoding": "base64"
          }
        ]
      }
    }
    ```

  ```json
  {
    "smtpCredentials": {
      "host": "smtp.gmail.com",
      "port": "587",
      "secure": false,
      "auth": {
        "user": "source_email",
        "accessToken": "*",
        "refreshToken": "*",
        "type": "OAuth2"
      }
    },
    "mailOptions": {}
  }
  ```

## Retrieving Email API:

- Endpoint: https://d6aljed0n5.execute-api.eu-west-1.amazonaws.com/v1/retrieve-emails
- Payload:

  ```json
  {
    "smtpCredentials": {
      "host": "*",
      "port": 993,
      "secure": true,
      "auth": {
        "user": "*",
        "pass": "*"
      }
    },
    "path": "INBOX",
    "page": 1,
    "pageSize": 10
  }
  ```
  ```json
  {
    "smtpCredentials": {
      "host": "imap.gmail.com",
      "port": 993,
      "secure": true,
      "auth": {
        "user": "*",
        "accessToken": "*",
        "refreshToken": "*",
        "type": "OAuth2"
      }
    },
    "path": "INBOX",
    "page": 1,
    "pageSize": 10
  }
  ```

## Saving emails as drafts

- Endpoint: https://d6aljed0n5.execute-api.eu-west-1.amazonaws.com/v1/save-to-draft
- Payload:
  ```json
  {
    "smtpCredentials": {
      "host": "*",
      "port": 993,
      "secure": true,
      "auth": {
        "user": "*",
        "pass": "*"
      }
    },
    "mailOptions": {
      "from": "*",
      "to": [
        "*"
      ],
      "subject": "Hello from SendGrid!",
      "text": "This is a test email using SendGrid API in Node.js.",
      "html": "<strong>This is a test email using SendGrid API in Node.js.</strong>",
      "attachments": [
        {
          "filename": "test.txt",
          "content": "VGhpcyBpcyBhdHRhY2htZW50IHRlc3Qu",
          "encoding": "base64"
        },
        {
          "filename": "test1.txt",
          "content": "VGhpcyBpcyBhdHRhY2htZW50IHRlc3Qu",
          "encoding": "base64"
        }
      ]
    }
  }
  ```
  ```json
  {
    "smtpCredentials": {
      "host": "imap.gmail.com",
      "port": 993,
      "secure": true,
      "auth": {
        "user": "*",
        "accessToken": "*",
        "refreshToken": "*",
        "type": "OAuth2"
      }
    },
    "mailOptions": {}
  }
  ```

## Moving emails to trash

- Endpoint: https://d6aljed0n5.execute-api.eu-west-1.amazonaws.com/v1/move-to-trash
- Payload:
  ```json
  {
    "smtpCredentials": {},
    "uid": 2,
    "path": "Sent"
  }
  ```

## Delete email from trash

- Endpoint: https://d6aljed0n5.execute-api.eu-west-1.amazonaws.com/v1/empty-trash
- Payload:
  ```json
  {
    "smtpCredentials": {},
    "uid": 1
  }
  ```
