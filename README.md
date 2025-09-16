# 📦 openmp-query Module

A simple and efficient Node.js module that fetch data from the openmp client

---

## 🚀 Installation
Install via **npm** (recommended):
```bash
npm i openmp-query
```

## 🛠️ Usage Example
```js
import OpenQuery from 'openmp-query';

const main = async () => {
    OpenQuery({ host: "51.79.xx.xx", port: 7777, timeout: 1500 }, (err, data) => {
        if (err) {
            console.error("❌ Failed to query server:", err);
            return;
        }

        console.log("✅ Server is online!");
        console.log(`📍 Address: ${data.address}:${data.port}`);
        console.log(`🏷️ Hostname: ${data.hostname}`);
        console.log(`🎮 Gamemode: ${data.gamemode}`);
        console.log(`🗣️ Language: ${data.language}`);
        console.log(`🔑 Passworded: ${data.passworded ? "Yes" : "No"}`);
        console.log(`👥 Players: ${data.online}/${data.maxplayers}`);
        console.log("⚙️ Rules:", data.rules);

        if (data.players.length > 0) {
            console.log("👤 Players online:");
            data.players.forEach(player => {
                console.log(`- ${player.name} (Score: ${player.score}, Ping: ${player.ping})`);
            });
        }
    });
};

main();
```

## API
| Property     | Type      | Description                                                                       |
| ------------ | --------- | --------------------------------------------------------------------------------- |
| `address`    | `string`  | Queried server address.                                                           |
| `port`       | `number`  | Server port.                                                                      |
| `hostname`   | `string`  | Server hostname.                                                                  |
| `gamemode`   | `string`  | Running gamemode.                                                                 |
| `language`   | `string`  | Server language (if available).                                                   |
| `passworded` | `boolean` | Whether the server is password-protected.                                         |
| `maxplayers` | `number`  | Maximum player slots available.                                                   |
| `online`     | `number`  | Current online players.                                                           |
| `rules`      | `object`  | Key-value object containing server rules (`mapname`, `lagcomp`, `version`, etc.). |
| `players`    | `array`   | Array of connected players (empty if more than 100 players online).               |

