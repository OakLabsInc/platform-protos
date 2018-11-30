# OakOS Platform Protocol Buffers

The `.proto` files in this repo define the services that the OakOS
Platform provides for applications and dashboard functionality. Each
file contains its own documentation for the RPCs that is defines.

When using the Platform, all fields of all messages are required to be
set unless otherwise specified.

The `.proto` files under [google/](google/) are cloned from Google's
official package because certain gRPC clients do not provide them.

See https://docs.zivelo.com for more information about the OakOS
Platform. See https://developers.google.com/protocol-buffers/ for more
about Protocol Buffers (Protobufs).
