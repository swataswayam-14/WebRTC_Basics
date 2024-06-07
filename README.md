# WebRTC Basics


## Introduction

### WebRTC (Web Real-Time Communication) is a set of APIs and protocols for real-time communication over peer-to-peer connections. This repository provides a basic implementation of WebRTC using a WebSocket signaling server and React frontend components for sender and receiver.

## Overview

### The repository includes:
1. backend (signaling server): A WebSocket server that caches two WebSocket instances for two parties to communicate.
2. frontend: A React application with two components, Sender and Receiver, that establish a peer-to-peer connection using WebRTC.

## Components

### Sender
 - Creates an RTCPeerConnection: This establishes a connection object for communication.

 - Creates an offer: The sender initiates the connection by generating an offer that specifies its capabilities. 

 - Sets the local description to the offer: This informs the browser about the sender's proposed connection details.

 - Sends the offer to the other side through the signaling server: The offer is sent via a separate signaling channel (not WebRTC itself) to the receiver. This signaling server can be implemented using WebSockets or other protocols. Here it is implemented using WebSockets.

 - Receives the answer from the other side through the signaling server: The receiver responds with an answer that confirms or modifies the offer based on its capabilities.

 - Sets the remote description to the answer: The sender updates its connection details based on the receiver's answer.


### Receiver
 - Receives the offer from the other side through the signaling server: The receiver gets the offer sent by the sender.

 - Sets the remote description to the offer: The receiver informs its browser about the sender's proposed connection details.

 - Creates an answer: The receiver generates an answer that accepts or modifies the offer.

 - Sets the local description to the answer: The receiver updates its connection details based on its own answer.

 - Sends the answer to the other side through the signaling server: The answer is sent back to the sender via the signaling server.

 - Receives the media (video and audio) from the other side: Once the connection is established, the receiver starts receiving the media stream from the sender.