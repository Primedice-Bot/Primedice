We're back again with a new gambling bot.
We're the makers of the [csgodouble/csgopolygon bot](https://github.com/Csdouble-bot/csgodouble), due to the sites getting closed down we have decided to focus on bitcoin gambling bots.
With this bot we guarantee that you'll make profit, this depends on the amount being gambled.

Just like our csgodouble bot, this bot needs you to meet one of the requirements.

## Requirements
Requires [Greasemonkey](http://www.greasespot.net/) on Firefox and [Tampermonkey](http://tampermonkey.net/) on Chrome.

Avoid any bugs by having already deposited some bitcoin.

## [Install](	https://raw.githubusercontent.com/Primedice-Bot/primedice/master/bot.js)

## Site looks like this when bot is installed correctly.

Program interface

![Screenshot](https://i.gyazo.com/0309c776813d575d0738a51b2a95a1fd.png)
![Screenshot](https://i.gyazo.com/106f421b0dd7fe3572b806dcaf5d2aa8.png)


## Is it safe?

Yes, you can use this script/bot and don't worry about Primedice banning you - firstly, they don't really lose anything on you, secondary, checking for such activity is really troublesome.
## About

The script uses martingale to bet your coins, this means that with every lose it doubles bet value, changing it back to base after win. That, in theory, means you always win base value.

#### Why in theory?

In theory, because the situation takes player with infinite wealth (in our case - `coins`). With every lost bet the value is doubled - let's take `1` as base, here is possible scenario, 16 loses in a row:
```
 1 | Value:     1 | Total amount invested:      1 | Result: Lose
 2 | Value:     2 | Total amount invested:      3 | Result: Lose
 3 | Value:     4 | Total amount invested:      7 | Result: Lose
 4 | Value:     8 | Total amount invested:     15 | Result: Lose
...
12 | Value:  2048 | Total amount invested:   4095 | Result: Lose
...
16 | Value: 32768 | Total amount invested:  65535 | Result: Lose
17 | Value: 65536 | Total amount invested: 131071 | Result: Win
```
As you can see, it took `132071` coins just to get base `1` coin back.

#### Does that mean I may lose everything in one unlucky streak?

Yes. That is what I'm trying to say. That also means you will eventually *lose everything* using this algorithm (algorithm, not the script itself, applies to any other script using this system).
To cheer you up a bit I can say that within gambling's very nature lays the possiblity of losing everything. All you can do is to play safe and use only funds you can afford to lose!

#### Why would I play the game if i can lose everything?

Because that doesn't mean you may not earn anything - calculate base value depending on your balance and risk you want to take.

**How to calculate**

``floor(balance / 2^(loses_in_a_row_you_want_to_cover + 1))``

Examples:
```
Balance: 10000
Safety: Medium, want to be safe even if the streak is 8 turns long
Base value: floor(10000/2^9) = 19
```
```
Balance: 250000
Safety: High-medium, want to be safe with 12 turns long streaks
Base value: floor(250000/2^13) = 30
```
```
Balance: 5000000
Safety: High, you are risking a lot of money, you want to be safe with 15 turns long streaks
Base value: floor(5000000/2^16) = 76
```

## Changelog
1.33:

-Bug fixes

1.32:

- Made it works with new address

1.26:

- New bet system - `D'alembert`

1.24:

- Great martingale

1.23:

- Base bet calculation based on given failsafe value


1.22:

- Auto reconnect (without reloading the page!);
- Switched to chat notifications - no longer need to open the console;
- Fixed an issue when the script bets twice right after starting;
- Fixed intervals not being cleared after stopping (backend change);
- Removed an option to bet negative values;


1.2:

- Dark theme


1.18:

- Fixed wrong balance showed in statistics after stopping/aborting betting;
- Better mobile support (didn't I mention that it works on mobile devices as well?), but it's still on dev stages.;


1.16:

- Bet statistics;
- It stops at given balance limit, in other words not allow you to lose everything, depending on settings it may stop betting at all or start at base value;
- Automatically calculates safe base value for you (I still recommend calculating it on your own );
- Bugfixes
