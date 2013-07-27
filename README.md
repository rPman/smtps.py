smtps.py - A Python SMTP Server. Listens on a socket for RFC821
messages. As each message is processed, methods on the class
SMTPServerInterface are called. Applications should sub-class this and
specialize the methods to suit. The default implementation does
nothing. 

The usage pattern is to subclass SMTPServerInterface, overriding
methods as appropriate to the application. An instance of this
subclass should be passed to the SMTPServer object, and then the
SMTPServer.serve method should be called. This blocks forever, serving
the given port. See the __main__ code below for an example.

The SMTPServerInterface subclass should keep state information such as
the FROM: and RCPT TO: addresses. The 'SMTPServerInterface.data' is
called when the complete RFC821 data messages has been received. The
application can then do what it likes with the message.

A couple of helper functions are defined that manipulate from & to
addresses. 

Usage: python smtps.py [port].
    Where 'port' is SMTP port number, 25 by default.
Each received mail saved to own file named <microtime>.json.pymail with json serialized array {body:'',from:'',to:''}
