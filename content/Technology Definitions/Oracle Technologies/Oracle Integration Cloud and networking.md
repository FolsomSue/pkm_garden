[Léopold Gault](https://fr.linkedin.com/in/leopoldgault/en?trk=article-ssr-frontend-pulse_publisher-author-card) ![Léopold Gault](https://static.licdn.com/aero-v1/sc/h/9c8pery4andzj6ohjkjp54ma2)

### Léopold Gault

#### Cloud solutions architect

Published May 10, 2021

Oracle Integration Cloud (OIC) is a widely used apps-integration PaaS service, that includes enterprise service bus (ESB) features, and business processes automation (BPM) features.

OIC is a managed PaaS service that can interact with both your public and private apps. Thanks to this article, you will understand:

-   How OIC fits in your network topology; allowing it to integrate apps sitting anywhere (on-premises, in 3rd party cloud providers, in the Oracle cloud, or at a public endpoint).
-   Why your network topology will be secure.

## Bird-eye-view of your apps-integration architecture

Let's start by having a bird-eye-view of your architecture for apps-integration.

![Bird eye view of your apps-integration architecture](https://www.linkedin.com//:0)

It will feature:

-   \[In the middle\] Your apps-integration solution: OIC.
-   \[On the right\] The apps that will be integrated by OIC. You will configure your integrations to either be triggered by the scheduler included in OIC; or to be exposed as SOAP or RESTful APIs. In the latter case, those integrations will be triggered by API clients, as shown on the left.
-   \[On the left\] API clients invoking integrations that you have exposed on OIC. Note: I represent API clients with a smiley, but those are machines; not humans.

### Notes about this architecture

Note 1: As I said, not all your integrations will be triggered by API clients: you can configure OIC's scheduler to periodically trigger some of your integrations.

![No alt text provided for this image](https://www.linkedin.com//:0)

Note 2: If you're coming from Azure, AWS or GCP, you may be anxious about the cost of _outbound data transfer_. Don't worry, in the Oracle Cloud, it's virtually free!

![No alt text provided for this image](https://www.linkedin.com//:0)

Note 3: As we'll see in the next section, you can optionally restrict the access to your exposed OIC integrations to only a whitelist of IPs.

![No alt text provided for this image](https://www.linkedin.com//:0)

## OIC and networking

### In a nutshell

-   OIC is hosted at a _public_ URL. By "_public_", I mean that its URL resolves to a public IP.
-   However, you can restrict the access to that URL, by configuring an A_ccess Control List_ (ACL). You will specify in this ACL a whitelist of public IPs (e.g. IPs of NAT Gateways) that are allowed access to your OIC instance. Traffic originating from any other IP will be blocked.
-   Despite sitting outside your VPN, OIC is able to call apps within your private networks, thanks to OIC agents.

![No alt text provided for this image](https://www.linkedin.com//:0)

### Understanding OIC agents

You may be wondering: "_How can OIC invoke apps sitting behind a NAT gateway? This is impossible: servers sitting beyond the NAT Gateway (such as OIC ) are only able to respond to requests originating from the private network; they are never able to initiate the request themselves, and therefore never able to invoke apps sitting behind the NAT Gateway_." And you are right! But here's the trick: OIC agents allow to **simulate** OIC invokes. In reality, the traffic always originates from the OIC agent.

![No alt text provided for this image](https://www.linkedin.com//:0)

Note 1: You can set up several OIC agents, to ensure high availability.

![No alt text provided for this image](https://www.linkedin.com//:0)

Note 2: your OIC agent(s) can be shared by all the apps sitting within your private network.

![No alt text provided for this image](https://www.linkedin.com//:0)

Note 3: Connection information to the target apps is managed centrally in OIC. Your OIC agents don't store any connection information.

![No alt text provided for this image](https://www.linkedin.com//:0)

Note 4: You can host your OIC agents in the Oracle Cloud, instead of deploying them on-premises.

![No alt text provided for this image](https://www.linkedin.com//:0)

If you want your OIC instance to be only accessible from your within VPN, you can write the ACL so as to only whitelist the IP of your Service Gateway.

![No alt text provided for this image](https://www.linkedin.com//:0)

Also, you may be wondering why I have represented 2 VPN gateways on the on-premises side, but I have only represented a single one on the cloud side. That's because the latter is redundant under the hood.

![No alt text provided for this image](https://www.linkedin.com//:0)

Here's how a complete topology would look like, if you'd want OIC to invoke apps located both in the Oracle Cloud, on premises, and on a 3rd party cloud provider:

![No alt text provided for this image](https://www.linkedin.com//:0)

![No alt text provided for this image](https://www.linkedin.com//:0)

Note 5: Just to be clear: OIC agents are only used when OIC invokes an app located in one of your private networks. If instead it is an app (sitting in your private network) that invokes an exposed OIC integration, then OIC agents are by-passed.

![No alt text provided for this image](https://www.linkedin.com//:0)

## Conclusion

Even though your OIC instance will be hosted at a url that resolves to a public IP,

-   You can restrict the access to that url, for only a whitelist of public IPs. If you choose to include in this whitelist only the IPs of your NAT Gateways or Service Gateways, this means that OIC will be accessible only from within your VPN.
-   Even though OIC doesn't sit in a private network, it will be able to invoke apps sitting behind a NAT gateway (thanks to OIC agents).