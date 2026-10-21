# shinJS

[![GitHub Repo](https://img.shields.io/badge/GitHub-MinatoAka%2FshinJS-181717?logo=github)](https://github.com/MinatoAka/shinJS)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Node.js](https://img.shields.io/badge/Node.js-%3E%3D8.x-43853d?logo=node.js&logoColor=white)](https://nodejs.org/)
[![JavaScript](https://img.shields.io/badge/Language-JavaScript-F7DF1E?logo=javascript&logoColor=black)](https://developer.mozilla.org/docs/Web/JavaScript)

A lightweight Node.js LINE bot client and automation toolkit built for experimenting with LINE messaging features, group management, and custom command handling.

This project is a fork/variant of the original LINE bot implementation and includes custom command logic, poll loop handling, and generated Thrift bindings for LINE services.

## Features

- LINE authentication via QR login or token-based setup
- Long-polling event handling
- Group interaction utilities
- Message and command dispatch system
- Media download/upload helpers
- Instagram and lyrics helper integrations
- Generated Thrift service bindings for LINE APIs

## Requirements

- Node.js >= 8.x
- npm
- LINE account credentials or QR login flow

## Installation

```bash
git clone https://github.com/MinatoAka/shinJS.git
cd shinJS
npm install
```

## Running the bot

```bash
npm start
```

This will execute:

```bash
node ./src/bot.js
```

## Configuration

The project includes a local auth placeholder in `src/bot.js`:

```javascript
const auth = {
  authToken: '',
  certificate: '',
  email: '',
  password: ''
};
```

You can either:

1. Use QR login flow (`src/connect.js` handles this automatically), or
2. Provide `authToken`, `certificate`, or `email` / `password` before starting the client.

## Project structure

```text
.
├── README.md
├── package.json
├── package-lock.json
├── .gitignore
├── .npmignore
├── src/
│   ├── api.js
│   ├── bot.js
│   ├── command.js
│   ├── config.js
│   ├── connect.js
│   ├── main.js
│   ├── pinVerifier.js
│   └── ...
├── curve-thrift/
│   ├── line_types.js
│   ├── AuthService.js
│   ├── BotService.js
│   ├── LineService.js
│   └── ...
├── helpers/
│   ├── instagram.js
│   └── lirik.js
└── download/
```

## How it works

- `src/bot.js` starts the bot session and begins polling for LINE operations.
- `src/connect.js` handles login and establishes the long-poll connection.
- `src/main.js` receives LINE operation events and routes them into command logic.
- `src/command.js` contains message handlers and utility actions such as group cleaning, invitations, media handling, and admin-related commands.
- `curve-thrift/` contains generated service definitions used for LINE protocol communication.

## Notes

This repository is intended for learning, experimentation, and personal bot development. Some parts of the code are highly specific to LINE internals and may require maintenance depending on LINE API changes.

## TODO

- Improve code maintainability and structure
- Clean up old or deprecated logic
- Expand and refactor command handling
- Better documentation for auth and runtime setup

## License

MIT

## Credits

This project is based on and forked from the LINE bot ecosystem with custom modifications for personal experimentation.
