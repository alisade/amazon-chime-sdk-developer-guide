# Creating an attendee<a name="create-attendee"></a>

After you create a meeting, you create an attendee resource that represents each user trying to join the media session\. The CreateAttendee API takes in the following: 
+ The MeetingId of the meeting to which you're adding the user\.
+ An ExternalUserId, which can be any opaque user identifier from your identity system\. 

For example, if you use Active Directory \(AD\), this can be the Object Id of the user in the AD\. The ExternalUserId is valuable as it is passed back to the client applications when they receive attendee events from the client SDKs\. This allows the client application to know who joined or left the meeting and retrieve additional information from the server application about that user, such as a display name, email, or a picture\.

The response to the CreateAttendee API is an Attendee object\. The object contains a unique AttendeeId that is generated by the service, the ExternalUserId that was passed in, and a signed JoinToken that allows the attendee to access the meeting for its duration, or until the DeleteAttendee API deletes the attendee\.

```
    attendee = await chime.createAttendee({
                MeetingId: meeting.MeetingId,
                ExternalUserId: externalUserId,
              }).promise();
```