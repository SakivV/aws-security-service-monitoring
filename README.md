# Monitoring AWS Security Services.
![Alt text](cg-sec-event-monitor.png)

## How it Works.
1. EventRule that get trigger as soon as if any one of the Security services get deactivated/disabled/deleted.

2. Event rule target is Lambda function, that extract details for corresponding event. Details like, username - who disabled service, source ip, timestamp, eventname, eventsource. This will help us in investigation.

3. Once event is processed by Lambda, lambda publish message to SNS.

4. With SNS, depending on subscription (Email, SMS, HTTPs) we will get notified. Here we can cofigure any communication channel thats feasible for us. For this blog and demo, I'm using only Email and OpsGenie.

5. If you want to include more AWS services, update lambda functiong and event rule.