- [ng2-stompjs](https://github.com/stomp-js/ng2-stompjs) is a [stompjs](https://github.com/stomp-js/stompjs) wrapped as an Angular service.
    - ng2-stompjs [documentation](https://stomp-js.github.io/ng2-stompjs/)
    - stompjs [documentation](https://stomp-js.github.io/stompjs/)
- The Angular service is called [StompService](https://stomp-js.github.io/ng2-stompjs/injectables/StompService.html) or [StompRService](https://stomp-js.github.io/ng2-stompjs/injectables/StompRService.html)
- To send a message: [`StompService.publish(queueName: string, message: string, headers: Object)`](https://stomp-js.github.io/ng2-stompjs/injectables/StompRService.html#publish)
- To subscribe to a queue: [`StompService.subscribe(queueName: string, headers: Object)`](https://stomp-js.github.io/ng2-stompjs/injectables/StompRService.html#subscribe)
- To specify the properties of a queue (if it will be created or if it already exists): specify the following properties in the `headers` object: `durable`, `auto-delete`, `exclusive`. For example:

    ~~~json
    {durable: false, 'auto-delete': true, exclusive: true}
    ~~~

    The default, if nothing is specified is: `durable: true, 'auto-delete': false, exclusive: false`.

    The properties in effect (explicitely defined or the implicit defaults) *must* match the properties of the existing queue, if the queue already exists.

- To include a custom header in the message, just include it in the `headers` object:

    ~~~json
    {'my-custom-header': 'Hello World'}
    ~~~

- To specify the correlation ID of the message, include the `correlation-id` property in the `headers` object:

    ~~~json
    {'correlation-id': 12345}
    ~~~

- When you receive a message, the headers object is in `Message.headers`. The body is in `Message.body`.
- To specify the "reply to" queue, include the `reply-to` property in the `headers` object:

    ~~~json
    {'reply-to': 'my-reply-queue'}
    ~~~

