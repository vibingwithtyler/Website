<span class="ai-badge">Written with AI</span>

# Clue Tracker: A Deduction Engine for the Board Game Clue

If you've ever played Clue and lost track of who showed what card three turns ago, this one's for you.

The [Clue Tracker](https://tylervibes.com/clue-tracker/clue_tracker_v3.html) is a free, browser-based tool that tracks every piece of information revealed during a game of Clue (or Cluedo, if that's your thing) and uses deduction logic to help you figure out who did it, with what weapon, and where.

## Why a Digital Tracker?

The classic Clue detective sheet works, but it has limits. You can mark that a player *showed* you a card, but you can't easily track:

- When a player shows a card in response to someone else's guess, you only know they have *one of* those three cards — but which one?
- When a player *doesn't* show a card, that's information too — they don't have any of those three.
- As the game goes on, earlier ambiguous information can become certain through elimination.

The Clue Tracker handles all of this automatically.

## How It Works

### Setup

1. **Enter player names** and select how many players are in the game.
2. **Pick which player is you** so the tracker knows your perspective.
3. **Select your cards** — the ones dealt to you at the start. The tracker immediately marks these as eliminated from the mystery.

### During the Game

Every time someone makes a guess and another player shows (or doesn't show) a card:

- **Record the guess** — who guessed, what suspect/weapon/room they named, and who showed a card (or if no one did).
- The tracker updates a grid showing what's known about each player and each card.
- Cards are marked as **has** (confirmed), **not** (confirmed they don't have it), or **maybe** (still unknown).

### The Deduction Engine

This is the core of the tool. The tracker doesn't just record — it *reasons*. Here's what it does behind the scenes:

- **Clause-based logic:** When a player shows a card from a guess of three cards, the tracker stores this as a clause — "Player X has at least one of [Card A, Card B, Card C]." As other information rules out cards, clauses get resolved.
- **Elimination cascading:** When a clause is narrowed to a single possible card, the tracker automatically confirms that player has that card, which can trigger further deductions.
- **Negative inference:** If every player is ruled out for a card, it must be in the envelope — part of the solution.

### Smart Suggestions

The tracker also suggests what you should guess next, based on which guesses would give you the most new information. It considers what's still unknown and recommends guesses that are most likely to resolve open clauses.

## The Full Suite

The Clue Tracker actually comes with several companion tools:

- **[Possibilities Calculator](https://tylervibes.com/clue-tracker/clue_possibilities_v2.html)** — shows all remaining possible solutions and their probabilities
- **[Bluff Analysis](https://tylervibes.com/clue-tracker/clue_bluff_analysis.html)** — detects when players might be strategically showing specific cards
- **[Player Intelligence](https://tylervibes.com/clue-tracker/clue_player_intelligence.html)** — profiles each player's behavior and deduction patterns
- **[Stats & Graphs](https://tylervibes.com/clue-tracker/clue_stats_graph.html)** — visualizes the game state and information flow
- **[Diagnostic Tool](https://tylervibes.com/clue-tracker/clue_diagnostic.html)** — validates game state and catches data entry errors

All of these tools share game state, so you set up once and everything stays in sync.

## Tips for Winning at Clue

- **Pay attention to what OTHER players ask, not just your own turns.** Every guess and response is information, even when it's not your turn.
- **Track who doesn't show.** A player passing on a guess is just as valuable as a player showing a card — it rules out three cards at once.
- **Don't guess cards you already know.** Use your guesses to test cards you're unsure about. The tracker's suggestion system helps with this.
- **Move to rooms strategically.** You have to be in a room to guess it. Plan your movement to rooms you need to test.

## Try It Out

Pull it up on your phone or laptop at your next game night. Free, no sign-up, no download.

**[Open Clue Tracker →](https://tylervibes.com/clue-tracker/clue_tracker_v3.html)**
