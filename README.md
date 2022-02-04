# Wordle Open Rrecovery Data System ("WORDS")
## An open standard schema for importing and exporting Wordle state

With the proliferation of Wordle clones out there, the industry *deparately* needs an open standard schema for data interchange among them. Wordle lock-in is real, and we deserve the right of data sovereignty of our guess distribution and active win streak.

![image](https://user-images.githubusercontent.com/11475352/152610450-07eedc13-a4b9-4733-a277-df3e4fdb6ad6.png)

A reference implementation is included to demonstrate how to import and export this precious user state.

![image](https://user-images.githubusercontent.com/11475352/152611186-1c14578f-ee99-4db6-b67c-69b5e7e3e2e3.png)


## Notes to implementors of _state export_

Several of the fields in the WORDS format SHOULD be derived from user input, and not requested from users directly. These are:

- Games won (SHOULD be derived from the guess distribution that users provide)
- Games lost (SHOULD be derived from "games played" minus "games won")
- Average guesses (SHOULD be derived from the guess distribution that users provide)

## Notes to implementors of _state import_

The WORDS data format should be imported into the `statistics` local storage item. After import, the `gameState` local storage item MUST be updated to retain user state by setting the `lastCompletedTs` and `lastPlayedTs` to the previous date. A reference implementation is included.
