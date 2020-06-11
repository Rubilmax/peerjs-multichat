# peerjs-multichat

Secure, persistent, almost serverless, one-page real-time chat proof-of-concept, built in under 3 hours using WebRTC, PeerJS, Vue and javascript cookies!

Use this project to securely chat with your friends, in real-time.

## Installation

Simply download [index.html](./index.html) and open it with a decent (javascript-enabled) recent browser!

# The challenge

Today's internet infrastructures rely almost every time on data centers, which have a **cost** and an **environmental impact**. To be more specific, [data centers are responsible for approx. 4% of the world's energy consumption](https://data-economy.com/data-centres-world-will-consume-1-5-earths-power-2025/) (and growing). But how would you do your day without your daily binge-watching on demand?

The goal of this project is to simplify and demonstrate the *power, security* and *persistency* of serverless data exchanges. Here is the complete list of features:
- Basic chat application with usernames
- Any user must be able to join any other user (in chat rooms)
- **Security:** data exchanges must be encrypted
- **Persistency:** data must be saved throught sessions (username, chat)
- **Serverless:** data must be exchanged between peers without the need of a server
- **Simplicity:** anyone must be able to use this project without knowledge of anything

# The solution

I've designed the most simple solution to fulfill the previous requirements, using:
- [*WebRTC*](https://webrtc.org/), for secure, reliable and serverless data exchanges
- [*Vue.js*](https://vuejs.org/), for fast & light-weight dynamic rendering & state management
- [*PeerJS*](https://peerjs.com), for development simplicity over WebRTC
- [*MaterializeCSS*](https://materializecss.com/), for fast & modern design
- [*JavaScript localStorage*](https://developer.mozilla.org/en-US/docs/Web/API/Window/localStorage), for data persistency

WebRTC is the Google's open-source base for peer communication in-the-browser, using [QUIC protocol](https://en.wikipedia.org/wiki/QUIC) (the most recent, fast & reliable [transport layer](https://en.wikipedia.org/wiki/Transport_layer) [network protocol](https://en.wikipedia.org/wiki/Network_protocol)). It's supported by almost every decent browser and provides a way to establish data channels between peers supporting any type of data, including real-time audio and video.

PeerJS provides a way to conect the client the a server's endpoint, waiting for peer connections from other clients. Once a connection's established, both peers communicate over WebRTC data channels from which only them can read/write.

## Why is this solution a great proof of concept?

The strength of this solution is in its simplicity and security:
- Any user can log in with a username and join any other friend it knows
- Any user has a complete access to its chat history
- Data exchanges are fully encrypted and cannot be interpreted by a man-in-the-middle (see [A Study of WebRTC Security](https://webrtc-security.github.io/) for more information)

## Why is this solution **only** a proof of concept?

Many aspects are still to be discussed and thought again:
- You wouldn't use an application which stores data as javascript cookies!
- A server is still needed to establish a peer connection (see [WebRTC: the ICE Framework, STUN and TURN Servers](https://levelup.gitconnected.com/webrtc-the-ice-framework-stun-and-turn-servers-10b2972483bb) to learn more about the why). In our case, we use a high-level PeerJS signaling server by default, in comparison with a low-level STUN server (which we could use, with more low-level code)
- Data exchanged is only read and written by peers, which is why this solution is not suitable for exchanging (for example) gaming data (any user could cheat!)