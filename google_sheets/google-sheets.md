# Apps scripts

## Increment date in google sheets

[gist](https://gist.github.com/kukinpower/51d22d60a1db8aa0a19558b5abb07285)

```js
function plusDay(zeroDate) {
  var shet = SpreadsheetApp.getActiveSheet()
  var date = new Date(zeroDate)

  var maxRaw = 10
  var maxCol = 10

  for (var raw = 1; raw <= maxRaw; raw++) {
    for (var col = 1; col <= maxCol; col++) {
      shet.getRange(raw,col).setValue(date)
      date.setDate(date.getDate() + 1);
    }
  }
}

function onOpen() {
  var ui = SpreadsheetApp.getUi();
  ui.createMenu('Custom Menu')
      .addItem('plusDay()', 'showPrompt')
      .addToUi();
}

function showPrompt() {
  var ui = SpreadsheetApp.getUi()

  var result = ui.prompt(
      'Enter zero date in format mm/dd/yyyy:',
      ui.ButtonSet.OK_CANCEL)

  var button = result.getSelectedButton();
  var date = result.getResponseText();
  if (button == ui.Button.OK) {
    // User clicked "OK".
    plusDay(date)
  } else if (button == ui.Button.CANCEL) {
    // User clicked "Cancel".
    ui.alert('I didn\'t get your date.');
  } else if (button == ui.Button.CLOSE) {
    // User clicked X in the title bar.
    ui.alert('You closed the dialog.');
  }
}
```
