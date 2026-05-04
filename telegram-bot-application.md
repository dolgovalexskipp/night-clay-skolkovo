# Telegram bot application flow

## Goal
Collect an application for Skolkovo Night Clay League with the minimum amount of manual back-and-forth.

## Flow
1. Ask whether the player comes with a ready partner.
   - Buttons: `Да, пара готова` / `Пока ищу`
2. Collect name and surname of the first player.
3. Collect name and surname of the partner.
   - If there is no partner yet, mark the application as `need_pair` and continue collecting the first player data.
4. Collect Telegram contact for both players.
5. Ask for pair rating or current playing level.
6. Ask who plays first number and who plays second number.
7. Ask for hand and profile.
   - Right / left hand
   - Stronger side
8. Ask about tennis background and schedule fit.
   - Years of play
   - Short style note
   - Tuesday / Thursday 20:00-22:00 availability
9. Final confirmation: ready to join the season and receive organizer follow-up.

## Branches
- If a player does not have a partner yet, collect the player details and mark the application as `need_pair`.
- If the pair rating is outside the target range, collect the application anyway and flag it for manual review.
- If availability does not fit the schedule, mark it as `needs_schedule_check`.
- If the pair is ready, create the application card for the organizer and send a success confirmation.

## Organizer handoff
- Send the pair name, player contacts, rating, role split, availability, and notes in one compact summary.
- Keep a short status field: `new`, `review`, `approved`, `waitlist`, `need_pair`.
- Add a clear next action:
  - `approve`
  - `hold`
  - `find partner`
  - `schedule check`

## Tone
- Short, clear, specific.
- No marketing copy inside the bot.
- No long explanations before the user has answered the core questions.

## Suggested bot message format
- One question per message.
- One primary action per screen.
- Short helper line under the question.
- Keep answer buttons where possible instead of long free text.

## Example screens
1. `Вы заходите с партнером?`
2. `Ваши имя и фамилия`
3. `Имя и фамилия партнера`
4. `Какой у вас рейтинг пары?`
5. `Кто играет первым номером?`
6. `Правша / левша и сильная сторона`
7. `Сколько лет вы играете и какой у вас стиль?`
8. `Сможете играть по вт / чт 20:00-22:00?`
