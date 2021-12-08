# Network configuration<a name="network-config"></a>

When you integrate the Amazon Chime SDK into your client application, the SDK connects to the Amazon Chime service to send and receive audio, video, content sharing, and data messages\. If your users' network blocks traffic to the Amazon Chime service, their ability to use the service will be impaired\. Network administrators can use this information to reconfigure their network to allow access to the Amazon Chime service\.

**Topics**
+ [Configuring for media and signaling](#media-signaling)
+ [Configuring for Amazon Voice Focus](#voice-focus)
+ [Configuring for background blur](#config-blur)
+ [Configuring browser content security policies](#configure-browser-policy)

## Configuring for media and signaling<a name="media-signaling"></a>

Amazon Chime SDK audio, video, and content use User Datagram Protocol \(UDP\) transport whenever possible\. If UDP is blocked, the Amazon Chime SDK tries to establish a Transport Layer Security \(TLS\) connection for bidirectional media transport\. Amazon Chime SDK signaling and data messages use Transmission Control Protocol \(TCP\) and WebSocket connections\.

The following diagram shows a typical network with an application that runs the Amazon Chime SDK\. 

![\[A network configured to run an Amazon Chime SDK application, with two-way communication between the SDK and a meeting.\]](http://docs.aws.amazon.com/chime/latest/dg/images/net-config-diagram.png)

The Amazon Chime SDK uses the following destinations and ports for media and signaling\.


| Domain | Subnet | Ports | 
| --- | --- | --- | 
| \*\.chime\.aws | 99\.77\.128\.0/18 | TCP:443 UDP:3478 | 

This subnet is the `CHIME_MEETINGS` service in the AWS [IP address ranges](https://docs.aws.amazon.com/general/latest/gr/aws-ip-ranges.html)\.

## Configuring for Amazon Voice Focus<a name="voice-focus"></a>

The Amazon Chime SDKs for iOS and Android include the Amazon Voice Focus module\. The Amazon Chime SDK for Javascript downloads the Amazon Voice Focus module from Amazon CloudFront\.

Amazon Voice Focus uses the following destinations and ports\.


| Domain | Ports | 
| --- | --- | 
| \*\.sdkassets\.chime\.aws | TCP:443 | 

This subnet is the `CLOUDFRONT` service in the AWS [IP address ranges](https://docs.aws.amazon.com/general/latest/gr/aws-ip-ranges.html)\.

## Configuring for background blur<a name="config-blur"></a>

The Amazon Chime SDK for Javascript downloads the background blur module from Amazon CloudFront\.

Background blur uses the following destinations and ports\.


| Domain | Ports | 
| --- | --- | 
| \*\.sdkassets\.chime\.aws | TCP:443 | 

This subnet is the `CLOUDFRONT` service in the AWS [IP address ranges](https://docs.aws.amazon.com/general/latest/gr/aws-ip-ranges.html)\.

## Configuring browser content security policies<a name="configure-browser-policy"></a>

When you build an application with the Amazon Chime SDK for Javascript, you need to configure the browser content security policies in your application\. For more information, refer to the [Content Security Policy Guide](https://aws.github.io/amazon-chime-sdk-js/modules/contentsecurity_policy.html) on GitHub\. 