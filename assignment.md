AB test
=======

## Setup

Players (users) are randomly split in two groups:

- group1 - even loginIDs
- group2 - odd loginIDs

We are testing which is the best time / place to show popup to players asking them to allow push notifications:

- group1 - immediately after the installation (before the first tutorial battle)
- group2 - after the tutorial (which consists of 5 battles)

We are optimizing towards:

- Hit rate (% of players who allow push notifications)
- Player Retention

Test was run for two weeks (14 days). Only players that participated in the test appear in the provided data.

## Data

There are two anonimized files:

- `notification_allowed.csv`
- `user_history.csv`

### notification_allowed.csv
Sent after request popup has been shown and player has answered (closing the app defaults to `false` as an answer).

```
login_id = int, starting from 1
time
allowed_notifications = true / false
date_id = int, starting from 0, measuring days since the start of the test
```

### user_history.csv
Generated at the end of each day. It is sent for every active user and for every payer (all time payer). When 21 days pass after the player has logged in for the last time, player no longer appears in this table. This is not true for payers, as they are eligible to appear in this table no matter how long has passed since the last log in.

```
  login_id = int, starting from 1
  registration_date_id = date_id when a player has joined the game
  registration_channel = Paid/Organic
  registration_country = country of origin of the first session
  payer = player has spent money at any time in the past
  dau = daily active player: 0 or 1 in this table
  sessions_count = daily count of sessions
  playtime = daily total playtime
  last_login_day = date_id of the last login, up to this day
  days_active_last_7_days = number of days user was active, including this day
  cohort_size = 1 for all in this table
  elo_rating = elo (trophie count) at the end of the day
  arena_level = arena level at the end of the day
  gold = gold stash at the end of the day
  runes_stash_class1_tier1 = stash of various currencies
  runes_stash_class2_tier1
  runes_stash_class3_tier1
  runes_stash_tier2
  spell_runes_stash
  hero_dust
  item_dust
  gold_gained_total = stats for various currencies
  gold_bought_total
  gold_spent_total
  runes_gained_total_class1_tier1
  runes_gained_total_class2_tier1
  runes_gained_total_class3_tier1
  runes_gained_total_tier_2
  spell_runes_gained_total
  runes_spent_class1_tier1
  runes_spent_class2_tier1
  runes_spent_class3_tier1
  runes_spent_total_tier2
  spell_runes_spent_total
  hero_dust_spent_total
  hero_dust_gained_total
  tokens
  tokens_gained_total
  enter_queue_count = number of times player has entered PvP queue
  battles_played = daily battles played
  battles_won = daily battles won
  battles_played_total = battles played up to this day
  battles_won_total = battles won up to this day
  heroes_unlocked = heroes unlocked up to this day
  heroes_level = hero stats
  hero_shards = hero stats
  minion_upgrades = number of times user has upgraded minions
  free_chests_opened_total = various chest stats
  silver_chests_opened_total
  golden_chests_opened_total
  magical_chests_opened_total
  victory_chests_opened_total
  pvp_event_small_chest_small
  pvp_event_small_chest_medium
  pvp_event_small_chest_large
  pvp_event_big_chest_small
  pvp_event_big_chest_medium
  pvp_event_big_chest_large
  cards_gained_total = various card stats
  minion_cards_gained_common_total
  minion_cards_gained_rare_total
  minion_cards_gained_epic_total
  minion_cards_gained_legendary_total
  spell_cards_gained_common_total
  spell_cards_gained_rare_total
  spell_cards_gained_epic_total
  spell_cards_gained_legendary_total
  campaign_tickets = various campaign stats
  max_campaign_level
  equipment_bonus
  campaign_battles
  campaign_battles_total
  event_battles = various live event stats
  event_battles_total
  event_tokens
  group_points
  lives_spent
  milestone_points
  date_id = int, starting from 0, measuring days since the start of the test
```
