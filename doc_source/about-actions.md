# Understanding actions<a name="about-actions"></a>

In the PSTN Audio service, SIP media applications trigger AWS Lambda functions\. In turn, the AWS Lambda functions can return a list of instructions known as *actions*\. An action is an item that you want to run on a leg of a phone call, such as sending or receiving digits, joining a meeting, and so on\. Actions can also return data, so you can think of actions as objects with data fields\. For more information about the actions invoked by the PSTN Audio service, see [Understanding telephony events](pstn-invocations.md)\.