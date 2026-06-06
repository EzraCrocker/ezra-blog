---
title: 'QUICker than TCP but more reliable than UDP?'
description: 'A beginner-friendly explanation of TCP, UDP, and QUIC, including how they work, where they are used, and why they matter in networking.'
pubDate: 'Jun 6 2026'
heroImage: '../../assets/Fig2_UDPwork.jpg'
---
# TCP vs UDP vs QUIC

TCP, UDP, and QUIC are transport protocols that help applications communicate across networks. They all move data between devices, but they make different tradeoffs around reliability, speed, connection setup, and performance.

Below is a summary but if you would like to read more about these protocols look no further than:

TCP -  https://www.ietf.org/rfc/rfc9293.html

UDP -  https://www.rfc-editor.org/info/rfc768/

QUIC - https://www.rfc-editor.org/rfc/rfc9000.html

## Why Transport Protocols Matter

When two devices communicate, the application usually does not just send raw data directly across the internet. The data has to be packaged, addressed, transmitted, received, checked, and sometimes retransmitted.

That is where transport protocols matter.

TCP, UDP, and QUIC help answer questions like:

- Should the connection be reliable?
- Should lost data be retransmitted?
- Does order matter?
- Is speed more important than guaranteed delivery?
- How much setup should happen before data is sent?
- How should encryption and performance be handled?

## Quick Summary

TCP is reliable and connection-oriented. It is used when data needs to arrive completely and in order.

UDP is lightweight and connectionless. It is used when speed and low overhead matter more than guaranteed delivery.

QUIC is a newer transport protocol built on top of UDP. It adds reliability, encryption, and performance improvements while avoiding some of TCP’s limitations.

## What Is TCP?

TCP stands for Transmission Control Protocol.

TCP is connection-oriented, meaning a connection is established before data is sent. It is designed for reliable communication.

### TCP focuses on:

- Reliability
- Ordered delivery
- Error recovery
- Flow control
- Congestion control

## What Is UDP?

UDP stands for User Datagram Protocol.

UDP is connectionless, meaning it sends data without first establishing a formal connection. It has much less overhead than TCP, but it does not guarantee delivery by itself.

### UDP focuses on:

- Speed
- Low overhead
- Simplicity
- Real-time communication

## What Is QUIC?

QUIC is a modern transport protocol originally developed by Google and later standardized by the IETF.

QUIC runs over UDP, but it adds features that UDP does not provide by itself, including reliability, encryption, stream management, and faster connection setup.

QUIC is most commonly associated with HTTP/3.

## TCP vs UDP vs QUIC Comparison

| Feature | TCP | UDP | QUIC |
|---|---|---|---|
| Connection style | Connection-oriented | Connectionless | Connection-oriented over UDP |
| Reliability | Yes | No, not by default | Yes |
| Ordering | Yes | No | Yes, per stream |
| Speed | More overhead | Low overhead | Faster setup than TCP + TLS |
| Encryption | Usually added with TLS | Not built in | Built in with TLS 1.3 |
| Common use cases | HTTPS, SSH, email, file transfers | DNS, DHCP, VoIP, gaming, streaming | HTTP/3, modern web apps, low-latency web traffic |

## Why TCP Is Still Important

TCP is still widely used because it is reliable and mature. Many applications depend on TCP because they need data to arrive completely and in the correct order.

Examples include:

- Web browsing with HTTP/1.1 and HTTP/2
- SSH
- Email
- File transfers
- Database connections

## Why UDP Is Still Important

UDP is useful when speed matters more than perfect reliability.

Examples include:

- DNS
- DHCP
- VoIP
- Video streaming
- Online gaming

With UDP, the application can decide how much reliability it actually needs.

## Why QUIC Exists

QUIC exists because the modern internet needed something faster and more flexible than traditional TCP plus TLS.

QUIC improves connection setup time, handles packet loss better across multiple streams, and includes encryption by default.

## Troubleshooting Perspective

From a troubleshooting perspective, knowing the transport protocol helps narrow down the problem.

If an application uses TCP, I would think about:

- Is the TCP handshake completing?
- Is the port open?
- Is a firewall blocking the connection?
- Are packets being retransmitted?
- Is TLS negotiation failing after TCP connects?

If an application uses UDP, I would think about:

- Is the destination port reachable?
- Is a firewall silently dropping traffic?
- Is the application expecting a reply?
- Is packet loss affecting quality?

If an application uses QUIC, I would think about:

- Is UDP allowed through the firewall?
- Is UDP/443 blocked?
- Is the browser falling back to TCP/TLS?
- Is HTTP/3 enabled or disabled?

## My Summary

TCP is best when reliability and ordered delivery matter.

UDP is best when low overhead and real-time performance matter.

QUIC tries to combine the speed benefits of UDP with the reliability, encryption, and connection management expected from modern web traffic.

Understanding all three helps when troubleshooting web performance, DNS, firewalls, packet loss, application behavior, and modern internet traffic.