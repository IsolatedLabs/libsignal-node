# <div align='center'>libsignal-node</div>

<div align='center'>

Signal protocol implementation for Node.js based on
[libsignal-protocol-javascript](https://github.com/WhisperSystems/libsignal-protocol-javascript).

[![License: GPLv3](https://img.shields.io/badge/License-GPLv3-blue.svg)](LICENSE)
[![Node](https://img.shields.io/badge/node-%3E%3D14.0.0-brightgreen)](package.json)

**Desarrollado por [Isolated Labs](https://github.com/IsolatedLabs)** — Proyectos experimentales y de producción para el público general.

</div>

---

## Overview

A ratcheting forward secrecy protocol that works in synchronous and asynchronous messaging environments. This is the core cryptographic library used by Signal and WhatsApp-like end-to-end encryption.

## PreKeys

This protocol uses a concept called 'PreKeys'. A PreKey is an ECPublicKey and an associated unique ID which are stored together by a server. PreKeys can also be signed.

At install time, clients generate a single signed PreKey, as well as a large list of unsigned PreKeys, and transmit all of them to the server.

## Sessions

Signal Protocol is session-oriented. Clients establish a "session," which is then used for all subsequent encrypt/decrypt operations. There is no need to ever tear down a session once one has been established.

Sessions are established in one of two ways:

1. **PreKeyBundles** — A client that wishes to send a message to a recipient can establish a session by retrieving a PreKeyBundle for that recipient from the server.
2. **PreKeySignalMessages** — A client can receive a PreKeySignalMessage from a recipient and use it to establish a session.

## State

An established session encapsulates a lot of state between two clients. That state is maintained in durable records which need to be kept for the life of the session.

State is kept in the following places:

- **Identity State** — Clients maintain their own identity key pair and identity keys received from others.
- **PreKey State** — Clients maintain their generated PreKeys.
- **Signed PreKey States** — Clients maintain their signed PreKeys.
- **Session State** — Clients maintain established sessions.

## Usage

```javascript
const libsignal = require('libsignal');

// Generate identity key pair
const identityKeyPair = libsignal.keyhelper.generateIdentityKeyPair();

// Generate registration ID
const registrationId = libsignal.keyhelper.generateRegistrationId();

// Create a protocol address
const address = new libsignal.ProtocolAddress('user-id', 1);

// Create a session builder with your storage
const builder = new libsignal.SessionBuilder(storage, address);

// Create a session cipher for encrypting/decrypting
const cipher = new libsignal.SessionCipher(storage, address);
```

## Installation

```bash
npm install @isolatedlabs/libsignal-node
```

---

## Organización

<div align='center'>

| | |
|---|---|
| **Organización** | [Isolated Labs](https://github.com/IsolatedLabs) |
| **Web** | [adoolab.xyz](http://adoolab.xyz) |
| **Email** | isolatedlabs.cn@gmail.com |

</div>

### Creador Principal

<div align='center'>
  <a href='https://github.com/Manuel5906'><img src='https://github.com/Manuel5906.png' width='120' height='120' style='border-radius:50%;border:3px solid gold' alt='Manuel5906'></a>
  <br>
  <strong>Manuel5906</strong>
  <br>
  <em>Fundador & Desarrollador Principal</em>
</div>

### Colaboradores

<div align='center'>
  <a href='https://github.com/thisAdo'><img src='https://github.com/thisAdo.png' width='70' height='70' style='border-radius:50%;border:2px solid #8A2BE2' alt='thisAdo' title='Admin / Developer'></a>
  <a href='https://github.com/Andresv27728'><img src='https://github.com/Andresv27728.png' width='70' height='70' style='border-radius:50%;border:2px solid #555' alt='Andresv27728' title='Developer'></a>
  <a href='https://github.com/SoyMaycol'><img src='https://github.com/SoyMaycol.png' width='70' height='70' style='border-radius:50%;border:2px solid #555' alt='SoyMaycol' title='Developer'></a>
  <a href='https://github.com/picolasYT'><img src='https://github.com/picolasYT.png' width='70' height='70' style='border-radius:50%;border:2px solid #555' alt='picolasYT' title='Developer'></a>
</div>

---

## License

Licensed under the GPLv3: http://www.gnu.org/licenses/gpl-3.0.html

- Copyright 2015-2016 Open Whisper Systems
- Copyright 2017-2018 Forsta Inc
- Copyright 2026 Isolated Labs
