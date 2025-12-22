# Events

TODO: finish/revise page

Use Events when you want to communicate that something happened. 
e.g.
* temperature is within X range again,
* we have data!

sidenote: TCP and UDP
* TCP: is a guaranteed delivery, guaranteed order (most computers, places wehere you can't afford to lose data). must be always one to one. has a handshake, plus various acknowledgements that go back and forth.
* UDP: guaranteed nothing, but fast (video streaming, gaming, places where losing data doesn't matter). often one to one, but can do one to many (multicast, which means you can just send it out and whoever is listening can have it)


MDSplus events mostly use UDP beacuse Events don't (shouldn't) contain data, although technically they can be either TCP or UDP
Anything can create an event and anything can listen for an event. E.g., a device might have an event saying "I'm done"

Whatever you do with the knowledge from the event is up to you.
Whatever made you decide to send the event is also up to you. 

Events are different from a state machine which deals in concrete hard stops. 
Events are mostly useful for updating scopes and not much else.