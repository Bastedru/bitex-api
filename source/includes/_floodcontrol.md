# Flood control system

<aside class="warning">
Websocket API and web terminal have joint list of blocked IPs
</aside>

### Principle of operation

> Example of the response message of the flood control system:

```javascript
// 400 - GeneralError message, 23 - FloodControl error code
[400,[23]]
```

The client has 100 points, which can be used to send messages to the server. Each sent message reduces them by 1. Points are restored, 1 point every 600 ms.
The developer on his side should implement a flood control system and ensure that the number of points does not reach 0.

<aside class="notice">
Adding, moving and cancelling a batch of orders is counted for 1 point
</aside>

### Penalties

If the points of the flood control system have dropped below 0, the developer will receive a message 400 (GeneralError) with error code 23 (FloodControl) on every sended message. If points dropped below -10 then the connection will forcibly terminate. 
If the flood control system terminate connection 3 times in an hour, the client will be blocked by the IP address for 1 hour. In the event that the flood control system is terminate connection 6 times in 24 hours, the client will be blocked by the IP on 24 hours.
