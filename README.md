# Family Game Night

A set of party games for family and friends, played remotely, each person on their own phone. No app to install and no accounts: open the page, start a room, share the code.

**Play it:** https://ajokukk.github.io/family-game-night/

## Games

| Game | Players | What it is |
|---|---|---|
| **Rebus Challenge** | 2+ | Decode picture puzzles into a phrase. Faster guesses score more. |
| **Imposter** | 3+ | Everyone gets the same secret word except one person. Find the imposter. |
| **Person on the Forehead** | 2+ | Guess who you are with yes/no questions. Everyone else can see your name. |
| **Guess the Flag** | 2+ | Pick the right country for each flag. |
| **Name, Animal, Place, Thing, Food** | 2+ | Fill the categories for a letter before time runs out. |
| **Whot** | 2+ | The Nigerian card game. The host chooses which action cards are active. |
| **Ludo** | 2–4 | Race four tokens home. Roll a 6 to come out. |
| **Lagos Landlords** | 2–6 | A Monopoly-style property game on a board of Lagos areas. |
| **Ayo Olopon** | 2, 3, 4, 6 or 12 | The traditional Yoruba seed game, also known as Nchoro, Awele and Nacho. |

Whot, Ludo, Lagos Landlords and Ayo can be played against **computer players** (Easy, Medium or Hard). The host sets this on the game list. The party games need real people.

Coins carry across games in a session, and the host can switch games without anyone leaving the room.

## How to play

1. One person opens the page, enters a name and taps **Start a new room**.
2. They share the room code (or tap **Send on WhatsApp**).
3. Everyone else opens the same page, enters a name, and taps **Join room** with the code.
4. The host picks a game. The in-app **Help** page has the rules for each game.

## Ayo rules as implemented

- 12 pits, 4 seeds each, shared equally between players. Seeds are sown counter-clockwise.
- A turn is a chain of runs. Look at where your last seed lands:
  - in an empty pit: your turn ends;
  - in a pit that now holds exactly 4: you take those 4 seeds and your turn ends;
  - in any other pit with seeds: pick up everything in it (even an opponent's) and sow again.
- A pit that fills to 4 in the middle of a run is taken by its owner.
- 25 seeds wins outright. Otherwise the most captured seeds wins.

Rules differ between regions and households, so these may not match how your family plays.

## Run or host it yourself

The whole game is one file: `index.html`. No build step and no dependencies to install.

**GitHub Pages:** put `index.html` in the root of a repository, then go to *Settings → Pages*, choose *Deploy from a branch*, pick `main` and `/ (root)`, and save. The site appears at `https://<username>.github.io/<repository>/`.

Any static host works too (Netlify Drop, Cloudflare Pages, and so on). The page must be served over **HTTPS**, because it uses secure WebSockets.

## How it works

- **Single file.** HTML, CSS and JavaScript are inline, and the MQTT client library is bundled in.
- **Realtime.** Players connect through free public MQTT brokers over secure WebSockets. The room code selects the broker, and the app falls back to another one if a broker is down.
- **Host-authoritative.** The host's browser runs the game and holds private information (Whot hands, the imposter's word). Other players send their moves and receive the public state. Private data goes only to the player it belongs to.
- **Computer players** run in the host's browser and play through the same moves as people.
- Sound and vibration can be turned off in **Settings**.

## Known limitations

- Public brokers are free and not guaranteed. If a room will not open, try again.
- The host's browser must stay open. If the host leaves, the room ends.
- Reloading the page mid-round loses that player's private cards or state for the round. They can rejoin the room.
- Room messages are not encrypted or authenticated. Do not use the game for anything sensitive, and keep the room code among people you trust.
- The Rebus Challenge currently uses placeholder puzzles.

## Contributing

Ideas and puzzles are welcome. Rebus puzzles need an image or description, the answer, and any accepted alternate answers.

## License

Add a license of your choice before sharing the code publicly (for example MIT).
