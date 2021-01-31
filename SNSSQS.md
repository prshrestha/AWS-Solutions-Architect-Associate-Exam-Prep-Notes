## MQ/SQS/SNS

### MQ
- Fully managed
- Used to migrate existing message broker (on premise) to cloud
- Supports existing protocols

*******************************************
### SQS
- Serverless
- Use for queuing when you start new application
- can use between two AWS services or between AWS and on premise services
- by default SQS doesn’t do FIFO; have to set it to FIFO if you want it
- SQS doesn’t guarantee only one time delivery
- default visibility timeout - 30 sec
- default retention - 4 days
- max retention - 14 days
- delay queue - postpone the delivery of new messages to a queue for a number of seconds

*******************************************
### SNS
- Fanout notification system to send sms or email as a notification

*******************************************