# Core

If you want to write a JVM-based program that sends data to Druid, you can embed Tranquillity directly in your
program as a library. To do this, use one of the three Core APIs:

- *Tranquilizer*, a high-level API where you provide single messages and get a future for each message reporting
success or failure. Tranquilizers handle batching internally.
- *Beam*, a low-level API where you provide a batch of messages and get a future for that batch. You need to handle
batching yourself.

## DruidBeams

To start using the Core APIs, the first thing you need to do is build up a DruidBeams stack. See the
[Configuration documentation](configuration.md) for details.

## Tranquilizer API

Tranquilizers allow you to provide single messages and get a future for each message reporting success or failure.
They are thread-safe and provide batching and backpressure. This API is most appropriate when you want to send several
individual messages, possibly from multiple threads, and receive success or failure information about each message.

For usage documentation, see: http://static.druid.io/tranquility/api/latest/#com.metamx.tranquility.tranquilizer.Tranquilizer

## Beam API

Beams are used internally by Tranquility and are the lowest-level API available. They accept batches of messages and
generally do not do any further batching internally. They also generally do not provide backpressure. This API is most
appropriate when you need full control over how messages are sent.

For usage documentation, see: http://static.druid.io/tranquility/api/latest/#com.metamx.tranquility.beam.Beam

## Examples

- [Java example](https://github.com/druid-io/tranquility/blob/master/core/src/test/java/com/metamx/tranquility/example/JavaExample.java)
- [Scala example](https://github.com/druid-io/tranquility/blob/master/core/src/test/scala/com/metamx/tranquility/example/ScalaExample.scala)
