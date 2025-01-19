#OIC #Integration #Patterns #Pub-Sub #Oracle 

## Create Integrations to Publish and Subscribe to Oracle Integration

You can create integrations that enable you to publish messages to Oracle Integration. and integrations that enable you to subscribe to messages from Oracle Integration.

Topics:

Note:

**The integration styles to publish messages to Oracle Integration and to subscribe to messages from Oracle Integration have been deprecated.**

-   For the **publish** messages to Oracle Integration style, Oracle recommends that you create an app driven orchestration integration and use an invoke to publish a message into the Oracle Cloud Infrastructure streaming service.
-   For the **subscribe** to messages from Oracle Integration style, Oracle recommends that you either use an app driven orchestration integration with a trigger or a scheduled orchestration integration with a poll to retrieve published messages from the Oracle Cloud Infrastructure streaming service.