When Oracle Cloud Infrastructure (OCI) Queue was launched in December 2022, we focused on demonstrating the OCI native features available because it allowed us to show all the features through its APIs. While [product documentation](https://docs.oracle.com/en-us/iaas/Content/queue/messages-stomp.htm) addressed the OCI API and open standards support, referenceable example code showing how to use OCI Queue with a vendor and language-agnostic protocol was limited. Now, we have addressed this limitation.

## OCI Queue with Stomp open standard

From its launch, OCI Queue, like many other messaging products such as ActiveMQ and RabbitMQ, supports the open protocol [Stomp](https://stomp.github.io/). Simple (or streaming) text-oriented messaging protocol (Stomp)  is a mature, proven standard that’s widely supported with not just server implementations but client libraries across a broad range of languages. Here are a some of the Stomp implementations:

-   Java: [Vertx](https://vertx.io/docs/vertx-stomp/java/), [Spring](https://docs.spring.io/spring-integration/reference/html/stomp.html)
-   Python: [stomp.py](https://pypi.org/project/stomp.py/), [stomp\_ws\_py](https://github.com/GlassyWing/stomp_ws_py)
-   Node.js: [Stomp JS](https://stomp-js.github.io/stomp-websocket/codo/extra/docs-src/Usage.md.html), [node-stomp-client](https://github.com/easternbloc/node-stomp-client)
-   C/C++: [ActiveMQ CMS](https://activemq.apache.org/components/cms/documentation), [c-stomp](https://github.com/Taymindis/c-stomp), [libstomp](https://github.com/getCUJO/libstomp)
-   .Net: [Stomp.Net](https://github.com/DaveSenn/Stomp.Net)

The [Stomp website](https://stomp.github.io/implementations.html) lists other options available. Stomp’s simplicity comes from defining a way of using WebSockets, as defined by [RFC 6455](https://www.rfc-editor.org/rfc/rfc6455), and is recognized by the IANA WebSockets [subprotocol registry](https://www.iana.org/assignments/websocket/websocket.xhtml). The use of WebSockets means that no unnecessary demands are placed on network configurations because it resides on HTTP/S traffic, which can be easily secured and managed.

The use of WebSockets means that, with being an open standard and portable, it has performance benefits over standard web services. For example, non-socket-based APIs, such as REST perform a handshake on every call to authenticate and negotiate the use of the security layer, such as encryption algorithms. Web sockets only perform this during the initial connection, and all subsequent data flows are transmitted on the opened connection.

In our extension of the OCI Queue demo to show the use of Stomp, we used the [Vertx Stomp](https://vertx.io/docs/vertx-stomp/java/) client to connect and send and receive  messages. with only a few statements, such as the following example:

Copied to Clipboard

Error: Could not Copy

Copied to Clipboard

Error: Could not Copy

```
StompClient.create(Vertx.vertx(),

new StompClientOptions()

            .setHost(props.getProperty(HOSTNAME))

            .setPort(61613)

            .setSsl(true)

            .setLogin(props.getProperty(LOGIN))

            .setPasscode(props.getProperty(BASE64ENCODEDTOKEN));

            options.setTcpKeepAlive(true)))

.connect().onSuccess(connection -> {

    connection.send(props.getProperty(QUEUEOCID),

Buffer.buffer(“my message));

  })));
```

This code fragment represents the most code compact approach rather than the most efficient and maintainable approach. But it conveys the simplicity and elegance of using OCI Queue with portable code.

## Deploying OCI Queue with Infrastructure as Code

While Stomp doesn’t provide all the features of the [OCI REST API](https://docs.oracle.com/en-us/iaas/api/#/en/queue), like creating and destroying queues, you can address these issues programmatically using the [OCI Queue Terraform provider](https://registry.terraform.io/providers/oracle/oci/latest/docs/resources/queue_queue). The following code block provides an example:

Copied to Clipboard

Error: Could not Copy

Copied to Clipboard

Error: Could not Copy

```
resource "oci_queue_queue" "test_queue" {
    #Required
    compartment_id = ocid1.queue.oc1.iad.aaaabbbbcc
    display_name = “test_queue”

    #Optional
    dead_letter_queue_delivery_count = 5 
    retention_in_seconds = 172800 # 2 days
    timeout_in_seconds = 300
    visibility_in_seconds = 60
}
```

As with our code fragment, this code fragment doesn’t reflect Terraform’s best practices, but it does show the potential simplicity.

Because our Stomp example using OCI Queue is an extension of the API-based demo solution, it you can be deploy and run it using the same control script, which sets up all the key control values and dictates behavior. Modify the script to set up the credentials and Queue OCID, and then run the script after Java is installed and the Vertx library is downloaded. The [reference architecture](https://docs.oracle.com/en/solutions/use-oci-queues-api-sdk/index.html) describe the OCI architecture options available, and the [GitHub repository](https://github.com/oracle-devrel/oci-arch-queue-demo) includes all the documentation and source code needed.

## Get started now

For more information about Oracle Cloud Infrastructure Queue, visit the following resources:

-   [Product page](https://www.oracle.com/cloud/cloud-native/queue/)
-   [Product documentation](https://docs.oracle.com/en-us/iaas/Content/queue/)
-   [Architecture Center playbook for OCI Queue](https://docs.oracle.com/en/solutions/use-oci-queues-api-sdk/index.html)
-   [GitHub](https://github.com/oracle-devrel/oci-arch-queue-demo) repository with demo
-   Previous [OCI Queue blogs](http://blogs.oracle.com/cloud-infrastructure/post/announcing-oci-queue) with details of [other capabilities](https://blogs.oracle.com/cloud-infrastructure/post/oci-queue-limited-availability-program)
-   [OCI Queue API](https://docs.oracle.com/en-us/iaas/api/#/en/queue)
-   [Stomp specification](https://stomp.github.io/stomp-specification-1.2.html)
-   [Some of the known Stomp library implementations](https://stomp.github.io/implementations.html)
-   [OCI Terraform](https://registry.terraform.io/providers/oracle/oci/latest/docs/resources/queue_queue) 

![](https://blogs.oracle.com/content/published/api/v1.1/assets/CONT8F8855FD551B43FAA8BC9AFD8462C4E9/Thumbnail?cb=_cache_60c0&format=jpg&channelToken=f7814d202b7d468686f50574164024ec)

#### Philip Wilkins

##### Cloud Developer Evangelist at OCI