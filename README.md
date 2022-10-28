# E-wallet
## Description
- This is a digital wallet which stores all credit cards. One can check one's cards and can add new cards.
- This is a Single Page Application(SPA) developed in Javacript using Vue framework.

- There are two Views: Home and Add card.
 ### Home
  - The card at the top is the active card.
  - When clicking on a card in the list, it is shown as the active card at the top of the view.
  - When clicking on Add new card, the AddCard page is displayed.
  - The AddCard view has a form that is reflected in a preview of how the card would look.
  - Each new card that is added is appeared in a list in this view.

 ### Add Card
  - A new card can be added with the following information:<br />
   { <br />
    vendor,<br />
    cardNumber,<br />
    cardholder, <br />
    expireMonth, <br />
    expireYear, <br />
    CCV<br />
  }


## Technical Specifications
 - Saves the cards and all new cards that are added in local storage as well as read from local storage
 - Removes a card with a confirmation dialog
 - The fields when a card is added are validated so that one can only enter numbers in the card number field and the maximum is 16 numbers. The name field only takes letters.
- Validates so one cannot add two cards with the same number


## Project setup
```
npm install
```
